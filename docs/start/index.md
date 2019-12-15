# Get started with k



Download and install k
on Linux <i class="fab fa-linux"></i> 
or macOS <i class="fab fa-apple"></i>.

The binary has no dependencies.


## From shakti.com

1.  Unzip the `k` binary from the downloaded file into either your home directory or the default home for binaries: `/usr/local/bin`. 
2.  Open a shell and confirm `rlwrap` is installed: type `rlwrap --version`. If you see no version number, search for, find, and follow install instructions for your OS.
3.  In a text editor open your Bash profile `.bash_profile` and append the following, making the appropriate substitution if you put the `k` binary somewhere else.

    ```
    alias k='export KHOME=/usr/local/bin; rlwrap -r $KHOME/k'
    ```

4.  In the shell, apply your profile and launch k: 

    ```
    $ source ~/.bash_profile
    $ k
    ```

    You should see the k banner: something like

    ```
    2019-05-24 16:37:43 4core 1gb avx2 © shakti m2.0 test
    ```


## From anaconda.org 
Navigate to [anaconda.org/shaktidb/shakti](https://anaconda.org/shaktidb/shakti) and follow the instructions.


## With `npm` 

```bash
$ npm i @kparc/k -g
```

