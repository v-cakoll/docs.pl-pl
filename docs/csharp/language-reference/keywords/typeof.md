---
title: "typeof (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords: typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: be24740ea7f6fbe8780dd9cac58b7dea9aaf6872
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="typeof-c-reference"></a>typeof (odwołanie w C#)
Używany do uzyskania `System.Type` obiektu dla typu. A `typeof` wyrażenie ma następującą postać:  
  
```  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać typu run-time wyrażenia, można użyć metody .NET Framework <xref:System.Object.GetType%2A>, jak w poniższym przykładzie:  
  
```  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 `typeof` Operator nie może być przeciążony.  
  
 `typeof` Operatora można używać na otwieranie typów ogólnych. Typy z więcej niż jeden parametr typu musi mieć odpowiednią liczbę przecinków w specyfikacji. Poniższy przykład przedstawia sposób ustalić, czy typ zwracany metody jest rodzajowy <xref:System.Collections.Generic.IEnumerable%601>. Załóżmy, że metoda jest wystąpieniem typu MethodInfo:  
  
```  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## <a name="example"></a>Przykład  
 W przykładzie użyto <xref:System.Object.GetType%2A> metodę, aby określić typ, który zawiera wynik obliczenia liczbowych. Zależy to od liczby wynikowy wymagania dotyczące magazynu.  
  
 [!code-csharp[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Type?displayProperty=nameWithType>  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [jest](../../../csharp/language-reference/keywords/is.md)  
 [Słowa kluczowe operatora](../../../csharp/language-reference/keywords/operator-keywords.md)
