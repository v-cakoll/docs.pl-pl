---
title: try-finally — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 20a608c208a7c5e6f00b85dfc10cf14202a78446
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633139"
---
# <a name="try-finally-c-reference"></a>try-finally (odwołanie w C#)

Za pomocą `finally` bloku, można oczyścić wszystkie zasoby, które są przydzielane w [spróbuj](try-catch.md) bloku, a może uruchamiać kod, nawet jeśli wystąpi wyjątek w `try` bloku. Typowo, instrukcje `finally` uruchamiania, kiedy formant opuszcza blok `try` instrukcji. Przeniesienie kontroli może wystąpić w wyniku normalnego wykonania, wykonanie `break`, `continue`, `goto`, lub `return` instrukcji lub propagacji wyjątku z `try` instrukcji.

Wewnątrz obsługiwanego wyjątku, powiązany `finally` bloku jest gwarantowane do uruchomienia. Jednak jeśli nieobsługiwanego wyjątku wykonanie `finally` bloku jest zależny od jest wyzwalany, jak wyjątku operacji rozwijania. Który z kolei jest zależny od konfiguracji komputera.

Zwykle, kiedy nieobsłużony wyjątek kończy aplikację, czy `finally` uruchomieniu bloku nie jest ważna. Jednak jeśli masz instrukcje `finally` blok, który musi być uruchamiany nawet w tej sytuacji, rozwiązaniem jest dodanie `catch` za pomocą bloku `try` - `finally` instrukcji. Alternatywnie, można wychwycić wyjątek, który może zostać wygenerowany w `try` bloku `try` - `finally` instrukcji wyższego rzędu stosu wywołań. Oznacza to, że może przechwycić wyjątek w metodzie, która wywołuje metodę, która zawiera `try` - `finally` instrukcji, lub w metodzie, która wywołuje tę metodę, lub dowolną metodę w stosie wywołań. Jeśli wyjątek nie zostanie przechwycony, wykonanie `finally` bloku zależy od tego, czy system operacyjny wybierze wywołanie wyjątku operacji rozwijania.

## <a name="example"></a>Przykład

W poniższym przykładzie instrukcja nieprawidłowej konwersji powoduje, że `System.InvalidCastException` wyjątku. Wyjątek jest nieobsługiwany.

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

W poniższym przykładzie, wyjątek od `TryCast` metoda padł w metodzie dalej położonej w stosie wywołań.

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

Aby uzyskać więcej informacji na temat `finally`, zobacz [try-catch-finally](try-catch-finally.md).

C# zawiera również [za pomocą instrukcji](using-statement.md), który zapewnia podobną funkcjonalność dla <xref:System.IDisposable> obiektów w wygodnej składni.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Instrukcje try, throw i catch (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [Instrukcje obsługi wyjątków](exception-handling-statements.md)
- [throw](throw.md)
- [try-catch](try-catch.md)
- [Instrukcje: Jawne zgłaszanie wyjątków](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
