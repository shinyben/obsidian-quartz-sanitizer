# obsidian-quartz-sanitizer
Given a directory of [Obsidian](https://obsidian.md/) notes, clones the directory into a [Quartz](https://github.com/jackyzha0/quartz)-compliant structure. Written because [the previous code](https://github.com/trojblue/Obsidian-wiki-fix) didn't handle `#` or `|` or spaces.

Hugo, the back-end of Quartz, can't handle note names that include characters that are URL-unfriendly, including spaces and emojis. This will, if given a Obsidian vault containing Wikilinked ( [[NOTE-NAME]] ) notes, generate a vault that is visually identical but Quartz-compliant.

## How to Use
1. Make a backup of your Obsidian vault in case something breaks (unlikely)
2. Don't forget step #1
3. Edit IN_DIR to be full path to the input Obsidian directory
4. If you don't want the new notes to be drafts by default, change to `DEFAULT_DRAFT = False`
5. Run using `python main.py`

## Features:
- Translates all Wikilinks in the form [[FILENAME#HEADER|VISIBLE]] to \[VISIBLE\](FILENAME#HEADER)
	- Retains identical reader-view notes
	- Includes block links `^blocklink`
- Adds frontmatter to all notes, creating the tags `title` and `draft` by default and cleaning the tags `title` and `url` if they exist and would break Quartz.

## To Do
- Handle non-`.md` media files
- Conform functional on non-Windows machines
- Speed up with dictionary (if someone bugs me about it enough)
