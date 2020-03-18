---
title: try-finally - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 2c4c69b1e104aed968bc24bac690de83026643a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713017"
---
# <a name="try-finally-c-reference"></a>try-finally (odwołanie w C#)

Za pomocą `finally` bloku, można oczyścić wszystkie zasoby, które są przydzielane w [try](try-catch.md) bloku `try` i można uruchomić kod, nawet jeśli wystąpi wyjątek w bloku. Zazwyczaj instrukcje `finally` bloku uruchomić, gdy formant `try` pozostawia instrukcji. Przeniesienie kontroli może nastąpić w wyniku normalnego wykonania, `break` `continue`wykonania `goto`, `return` , lub instrukcji lub propagacji `try` wyjątku z instrukcji.

W ramach obsługiwanego wyjątku skojarzony `finally` blok jest gwarantowany do uruchomienia. Jednak jeśli wyjątek jest nieobsługiwany, wykonanie `finally` bloku zależy od sposobu wyzwalania operacji unwind wyjątku. To z kolei zależy od konfiguracji komputera.

Zazwyczaj po zakończeniu nieobsługiwanego wyjątku aplikacja, `finally` czy blok jest uruchamiany nie jest ważne. Jednak jeśli masz instrukcje `finally` w bloku, które muszą być uruchamiane nawet `catch` w tej `try` - `finally` sytuacji, jednym rozwiązaniem jest dodanie bloku do instrukcji. Alternatywnie można przechwycić wyjątek, który może `try` zostać `try` - `finally` wygenerowany w bloku instrukcji wyżej stosu wywołań. Oznacza to, że można przechwycić wyjątek w metodzie, która wywołuje metodę, która zawiera instrukcję `try` - `finally` lub w metodzie, która wywołuje tę metodę lub w dowolnej metody w stosie wywołań. Jeśli wyjątek nie zostanie przechwycona, wykonanie `finally` bloku zależy od tego, czy system operacyjny zdecyduje się wyzwolić operację unwind wyjątku.

## <a name="example"></a>Przykład

W poniższym przykładzie nieprawidłowe oświadczenie konwersji `System.InvalidCastException` powoduje wyjątek. Wyjątek jest nieobsługiwany.

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

W poniższym przykładzie wyjątek `TryCast` od metody jest przechwycone w metodzie dalej stosu wywołań.

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

Aby uzyskać `finally`więcej informacji na temat , zobacz [try-catch-finally](try-catch-finally.md).

C# zawiera również [using instrukcji](using-statement.md), który <xref:System.IDisposable> zapewnia podobne funkcje dla obiektów w składni wygodne.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [instrukcja wypróbuj](~/_csharplang/spec/statements.md#the-try-statement) [specyfikację języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Instrukcje try, throw i catch (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [throw](throw.md)
- [try-catch](try-catch.md)
- [Instrukcje: Jawne zgłaszanie wyjątków](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
