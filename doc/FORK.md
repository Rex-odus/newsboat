# Newsboat Fork - Arrow Key Navigation

## About This Fork

This is a modified version of [Newsboat](https://github.com/newsboat/newsboat), the RSS/Atom feed reader for the text console.

**Original Project:** https://github.com/newsboat/newsboat  
**Fork Repository:** https://github.com/Rex-odus/newsboat

## What's Different?

This fork adds **intuitive arrow key navigation** to make Newsboat easier to use without memorizing keyboard shortcuts.

### Navigation Changes

| Context | ENTER | RIGHT → | LEFT ← | q/Q |
|---------|-------|---------|--------|-----|
| **Feed List** (main screen) | Opens feed URL in browser | Go to article list | **Ignored** (no action) | Quit program (with confirmation) |
| **Article List** | Opens article URL in browser | Go to article view | Back to feed list | Back to feed list |
| **Article View** | Opens article URL in browser | - | Back to article list | Back to article list |

### Why These Changes?

The original Newsboat requires memorizing many keyboard shortcuts:
- `ENTER` to navigate deeper into feeds/articles
- `o` to open in browser
- `q` to go back/quit

This fork makes navigation more intuitive:
- **ENTER** always opens content in your browser (what most users want)
- **RIGHT arrow** navigates deeper (natural direction)
- **LEFT arrow** goes back (natural direction)
- **q/Q** still available for quitting

### Original Behavior Preserved

All original Newsboat features remain unchanged:
- All keyboard shortcuts still work (can be rebound in config)
- All configuration options work the same
- All feed services integrations work
- All scripts and filters work
- Podboat unchanged

You can restore original keybindings in your config file if preferred:
```
bind-key ENTER open feedlist
bind-key ENTER open articlelist
unbind-key RIGHT
unbind-key LEFT
```

## Updating from Upstream

To get updates from the original Newsboat project:

```bash
# Add upstream remote (one-time setup)
git remote add upstream https://github.com/newsboat/newsboat

# Fetch upstream changes
git fetch upstream

# Merge into your fork
git merge upstream/master
```

**Note:** After merging, you may need to re-apply the arrow key navigation changes if there are conflicts in:
- `include/keymap.h`
- `src/keymap.cpp`
- `src/feedlistformaction.cpp`
- `src/itemlistformaction.cpp`
- `test/keymap.cpp`
- `doc/keycmds.dsv`

## Files Modified

The following files were changed to implement arrow key navigation:

1. `include/keymap.h` - Added OP_SK_RIGHT, OP_SK_LEFT operations
2. `src/keymap.cpp` - Added keybindings for ENTER, RIGHT, LEFT
3. `src/feedlistformaction.cpp` - Updated keymap hint ("Open in Browser")
4. `src/itemlistformaction.cpp` - Updated keymap hint ("Open in Browser")
5. `test/keymap.cpp` - Updated tests for new default bindings
6. `doc/keycmds.dsv` - Updated documentation

## License

This fork inherits the MIT license from the original Newsboat project.  
See [LICENSE](../LICENSE) file.

## Contact

For issues specific to this fork (arrow key navigation), open an issue at:  
https://github.com/Rex-odus/newsboat/issues

For general Newsboat issues, please use the upstream repository:  
https://github.com/newsboat/newsboat/issues
