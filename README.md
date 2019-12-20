rebar3_svn_deps
=====

A rebar3 plugin for fetching dependencies from a subversion repository.

Build
-----

    $ rebar3 compile

Use
---

Add the plugin to your `rebar.config`:

    {plugins, [
        {rebar3_svn_deps, ".*",
           {git, "git://github.com/seanhinde/rebar3_svn_deps.git", {branch, "master"}}}
    ]}.

Configure subversion hosted dependencies with entries in deps:

```erlang
{deps, [
  {hello_lib, "." {svn, "svn://svnrepo/hello_lib/trunk", "HEAD"}},
  {hello,     "." {svn, "svn://svnrepo/hello", {branch, "feature1"}}},
  {hello_app, "." {svn, "svn://svnrepo/hello_app", {tag, "release_tag1"}}},
  {hello_dep, "." {svn, "svn://svnrepo/hello_dep/trunk", {rev, "17983"}}}
  ..
]

```

Specify a branch or tag by providing the full path to the branch/tag
svn directory or using tuple notation.

Pull in a specific svn repository revision by provising the rev number
as a string.

Then just compile your application

    $ rebar3 compile
    ===> Compiling rebar3_svn_deps
    ===> Verifying dependencies...
    ===> Fetching hello_lib (from {svn,"svn://svnrepo/hello_lib/trunk","HEAD"})
    ===> Fetching hello (from {svn,"svn://svnrepo/hello_lib",
                 {branch, "feature1"}})
    ===> Fetching hello_app (from {svn,"svn://svnrepo/hello_app",
                 {tag, "release_tag1"}})
    ===> Fetching hello_dep (from {svn,"svn://svnrepo/hello_app",
                 {rev, "17983"}})
    ===> Compiling..
..
