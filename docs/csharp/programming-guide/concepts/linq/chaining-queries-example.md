---
title: "Tworzenie łańcuchów przykład kwerendy (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 74d3dcaca686487d79a90f28faf4d9c00218f6a2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="chaining-queries-example-c"></a>Tworzenie łańcuchów przykład kwerendy (C#)
W tym przykładzie jest oparty na poprzednim przykładzie i pokazuje, co się stanie w przypadku łańcucha ze sobą dwie kwerendę dotyczącą zarówno Użyj odroczonego wykonania i obliczanie leniwe.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wprowadzono inną metodę rozszerzenia, `AppendString`, które dołącza określony ciąg na ciąg, co w kolekcji źródłowej, a następnie daje nowych ciągów.  
  
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
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 W tym przykładzie widać, że każda metoda rozszerzenia działa jeden z nich, dla każdego elementu w kolekcji źródłowej.  
  
 Co powinno być wolne w tym przykładzie jest, mimo że firma Microsoft ma połączone zapytań, które zwracają kolekcje, żadne kolekcje pośredniego jest zmaterializowany. Zamiast tego każdy element jest przekazywany z jedną metodę opóźnieniem do następnego. Powoduje to mniejsze zużycie pamięci, niż metody, które będzie najpierw wykonać jedną tablicą ciągów, a następnie utworzyć drugi tablicy ciągów, który został przekonwertowany na wielkie litery, a na koniec Utwórz trzeci tablicy ciągów, gdzie każdy ciąg ma wykrzyknika punkty dołączone do niego.  
  
 Następnego tematu w tym samouczku przedstawiono materialization pośredniego:  
  
-   [Pośredni Materialization (C#)](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek: Tworzenie łańcuchów zapytań razem (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
