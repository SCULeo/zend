本版本主要工作是，将zend引擎检测代码的机制，从读取文件改写到能够直接识别字符串输入，
这个过程中需要在do_cli函数里面打断点，断点打在exit_status = php_lint_script(&file_handle);
修改file_handle.handle.buf的值，buf里面是用于检测的php代码部分。
for example :set file_handle.handle.buf="<html><body><h1>My first PHP page</h1><?php echo 123  \"Hello World!\";?></body></html>\n"
