---
title: Pośredni materializację (C#)
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: 273cd68b9714287f259e763c9b7c534aac1931e6
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592134"
---
# <a name="intermediate-materialization-c"></a>Pośredni materializację (C#)
Jeśli nie jest to dokładne, w niektórych sytuacjach można radykalnie zmienić profil pamięci i wydajności aplikacji, powodując przedwcześnie materializację kolekcji w zapytaniach. Niektóre standardowe operatory zapytań powodują materializację kolekcji źródłowej przed uzyskaniem pojedynczego elementu. Na przykład program <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> najpierw wykonuje iterację w całej kolekcji źródłowej, sortuje wszystkie elementy, a następnie zwraca pierwszy element. Oznacza to, że jest kosztowne uzyskanie pierwszego elementu kolekcji uporządkowanej; Każdy element nie jest kosztowny. Ma to sens: Wykonanie tej czynności przez operatora kwerendy może być niemożliwe.  
  
## <a name="example"></a>Przykład  
 Ten przykład zmienia poprzedni przykład. `AppendString` Metoda wywołuje<xref:System.Linq.Enumerable.ToList%2A> przed iteracją w źródle. Powoduje to materializację.  
  
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
  
 W tym przykładzie można zobaczyć, że wywołanie <xref:System.Linq.Enumerable.ToList%2A> powoduje `AppendString` Wyliczenie całego źródła przed uzyskaniem pierwszego elementu. Jeśli źródłem była duża tablica, znacznie zmienia profil pamięci aplikacji.  
  
 Standardowe operatory zapytań można również łączyć ze sobą. Ten samouczek ilustruje ostatni temat w tym samouczku.  
  
- [Łączenie standardowych operatorów zapytań (C#)](./chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a>Zobacz także

- [Samouczek: Łączenie łańcuchowe zapytań (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
