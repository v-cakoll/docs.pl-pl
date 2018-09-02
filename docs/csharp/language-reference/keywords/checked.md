---
title: Checked — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 892b24b0283314f5aded0405df55a93069cf91e2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404032"
---
# <a name="checked-c-reference"></a>checked (odwołanie w C#)

`checked` Słowo kluczowe jest używane, aby jawnie włączyć sprawdzanie typu całkowitego operacjach arytmetycznych i konwersjach przepełnienia.

Domyślnie wyrażenie, które zawiera tylko wartości stałych powoduje błąd kompilatora, jeśli wyrażenie generują wartość, która znajduje się poza zakresem typu docelowego. Jeśli wyrażenie zawiera co najmniej jedną wartość niebędącą stałą, kompilator nie może wykryć przepełnienia. Obliczenie wyrażenia przypisane do `i2` w poniższym przykładzie nie powoduje błędu kompilatora.

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

Domyślnie te wyrażenia niestałe nie są sprawdzane na przepełnienie w czasie wykonywania albo, a nie zgłaszaj wyjątków przepełnienia. Poprzedni przykład wyświetla-2,147,483,639 jako suma dwie dodatnie liczby całkowite.

Sprawdzanie przepełnienia może włączyć opcje kompilatora, konfiguracji środowiska i użyciem `checked` — słowo kluczowe. W poniższych przykładach pokazano sposób użycia `checked` wyrażenie lub `checked` bloku, aby wykryć przepełnienia, który jest wytwarzany przez poprzednie sum w czasie wykonywania. Oba przykłady zgłosić wyjątek przepełnienia.

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

[Unchecked](../../../csharp/language-reference/keywords/unchecked.md) — słowo kluczowe może służyć do uniemożliwić sprawdzanie przepełnienia.

## <a name="example"></a>Przykład

Ten przykład ilustruje sposób używania `checked` umożliwiające przepełnienie sprawdzanie w czasie wykonywania.

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [Checked i Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
- [unchecked](../../../csharp/language-reference/keywords/unchecked.md)
