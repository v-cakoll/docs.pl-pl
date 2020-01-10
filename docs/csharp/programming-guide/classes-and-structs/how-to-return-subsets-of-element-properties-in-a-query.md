---
title: Jak zwrócić podzbiory właściwości elementu w przewodniku C# programowania zapytań
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 27a2626fc46307a7195040adf746d8d8757d2f82
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714857"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Jak zwrócić podzbiory właściwości elementu w zapytaniu (C# Przewodnik programowania)
Użyj typu anonimowego w wyrażeniu zapytania, jeśli są spełnione oba te warunki:  
  
- Chcesz zwrócić tylko niektóre właściwości każdego elementu źródłowego.  
  
- Nie jest konieczne przechowywanie wyników zapytania poza zakresem metody, w której jest wykonywane zapytanie.  
  
 Jeśli chcesz zwrócić tylko jedną właściwość lub pole z każdego elementu źródłowego, możesz po prostu użyć operatora kropki w klauzuli `select`. Aby na przykład zwrócić tylko `ID` poszczególnych `student`, należy napisać klauzulę `select` w następujący sposób:  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać typu anonimowego, aby zwrócić tylko podzestaw właściwości każdego elementu źródłowego, który jest zgodny z określonym warunkiem.  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 Należy pamiętać, że typ anonimowy używa nazw elementów źródłowych dla jego właściwości, jeśli nie określono żadnych nazw. Aby nadać nowym nazw właściwościom typu anonimowego, należy napisać instrukcję `select` w następujący sposób:  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Jeśli spróbujesz użyć tego w poprzednim przykładzie, należy również zmienić instrukcję `Console.WriteLine`:  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
Aby uruchomić ten kod, skopiuj i wklej klasę do aplikacji C# konsolowej z `using` dyrektywie for System. LINQ.
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Typy anonimowe](./anonymous-types.md)
- [LINQ w C#](../../linq/index.md)
