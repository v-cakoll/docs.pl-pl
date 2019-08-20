---
title: instrukcja break- C# Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 77d18d12cd0fabb26906a5b58dc3939da6214a29
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602245"
---
# <a name="break-c-reference"></a>break (odwołanie w C#)

Instrukcja kończy najbliższą otaczającą pętlę lub instrukcję Switch, w której występuje. [](./switch.md) `break` Kontrolka jest przenoszona do instrukcji, która następuje po instrukcji zakończony (jeśli istnieje).

## <a name="example"></a>Przykład

W tym przykładzie Instrukcja warunkowa zawiera licznik, który powinien być liczony od 1 do 100; `break` Jednakże instrukcja kończy pętlę po 4 zliczenia.

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a>Przykład

W tym przykładzie `break` instrukcja jest używana do przerywania wewnętrznej pętli zagnieżdżonej i zwracania kontroli do pętli zewnętrznej.

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a>Przykład

Ten przykład ilustruje użycie `break` w instrukcji [Switch](./switch.md) .

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

W przypadku wprowadzenia `4`danych wyjściowych będzie:

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [switch](./switch.md)
