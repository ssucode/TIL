### SQL Injection(sql 삽입 공격)이란?
- **악의적인 사용자가 임의의 SQL문을 주입하여 말 그대로 그 SQL로 데이터베이스가 비정상적인 동작을 하도록 조작하는 행위**

#### 취약한 Query
```Php
function getUserById($id) {
    $sql = "SELECT * FROM users WHERE id=$id;";
    $query = $this->db->query($sql);
    return $query->result();
}
```

### 해결방법
기본적으로 CodeIgniter 의 **ActiveRecord** 를 사용, 사용이 불가할 경우 **$this->db->escape** 를 권장합니다.
- ActiveRecord
    - 자동으로 보호 처리가 됨.
    - https://www.codeigniter.com/userguide2/database/active_record.html
```Php
function getUserById($id) {
    $this->db->select(*);
    $this->db->from(users);
    $this->db->where('id', $id);
    $query = $this->db->get();
    return $query->result();
}
```

- Escaping Queries
    - $this->db->escape($data);
```Php
function getUserById($id) {
    $sql = "SELECT * FROM users WHERE id='".$this->db->escape($id)."';";
    $query = $this->db->query($sql);
    return $query->result();
}
```

- PreparedStatement(데이터 바인딩)
    - ? 를 데이터로 치환
    - $this->db->query($sql, array($data));
```Php
function getUserById($id) {
    $sql = "SELECT * FROM users WHERE id=?;";
    $query = $this->db->query($sql, array($id));
    return $query->result();
}
```
