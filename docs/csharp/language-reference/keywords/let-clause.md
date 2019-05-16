---
title: Let — klauzula - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: e9e10957e7ebe93a6dea9bbb6233ca7733f68e20
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633458"
---
# <a name="let-clause-c-reference"></a>Klauzula Let (odwołanie w C#)

W wyrażeniu zapytania jest czasami warto przechowywać wyników wyrażeń podrzędnych do jej używania w kolejnych klauzul. Można to zrobić za pomocą `let` słowo kluczowe, które tworzy nową zmienną zakresu i inicjuje ją z wynikiem wyrażenia dostarczasz. Po zainicjowaniu z wartością, zmienna zakresu nie może służyć do przechowywania inną wartość. Jednakże jeśli typ odpytywalny jest przechowywana w zmiennej zakresu, może być badana.

## <a name="example"></a>Przykład

W poniższym przykładzie `let` jest używany na dwa sposoby:

1. Aby utworzyć typ wyliczalny, który sam można wykonywać zapytania.

2. Aby włączyć zapytanie, aby wywołać `ToLower` tylko jeden raz na zmiennej zakresu `word`. Bez użycia `let`, trzeba wywoływać `ToLower` w każdej predykat w `where` klauzuli.

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../language-reference/index.md)
- [Słowa kluczowe zapytania (LINQ)](query-keywords.md)
- [Language Integrated Query (LINQ)](../../linq/index.md)
- [Wprowadzenie do korzystania z LINQ w C#](../../programming-guide/concepts/linq/getting-started-with-linq.md)
- [Obsługa wyjątków w wyrażeniach zapytań](../../linq/handle-exceptions-in-query-expressions.md)
