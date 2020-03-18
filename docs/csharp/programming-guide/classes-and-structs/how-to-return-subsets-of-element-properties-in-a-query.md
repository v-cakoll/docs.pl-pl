---
title: Jak zwrócić podzestawy właściwości elementu w kwerendzie — Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 27a2626fc46307a7195040adf746d8d8757d2f82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714857"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Jak zwrócić podzestawy właściwości elementu w kwerendzie (Przewodnik programowania C#)
Użyj typu anonimowego w wyrażeniu kwerendy, gdy obowiązują oba te warunki:  
  
- Chcesz zwrócić tylko niektóre właściwości każdego elementu źródłowego.  
  
- Nie trzeba przechowywać wyniki kwerendy poza zakresem metody, w którym kwerenda jest wykonywana.  
  
 Jeśli chcesz zwrócić tylko jedną właściwość lub pole z każdego elementu źródłowego, `select` można po prostu użyć operatora kropki w klauzuli. Na przykład, aby `ID` zwrócić `student`tylko z `select` każdego , należy napisać klauzulę w następujący sposób:  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak użyć typu anonimowego, aby zwrócić tylko podzbiór właściwości każdego elementu źródłowego, który pasuje do określonego warunku.  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 Należy zauważyć, że typ anonimowy używa nazwy elementu źródłowego dla jego właściwości, jeśli nie określono nazwy. Aby nadać nowe nazwy właściwościom typu anonimowego, należy napisać instrukcję w `select` następujący sposób:  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Jeśli spróbujesz tego w `Console.WriteLine` poprzednim przykładzie, instrukcja musi również ulec zmianie:  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
Aby uruchomić ten kod, skopiuj i wklej `using` klasę do aplikacji konsoli C# z dyrektywą dla System.Linq.
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Typy anonimowe](./anonymous-types.md)
- [LINQ w C#](../../linq/index.md)
