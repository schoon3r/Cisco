# NUMBERED Standard ACL

## 1 - 99 | 1300 - 1999

```
access-list 10 {deny | permit | remark text} source [source-wildcard] [log]
```

# NAMED Standard ACL

## 1 - 99 | 1300 - 1999

```
ip access-list standard 'access-list-name'
```

![ACL1](../Images/ACL1.png)

## Apply a Standard ACL to an Interface

```
interface f0/0
ip access-group {access-list-number | access-list-name} {in | out}
```

### Standard ACL Sample

![ACL2](Images/ACL2.png)
\*\* _Remarks only show in the running config and not displayed here_
