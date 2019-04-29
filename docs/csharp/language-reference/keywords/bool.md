---
title: bool — słowo kluczowe - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: d87da29872582e9c0d47a6c999312ce88252a5cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662078"
---
# <a name="bool-c-reference"></a>bool (odwołanie w C#)

`bool` — Słowo kluczowe jest aliasem <xref:System.Boolean?displayProperty=nameWithType>. Służy do deklarowania zmiennych do przechowywania wartości logiczne: [true](true-literal.md) i [false](false-literal.md).

> [!NOTE]
> Użyj `bool?` typu, jeśli wymagana jest obsługa przechowywanymi w trzech logiki, na przykład podczas pracy z bazami danych, które obsługują przechowywanymi w trzech typu Boolean. Dla `bool?` argumentów operacji, wstępnie zdefiniowane `&` i `|` Operatorzy pomocy technicznej przechowywanymi w trzech logiki. Aby uzyskać więcej informacji, zobacz [Nullable logiczna operatorów logicznych](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) części [logiczna operatorów logicznych](../operators/boolean-logical-operators.md) artykułu.

## <a name="literals"></a>Literały

Można przypisać wartość logiczną umożliwiającą `bool` zmiennej. Można także przypisać wyrażenie, które daje w wyniku `bool` do `bool` zmiennej.

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

Wartość domyślna `bool` zmienna jest `false`. Wartość domyślna `bool?` zmienna jest `null`.

## <a name="conversions"></a>Konwersje

W języku C++, wartości typu `bool` można przekonwertować na wartość typu `int`; innymi słowy, `false` jest odpowiednikiem zero i `true` jest odpowiednikiem wartości niezerowych. W języku C# jest konwersja między `bool` typu a innymi typami danych. Na przykład następująca `if` instrukcja jest nieprawidłowa w języku C#:

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

Aby przetestować zmiennej typu `int`, trzeba jawnie porównania wartości, takich jak zero, w następujący sposób:

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a>Przykład

W tym przykładzie Wprowadź znak przy użyciu klawiatury i program sprawdza, czy znak danych wejściowych jest literą. Jeśli jest literą, sprawdza, czy jest wielką czy małą literą. Te testy są wykonywane przy użyciu <xref:System.Char.IsLetter%2A>, i <xref:System.Char.IsLower%2A>, zarówno które zwrotu `bool` typu:

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
- [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)
- [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [Tabela niejawnych konwersji liczbowych](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [Tabela jawnych konwersji liczbowych](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
