---
title: 'Porady: zwracanie podzbiorów właściwości elementu w zapytaniu (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 3b43e7e3aafda5ee5b6a49f271f725fb8eeeca59
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39198172"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Porady: zwracanie podzbiorów właściwości elementu w zapytaniu (Przewodnik programowania w języku C#)
Użyj typu anonimowego w wyrażeniu zapytania, gdy oba te warunki zostaną spełnione:  
  
-   Należy zwrócić tylko niektóre właściwości każdego elementu źródłowego.  
  
-   Nie masz do przechowywania wyników zapytania poza zakresem metody wykonywania zapytania.  
  
 Jeśli chcesz tylko do zwrócenia jedną właściwość lub pole z każdego elementu źródłowego, a następnie można użyć operatora z dot `select` klauzuli. Na przykład, aby zwrócić tylko `ID` każdego `student`, zapis `select` klauzuli w następujący sposób:  
  
```  
select student.ID;  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak użyć typu anonimowego w celu zwracania tylko podzbiór właściwości każdego elementu źródłowego, który odpowiada określony warunek.  
  
 [!code-csharp[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]  
  
 Pamiętaj, że typ anonimowy używa nazwy elementu źródłowego dla jego właściwości, jeśli nie określono żadnych nazw. Aby udostępnić nowe nazwy właściwości w typ anonimowy, należy napisać `select` instrukcji w następujący sposób:  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Jeśli spróbujesz to w poprzednim przykładzie, a następnie `Console.WriteLine` instrukcji należy także zmienić:  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Aby uruchomić ten kod, skopiuj i Wklej klasy Visual C# projekt aplikacji konsoli, która została utworzona w programie Visual Studio. Domyślnie ten projekt jest przeznaczony dla wersji 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], które będzie mieć odwołania do System.Core.dll i `using` dyrektywy dla System.Linq. Jeśli co najmniej jeden z tych wymagań brakuje z projektu, możesz je dodać ręcznie.   
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
