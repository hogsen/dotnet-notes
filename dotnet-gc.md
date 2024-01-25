# 释放非托管资源

dispose()方法可以释放托管和非托管资源
using 语句会自动调用 dispose 方法
在析构函数中调用 dispose 方法
在 finally 块中调用 dispose 方法
尽量避免使用析构函数

```cs
using System.Diagnostics;

// 使用using dispose会自动调用
using (TestDispose ts = new())
{
  ts.Show();

}
class TestDispose : IDisposable
{
  public TestDispose()
  {
    Debug.WriteLine("Constructor called");
  }
  ~TestDispose()
  {
    Debug.WriteLine("Finalizer called");
  }
  public void Dispose()
  {
    Debug.WriteLine("Dispose called");
  }
  public void Show()
  {
    Debug.WriteLine("Show called");
  }
}
```
