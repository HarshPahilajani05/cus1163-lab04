What happens to the child's memory when exec() is called?
-When exec() is called, what happens to the child memory is that all the code, data, and stack are replaced with a new program. Also, the PID stays the same.

Why do we need both fork() and exec()? Why not one system call?
-Fork() and exec() both have significance. What fork() does is it duplicates the parent, then creates a new child process with same memory along with the file descriptors. Exec() replaces the child with a new program. Both fork() and exec() is needed so parent can keep running while the child runs new program. This is how Unix uses the fork-exec-wait pattern.

What happens if you call exec() in the parent process instead of the child?
-If you call exec() in the parent process instead of child, it turns into new program and stop being the shell. It then cannot wait or control for the child.

Why must the child call exit() instead of return after a failed exec()?
-The reason why child must call exit() instead of return after failed exec() is because calling it can safely end the child and let the parent clean it up, according to the material using waitpid(). If the exec() fails and child returns it, the parent code will just keep running.
