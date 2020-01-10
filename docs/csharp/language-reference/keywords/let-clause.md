---
title: klauzula Let- C# Reference
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 32bb5d2138c0b86bf58d26015aa208f655229129
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715226"
---
# <a name="let-clause-c-reference"></a>Klauzula Let (odwołanie w C#)

W wyrażeniu zapytania czasami warto przechowywać wynik wyrażenia podrzędnego w celu użycia go w kolejnych klauzulach. Można to zrobić za pomocą słowa kluczowego `let`, które tworzy nową zmienną zakresu i inicjuje ją z wynikiem podania wyrażenia. Po zainicjowaniu z wartością zmienna zakresu nie może być używana do przechowywania innej wartości. Jeśli jednak zmienna zakresu zawiera typ queryable, może to być zapytanie.

## <a name="example"></a>Przykład

W poniższym przykładzie `let` jest używany na dwa sposoby:

1. Aby utworzyć wyliczalny typ, który może być badany.

2. Aby włączyć wywołanie kwerendy `ToLower` tylko jeden raz w zmiennej zakresu `word`. Bez korzystania z `let`należy wywołać `ToLower` w każdym predykacie w klauzuli `where`.

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../language-reference/index.md)
- [Słowa kluczowe zapytania (LINQ)](query-keywords.md)
- [Language Integrated Query (LINQ)](../../linq/index.md)
- [Wprowadzenie do korzystania z LINQ w C#](/dotnet/csharp/programming-guide/concepts/linq/)
- [Obsługa wyjątków w wyrażeniach zapytań](../../linq/handle-exceptions-in-query-expressions.md)
