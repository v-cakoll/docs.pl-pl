---
title: bool — słowo C# kluczowe-odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 880e8c0b733afbf5c09f543e06a5a4a858d2b456
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771845"
---
# <a name="bool-c-reference"></a>bool (odwołanie w C#)

Słowo kluczowe `bool` jest aliasem <xref:System.Boolean?displayProperty=nameWithType>. Służy do deklarowania zmiennych do przechowywania wartości logicznych: [true](true-literal.md) i [false](false-literal.md).

> [!NOTE]
> Użyj typu `bool?`, jeśli musisz obsługiwać logikę o wartości trójwarstwowej, na przykład podczas pracy z bazami danych, które obsługują typ Boolean o wartości 3. W przypadku operandów `bool?` wstępnie zdefiniowane `&` i operatory `|` obsługują logikę z trzema wartościami. Aby uzyskać więcej informacji, zobacz sekcję [Operatory logiczne wartości null](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) w artykule [Operatory logiczne Boolean](../operators/boolean-logical-operators.md) .

## <a name="literals"></a>Literały

Do zmiennej `bool` można przypisać wartość logiczną. Można również przypisać wyrażenie, które oblicza `bool` do zmiennej `bool`.

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

Wartość domyślna zmiennej `bool` jest `false`. Wartość domyślna zmiennej `bool?` jest `null`.

## <a name="conversions"></a>Konwersje

W C++programie wartość typu `bool` może zostać przekonwertowana na wartość typu `int`; Innymi słowy, `false` jest równoważne zero i `true` jest równoważne wartościom niezerowym. W C#programie nie ma konwersji między typem `bool` i innymi typami. Na przykład następująca instrukcja `if` jest nieprawidłowa w C#:

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

Aby przetestować zmienną typu `int`, należy jawnie porównać ją z wartością, taką jak zero, w następujący sposób:

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a>Przykład

W tym przykładzie wprowadzasz znak z klawiatury, a program sprawdza, czy znak wejściowy jest literą. Jeśli jest to litera, sprawdza, czy jest mała lub Wielka litera. Te testy są wykonywane z <xref:System.Char.IsLetter%2A> i <xref:System.Char.IsLower%2A>, z których oba zwracają `bool` typ:

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [C#Odwoła](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Typy całkowite](../builtin-types/integral-numeric-types.md)
- [Tabela typów wbudowanych](./built-in-types-table.md)
