---
title: 'Instrukcje: Zwracanie podzbiorów właściwości elementu w zapytaniu — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: da4ecb11c51f42c2297b6d40ed9a963590b3f441
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599992"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Instrukcje: Zwracanie podzbiorów właściwości elementu w zapytaniu (C# Programming Guide)
Użyj typu anonimowego w wyrażeniu zapytania, gdy oba te warunki zostaną spełnione:  
  
- Należy zwrócić tylko niektóre właściwości każdego elementu źródłowego.  
  
- Nie masz do przechowywania wyników zapytania poza zakresem metody wykonywania zapytania.  
  
 Jeśli chcesz tylko do zwrócenia jedną właściwość lub pole z każdego elementu źródłowego, a następnie można użyć operatora z dot `select` klauzuli. Na przykład, aby zwrócić tylko `ID` każdego `student`, zapis `select` klauzuli w następujący sposób:  
  
```  
select student.ID;  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak użyć typu anonimowego w celu zwracania tylko podzbiór właściwości każdego elementu źródłowego, który odpowiada określony warunek.  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 Pamiętaj, że typ anonimowy używa nazwy elementu źródłowego dla jego właściwości, jeśli nie określono żadnych nazw. Aby udostępnić nowe nazwy właściwości w typ anonimowy, należy napisać `select` instrukcji w następujący sposób:  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Jeśli spróbujesz to w poprzednim przykładzie, a następnie `Console.WriteLine` instrukcji należy także zmienić:  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Aby uruchomić ten kod, skopiuj i Wklej klasy Visual C# projekt aplikacji konsoli, która została utworzona w programie Visual Studio. Domyślnie ten projekt jest przeznaczony dla wersji 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], które będzie mieć odwołania do System.Core.dll i `using` dyrektywy dla System.Linq. Jeśli co najmniej jeden z tych wymagań brakuje z projektu, możesz je dodać ręcznie.   
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
