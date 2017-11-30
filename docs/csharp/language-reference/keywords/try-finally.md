---
title: "try-finally (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 927b851419f2c5245518ee39bf847cb1f1664917
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="try-finally-c-reference"></a>try-finally (odwołanie w C#)
Za pomocą `finally` bloku, możesz wyczyścić wszystkie zasoby, które są przydzielane w [spróbuj](../../../csharp/language-reference/keywords/try-catch.md) bloku, a można uruchomić kod, nawet jeśli wystąpienia wyjątku w `try` bloku. Zazwyczaj instrukcje `finally` bloku uruchamiany, gdy formant pozostawia `try` instrukcji. Przekazanie sterowania może wystąpić w wyniku normalnego wykonywania wykonywania `break`, `continue`, `goto`, lub `return` instrukcji lub propagacji wyjątek poza `try` instrukcji.  
  
 W ramach obsłużył wyjątek skojarzony `finally` bloku jest gwarantowana do uruchomienia. Jednak jeśli nieobsłużony wyjątek, wykonywanie `finally` bloku jest zależna od jak wyjątek unwind operacji zostanie wywołany. Który z kolei jest zależny od konfiguracji komputera.
  
 Zwykle, gdy wystąpił nieobsługiwany wyjątek kończy się aplikacji, czy `finally` uruchomieniu bloku nie jest ważna. Jednak jeśli w instrukcji `finally` bloku, które muszą być uruchamiane, nawet w takiej sytuacji jedno rozwiązanie polega na dodaniu `catch` za pomocą bloku `try` - `finally` instrukcji. Alternatywnie można przechwycić wyjątek, który może zostać zgłoszone w `try` zablokować z `try` - `finally` instrukcji górę stosu wywołań. Oznacza to, że zostaną wychwycone wyjątek w metodzie, która wywołuje metodę, która zawiera `try` - `finally` instrukcji, lub w metodzie, która wywołuje tę metodę, lub w dowolnej metody w stosie wywołań. Jeśli nie zostanie przechwycony wyjątek, wykonywanie `finally` bloku zależy od tego, czy system operacyjny wybierze do wyzwolenia wyjątek operacji unwind.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie instrukcja Nieprawidłowa konwersja powoduje `System.InvalidCastException` wyjątku. Wyjątkiem jest nieobsługiwany.  
  
 [!code-csharp[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 W poniższym przykładzie wyjątku z `TryCast` metody zostanie przechwycony w metodzie dalej górę stosu wywołań.  
  
 [!code-csharp[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 Aby uzyskać więcej informacji na temat `finally`, zobacz [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).  
  
 C# zawiera także [za pomocą instrukcji](../../../csharp/language-reference/keywords/using-statement.md), która oferuje podobne funkcje dla <xref:System.IDisposable> obiektów w dogodnym składni.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Spróbuj, throw i catch instrukcji (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)  
 [Instrukcje obsługi wyjątków](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [throw](../../../csharp/language-reference/keywords/throw.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [Porady: jawne zgłaszanie wyjątków](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
