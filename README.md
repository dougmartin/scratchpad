# scratchpad
This is a disposable repo for a meeting about how git/GitHub works

## Agenda

- What is git and GitHub?
    - [Git is a distributed revision control system.... Git was initially designed and developed by Linus Torvalds for Linux kernel development in 2005. As with most other distributed revision control systems, and unlike most client–server systems, every Git working directory is a full-fledged repository with complete history and full version-tracking capabilities, independent of network access or a central server.](http://en.wikipedia.org/wiki/Git_%28software%29)
    - [GitHub is a web-based Git repository hosting service, which offers all of the distributed revision control and source code management (SCM) functionality of Git as well as adding its own features. Unlike Git, which is strictly a command-line tool, GitHub provides a web-based graphical interface and desktop as well as mobile integration. It also provides access control and several collaboration features such as wikis, task management, and bug tracking and feature requests for every project.](http://en.wikipedia.org/wiki/GitHub)
- A brief tour of git's internals
    - Git is really a content-addressable filesystem.  Version control is just one use of it.
    - Git is a key/value store where the key is a 20-byte [SHA-1 Hash](http://en.wikipedia.org/wiki/SHA-1) and the value is one of three things
        - "blob" which is a plain file like a source code file or an image.  Lets say a file named 'hello.js' contains this:
                alert('hello, world!')
            The blob's key would be the SHA-1 hash of that text which is 7eb912663f26be9296e7a748ce28973e1524045f
        - "tree" which contains lists of blobs or trees and looks like this
                100644 blob a906cb2a4a904a152e80877d4088654daad0c859      README
                100644 blob 7eb912663f26be9296e7a748ce28973e1524045f      hello.js
                040000 tree 99f1a6d12cb4b6f19c8655fca46c3ecf317074e0      lib
        - "commit" which contains a pointer to the top tree, the author, committer and comment like this:
                tree d8329fc1cc938780ffdd9f94e0d364e0ea74f579
                author Scott Chacon <schacon@gmail.com> 1243040974 -0700
                committer Scott Chacon <schacon@gmail.com> 1243040974 -0700

                first commit
    - For version control Git then adds the concept of references (refs) to point to commits.  Refs can be branches, tags, and remotes.  The default branch is "master" and the default remote is "origin" - there is no default tag.  You can easily create new branches both locally and remotely and then merge those changes back into another branch.  By convention "master" is the known good branch shared by everyone.
    - [More info here...](http://git-scm.com/book/en/v1/Git-Internals)
- Working with GitHub
    - There are two common models of changing code on GitHub
        - commiting to the repo - this directly changes the remote repo
        - "forking" the repo and then doing a "pull request" - this lets the repo owners accept/reject changes to the repo.  GitHub has added their own web UI for this.
    - Other GitHub features
        -  issues
        -  wiki
        -  github.io for static pages
        