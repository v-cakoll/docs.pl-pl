---
title: 'Instrukcje: Zwróć podzbiory właściwości elementu w przewodniku C# programowania zapytań'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 2c9fea2189819058187020c2e67b8826659fbed4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205446"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Instrukcje: Zwracanie podzbiorów właściwości elementu w zapytaniu (C# Przewodnik programowania)
Użyj typu anonimowego w wyrażeniu zapytania, jeśli są spełnione oba te warunki:  
  
- Chcesz zwrócić tylko niektóre właściwości każdego elementu źródłowego.  
  
- Nie jest konieczne przechowywanie wyników zapytania poza zakresem metody, w której jest wykonywane zapytanie.  
  
 Jeśli chcesz zwrócić tylko jedną właściwość lub pole z każdego elementu źródłowego, możesz po prostu użyć operatora kropki w `select` klauzuli. Aby na przykład zwrócić tylko te dane `ID` `student`, należy napisać `select` klauzulę w następujący sposób:  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać typu anonimowego, aby zwrócić tylko podzestaw właściwości każdego elementu źródłowego, który jest zgodny z określonym warunkiem.  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 Należy pamiętać, że typ anonimowy używa nazw elementów źródłowych dla jego właściwości, jeśli nie określono żadnych nazw. Aby nadać nowym nazw właściwościom typu anonimowego, należy napisać `select` instrukcję w następujący sposób:  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Jeśli spróbujesz użyć tego w poprzednim przykładzie, `Console.WriteLine` należy również zmienić instrukcję:  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
Aby uruchomić ten kod, skopiuj i wklej klasę do aplikacji C# konsolowej z `using` dyrektywą dla System. LINQ.
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Typy anonimowe](./anonymous-types.md)
- [Wyrażenia zapytania LINQ](../linq-query-expressions/index.md)
