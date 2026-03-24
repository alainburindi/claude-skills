# Shell Optimization Reference

## Measuring Startup Time

```bash
# Measure current startup time (run 3 times and average)
time zsh -i -c exit
```

Anything over 500ms is worth optimizing.

## Common Slow Loaders

### NVM (typically adds 300ms-1s)

**Before (slow):**
```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"
```

**After (lazy load):**
```bash
export NVM_DIR="$HOME/.nvm"
node() { unset -f node npm npx nvm && [ -s "$NVM_DIR/nvm.sh" ] && source "$NVM_DIR/nvm.sh" && node "$@"; }
npm()  { unset -f node npm npx nvm && [ -s "$NVM_DIR/nvm.sh" ] && source "$NVM_DIR/nvm.sh" && npm "$@"; }
npx()  { unset -f node npm npx nvm && [ -s "$NVM_DIR/nvm.sh" ] && source "$NVM_DIR/nvm.sh" && npx "$@"; }
nvm()  { unset -f node npm npx nvm && [ -s "$NVM_DIR/nvm.sh" ] && source "$NVM_DIR/nvm.sh" && nvm "$@"; }
```

---

### pyenv (typically adds 200-500ms)

**Before (slow):**
```bash
export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv init --path)"
eval "$(pyenv virtualenv-init -)"
```

**After (lazy load):**
```bash
export PATH="$HOME/.pyenv/bin:$PATH"
python()  { unset -f python python3 pip pip3 pyenv && eval "$(pyenv init -)" && eval "$(pyenv init --path)" && eval "$(pyenv virtualenv-init -)" && python "$@"; }
python3() { unset -f python python3 pip pip3 pyenv && eval "$(pyenv init -)" && eval "$(pyenv init --path)" && eval "$(pyenv virtualenv-init -)" && python3 "$@"; }
pip()     { unset -f python python3 pip pip3 pyenv && eval "$(pyenv init -)" && eval "$(pyenv init --path)" && eval "$(pyenv virtualenv-init -)" && pip "$@"; }
pip3()    { unset -f python python3 pip pip3 pyenv && eval "$(pyenv init -)" && eval "$(pyenv init --path)" && eval "$(pyenv virtualenv-init -)" && pip3 "$@"; }
pyenv()   { unset -f python python3 pip pip3 pyenv && eval "$(pyenv init -)" && eval "$(pyenv init --path)" && eval "$(pyenv virtualenv-init -)" && pyenv "$@"; }
```

---

### rbenv (typically adds 100-300ms)

**Before (slow):**
```bash
eval "$(rbenv init -)"
```

**After (lazy load):**
```bash
rbenv()  { unset -f rbenv ruby gem bundle && eval "$(command rbenv init -)" && rbenv "$@"; }
ruby()   { unset -f rbenv ruby gem bundle && eval "$(command rbenv init -)" && ruby "$@"; }
gem()    { unset -f rbenv ruby gem bundle && eval "$(command rbenv init -)" && gem "$@"; }
bundle() { unset -f rbenv ruby gem bundle && eval "$(command rbenv init -)" && bundle "$@"; }
```

---

### jenv (typically adds 100-200ms)

**Before (slow):**
```bash
eval "$(jenv init -)"
```

**After (lazy load):**
```bash
jenv() { unset -f jenv java javac && eval "$(command jenv init -)" && jenv "$@"; }
java()  { unset -f jenv java javac && eval "$(command jenv init -)" && java "$@"; }
javac() { unset -f jenv java javac && eval "$(command jenv init -)" && javac "$@"; }
```

---

### SDKMAN (typically adds 500ms+)

**Before (slow):**
```bash
export SDKMAN_DIR="$HOME/.sdkman"
[[ -s "$HOME/.sdkman/bin/sdkman-init.sh" ]] && source "$HOME/.sdkman/bin/sdkman-init.sh"
```

**After (lazy load):**
```bash
export SDKMAN_DIR="$HOME/.sdkman"
sdk() {
  unset -f sdk java javac kotlin gradle
  [[ -s "$SDKMAN_DIR/bin/sdkman-init.sh" ]] && source "$SDKMAN_DIR/bin/sdkman-init.sh"
  sdk "$@"
}
```

---

## Other Optimizations

### Remove duplicate PATH entries
```bash
# Add to .zshrc to deduplicate PATH
typeset -U PATH
```

### Use `zsh-defer` for non-critical plugins
```bash
# Install: brew install romkatv/zsh-defer/zsh-defer
# Then wrap slow plugins:
zsh-defer source /path/to/slow/plugin.zsh
```

### Profile what's slow
```bash
# Add to top of .zshrc temporarily:
zmodload zsh/zprof

# Add to bottom of .zshrc:
zprof
```

This prints a profile of every function called during startup — useful for pinpointing the exact culprit.
