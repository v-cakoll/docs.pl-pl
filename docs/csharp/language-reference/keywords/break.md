---
title: instrukcja break - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: ef276fd9e8da0ea25695c5afdf06a300bbd2a123
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713750"
---
# <a name="break-c-reference"></a>break (odwołanie w C#)

Instrukcja `break` kończy najbliższą otaczającej pętli lub [switch](./switch.md) instrukcji, w którym pojawia się. Formant jest przekazywany do instrukcji, która następuje zakończone instrukcji, jeśli istnieje.

## <a name="example"></a>Przykład

W tym przykładzie instrukcja warunkowa zawiera licznik, który ma liczyć od 1 do 100; jednak instrukcja `break` kończy pętlę po 4 liczy.

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a>Przykład

W tym przykładzie przedstawiono `break` użycie w [instrukcji switch.](./switch.md)

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

Jeśli wprowadzono, `4`wyjście będzie:

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a>Przykład

W tym przykładzie `break` instrukcja jest używana do wyrwania się z wewnętrznej pętli zagnieżdżonej i przywrócenia formantu do pętli zewnętrznej. Formant jest zwracany _tylko_ jeden poziom w górę w pętli zagnieżdżonych.

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a>Przykład

W tym przykładzie `break` instrukcja jest używana tylko do wyrwania się z bieżącej gałęzi podczas każdej iteracji pętli. Sama pętla nie ma wpływu `break` przez wystąpienia, które należą do zagnieżdżonej [instrukcji switch.](./switch.md)

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Przełącznik](./switch.md)
