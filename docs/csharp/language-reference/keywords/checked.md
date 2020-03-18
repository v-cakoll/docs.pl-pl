---
title: zaznaczone słowo kluczowe - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 5963bb85ef4b61c1dc478667fb0e2e5438f3e4ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713707"
---
# <a name="checked-c-reference"></a>checked (odwołanie w C#)

Słowo `checked` kluczowe służy do jawnego włączania sprawdzania przepełnienia dla operacji arytmetycznych typu integralnego i konwersji.

Domyślnie wyrażenie, które zawiera tylko wartości stałe powoduje błąd kompilatora, jeśli wyrażenie tworzy wartość, która znajduje się poza zakresem typu docelowego. Jeśli wyrażenie zawiera co najmniej jedną niestałą wartość, kompilator nie wykrywa przepełnienia. Ocena wyrażenia przypisanego `i2` do w poniższym przykładzie nie powoduje błędu kompilatora.

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

Domyślnie te wyrażenia niestałe nie są sprawdzane pod kątem przepełnienia w czasie wykonywania i nie zgłaszają wyjątków przepełnienia. W poprzednim przykładzie jest wyświetlana wartość -2,147,483,639 jako suma dwóch dodatnich liczb całkowitych.

Sprawdzanie przepełnienia można włączyć za pomocą opcji kompilatora, konfiguracji środowiska lub użycia słowa kluczowego. `checked` W poniższych przykładach pokazano, jak użyć `checked` wyrażenia lub `checked` bloku do wykrywania przepełnienia, który jest produkowany przez poprzednią sumę w czasie wykonywania. Oba przykłady zgłaszają wyjątek przepełnienia.

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

[Niezaznaczone](./unchecked.md) słowo kluczowe może służyć do zapobiegania sprawdzaniu przepełnienia.

## <a name="example"></a>Przykład

W tym przykładzie `checked` pokazano, jak włączyć sprawdzanie przepełnienia w czasie wykonywania.

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Checked i Unchecked](./checked-and-unchecked.md)
- [unchecked](./unchecked.md)
