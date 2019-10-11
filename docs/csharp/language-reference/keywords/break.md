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
ms.openlocfilehash: 2628da73364cf94a52e2862d349243c100d4afaf
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179936"
---
# <a name="break-c-reference"></a>Break (C# odwołanie)

Instrukcja `break` kończy najbliższą otaczającą pętlę lub instrukcję [Switch](./switch.md) , w której występuje. Kontrolka jest przenoszona do instrukcji, która następuje po instrukcji zakończony (jeśli istnieje).

## <a name="example"></a>Przykład

W tym przykładzie Instrukcja warunkowa zawiera licznik, który powinien być liczony od 1 do 100; Jednakże instrukcja `break` przerywa pętlę po 4 zliczenia.

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a>Przykład

W tym przykładzie pokazano sposób użycia `break` w instrukcji [Switch](./switch.md) .

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

W przypadku wprowadzenia `4` dane wyjściowe byłyby następujące:

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a>Przykład

W tym przykładzie instrukcja `break` jest używana do przerywania wewnętrznej pętli zagnieżdżonej i zwracania kontroli do pętli zewnętrznej. Formant jest zwracany _tylko_ jeden poziom w pętli zagnieżdżonych.

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a>Przykład

W tym przykładzie instrukcja `break` jest używana tylko do rozbicia z bieżącej gałęzi podczas każdej iteracji pętli. Wystąpienia `break` nie wpływają na samą pętlę, która należy do zagnieżdżonej instrukcji [Switch](./switch.md) .

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a>C#Specyfikacja języka

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [C#Odwoła](../index.md)
- [C#Przewodnik programowania](../../programming-guide/index.md)
- [C#Służąc](./index.md)
- [przełącznika](./switch.md)
