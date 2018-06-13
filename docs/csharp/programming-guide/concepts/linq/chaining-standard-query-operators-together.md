---
title: CBC standardowych operatorów zapytań razem (C#)
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 9e59c12873b8e8afeaad43b8ffbe400b43b55747
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33326153"
---
# <a name="chaining-standard-query-operators-together-c"></a>CBC standardowych operatorów zapytań razem (C#)
Jest ostatnim tematu w [samouczek: tworzenie łańcuchów zapytań razem (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md) samouczka.  
  
 Standardowe operatory zapytań można również zostaną połączone. Na przykład można interject <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operatora, a także działa w sposób opóźnieniem. Brak wyników pośrednich materializować są przez nią.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie <xref:System.Linq.Enumerable.Where%2A> metoda jest wywoływana przed wywołaniem `ConvertCollectionToUpperCase`. <xref:System.Linq.Enumerable.Where%2A> Metoda działa w prawie dokładnie tak samo jak opóźnieniem metody używane w poprzednich przykładach, w tym samouczku `ConvertCollectionToUpperCase` i `AppendString`.  
  
 Jedną różnicą jest to, że w takim przypadku <xref:System.Linq.Enumerable.Where%2A> metody iteruje po jego kolekcji źródłowej Określa pierwszy element predykatu nie zostały spełnione, a następnie pobiera następnego elementu przekazywania. Powoduje ona następnie drugiego elementu.  
  
 Jednak podstawową koncepcją jest taka sama: pośredni kolekcje nie są zmaterializowany, chyba że mają być.  
  
 W przypadku używania wyrażenia zapytania są konwertowane na wywołania standardowych operatorów zapytań i Zastosuj te same zasady.  
  
 Przykłady w tej sekcji, w których jest kwerenda dokumentów pakietu Office Open XML używają tej samej zasadzie. Wykonanie odroczone i obliczanie leniwe przedstawiono niektóre podstawowe założenia, że rozumiesz musi wykorzystywać LINQ (i LINQ do XML).  
  
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
 [Samouczek: Tworzenie łańcuchów zapytań razem (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
