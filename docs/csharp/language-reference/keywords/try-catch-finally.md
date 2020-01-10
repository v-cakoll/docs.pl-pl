---
title: try-catch-finally- C# Reference
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 5d98f6967595c7c32b23ba5422a8d9ca79f7f54c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713043"
---
# <a name="try-catch-finally-c-reference"></a>try-catch-finally (odwołanie w C#)

Typowym zastosowaniem `catch` i `finally` jednocześnie jest uzyskanie zasobów i używanie ich w bloku `try`, zaradzenie sobie z wyjątkowymi okolicznościami w bloku `catch` i zwolnienie zasobów w bloku `finally`.

 Aby uzyskać więcej informacji i przykładów dotyczących ponownego zgłaszania wyjątków, zobacz [try-catch](try-catch.md) i [wyrzucanie wyjątków](../../../standard/exceptions/index.md). Aby uzyskać więcej informacji na temat bloku `finally`, zobacz [try-finally](try-finally.md).

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
