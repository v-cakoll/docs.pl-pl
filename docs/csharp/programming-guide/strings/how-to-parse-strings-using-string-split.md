---
title: "Porady: analizowanie ciągów za pomocą String.Split (C# przewodnik programowania w języku)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b97d1d89a4c74a4c759d1ed41a0bc2476b3b07a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-parse-strings-using-stringsplit-c-programming-guide"></a>Porady: analizowanie ciągów za pomocą String.Split (C# przewodnik programowania w języku)
W poniższym przykładzie kodu pokazano, jak ciąg można analizować przy użyciu <xref:System.String.Split%2A?displayProperty=nameWithType> metody. Jako dane wejściowe <xref:System.String.Split%2A> pobiera tablicę znaków, które wskazują znaki rozdzielania interesujące ciągów sub ciągu docelowego.  Funkcja zwraca tablicę ciągów sub.  
  
 W tym przykładzie użyto spacji, przecinków, okresów, dwukropki i karty wszystkie przekazana tablica zawierająca te oddzielanie znaków do <xref:System.String.Split%2A>.  Każdego wyrazu w zdaniu ciąg docelowego Wyświetla oddzielnie od wynikowy tablicy ciągów.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideStrings#16](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-parse-strings-using-string-split_1.cs)]  
  
## <a name="example"></a>Przykład  
 Domyślnie String.Split zwraca puste ciągi, gdy dwa znaki rozdzielające ciągłym pojawią się w ciągu docelowego.  Można przekazać parametr opcjonalny StringSplitOptions.RemoveEmptyEntries do wykluczenia żadnych pustych ciągów w danych wyjściowych.  
  
 String.Split może być tablicą ciągów (sekwencji znaków, które działają jako separatorów do analizowania parametrów docelowej, zamiast pojedynczy znaki).  
  
```csharp  
class TestStringSplit  
{  
    static void Main()  
    {  
        string[] separatingChars = { "<<", "..." };  
  
        string text = "one<<two......three<four";  
        System.Console.WriteLine("Original text: '{0}'", text);  
  
        string[] words = text.Split(separatingChars, System.StringSplitOptions.RemoveEmptyEntries );  
        System.Console.WriteLine("{0} substrings in text:", words.Length);  
  
        foreach (string s in words)  
        {  
            System.Console.WriteLine(s);  
        }  
  
        // Keep the console window open in debug mode.  
        System.Console.WriteLine("Press any key to exit.");  
        System.Console.ReadKey();  
    }  
}  
/* Output:  
    Original text: 'one<<two......three<four'  
    3 words in text:  
    one  
    two  
    three<four  
*/  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Ciągi](../../../csharp/programming-guide/strings/index.md)  
 [.NET framework — nieprawidłowe wyrażenia](https://msdn.microsoft.com/library/hs600312)
