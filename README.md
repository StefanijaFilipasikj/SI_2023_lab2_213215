SI_Lab2_213215

# Control Flow Control ( CFG ) 

![image](https://github.com/StefanijaFilipasikj/SI_2023_lab2_213215/assets/127665193/47a3fb3f-005f-458d-96b6-e687dea21a5f)

# Цикломатската комплексност

Edges (E):

Е = 24

Nodes (N):

N = 15

Користејќи ја формулата V(G) = E - N + 2, можеме да ја пресметаме цикломатската сложеност:

V(G) = 24 - 15 + 2
V(G) = 11

Цикломатската сложеност на дадениот CFG е 11.

# Every Branch

<table><thead><tr><th>Branch</th><th>Completed</th></tr></thead><tbody><tr><td>[2]</td><td>*</td></tr><tr><td>[4]</td><td>*</td></tr><tr><td>[7]</td><td>*</td></tr><tr><td>[9]</td><td>*</td></tr><tr><td>[11]</td><td>*</td></tr><tr><td>[13]</td><td>*</td></tr><tr><td>[18]</td><td>*</td></tr><tr><td>[20]</td><td>*</td></tr><tr><td>[21]</td><td>*</td></tr><tr><td>[22]</td><td>*</td></tr></tbody></table>

Објаснување:
<ol>
  <li>Гранка [2] се завршува кога условот (user == null || user.getPassword() == null || user.getEmail() == null) е точен.</li>
  <li>Гранка [4] се завршува кога условот user.getUsername() == null е точен.</li>
  <li>Гранка [7] се завршува кога условот user.getEmail().contains("@") && user.getEmail().contains(".") е точен.</li>
  <li>Гранка [9] се завршува кога условот i < allUsers.size() во циклусот е точен.</li>
  <li>Гранка [11] се завршува кога условот existingUser.getEmail() == user.getEmail() е точен.</li>
  <li>Гранка [13] се завршува кога условот existingUser.getUsername() == user.getUsername() е точен.</li>
  <li>Гранка [18] се завршува кога условот passwordLower.contains(user.getUsername().toLowerCase()) || password.length() < 8 е точен.</li>
  <li>Гранка [20] се завршува кога условот !passwordLower.contains(" ") е точен.</li>
  <li>Гранка [21] се завршува кога условот i < specialCharacters.length() во циклусот е точен.</li>
  <li>Гранка [22] се завршува кога условот password.contains(String.valueOf(specialCharacters.charAt(i))) е точен.</li>
</ol>

# Multiple Condition

Multiple Condition критериумот на условот if (user == null || user.getPassword() == null || user.getEmail() == null): 

<ol>
  <li>
    Тест случај за `user == null`:
    <ul>
      <li>Влез: `user = null`</li>
      <li>Очекуван излез: `RuntimeException("Обавезна информација недостасува!")`</li>
    </ul>
  </li>
  <li>
    Тест случај за `user.getPassword() == null`:
    <ul>
      <li>Влез: `user.getPassword() = null`</li>
      <li>Очекуван излез: `RuntimeException("Обавезна информација недостасува!")`</li>
    </ul>
  </li>
  <li>
    Тест случај за `user.getEmail() == null`:
    <ul>
      <li>Влез: `user.getEmail() = null`</li>
      <li>Очекуван излез: `RuntimeException("Обавезна информација недостасува!")`</li>
    </ul>
  </li>
  <li>
    Тест случај за `user.getUsername() == null`:
    <ul>
      <li>Влез: `user.getUsername() = null`</li>
      <li>Очекуван излез: `user.getUsername() = user.getEmail()`</li>
    </ul>
  </li>
  <li>
    Тест случај за `user.getEmail()` без "@" и "." знаци:
    <ul>
      <li>Влез: `user.getEmail() = "email"`</li>
      <li>Очекуван излез: `same = 1`</li>
    </ul>
  </li>
  <li>
    Тест случај за `user.getEmail()` со постоечка е-пошта во `allUsers`:
    <ul>
      <li>Влез: `user.getEmail() = "existingEmail"`</li>
      <li>Очекуван излез: `same > 0`</li>
    </ul>
  </li>
  <li>
    Тест случај за `passwordLower.contains(user.getUsername().toLowerCase())`:
    <ul>
      <li>Влез: `passwordLower = "password"`, `user.getUsername() = "pass"`</li>
      <li>Очекуван излез: `false`</li>
    </ul>
  </li>
  <li>
    Тест случај за `password.length() < 8`:
    <ul>
      <li>Влез: `password = "pass"`, `password.length() = 4`</li>
      <li>Очекуван излез: `false`</li>
    </ul>
  </li>
  <li>
    Тест случај за `!passwordLower.contains(" ")` и нема специјални знаци во лозинката:
    <ul>
      <li>Влез: `passwordLower = "password"`</li>
      <li>Очекуван излез: `false`</li>
    </ul>
  </li>
  <li>
    Тест случај за `!passwordLower.contains(" ")` и специјален знак во лозинката:
    <ul>
      <li>Влез: `passwordLower = "pass@word"`, `specialCharacters = "!#$%&amp;'()*+,-./:;&lt;=&gt;?@[]^_</code>{|}"`</li>
      <li>Очекуван излез: `same == 0`</li>
    </ul>
  </li>
</ol>
