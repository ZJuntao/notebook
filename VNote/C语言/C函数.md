# 函数
## 1. glob函数
* 接口：
```c
#include <glob.h>
int glob(const char *pattern, int flags,
        int (*errfunc) (const char *epath, int eerrno),
        glob_t *pglob);
void globfree(glob_t *pglob);
```
* 功能：
>Linux文件系统中路径名称的模式匹配，即查找文件系统中指定模式的路径。
* 参数：
>pattern： 匹配模型。如/*是匹配根文件下的所有文件（不包括隐藏文件，要找的隐藏文件需要从新匹配）
>errfunc： 选择匹配模式。
>errfunc:：查看错误信息用，一般置为NULL
>pglob：存放匹配出的结果 
* 结构体：
```c
        typedef struct {
               size_t   gl_pathc;    /* Count of paths matched so far  */
               char   **gl_pathv;    /* List of matched pathnames.  */
               size_t   gl_offs;     /* Slots to reserve in gl_pathv.  */
           } glob_t;
```
## 2. strtok函数
* 接口：
```c
#include<string.h>
char *strtok(char *str, const char *delim)
```
* 功能：
>分解字符串 str 为一组字符串，delim 为分隔符
* 参数：
>str -- 要被分解成一组小字符串的字符串
>delim -- 包含分隔符的 C 字符串
* 返回值：
>该函数返回被分解的第一个子字符串，如果没有可检索的字符，则返回一个空指针