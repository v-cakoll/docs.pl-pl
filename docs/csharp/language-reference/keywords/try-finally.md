---
title: try-finally (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: beb54cf6c4e6dc87b9a08b81586b24d72f92b84b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481959"
---
# <a name="try-finally-c-reference"></a>try-finally (odwołanie w C#)
Za pomocą `finally` bloku, można oczyścić wszystkie zasoby, które są przydzielane w [spróbuj](../../../csharp/language-reference/keywords/try-catch.md) bloku, a może uruchamiać kod, nawet jeśli wystąpi wyjątek w `try` bloku. Typowo, instrukcje `finally` uruchamiania, kiedy formant opuszcza blok `try` instrukcji. Przeniesienie kontroli może wystąpić w wyniku normalnego wykonania, wykonanie `break`, `continue`, `goto`, lub `return` instrukcji lub propagacji wyjątku z `try` instrukcji.  
  
 Wewnątrz obsługiwanego wyjątku, powiązany `finally` bloku jest gwarantowane do uruchomienia. Jednak jeśli nieobsługiwanego wyjątku wykonanie `finally` bloku jest zależny od jest wyzwalany, jak wyjątku operacji rozwijania. Który z kolei jest zależny od konfiguracji komputera.
  
 Zwykle, kiedy nieobsłużony wyjątek kończy aplikację, czy `finally` uruchomieniu bloku nie jest ważna. Jednak jeśli masz instrukcje `finally` blok, który musi być uruchamiany nawet w tej sytuacji, rozwiązaniem jest dodanie `catch` za pomocą bloku `try` - `finally` instrukcji. Alternatywnie, można wychwycić wyjątek, który może zostać wygenerowany w `try` bloku `try` - `finally` instrukcji wyższego rzędu stosu wywołań. Oznacza to, że może przechwycić wyjątek w metodzie, która wywołuje metodę, która zawiera `try` - `finally` instrukcji, lub w metodzie, która wywołuje tę metodę, lub dowolną metodę w stosie wywołań. Jeśli wyjątek nie zostanie przechwycony, wykonanie `finally` bloku zależy od tego, czy system operacyjny wybierze wywołanie wyjątku operacji rozwijania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie instrukcja nieprawidłowej konwersji powoduje, że `System.InvalidCastException` wyjątku. Wyjątek jest nieobsługiwany.  
  
 [!code-csharp[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 W poniższym przykładzie, wyjątek od `TryCast` metoda padł w metodzie dalej położonej w stosie wywołań.  
  
 [!code-csharp[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 Aby uzyskać więcej informacji na temat `finally`, zobacz [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).  
  
 C# zawiera również [za pomocą instrukcji](../../../csharp/language-reference/keywords/using-statement.md), który zapewnia podobną funkcjonalność dla <xref:System.IDisposable> obiektów w wygodnej składni.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [Instrukcje try, throw i catch (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)  
- [Instrukcje obsługi wyjątków](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
- [throw](../../../csharp/language-reference/keywords/throw.md)  
- [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
- [Instrukcje: Jawne zgłaszanie wyjątków](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
