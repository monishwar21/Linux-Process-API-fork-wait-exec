# Linux-Process-API-fork-wait-exec-
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
# REG NO : 212225230188

# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to create new process using Linux API system calls fork() and getpid() , getppid() and to print process ID and parent Process ID using Linux API system calls
```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main() {
    int pid = fork();

    if (pid == 0) { 
        printf("I am child, my PID is %d\n", getpid()); 
       printf("My parent PID is: %d\n", getppid()); 
        sleep(2);  // Keep child alive for verification
    } else { 
        printf("I am parent, my PID is %d\n", getpid()); 
        wait(NULL); 
    }
}


```

## OUTPUT

<img width="1574" height="999" alt="c4cc7442-b4f6-4e9b-8a05-895bccf35a19" src="https://github.com/user-attachments/assets/d78018c4-3e26-40b4-8b08-6d0c866e7161" />


## C Program to execute Linux system commands using Linux API system calls exec() , exit() , wait() family
```

#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>

int main() {
    int status;
    
    printf("Running ps with execl\n");
    if (fork() == 0) {        
execlp("ps", "ps", "-f", NULL);
        perror("execlp failed");
        exit(1);
    }
    wait(&status);
    
    if (WIFEXITED(status)) {
        printf("Child exited for execlp with status: %d\n", WEXITSTATUS(status));
    } else {
        printf("Child did not exit successfully\n");
    }
    
    printf("Done.\n");
    return 0;
}
```

## OUTPUT


<img width="1604" height="981" alt="53a4a1d7-c247-4816-9423-467c57405114" src="https://github.com/user-attachments/assets/89aa828d-c6d0-47df-81b1-9e0546661e3f" />


# RESULT:
The programs are executed successfully.
