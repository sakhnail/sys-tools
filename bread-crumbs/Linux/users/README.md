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