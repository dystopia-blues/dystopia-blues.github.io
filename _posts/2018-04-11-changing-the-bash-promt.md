---
title: Customizing the BASH Shell Prompt
tags: [ bash, shell-customization ]
---

## Customizing the BASH Shell Prompt

The [Bash](https://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) or *Bourne Again Shell* is default shell on most modern Linux ditros. Changing the default promt to something a little more usable via `PS1="\n[\w]\n>> "` is the first thing I tweak on a fresh install.

### Setting PS1 and the Default Prompt

The bash prompt can be changed from within the shell by setting the `PS1` variable. By default, this is set to:
```
PS1="\u@\h:\w\$"
```
Which yields a default along the lines of:

```
user@hostname:cwd$|
```

Where `user` is of course the current username, `hostname` is the machine I'm running on, and `cwd` is the current working directory. As you `cd` or *change directoy* within the shell the prompt will update with the new current working directory.

This is all useful on it's own, but I make a few modifications. Firstly, I like to drop the `user` and `hostname`, just to simplify things. The user name can be useful if you are logging in as `root` often and need to reminded not to do any thing too stupid, but I have other protections in place for that.
Having the `hostname` in the prompt can be useful too if your plan to `ssh` onto other machines or run interative shell through LSF but I don't need it on every line. If I forget where I am, I just type `hostname` or more commonly `uname -a`.

The current working directory is very useful, so that I keep. I decorate it with square brackets (why not?) and put it on it's on line. This allow the actuall prompt to start on the left of the screen. Without this step, if you `cd` deep into the directory tree the everything starts to wrap and becomes unreadable. Also adding an extra new line `\n` to the start gives each comamnd line input (and it's subsequent output) some isolation from the previous command.

Putting that all together the new prompt is set with:
```
PS1="\n[\w]\n>> "
```
Which yields an updated prompt along the lines of:

```

[cwd]
>> |
```

### Making the Change Permanent

Setting the PS1 variable in the above fashion will apply the change to your current shell only. Edit the \*rc file to apply the new prompt to each new shell going forward.


```
echo "export PS1=\"\n[\w]\n>> \" " >> ~/.bashrc

```

### Old vs New

To see how this works in context (with a lot of screen output) compare the two listings below. The difference is subtle but it is definitely appriciable when scrolling back through multiple pages of text.

```
user1@host001:~$cd ~
user1@host001:~$cd /opt/riscv/riscv64-unknown-elf/include/c++/7.2.0/ext/pb_ds/detail/gp_hash_table_map_/
user1@host001:/opt/riscv/riscv64-unknown-elf/include/c++/7.2.0/ext/pb_ds/detail/gp_hash_table_map_$ls
constructor_destructor_fn_imps.hpp                erase_store_hash_fn_imps.hpp      insert_store_hash_fn_imps.hpp
constructor_destructor_no_store_hash_fn_imps.hpp  find_fn_imps.hpp                  iterator_fn_imps.hpp
constructor_destructor_store_hash_fn_imps.hpp     find_no_store_hash_fn_imps.hpp    policy_access_fn_imps.hpp
debug_fn_imps.hpp                                 find_store_hash_fn_imps.hpp       resize_fn_imps.hpp
debug_no_store_hash_fn_imps.hpp                   gp_ht_map_.hpp                    resize_no_store_hash_fn_imps.hpp
debug_store_hash_fn_imps.hpp                      info_fn_imps.hpp                  resize_store_hash_fn_imps.hpp
erase_fn_imps.hpp                                 insert_fn_imps.hpp                trace_fn_imps.hpp
erase_no_store_hash_fn_imps.hpp                   insert_no_store_hash_fn_imps.hpp
user1@host001:/opt/riscv/riscv64-unknown-elf/include/c++/7.2.0/ext/pb_ds/detail/gp_hash_table_map_$ls ..
binary_heap_                 debug_map_base.hpp             pairing_heap_                     thin_heap_
binomial_heap_               eq_fn                          pat_trie_                         tree_policy
binomial_heap_base_          gp_hash_table_map_             priority_queue_base_dispatch.hpp  tree_trace_base.hpp
bin_search_tree_             hash_fn                        rb_tree_map_                      trie_policy
branch_policy                left_child_next_sibling_heap_  rc_binomial_heap_                 types_traits.hpp
cc_hash_table_map_           list_update_map_               resize_policy                     type_utils.hpp
cond_dealtor.hpp             list_update_policy             splay_tree_                       unordered_iterator
container_base_dispatch.hpp  ov_tree_map_                   standard_policies.hpp
user1@host001:/opt/riscv/riscv64-unknown-elf/include/c++/7.2.0/ext/pb_ds/detail/gp_hash_table_map_$cd ..
user1@host001:/opt/riscv/riscv64-unknown-elf/include/c++/7.2.0/ext/pb_ds/detail$ls -1 t*
thin_heap_
tree_policy
tree_trace_base.hpp
trie_policy
types_traits.hpp
type_utils.hpp
user1@host001:/opt/riscv/riscv64-unknown-elf/include/c++/7.2.0/ext/pb_ds/detail$cd /opt/riscv/riscv64-unknown-elf/include/c++/7.2.0/ext/pb_ds/detail/binary_heap_
user1@host001:/opt/riscv/riscv64-unknown-elf/include/c++/7.2.0/ext/pb_ds/detail/binary_heap_$ls -l i*
total 100
-rw-r--r-- 1 root root 2062 May  7 02:50 info_fn_imps.hpp
-rw-r--r-- 1 root root 4978 May  7 02:50 insert_fn_imps.hpp
-rw-r--r-- 1 root root 2270 May  7 02:50 iterators_fn_imps.hpp
user1@host001:/opt/riscv/riscv64-unknown-elf/include/c++/7.2.0/ext/pb_ds/detail/binary_heap_$
```

```
[~]
>> cd ~

[~]
>> cd /opt/riscv/riscv64-unknown-elf/include/c++/7.2.0/ext/pb_ds/detail/gp_hash_table_map_/

[/opt/riscv/riscv64-unknown-elf/include/c++/7.2.0/ext/pb_ds/detail/gp_hash_table_map_]
>> ls
constructor_destructor_fn_imps.hpp                erase_store_hash_fn_imps.hpp      insert_store_hash_fn_imps.hpp
constructor_destructor_no_store_hash_fn_imps.hpp  find_fn_imps.hpp                  iterator_fn_imps.hpp
constructor_destructor_store_hash_fn_imps.hpp     find_no_store_hash_fn_imps.hpp    policy_access_fn_imps.hpp
debug_fn_imps.hpp                                 find_store_hash_fn_imps.hpp       resize_fn_imps.hpp
debug_no_store_hash_fn_imps.hpp                   gp_ht_map_.hpp                    resize_no_store_hash_fn_imps.hpp
debug_store_hash_fn_imps.hpp                      info_fn_imps.hpp                  resize_store_hash_fn_imps.hpp
erase_fn_imps.hpp                                 insert_fn_imps.hpp                trace_fn_imps.hpp
erase_no_store_hash_fn_imps.hpp                   insert_no_store_hash_fn_imps.hpp

[/opt/riscv/riscv64-unknown-elf/include/c++/7.2.0/ext/pb_ds/detail/gp_hash_table_map_]
>> ls ..
binary_heap_                 debug_map_base.hpp             pairing_heap_                     thin_heap_
binomial_heap_               eq_fn                          pat_trie_                         tree_policy
binomial_heap_base_          gp_hash_table_map_             priority_queue_base_dispatch.hpp  tree_trace_base.hpp
bin_search_tree_             hash_fn                        rb_tree_map_                      trie_policy
branch_policy                left_child_next_sibling_heap_  rc_binomial_heap_                 types_traits.hpp
cc_hash_table_map_           list_update_map_               resize_policy                     type_utils.hpp
cond_dealtor.hpp             list_update_policy             splay_tree_                       unordered_iterator
container_base_dispatch.hpp  ov_tree_map_                   standard_policies.hpp

[/opt/riscv/riscv64-unknown-elf/include/c++/7.2.0/ext/pb_ds/detail/gp_hash_table_map_]
>> cd ..

[/opt/riscv/riscv64-unknown-elf/include/c++/7.2.0/ext/pb_ds/detail]
>> ls -1 t*
thin_heap_
tree_policy
tree_trace_base.hpp
trie_policy
types_traits.hpp
type_utils.hpp

[/opt/riscv/riscv64-unknown-elf/include/c++/7.2.0/ext/pb_ds/detail]
>> cd /opt/riscv/riscv64-unknown-elf/include/c++/7.2.0/ext/pb_ds/detail/binary_heap_

[/opt/riscv/riscv64-unknown-elf/include/c++/7.2.0/ext/pb_ds/detail/binary_heap_]
>> ls -l i*
total 100
-rw-r--r-- 1 root root 2062 May  7 02:50 info_fn_imps.hpp
-rw-r--r-- 1 root root 4978 May  7 02:50 insert_fn_imps.hpp
-rw-r--r-- 1 root root 2270 May  7 02:50 iterators_fn_imps.hpp

[/opt/riscv/riscv64-unknown-elf/include/c++/7.2.0/ext/pb_ds/detail/binary_heap_]
>>

```

## Trying Other Combinations

The following is a list of bash variables that can be used to modify the prompt to you needs. They range from useful (current time `\t` helps with profiling commands), to almost useless (I doubt anyone uses bash version `\v` on a day to day basis).

|Variable |Description
|---      |---
|\w       |The current working directory (full path)
|\W       |The current working directory (basename only)
|\u       |The username of the current user.
|\h       |The hostname, up to the first . (e.g. deckard)
|\H       |The full hostname. (e.g. deckard.SS64.com)
|\d       |The date, in "Weekday Month Date" format (e.g., "Tue May 26").
|\t       |The time, in 24-hour HH:MM:SS format.
|\T       |The time, in 12-hour HH:MM:SS format.
|\@       |The time, in 12-hour am/pm format.
|\j       |The number of jobs currently managed by the shell.
|\l       |The basename of the shell's terminal device name.
|\s       |The name of the shell, the basename of $0 (the portion following the final slash).
|\v       |The version of Bash (e.g., 2.00)
|\V       |The release of Bash, version + patchlevel (e.g., 2.00.0)
|\!       |The history number of this command.
|\#       |The command number of this command.
|\$       |Insets a `#` if root, else inserets a `$`.
|\nnn     |The character whose ASCII code is the octal value nnn.
|\n       |A newline.
|\r       |A carriage return.
|\e       |An escape character (typically a color code).
|\a       |A bell character.
|\\       |A backslash.
|\[       |Begin a sequence of non-printing characters (such as color escape sequences).
|\]       |End a sequence of non-printing characters.

The follow page has a generator where you can modify and test ann example bash prompt: https://www.kirsle.net/wizards/ps1.html
