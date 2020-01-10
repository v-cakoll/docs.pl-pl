---
title: try-finally- C# Reference
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 2c4c69b1e104aed968bc24bac690de83026643a0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713017"
---
# <a name="try-finally-c-reference"></a>try-finally (odwołanie w C#)

Za pomocą bloku `finally` można wyczyścić wszystkie zasoby, które są przydzielone w bloku [try](try-catch.md) , i można uruchomić kod nawet wtedy, gdy w bloku `try` wystąpi wyjątek. Zazwyczaj instrukcje bloku `finally` są uruchamiane, gdy kontrolka opuszcza instrukcję `try`. Transfer kontroli może odbywać się w wyniku normalnego wykonywania, wykonywania `break`, `continue`, `goto`lub instrukcji `return` lub propagacji wyjątku z `try` instrukcji.

W ramach obsłużonego wyjątku zagwarantowany jest, że skojarzony blok `finally` jest uruchamiany. Jeśli jednak wyjątek nie jest obsługiwany, wykonanie bloku `finally` jest zależne od tego, w jaki sposób wyzwalany jest wyjątek operacji unwind. To z kolei zależy od konfiguracji komputera.

Zwykle, gdy nieobsługiwany wyjątek powoduje zakończenie aplikacji, niezależnie od tego, czy blok `finally` jest uruchomiony, nie jest ważne. Jednakże jeśli masz instrukcje w bloku `finally`, który musi być uruchamiany nawet w takiej sytuacji, jedno rozwiązanie ma dodać blok `catch` do instrukcji `try`-`finally`. Alternatywnie można przechwytywać wyjątek, który może zostać wygenerowany w bloku `try` `try`-`finally` instrukcji wyższej stosu wywołań. Oznacza to, że można przechwytywać wyjątek w metodzie, która wywołuje metodę, która zawiera instrukcję `try`-`finally` lub w metodzie, która wywołuje tę metodę, lub w dowolnej metodzie stosu wywołań. Jeśli wyjątek nie zostanie przechwycony, wykonanie bloku `finally` zależy od tego, czy system operacyjny wybiera wyzwalacz operacji unwind.

## <a name="example"></a>Przykład

W poniższym przykładzie instrukcja konwersji nieprawidłowa powoduje wyjątek `System.InvalidCastException`. Wyjątek nie jest obsługiwany.

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

W poniższym przykładzie wyjątek z metody `TryCast` jest przechwytywany w metodzie dalej w stosie wywołań.

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

Aby uzyskać więcej informacji na temat `finally`, zobacz [try-catch-finally](try-catch-finally.md).

C#zawiera również [instrukcję using](using-statement.md), która zapewnia podobną funkcjonalność dla <xref:System.IDisposable> obiektów w wygodnej składni.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [try instrukcji](~/_csharplang/spec/statements.md#the-try-statement) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Instrukcje try, throw i catch (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [try-catch](try-catch.md)
- [Instrukcje: Jawne zgłaszanie wyjątków](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
