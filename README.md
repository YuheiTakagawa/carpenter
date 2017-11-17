# carpenter

[![GitHub release](https://img.shields.io/github/release/dev-cloverlab/carpenter.svg?style=flat-square)](https://github.com/dev-cloverlab/carpenter)
[![license](https://img.shields.io/github/license/dev-cloverlab/carpenter.svg?style=flat-square)](https://github.com/dev-cloverlab/carpenter)

carpenter is a tool to manage DB schema and data inspired by [naoina/migu](https://github.com/naoina/migu).  
By using this, you can manage the database structures and data as text (JSON, CSV) and it can be versioned.  
carpenter can restore the database structure and data from text, or can export them to text in easy.  

# How to use

Carpenter has four simple commands are classified database `structure` and `data`. For each command is also available to use as indivisually.

## commands for structure

### design 

`design` command can export database structure as JSON. By doing below, exports JSON file named `table.json` to current directory.

```
% carpenter -s test -d "root:@tcp(127.0.0.1:3306)" design -d ./
```

When you want to separate files for each tables, you can set `-s` option.  

options:

- `-s` export JSON files are separated for each table (default off)
- `-p` pretty output (default off)
- `-d` export directory path

Each option has alternative long name. Please see the help for details.

### build

`build` command can restore database structure from JSON files. By doing below, generate the difference SQLs between tables and JSON files and execute them.

```
% carpenter -s test -d "root:@tcp(127.0.0.1:3306)" build -d .
```

When you want to just show the generated SQLs, you can set `--dry-run` global option.

## commands for data

### export

`export` command can export data as CSV files. By doing below, export data as CSV files for each table.

```
% carpenter -s test -d "root:@tcp(127.0.0.1:3306)" export -d .
```

When you want to select exporting tables, you can set regular expression to `-r` option like below.

```
% carpenter -s test -d "root:@tcp(127.0.0.1:3306)" export -r "^master_*$" -d .
```

### import

`import` command can import CSV files to tables. By doing below, generate the difference SQLs between tables and CSV files and execute them.

```
% carpenter -s test -d "root:@tcp(127.0.0.1:3306)" import -d .
```

When you want to just show the generated SQLs, you can set `--dry-run` global option.

## Install

```
% brew tap dev-cloverlab/carpenter
% brew install dev-cloverlab/carpenter
```

for Gophers.

```
% go get github.com/dev-cloverlab/carpenter/cmd/carpenter
```

## Contribution

1. Fork ([https://github.com/dev-cloverlab/carpenter/cmd/carpenter/fork](https://github.com/dev-cloverlab/carpenter/cmd/carpenter/fork))
1. Create a feature branch
1. Commit your changes
1. Rebase your local changes against the master branch
1. Run test suite with the `go test ./...` command and confirm that it passes
1. Run `gofmt -s`
1. Create a new Pull Request

## Author

[@hatajoe](https://twitter.com/hatajoe)

## Licence

MIT
