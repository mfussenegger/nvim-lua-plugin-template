# nvim-lua-plugin-template

This repository is a template for Neovim plugins written in Lua.

The intention is that you use this template to create a new repository where you then adapt this readme and add your plugin code.
The template includes the following:

- GitHub workflows and configurations to run linters and tests
- Packaging of tagged releases and upload to [LuaRocks][luarocks]
  if a [`LUAROCKS_API_KEY`][luarocks-api-key] is added
  to the [GitHub Actions secrets][gh-actions-secrets]
- Minimal test setup:
  - A `scm` [rockspec][rockspec-format], `nvim-lua-plugin-scm-1.rockspec`
  - A `.busted` file
- EditorConfig
- A .luacheckrc


To get started writing a Lua plugin, I recommend reading `:help lua-guide` and
`:help write-plugin`.

## Scope

Anything that the majority of plugin authors will want to have is in scope of
this starter template. Anything that is controversial is out-of-scope.

## Usage

- Click [Use this template][use-this-template]. Do not fork.
- Rename `nvim-lua-plugin-scm-1.rockspec` and change the `package` name
  to the name of your plugin.

## Template License

The template itself is licensed under the [MIT license](https://en.wikipedia.org/wiki/MIT_License).
The template doesn't include a LICENSE file. You should add one after creating your repository.

---


The remainder of the README is text that can be preserved in your plugin:

---


## Development

### Run tests


Running tests requires either

- [luarocks][luarocks]
- or [busted][busted] and [nlua][nlua]

to be installed[^1].

[^1]: The test suite assumes that `nlua` has
      been added to the PATH.

You can then run:

```bash
luarocks test --local
# or
busted
```

Or if you want to run a single test file:

```bash
luarocks test spec/path_to_file.lua --local
# or
busted spec/path_to_file.lua
```

### Common Errors

If you encounter the `module 'busted.runner' not found`
or `pl.path requires LuaFileSystem` errors, fix it by
runing the following command the following command:

```bash
eval $(luarocks path --no-bin)
```

If you encounter `sh: nlua: command not found` error the error above occurs do[^1]:

#### Linux/Max

Run the following command:
```bash
export PATH=$PATH:~/.luarocks/bin
```

#### Windows

See the following guide to a variable to the PATH: [add to PATH][add-env-vars-windows].

> [!Note]
> For local testing to work you need to have Lua 5.1 set as your default version for
> luarocks. If that's not the case you can pass `--lua-version 5.1` to all the
> luarocks commands above, or set lua version 5.1 globally by running
> `luarocks config --scope system lua_version 5.1`.

[rockspec-format]: https://github.com/luarocks/luarocks/wiki/Rockspec-format
[luarocks]: https://luarocks.org
[luarocks-api-key]: https://luarocks.org/settings/api-keys
[gh-actions-secrets]: https://docs.github.com/en/actions/security-guides/encrypted-secrets#creating-encrypted-secrets-for-a-repository
[busted]: https://lunarmodules.github.io/busted/
[nlua]: https://github.com/mfussenegger/nlua
[use-this-template]: https://github.com/new?template_name=nvim-lua-plugin-template&template_owner=nvim-lua
[add-env-vars-windows]: https://answers.microsoft.com/en-us/windows/forum/all/adding-path-variable/97300613-20cb-4d85-8d0e-cc9d3549ba23
