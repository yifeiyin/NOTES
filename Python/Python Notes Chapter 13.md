### Chapter 13 Files

- Creating a File Handle
    ```python
    file = open("fileName.ext", "w|r|...")
    file.close()
    ```

    - > Note: The variable file is not actual file on the disk. Their relationship is like the one between a remote and the TV.

    - mode write `"w"`: 
        If there is no existing file, it will be created; if there is one, it will be cleared.

    - mode read `"r"`: (default)
        - Reads lines from an existing file. Trying opening a non-existing file will generates an error. 
        - Use `.readline()` to acquire a line. The `\n` is reserved at the end of the string. Therefore, to test if we reached the end, simply use `len(newLine)`.
        - Use `.readlines()` to get a list of strings containing the lines in the file.

    - For binary files such as pictures, zip files, use mode "rb" or "wb" where *b* is for binary. The result variable will be type `bytes`.


- The directory is defaulted to be the same as the program. Explictly say the absulote path when neccessary.

- An example using urllib.request to retrieve content from the web. 
    > socket: One end of a connection allowing one to read and write information to or from another computer.
    ```python
    import urllib.request
    
    def retrieve_page(url):
        """ Retrieve the contents of a web page.
            The contents is converted to a string before returning it.
        """
        my_socket = urllib.request.urlopen(url)
        dta = str(my_socket.readall())
        my_socket.close()
        return dta

    the_text = retrieve_page("http://xml.resource.org/public/rfc/txt/rfc793.txt")
    print(the_text)
    ```
