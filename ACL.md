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

<<<<<<< HEAD
![ACL1](mages/ACL1.PNG)
=======
![ACL1](Images/ACL1.PNG)

> > > > > > > f2d25544ab3200999564221fbd13a025b7fe9010

## Apply a Standard ACL to an Interface

```
interface f0/0
ip access-group {access-list-number | access-list-name} {in | out}
```

### Standard ACL Sample

<<<<<<< HEAD
![ACL2](mages/ACL2.PNG)
=======
![ACL2](Images/ACL2.PNG)

> > > > > > > f2d25544ab3200999564221fbd13a025b7fe9010
> > > > > > > \*\* _Remarks only show in the running config and not displayed here_
