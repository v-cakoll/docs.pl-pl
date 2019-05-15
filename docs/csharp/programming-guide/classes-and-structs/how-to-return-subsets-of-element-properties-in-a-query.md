---
title: 'Instrukcje: Zwracanie podzbiorów właściwości elementu w zapytaniu — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: acff804d87d67bf8758b97ad04805359bb3f2e32
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586068"
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
  
Aby uruchomić ten kod, skopiuj i Wklej klasy do C# aplikacji przy użyciu konsoli `using` dyrektywy dla System.Linq.
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
