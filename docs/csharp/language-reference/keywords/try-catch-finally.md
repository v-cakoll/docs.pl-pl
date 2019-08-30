---
title: try-catch-finally- C# Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 9f2c82fb140e18454491660d17b570db0a8a2aef
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168589"
---
# <a name="try-catch-finally-c-reference"></a>try-catch-finally (odwołanie w C#)

Typowym zastosowaniem `catch` i `finally` razem jest uzyskanie zasobów `try` i korzystanie z nich w `catch` bloku, zaradzenie sobie z wyjątkowymi okolicznościami w bloku i zwolnienie zasobów `finally` w bloku.

 Aby uzyskać więcej informacji i przykładów dotyczących ponownego zgłaszania wyjątków, zobacz [try-catch](try-catch.md) i wyrzucanie [wyjątków](../../../standard/exceptions/index.md). Aby uzyskać więcej informacji na `finally` temat bloku, zobacz [try-finally](try-finally.md).

## <a name="example"></a>Przykład

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [try instrukcji](~/_csharplang/spec/statements.md#the-try-statement) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Instrukcje try, throw i catch (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [Instrukcje: Jawne zgłaszanie wyjątków](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [using, instrukcja](using-statement.md)
