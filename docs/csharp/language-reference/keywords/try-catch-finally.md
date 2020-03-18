---
title: try-catch-finally - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 5d98f6967595c7c32b23ba5422a8d9ca79f7f54c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713043"
---
# <a name="try-catch-finally-c-reference"></a>try-catch-finally (odwołanie w C#)

Powszechnym zastosowaniem `catch` `finally` i razem jest uzyskanie i `try` wykorzystanie zasobów w bloku, radzić sobie z wyjątkowymi okolicznościami w `catch` bloku i zwolnić zasoby w `finally` bloku.

 Aby uzyskać więcej informacji i przykłady dotyczące ponownego zgłaszania wyjątków, zobacz [try-catch](try-catch.md) i [zgłaszanie wyjątków](../../../standard/exceptions/index.md). Aby uzyskać więcej `finally` informacji o bloku, zobacz [wypróbuj na końcu](try-finally.md).

## <a name="example"></a>Przykład

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [instrukcja wypróbuj](~/_csharplang/spec/statements.md#the-try-statement) [specyfikację języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Instrukcje try, throw i catch (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [Instrukcje: Jawne zgłaszanie wyjątków](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [za pomocą instrukcji](using-statement.md)
