# starship-cheat-sheet

# Install
- https://starship.rs/

## Ubuntu
```shell
curl -sS https://starship.rs/install.sh | sh

sudo gedit ~/.zshrc
eval "$(starship init zsh)"

# create config file if it it not already exists
mkdir -p ~/.config && touch ~/.config/starship.toml
```




## Windows

1. Install with powershell as admin
```shell
choco install starship
```


2. Find path for profile file
```shell
$PROFILE
```

**If the file does not exists then create it**:

### 1. Erstellen der Datei  
Öffne PowerShell und gib Folgendes ein:  
```powershell
New-Item -Path $PROFILE -ItemType File -Force
```
Das legt die Datei an, falls sie nicht existiert.

### 2. Bearbeiten der Datei  
Jetzt kannst du sie mit Notepad öffnen:  
```powershell
notepad $PROFILE
```
Falls du **Visual Studio Code** nutzt, geht auch:  
```powershell
code $PROFILE
```

### 3. Den Starship-Befehl hinzufügen  
Füge diese Zeile ans Ende der Datei:  
```powershell
Invoke-Expression (&starship init powershell)
```
Speichern und schließen.

### 4. PowerShell neu starten  
Damit die Änderungen greifen, schließe PowerShell und öffne sie neu.  
Falls es trotzdem nicht klappt, prüfe, ob PowerShell-Skripte ausgeführt werden dürfen:  
```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```
Falls gefragt wird, mit **"Ja" (Y)** bestätigen.  

Jetzt sollte Starship beim Start von PowerShell automatisch geladen werden. 🚀

Example:
```
# Starship Prompt
$env:STARSHIP_CONFIG = "C:\Users\denni\.config\starship.toml"
$env:Path += ";C:\Program Files\starship\bin"
Invoke-Expression (& "C:\Program Files\starship\bin\starship.exe" init powershell)

# Git Tools Path
$env:Path += ";C:\Projects\utils\git-tools\bin"

#GO
$env:Path += ";C:\Go\bin"

# Default editor
$ENV:EDITOR = "C:\Users\denni\AppData\Local\Programs\cursor\Cursor.exe"

# RooCode
# if ($env:TERM_PROGRAM -eq "vscode") { . "$(code --locate-shell-integration-path pwsh)" }
```














<br><br>
<br><br>
___
___
<br><br>
<br><br>


# Config
- https://starship.rs/config/


## Create config.toml

<br><br>

### Windows

<br><br>

#### Powershell

Add to your profile file:
```shell
notepad $PROFILE
```

Create your `starship.toml` at your wished location and then add this:
```
$ENV:STARSHIP_CONFIG = "C:\Users\yourusernamehere\.config\starship.toml"
```









<br><br>
<br><br>



## Design #1 **HOT**

<details><summary>Click to expand..</summary>

```toml
# Warning: This config does not include keys that have an unset value

# $all is shorthand for $username$hostname$localip$shlvl$singularity$kubernetes$directory$vcsh$git_branch$git_commit$git_state$git_metrics$git_status$hg_branch$docker_context$package$cmake$cobol$dart$deno$dotnet$elixir$elm$erlang$golang$haskell$helm$java$julia$kotlin$lua$nim$nodejs$ocaml$perl$php$pulumi$purescript$python$rlang$red$ruby$rust$scala$swift$terraform$vlang$vagrant$zig$buf$nix_shell$conda$memory_usage$aws$gcloud$openstack$azure$env_var$crystal$custom$sudo$cmd_duration$line_break$jobs$battery$time$status$container$shell$character
format = '$all'
right_format = ''
continuation_prompt = '[∙](bright-black) '
scan_timeout = 30
command_timeout = 500
add_newline = true

[aws]
format = 'on [$symbol($profile )(\($region\) )(\[$duration\])]($style)'
symbol = '☁️  '
style = 'bold yellow'
disabled = false
expiration_symbol = 'X'

[aws.region_aliases]

[aws.profile_aliases]

[azure]
format = 'on [$symbol($subscription)]($style) '
symbol = 'ﴃ '
style = 'blue bold'
disabled = true

[battery]
full_symbol = ' '
charging_symbol = ' '
discharging_symbol = ' '
unknown_symbol = ' '
empty_symbol = ' '
disabled = false
format = '[$symbol$percentage]($style) '

[[battery.display]]
threshold = 10
style = 'red bold'

[buf]
format = 'with [$symbol ($version)]($style)'
version_format = 'v${raw}'
symbol = ''
style = 'bold blue'
disabled = false
detect_extensions = []
detect_files = [
    'buf.yaml',
    'buf.gen.yaml',
    'buf.work.yaml',
]
detect_folders = []

[character]
format = '$symbol '
success_symbol = '[╰─>](bold #ffda10)'
error_symbol = '[╰─](bold red)[×](bold red)'
disabled = false

[cmake]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = '△ '
style = 'bold blue'
disabled = false
detect_extensions = []
detect_files = [
    'CMakeLists.txt',
    'CMakeCache.txt',
]
detect_folders = []

[cobol]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = '⚙️ '
style = 'bold blue'
disabled = false
detect_extensions = [
    'cbl',
    'cob',
    'CBL',
    'COB',
]
detect_files = []
detect_folders = []

[cmd_duration]
show_milliseconds = true
format = "took [$duration](bold yellow) "
disabled = true
show_notifications = true

[conda]
truncation_length = 1
format = 'via [$symbol$environment]($style) '
symbol = '🅒 '
style = 'green bold'
ignore_base = true
disabled = false

[container]
format = '[$symbol \[$name\]]($style) '
symbol = '⬢'
style = 'red bold dimmed'
disabled = false

[crystal]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = '🔮 '
style = 'bold red'
disabled = false
detect_extensions = ['cr']
detect_files = ['shard.yml']
detect_folders = []

[dart]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = '🎯 '
style = 'bold blue'
disabled = false
detect_extensions = ['dart']
detect_files = [
    'pubspec.yaml',
    'pubspec.yml',
    'pubspec.lock',
]
detect_folders = ['.dart_tool']

[deno]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = '🦕 '
style = 'green bold'
disabled = false
detect_extensions = []
detect_files = [
    'deno.json',
    'deno.jsonc',
    'mod.ts',
    'deps.ts',
    'mod.js',
    'deps.js',
]
detect_folders = []

[directory]
truncation_length = 3
truncate_to_repo = true
fish_style_pwd_dir_length = 0
use_logical_path = true
format = '[$path](bold #ffda10)[$read_only](bold yellow) '
repo_root_format = '[$before_root_path]($style)[$repo_root]($repo_root_style)[$path]($style)[$read_only]($read_only_style) '
style = 'bold underline'
disabled = false
read_only = ' 🔒'
read_only_style = 'red'
truncation_symbol = ''
home_symbol = '~'
use_os_path_sep = true

[directory.substitutions]

[docker_context]
symbol = '🐳 '
style = 'blue bold'
format = 'via [$symbol$context]($style) '
only_with_files = true
disabled = false
detect_extensions = []
detect_files = [
    'docker-compose.yml',
    'docker-compose.yaml',
    'Dockerfile',
]
detect_folders = []

[dotnet]
format = 'via [$symbol($version )(🎯 $tfm )]($style)'
version_format = 'v${raw}'
symbol = '.NET '
style = 'blue bold'
heuristic = true
disabled = false
detect_extensions = [
    'csproj',
    'fsproj',
    'xproj',
]
detect_files = [
    'global.json',
    'project.json',
    'Directory.Build.props',
    'Directory.Build.targets',
    'Packages.props',
]
detect_folders = []

[elixir]
format = 'via [$symbol($version \(OTP $otp_version\) )]($style)'
version_format = 'v${raw}'
symbol = '💧 '
style = 'bold purple'
disabled = false
detect_extensions = []
detect_files = ['mix.exs']
detect_folders = []

[elm]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = '🌳 '
style = 'cyan bold'
disabled = false
detect_extensions = ['elm']
detect_files = [
    'elm.json',
    'elm-package.json',
    '.elm-version',
]
detect_folders = ['elm-stuff']

[env_var]

[erlang]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = ' '
style = 'bold red'
disabled = false
detect_extensions = []
detect_files = [
    'rebar.config',
    'erlang.mk',
]
detect_folders = []

[fill]
style = 'bold black'
symbol = '.'
disabled = false

[gcloud]
format = 'on [$symbol$account(@$domain)(\($region\))]($style) '
symbol = '☁️  '
style = 'bold blue'
disabled = false

[gcloud.region_aliases]

[gcloud.project_aliases]

[git_branch]
format = 'on [$symbol$branch]($style)(:[$remote]($style)) '
symbol = ' '
style = 'bold blue'
truncation_length = 9223372036854775807
truncation_symbol = '…'
only_attached = false
always_show_remote = false
ignore_branches = []
disabled = false

[git_commit]
commit_hash_length = 7
format = '[\($hash$tag\)]($style) '
style = 'green bold'
only_detached = true
disabled = false
tag_symbol = ' 🏷  '
tag_disabled = true

[git_metrics]
added_style = 'bold green'
deleted_style = 'bold red'
only_nonzero_diffs = true
format = '([+$added]($added_style) )([-$deleted]($deleted_style) )'
disabled = true

[git_state]
rebase = 'REBASING'
merge = 'MERGING'
revert = 'REVERTING'
cherry_pick = 'CHERRY-PICKING'
bisect = 'BISECTING'
am = 'AM'
am_or_rebase = 'AM/REBASE'
style = 'bold yellow'
format = '\([$state( $progress_current/$progress_total)]($style)\) '
disabled = false

[git_status]
format = '([〘$all_status$ahead_behind〙]($style) )'
style = 'bold white'
stashed = '📦'
ahead = '⇡'
behind = '⇣'
up_to_date = ''
diverged = '🔀'
conflicted = '🔧'
deleted = '❌'
renamed = '🔄'
modified = '🔨'
staged = '➕'
untracked = '📝'
ignore_submodules = false
disabled = false

[golang]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = '🐹 '
style = 'bold cyan'
disabled = false
detect_extensions = ['go']
detect_files = [
    'go.mod',
    'go.sum',
    'glide.yaml',
    'Gopkg.yml',
    'Gopkg.lock',
    '.go-version',
]
detect_folders = ['Godeps']

[haskell]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = 'λ '
style = 'bold purple'
disabled = false
detect_extensions = [
    'hs',
    'cabal',
    'hs-boot',
]
detect_files = [
    'stack.yaml',
    'cabal.project',
]
detect_folders = []

[helm]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = '⎈ '
style = 'bold white'
disabled = false
detect_extensions = []
detect_files = [
    'helmfile.yaml',
    'Chart.yaml',
]
detect_folders = []

[hg_branch]
symbol = ' '
style = 'bold purple'
format = 'on [$symbol$branch]($style) '
truncation_length = 9223372036854775807
truncation_symbol = '…'
disabled = true

[hostname]
ssh_only = false
trim_at = '.'
format = '[$hostname](#4d4d4d) ⟶  '
style = 'bold'
disabled = false

[java]
disabled = false
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
style = 'red dimmed'
symbol = '☕ '
detect_extensions = [
    'java',
    'class',
    'jar',
    'gradle',
    'clj',
    'cljc',
]
detect_files = [
    'pom.xml',
    'build.gradle.kts',
    'build.sbt',
    '.java-version',
    'deps.edn',
    'project.clj',
    'build.boot',
]
detect_folders = []

[jobs]
threshold = 1
symbol_threshold = 1
number_threshold = 2
format = '[$symbol$number]($style) '
symbol = '✦'
style = 'bold blue'
disabled = true

[julia]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = 'ஃ '
style = 'bold purple'
disabled = false
detect_extensions = ['jl']
detect_files = [
    'Project.toml',
    'Manifest.toml',
]
detect_folders = []

[kotlin]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = '🅺 '
style = 'bold blue'
kotlin_binary = 'kotlin'
disabled = false
detect_extensions = [
    'kt',
    'kts',
]
detect_files = []
detect_folders = []

[kubernetes]
symbol = '☸ '
format = '[$symbol$context( \($namespace\))]($style) in '
style = 'cyan bold'
disabled = true

[kubernetes.context_aliases]

[line_break]
disabled = false

[localip]
ssh_only = true
format = '[$localipv4]($style) '
style = 'yellow bold'
disabled = true

[lua]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = '🌙 '
style = 'bold blue'
lua_binary = 'lua'
disabled = false
detect_extensions = ['lua']
detect_files = ['.lua-version']
detect_folders = ['lua']

[memory_usage]
threshold = 75
format = 'via $symbol[$ram( | $swap)]($style) '
style = 'white bold dimmed'
symbol = '🐏 '
disabled = true

[nim]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = '👑 '
style = 'yellow bold'
disabled = false
detect_extensions = [
    'nim',
    'nims',
    'nimble',
]
detect_files = ['nim.cfg']
detect_folders = []

[nix_shell]
format = 'via [$symbol$state( \($name\))]($style) '
symbol = '❄️  '
style = 'bold blue'
impure_msg = 'impure'
pure_msg = 'pure'
disabled = false

[nodejs]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = ' '
style = 'bold green'
disabled = false
not_capable_style = 'bold red'
detect_extensions = [
    'js',
    'mjs',
    'cjs',
    'ts',
    'mts',
    'cts',
]
detect_files = [
    'package.json',
    '.node-version',
    '.nvmrc',
]
detect_folders = ['node_modules']

[ocaml]
format = 'via [$symbol($version )(\($switch_indicator$switch_name\) )]($style)'
version_format = 'v${raw}'
global_switch_indicator = ''
local_switch_indicator = '*'
symbol = '🐫 '
style = 'bold yellow'
disabled = false
detect_extensions = [
    'opam',
    'ml',
    'mli',
    're',
    'rei',
]
detect_files = [
    'dune',
    'dune-project',
    'jbuild',
    'jbuild-ignore',
    '.merlin',
]
detect_folders = [
    '_opam',
    'esy.lock',
]

[openstack]
format = 'on [$symbol$cloud(\($project\))]($style) '
symbol = '☁️  '
style = 'bold yellow'
disabled = false

[package]
format = 'is [$symbol$version]($style) '
symbol = '📦 '
style = '208 bold'
display_private = false
disabled = false
version_format = 'v${raw}'

[perl]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = '🐪 '
style = '149 bold'
disabled = false
detect_extensions = [
    'pl',
    'pm',
    'pod',
]
detect_files = [
    'Makefile.PL',
    'Build.PL',
    'cpanfile',
    'cpanfile.snapshot',
    'META.json',
    'META.yml',
    '.perl-version',
]
detect_folders = []

[php]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = '🐘 '
style = '147 bold'
disabled = false
detect_extensions = ['php']
detect_files = [
    'composer.json',
    '.php-version',
]
detect_folders = []

[pulumi]
format = 'via [$symbol($username@)$stack]($style) '
version_format = 'v${raw}'
symbol = ' '
style = 'bold 5'
disabled = false

[purescript]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = '<=> '
style = 'bold white'
disabled = false
detect_extensions = ['purs']
detect_files = ['spago.dhall']
detect_folders = []

[python]
pyenv_version_name = false
pyenv_prefix = 'pyenv '
python_binary = [
    'python',
    'python3',
    'python2',
]
format = 'via [${symbol}${pyenv_prefix}(${version} )(\($virtualenv\) )]($style)'
version_format = 'v${raw}'
style = 'yellow bold'
symbol = '🐍 '
disabled = false
detect_extensions = ['py']
detect_files = [
    'requirements.txt',
    '.python-version',
    'pyproject.toml',
    'Pipfile',
    'tox.ini',
    'setup.py',
    '__init__.py',
]
detect_folders = []

[red]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = '🔺 '
style = 'red bold'
disabled = false
detect_extensions = [
    'red',
    'reds',
]
detect_files = []
detect_folders = []

[rlang]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
style = 'blue bold'
symbol = '📐 '
disabled = false
detect_extensions = [
    'R',
    'Rd',
    'Rmd',
    'Rproj',
    'Rsx',
]
detect_files = ['.Rprofile']
detect_folders = ['.Rproj.user']

[ruby]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = '💎 '
style = 'bold red'
disabled = false
detect_extensions = ['rb']
detect_files = [
    'Gemfile',
    '.ruby-version',
]
detect_folders = []
detect_variables = [
    'RUBY_VERSION',
    'RBENV_VERSION',
]

[rust]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = '🦀 '
style = 'bold red'
disabled = false
detect_extensions = ['rs']
detect_files = ['Cargo.toml']
detect_folders = []

[scala]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
disabled = false
style = 'red bold'
symbol = '🆂 '
detect_extensions = [
    'sbt',
    'scala',
]
detect_files = [
    '.scalaenv',
    '.sbtenv',
    'build.sbt',
]
detect_folders = ['.metals']

[shell]
format = '[$indicator]($style) '
bash_indicator = 'bsh'
fish_indicator = 'fsh'
zsh_indicator = 'zsh'
powershell_indicator = 'psh'
ion_indicator = 'ion'
elvish_indicator = 'esh'
tcsh_indicator = 'tsh'
nu_indicator = 'nu'
xonsh_indicator = 'xsh'
cmd_indicator = 'cmd'
unknown_indicator = ''
style = 'white bold'
disabled = true

[shlvl]
threshold = 2
format = '[$symbol$shlvl]($style) '
symbol = '↕️  '
repeat = false
style = 'bold yellow'
disabled = true

[singularity]
symbol = ''
format = '[$symbol\[$env\]]($style) '
style = 'blue bold dimmed'
disabled = false

[status]
format = '[$symbol$status]($style) '
symbol = '✖'
success_symbol = ''
not_executable_symbol = '🚫'
not_found_symbol = '🔍'
sigint_symbol = '🧱'
signal_symbol = '⚡'
style = 'bold red'
map_symbol = false
recognize_signal_code = true
pipestatus = false
pipestatus_separator = '|'
pipestatus_format = '\[$pipestatus\] => [$symbol$common_meaning$signal_name$maybe_int]($style)'
disabled = true

[sudo]
format = '[as $symbol]($style)'
symbol = '🧙 '
style = 'bold blue'
allow_windows = false
disabled = true

[swift]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = '🐦 '
style = 'bold 202'
disabled = false
detect_extensions = ['swift']
detect_files = ['Package.swift']
detect_folders = []

[terraform]
format = 'via [$symbol$workspace]($style) '
version_format = 'v${raw}'
symbol = '💠 '
style = 'bold 105'
disabled = false
detect_extensions = [
    'tf',
    'tfplan',
    'tfstate',
]
detect_files = []
detect_folders = ['.terraform']

[time]
format = 'at [$time]($style) '
style = 'bold yellow'
use_12hr = false
disabled = true
utc_time_offset = 'local'
time_range = '-'

[username]
format = '[╭─](bold #ffda10)[$user](bold #ffda10)[@](bold #4d4d4d)'
style_root = 'bold'
style_user = 'bold'
show_always = true
disabled = false

[vagrant]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = '⍱ '
style = 'cyan bold'
disabled = false
detect_extensions = []
detect_files = ['Vagrantfile']
detect_folders = []

[vcsh]
symbol = ''
style = 'bold yellow'
format = 'vcsh [$symbol$repo]($style) '
disabled = false

[vlang]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = 'V '
style = 'blue bold'
disabled = false
detect_extensions = ['v']
detect_files = [
    'v.mod',
    'vpkg.json',
    '.vpkg-lock.json',
]
detect_folders = []

[zig]
format = 'via [$symbol($version )]($style)'
version_format = 'v${raw}'
symbol = '↯ '
style = 'bold yellow'
disabled = false
detect_extensions = ['zig']
detect_files = []
detect_folders = []

[custom]
```

</details>
