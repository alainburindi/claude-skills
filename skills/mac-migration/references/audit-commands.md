# Audit Commands — Phase 1

Run these on the **old Mac** to audit the dev environment.

## System Info
```bash
echo "=== System ===" && sw_vers && uname -m && whoami
```

## Homebrew
```bash
echo "=== Homebrew Formulae ===" && brew leaves 2>/dev/null
echo "=== Homebrew Casks ===" && brew list --cask 2>/dev/null
echo "=== Homebrew Taps ===" && brew tap 2>/dev/null
```

## Node
```bash
echo "=== Node ===" && node --version 2>/dev/null || echo "not found"
echo "=== NVM versions ===" && ls ~/.nvm/versions/node 2>/dev/null || echo "nvm not found"
echo "=== fnm versions ===" && fnm list 2>/dev/null || echo "fnm not found"
echo "=== Global npm packages ===" && npm list -g --depth=0 2>/dev/null
echo "=== Bun ===" && bun --version 2>/dev/null || echo "not found"
echo "=== Deno ===" && deno --version 2>/dev/null || echo "not found"
```

## Python
```bash
echo "=== Python ===" && python3 --version 2>/dev/null || echo "not found"
echo "=== pyenv versions ===" && pyenv versions 2>/dev/null || echo "pyenv not found"
echo "=== pip globals ===" && pip3 list 2>/dev/null | grep -v "^Package\|^---"
echo "=== Poetry ===" && poetry --version 2>/dev/null || echo "not found"
echo "=== uv ===" && uv --version 2>/dev/null || echo "not found"
```

## Ruby
```bash
echo "=== Ruby ===" && ruby --version 2>/dev/null || echo "not found"
echo "=== rbenv versions ===" && rbenv versions 2>/dev/null || echo "rbenv not found"
echo "=== rvm versions ===" && rvm list 2>/dev/null || echo "rvm not found"
echo "=== Global gems ===" && gem list --local 2>/dev/null | head -20
```

## PHP
```bash
echo "=== PHP ===" && php --version 2>/dev/null || echo "not found"
echo "=== PHP versions ===" && brew list | grep php 2>/dev/null
echo "=== Composer ===" && composer --version 2>/dev/null || echo "not found"
```

## Go
```bash
echo "=== Go ===" && go version 2>/dev/null || echo "not found"
echo "=== Go binaries ===" && ls ~/go/bin 2>/dev/null || echo "not found"
```

## Rust
```bash
echo "=== Rust ===" && rustc --version 2>/dev/null || echo "not found"
echo "=== Cargo installs ===" && ls ~/.cargo/bin 2>/dev/null || echo "not found"
```

## Java
```bash
echo "=== Java ===" && java --version 2>/dev/null || echo "not found"
echo "=== jenv versions ===" && jenv versions 2>/dev/null || echo "jenv not found"
echo "=== SDKMAN ===" && sdk list java 2>/dev/null | grep installed || echo "not found"
echo "=== Homebrew Java ===" && brew list | grep openjdk 2>/dev/null
```

## Other Languages
```bash
echo "=== Elixir ===" && elixir --version 2>/dev/null || echo "not found"
echo "=== Flutter/Dart ===" && flutter --version 2>/dev/null || echo "not found"
echo "=== Swift ===" && swift --version 2>/dev/null || echo "not found"
echo "=== Kotlin ===" && kotlinc -version 2>/dev/null || echo "not found"
echo "=== R ===" && R --version 2>/dev/null | head -1 || echo "not found"
```

## Databases
```bash
echo "=== PostgreSQL ===" && psql --version 2>/dev/null || echo "not found"
echo "=== MySQL ===" && mysql --version 2>/dev/null || echo "not found"
echo "=== MongoDB ===" && mongod --version 2>/dev/null || echo "not found"
echo "=== Redis ===" && redis-server --version 2>/dev/null || echo "not found"
echo "=== SQLite ===" && sqlite3 --version 2>/dev/null || echo "not found"
echo "=== Running services ===" && brew services list 2>/dev/null
```

## Cloud & DevOps CLIs
```bash
echo "=== AWS ===" && aws --version 2>/dev/null || echo "not found"
echo "=== GCloud ===" && gcloud --version 2>/dev/null | head -1 || echo "not found"
echo "=== Azure ===" && az --version 2>/dev/null | head -1 || echo "not found"
echo "=== Fly.io ===" && flyctl version 2>/dev/null || echo "not found"
echo "=== Heroku ===" && heroku --version 2>/dev/null || echo "not found"
echo "=== Vercel ===" && vercel --version 2>/dev/null || echo "not found"
echo "=== Netlify ===" && netlify --version 2>/dev/null || echo "not found"
echo "=== Stripe ===" && stripe --version 2>/dev/null || echo "not found"
echo "=== Docker ===" && docker --version 2>/dev/null || echo "not found"
echo "=== kubectl ===" && kubectl version --client 2>/dev/null || echo "not found"
echo "=== Helm ===" && helm version 2>/dev/null || echo "not found"
echo "=== Terraform ===" && terraform --version 2>/dev/null || echo "not found"
echo "=== ngrok ===" && ngrok --version 2>/dev/null || echo "not found"
```

## Mobile Dev
```bash
echo "=== Xcode ===" && xcodebuild -version 2>/dev/null || echo "not found"
echo "=== CocoaPods ===" && pod --version 2>/dev/null || echo "not found"
echo "=== Fastlane ===" && fastlane --version 2>/dev/null || echo "not found"
echo "=== Android SDK ===" && echo $ANDROID_HOME
```

## Shell & Dotfiles
```bash
echo "=== Shell ===" && echo $SHELL
echo "=== .zshrc ===" && cat ~/.zshrc 2>/dev/null
echo "=== .zprofile ===" && cat ~/.zprofile 2>/dev/null
echo "=== .gitconfig ===" && cat ~/.gitconfig 2>/dev/null
echo "=== SSH keys ===" && ls ~/.ssh/ 2>/dev/null
```
