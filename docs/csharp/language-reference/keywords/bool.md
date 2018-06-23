---
title: bool — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: d6b0cb91dd9b8159919b0d155bb2f9773e7ba534
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2018
ms.locfileid: "36315111"
---
# <a name="bool-c-reference"></a>bool (odwołanie w C#)

`bool` — Słowo kluczowe jest aliasem <xref:System.Boolean?displayProperty=nameWithType>. Służy do deklarowania zmiennych do przechowywania wartości logicznych, [true](../../../csharp/language-reference/keywords/true.md) i [false](../../../csharp/language-reference/keywords/false.md).

> [!NOTE]
> Jeśli potrzebujesz zmienną wartości logicznej, która również może mieć wartość `null`, użyj `bool?`. Aby uzyskać więcej informacji, zobacz [typy dopuszczające wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md).

## <a name="literals"></a>Literały

Można przypisać wartość logiczną umożliwiającą `bool` zmiennej. Można także przypisać wyrażenie obliczane do `bool` do `bool` zmiennej.

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

Wartość domyślna `bool` zmienna jest `false`. Wartość domyślna `bool?` zmienna jest `null`.

## <a name="conversions"></a>Konwersje

W języku C++ wartości typu `bool` można przekonwertować wartości typu `int`; innymi słowy, `false` jest odpowiednikiem zero i `true` jest odpowiednikiem wartości niezerowych. W języku C# nie jest konwersja między `bool` typu i innych typów. Na przykład następująca `if` instrukcja jest nieprawidłowa w języku C#:

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

Aby przetestować zmiennej typu `int`, musisz jawnie porównaj je z wartość, na przykład wartość 0, w następujący sposób:

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a>Przykład

W tym przykładzie Wprowadź znak z klawiatury i program sprawdza, czy wprowadzany znak jest literą. Jest literą, sprawdza, czy jest małe lub wielkie litery. Te testy są wykonywane z <xref:System.Char.IsLetter%2A>, i <xref:System.Char.IsLower%2A>, zarówno które zwrotu `bool` typu:

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
[Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
[Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
[Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)  
[Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
[Tabela niejawnych konwersji liczbowych](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
[Tabela jawnych konwersji liczbowych](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  