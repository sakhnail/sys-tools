<p>Все действия выполняются от имени привелигирированного пользователя (sudo).</p>
<p>Добавить пользователя:</p>
<code>useradd -m UserTest</code>, где -m - это создать пользователя UserTest с home-директорией
<p>Создать пароль пользователю:</p>
<p><code>passwd UserTest</code>, создаем пароль пользователю UserTest</p>
<p>Посмотреть информацию о паролях пользователя: <code>sudo /cat/shadow</code> </p>
<p>Если необходимо создать шаблон профиля пользователя в Linux, то необходимо в директорию <code>/etc/skel/</code>добавить папки, файлы, скрипты и т.д., которые должны копироваться новому пользовател при создании.</p>
<p><code>id UserTest</code> - посмотреть id пользователя UserTest</p>
<p>Удалить пользователя:</p>
<p><code>userdel -r UserTest</code>, где -r - удалить пользователя вместе с home-директрорией.</p>
<p>Добавить новую группу:</p>
<p><code>groupadd NewGroup</code></p>
<p>Посмотреть список групп <code>/etc/group</code></p>
<p>Удалить группу:</p>
<p><code>groupdel NewGroup</code></p>
<p>Добавить пользователя в группу:</p>
<p><code>usermod -aG NewGroup UserTest</code> - <code>usermod</code>, модифицировать пользователя, <code>-aG</code> - добавить в группу NewGroup пользователя UserTest.</p>
<p><code>usermod -aG sudo UserTest</code> - сделает пользователя UserTest суперпользователем.</p>
<p><code>deluser UserTest NewGroup</code> - удалит пользователя UserTest из группы NewGroup</p>
<p>Права на каталоги и файлы:</p>
<p><pre><code>[vagrant@localhost ~]$ ls -la
drwx------. 7 vagrant vagrant  150 May 31 08:09 .
drwxr-xr-x. 3 root    root      21 Dec 28 06:48 ..
-rw-------. 1 vagrant vagrant 5852 May 31 08:05 .bash_history
-rw-r--r--. 1 vagrant vagrant   18 Apr  1  2020 .bash_logout
-rw-r--r--. 1 vagrant vagrant  193 Apr  1  2020 .bash_profile
-rw-r--r--. 1 vagrant vagrant  231 Apr  1  2020 .bashrc
drwx------. 3 vagrant vagrant   16 May 31 08:09 .cache
drwx------. 3 vagrant vagrant   16 May 31 08:09 .config
drwx------. 3 vagrant vagrant   19 May 31 08:09 .local
drwxrw----. 3 vagrant vagrant   19 May 28 10:06 .pki
drwx------. 2 vagrant root      29 May 28 09:40 .ssh
-rw-rw-r--. 1 vagrant vagrant 0 May 31 13:24 testfile
drwxrwxr-x. 2 vagrant vagrant 6 May 31 14:16 testfolder</code></pre></p>
<p>Где d - это каталоги, а - - это файлы, .config - скрытые файлы (все, что начинаются с точки)</p>
<p><code>-rw-r--r--</code> это права на ресурс. Три группы прав, где <code>rw-</code> права пользователя, <code>r--</code> права группы, <code>r--</code> everyone пользователи.</p>
<p><code>r</code> - read, чтение</p>
<p><code>w</code> - write, запись</p>
<p><code>x</code> - запускать, обычно используется для скриптов</p>
<p><code>chown UserTest testfolder/</code> изменить владельца папки testfolder на UserTest</p>
