---
layout: post
title: C# ??運算子
date: 2019-03-15 22:15
categories: [Dotnet, CSharp]
---

`??`運算子稱為 null 聯合運算子。如果運算元不是 null，則會傳回左方運算元，否則傳回右方運算元

在 C#中執行 ToString 的方法大部分都不會有問題，但值為 `null 執行 ToString 就會有問題`

```csharp
public class Program
{
	public static void Main()
	{
		string str1 = null;
		string str2 = str1.ToString(); // 發生NullReferenceException的例外錯誤
		Console.WriteLine(str2);
	}
}
```

所以必須在執行 ToString 前做一些檢查動作

### 方法一： 使用三元運算子避免

```csharp
public class Program
{
	public static void Main()
	{
		string str1 = null;
		string str2 = str1 == null ? "Empty" : str1.ToString();
		Console.WriteLine($"str2 is {str2}"); //str2 is Empty
	}
}
```

### 方法二： 使用?? operator

因為在括號內會先判斷左邊的運算元是否為 null，假如為 null 則回傳右方運算元

```csharp
public class Program
{
	public static void Main()
	{
		string str1 = null;
		string str2 = (str1 ?? "Empty").ToString();
		Console.WriteLine($"str2 is {str2}"); //str2 is Empty
	}
}
```

使用?? operator 的方式感覺更簡單 Code 也更簡潔了

參考資料：

- [?? operator](https://docs.microsoft.com/zh-tw/dotnet/csharp/language-reference/operators/null-coalescing-operator)
- [c# – 在 ToString()之前检查 null](https://codeday.me/bug/20170712/36415.html)
