---
title: "Pośredni Materialization (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 46d347921e24bc5504c69534d7b5c087818a6c7f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="intermediate-materialization-c"></a>Pośredni Materialization (C#)
Jeśli nie są dokładne, w niektórych sytuacjach można znacząco zmienić profil pamięci i wydajność aplikacji powodując przedwczesne materialization kolekcji zapytania. Niektóre standardowe operatory zapytań spowodować materialization ich kolekcji źródłowej przed reaguje pojedynczy element. Na przykład <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> najpierw iteruje po kolekcji jego całą źródłową, a następnie sortuje wszystkie elementy i ostatecznie zwraca pierwszy element. To oznacza, że jest kosztowne uzyskać pierwszy element uporządkowaną kolekcję; Każdy element nie jest następnie kosztowne. Jest to logiczne: byłoby niemożliwe dla operatora zapytania nie.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie powoduje zmianę poprzedniego przykładu. `AppendString` Wywołania metody <xref:System.Linq.Enumerable.ToList%2A> przed iteracji w źródle. Powoduje to materialization.  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        // the following statement materializes the source collection in a List<T>  
        // before iterating through it  
        foreach (string str in source.ToList())  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
ToUpper: source >abc<  
ToUpper: source >def<  
ToUpper: source >ghi<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 W tym przykładzie można stwierdzić, że wywołanie <xref:System.Linq.Enumerable.ToList%2A> powoduje, że `AppendString` wyliczyć całego źródła przed reaguje pierwszego elementu. Jeśli źródło dużą tablicę, to znacznie zmieniłaby profilu pamięci aplikacji.  
  
 Standardowe operatory zapytań można również zostaną połączone. Końcowe tematu w tym samouczku przedstawiono to.  
  
-   [CBC standardowych operatorów zapytań razem (C#)](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek: Tworzenie łańcuchów zapytań razem (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
