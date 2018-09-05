---
title: Łańcucha standardowych operatorów zapytań razem (C#)
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 07cc6769646f8f3f924b488e30ce2415c587ebe0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520871"
---
# <a name="chaining-standard-query-operators-together-c"></a>Łańcucha standardowych operatorów zapytań razem (C#)
To jest ostatnim temacie w [samouczek: tworzenie łańcuchów zapytania ze sobą (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md) samouczka.  
  
 Standardowe operatory zapytań można również łączyć w łańcuch. Na przykład można interject <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operatora, a także działa w sposób z opóźnieniem. Nie wyników pośrednich zmaterializowanego są przez nią.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie <xref:System.Linq.Enumerable.Where%2A> metoda jest wywoływana przed wywołaniem `ConvertCollectionToUpperCase`. <xref:System.Linq.Enumerable.Where%2A> Metoda działa w prawie dokładnie tak samo jak z opóźnieniem metody używane w poprzednich przykładach w tym samouczku `ConvertCollectionToUpperCase` i `AppendString`.  
  
 Jedną różnicą jest to, że w tym przypadku <xref:System.Linq.Enumerable.Where%2A> metoda iteruje przez jej kolekcji źródłowej Określa pierwszy element nie zostały spełnione predykat, a następnie pobiera następny element przekazać. Daje drugiego elementu.  
  
 Podstawowa koncepcja jest jednak takie same: pośredni kolekcje nie są zmaterializowanego, chyba że mają być.  
  
 W przypadku używania wyrażeń zapytania są konwertowane na wywołania do standardowych operatorów zapytań i obowiązują te same zasady.  
  
 Wszystkie przykłady w tej sekcji, które są wykonywanie zapytań względem dokumentów Office Open XML używać tej samej zasadzie. Wykonanie odroczone i obliczanie z opóźnieniem przedstawiono niektóre podstawowe pojęcia, które należy poznać efektywne wykorzystanie LINQ (i LINQ to XML).  
  
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
        foreach (string str in source)  
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
            where s.CompareTo("D") >= 0  
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
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
## <a name="see-also"></a>Zobacz też

- [Samouczek: Tworzenie łańcuchów zapytań razem (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
