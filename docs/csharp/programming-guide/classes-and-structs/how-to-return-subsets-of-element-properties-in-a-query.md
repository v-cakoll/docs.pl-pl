---
title: 'Porady: zwracanie podzbiorów właściwości elementu w zapytaniu (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 3b43e7e3aafda5ee5b6a49f271f725fb8eeeca59
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Porady: zwracanie podzbiorów właściwości elementu w zapytaniu (Przewodnik programowania w języku C#)
Użyj typu anonimowego w wyrażeniu zapytania, gdy oba te warunki mają zastosowanie:  
  
-   Chcesz przywrócić tylko niektóre właściwości każdego elementu źródłowego.  
  
-   Nie masz do przechowywania wyników zapytania poza zakresem metody wykonywania zapytania.  
  
 Jeśli chcesz zwracać jedną właściwość lub pole z każdego elementu źródłowego, a następnie można użyć kropka w `select` klauzuli. Na przykład, aby zwrócić tylko `ID` każdego `student`, zapisać `select` klauzuli w następujący sposób:  
  
```  
select student.ID;  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie typu anonimowego na zwracanie tylko podzestawu właściwości każdego elementu źródłowego odpowiadający określony warunek.  
  
 [!code-csharp[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]  
  
 Należy pamiętać, że typu anonimowego korzysta z nazw elementu źródła jego właściwości, jeśli nie określono żadnych nazw. Aby udostępnić nowe nazwy właściwości w typ anonimowy, należy zapisać `select` instrukcji w następujący sposób:  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Jeśli spróbujesz to w poprzednim przykładzie, a następnie `Console.WriteLine` także zmienić instrukcji:  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Aby uruchomić ten kod, skopiuj i Wklej klasy w projektach Visual C# console aplikacji utworzony w programie Visual Studio. Domyślnie ten projekt jest przeznaczony dla wersji 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], i ma on odwołania do System.Core.dll i `using` dyrektywy dla System.Linq. Jeśli co najmniej jeden z tych wymagań brakuje z projektu, należy je dodać ręcznie.   
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
