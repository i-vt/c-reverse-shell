# c-reverse-shell

## Info

A reverse shell for Windows and Linux written in C.

Features:
- Linux and Windows version.
- Runs in the background (on both, Linux and Windows, no blocking terminal or black screen).
- You can choose between waiting for the client (if it's no listening) or not.
- Compile with just one command (see at the bottom of the `README.md`), there is also a `Makefile`.

## Dependencies

For Windows you will need `mingw-w64` compiler (the `.exe` binary is compiled in linux):
```sh
sudo apt install gcc-mingw-w64
```

## How to use

1. Clone repo:
```sh
git clone https://github.com/izenynn/c-reverse-shell.git
```

2. Change client IP and client PORT with `change_client.sh` (you can change it manually inside `linux.c` and `windows.c` if you prefer):
```sh
./change_client.sh [CLIENT_IP] [CLIENT_PORT]
```

3. Compile for Linux and Windows with `make` (equivalent to `make all`):
```sh
make
```

4. And ✨ magic ✨ compile the program in your target, or just send the binary, and execute it, make sure your client is listening 😊.

Additionally you can compile with `WAIT_FOR_CLIENT` true, this will make the program loop until the connection to the client is established, instead of returning an error in the connection:
```sh
make WAIT_FOR_CLIENT=TRUE
```
*NOTE: this doen't work on windows, not sure why, but I'm sleepy, so maybe I fix it another day (or pull request if you fix it please 😊).*

Other `Makefile` rules:
- `make all`
- `make linux`
- `make windows`
- `make re`
-
- `make all WAIT_FOR_CLIENT=TRUE`
- `make linux WAIT_FOR_CLIENT=TRUE`
- `make windows WAIT_FOR_CLIENT=TRUE`
- `make re WAIT_FOR_CLIENT=TRUE`
-
- `make clean`

In case you don't have the `Makefile`, just copy the `reverse-shell.c` file and compile it with the following command:
- Linux
```sh
gcc -std=c99 linux.c -o rsh.out
```
```sh
gcc -std=c99 linux.c -o rsh.out -D WAIT_FOR_CLIENT
```
- Windows:
```sh
i686-w64-mingw32-gcc-win32 -std=c99 windows.c -o rsh.exe -lws2_32
```
```sh
i686-w64-mingw32-gcc-win32 -std=c99 windows.c -o rsh.exe -lws2_32 -D WAIT_FOR_CLIENT
```

## Disclaimer for "c-reverse-shell":

### Summary: 
Don't be an idiot and be responsible with usage. Pentesting without authorization is illegal.

### In depth: 
1. General Use: This software is provided "as is", without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and non-infringement. In no event shall the authors or copyright holders be liable for any claim, damages or other liability, whether in an action of contract, tort or otherwise, arising from, out of or in connection with the software or the use or other dealings in the software.
2. Potential Misuse: The software is designed for legitimate purposes only. Any misuse, including but not limited to illegal, unethical, or unauthorized activities, is strictly discouraged and not the intention of the developers.
3. User Responsibility: Any person, entity, or organization choosing to use this software bears the full responsibility for its actions while using the software. It is the user's responsibility to ensure that their use of this software complies with local, state, national, and international laws and regulations.
4. No Liability: The creators, developers, and distributors of this software are not responsible for any harm or damage caused, directly or indirectly, by the misuse or use of this software.
5. Updates and Monitoring: The developers reserve the right to update, modify, or discontinue the software at any time. Users are advised to always use the most recent version of the software. However, even with updates, the developers cannot guarantee that the software is completely secure or free from vulnerabilities.
6. Third-Party Software/Links: This software may contain links to third-party sites or utilize third-party software/tools. The developers are not responsible for the content or privacy practices of those sites or software.
7. Unauthorized Access: Using "c-reverse-shell" to access, probe, or connect to systems, networks, or data without explicit permission from appropriate parties is strictly discouraged, unethical, and illegal. Unauthorized access to systems, networks, or data breaches various local, national, and international laws, and can result in severe legal consequences. Always obtain the necessary permissions before accessing any systems or data. The developers of "c-reverse-shell" disavow any actions taken by individuals or entities that use this software for unauthorized activities.

By downloading, installing, or using "c-reverse-shell" you acknowledge that you have read, understood, and agreed to abide by this disclaimer. If you do not agree to these terms, do not use the software.
