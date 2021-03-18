# bash-notes
Advanced Bash notes

Tilde expansion https://www.gnu.org/software/bash/manual/html_node/Tilde-Expansion.html

The following table shows how Bash treats unquoted tilde-prefixes:

~
    The value of $HOME 
~/foo

    $HOME/foo
~fred/foo

    The subdirectory foo of the home directory of the user fred
~+/foo

    $PWD/foo
~-/foo

    ${OLDPWD-'~-'}/foo
~N

    The string that would be displayed by ‘dirs +N’
~+N

    The string that would be displayed by ‘dirs +N’
~-N

    The string that would be displayed by ‘dirs -N’ 
    
    
    
    
 Brace expansion
 touch file{apple,banana,mango}
 
 touch file_{1..100} # notice the ordering of the files
 
 touch file_{01.100} # append 0 at the beginning to fix order
 
 echo {A..Z}
 
 echo {a..Z}
 
 echo {A..z} # capital letters before small
    
 Pipes
 
 touch file_{1..100}
 
 ls file_{1..100} | more # paginated output
 
 Standard output and error
 
touch file_{1..10} 

chmod 000 file_{2..4} # block some files from being moved

mkdir tets

cp -v file_* tets/ # some succeed, some fail

cp -v file_* tets/ 1>success.out 2>faliure.out # redirecting success and failures

cat success.out 

cp -v file_* tets/ 1>success.out 2> faliure.out # this works as well

cat faliure.out

cp -v file_* tets/ &>success.out # & denotes both 1 and 2

cp -v file_* tets/ &>/dev/null # no output

Grep

echo "AUTO" > test.txt

grep -i auto test.txt # case insensitive

echo "auto text" > test.txt

cat test.txt | grep -i auto | awk {'print $2'} # prints text, second word after space


# do sed and awk on your own
 
ping -c 1 example.com | grep "bytes" | cut -d " " -f 7 # prints time=127.34

ping -c 1 example.com | grep "bytes" | cut -d " " -f 7 | cut -d "=" -f 2 # prints 127.34
