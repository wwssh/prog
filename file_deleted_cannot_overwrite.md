#### 可执行文件启动进程运行后不予续overwrite但是允许rm

覆盖时提示，Text file busy，查一下看到对应的错误码是ETXTBSY， 可以通过 lsof ceph-mds看到打开情况。