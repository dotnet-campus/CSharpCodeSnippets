# CSharpCodeSnippets

collections of C# code snippets

## 带通知属性

提供带通知的属性，快捷键 `props` 需要使用的类继承 `INotifyPropertyChanged` 

```csharp
        /// <summary>
        /// 获取设置 Str 
        /// </summary>
        public string Str
        {
            set => SetValue(ref _str, value);
            get => _str;
        }

        private string _str;
```

SetValue 是自己写的方法

```csharp
        protected void SetValue<T>(ref T filed, T value, [CallerMemberName] string propertyName = null)
        {
            if (Equals(filed, value))
                return;
            filed = value;
            OnPropertyChanged(propertyName);
        }
```

