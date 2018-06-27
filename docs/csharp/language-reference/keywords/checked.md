---
title: Checked — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: e6c28ee0c575bd6010a8aad76fc978062c5fc6a4
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948413"
---
# <a name="checked-c-reference"></a>checked (odwołanie w C#)

`checked` Słowo kluczowe jest używane do jawnie włączyć sprawdzanie operacji arytmetycznych typem całkowitym i konwersje przepełnienia.

Domyślnie wyrażenie, które zawiera tylko wartości stałych powoduje wystąpi błąd kompilatora, jeśli wyrażenie zwraca wartość, która jest poza zakresem typu docelowego. Jeśli wyrażenie zawiera jedną lub więcej wartości niż stała, kompilator nie wykrywa przeciążenia. Obliczenie wyrażenia przypisane do `i2` w poniższym przykładzie nie powoduje błąd kompilatora.

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

Domyślnie wyrażenia te z systemem innym niż stała nie są sprawdzane dla przepełnienie w czasie wykonywania albo, a nie wywołuj wyjątków przepełnienia. Poprzedni przykład przedstawia-2,147,483,639 jako suma wartości dwie dodatnie liczby całkowite.

Sprawdzanie przepełnienia można włączyć opcji kompilatora, konfiguracji środowiska lub użycie `checked` — słowo kluczowe. W poniższych przykładach pokazano, jak używać `checked` wyrażenie lub `checked` bloku, aby wykryć przepełnienie, wytworzonego przez poprzednie sum w czasie wykonywania. Oba przykłady zgłosić wyjątek przepełnienia.

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

[Niezaznaczone](../../../csharp/language-reference/keywords/unchecked.md) — słowo kluczowe może służyć do zapobiec sprawdzanie przepełnienia.

## <a name="example"></a>Przykład

Ten przykład przedstawia sposób użycia `checked` umożliwiające przepełnienie sprawdzenie w czasie wykonywania.

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
[Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
[Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
[Checked i Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
[unchecked](../../../csharp/language-reference/keywords/unchecked.md)
