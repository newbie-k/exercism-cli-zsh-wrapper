# exercism-cli-zsh-wrapper
shell wrapper from [exercism website](https://exercism.org/docs/tracks/bash/tests) modified for using in `zsh` instead of `bash`

## how to use
put the following code in `.zshrc` and reopen the terminal or run `source .zshrc`
```
exercism () {
	local out
	out=("${(@f)$(command exercism $@)}")
	printf '%s\n' "${out[@]}"
	if [[ $1 == "download" && -d "${out[-1]}" ]]; then
		cd "${out[-1]}" || return 1
	fi
}
```
