---
title: Obsługa wyjątków (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: bbe9db48ab5cc1313c18fce66312f4334b40b9c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="exception-handling-c-programming-guide"></a>Obsługa wyjątków (Przewodnik programowania w języku C#)
A [spróbuj](../../../csharp/language-reference/keywords/try-catch.md) blok jest używany przez programistów C# do kodu partycji, które mogą wpłynąć na wyjątek. Skojarzone [catch](../../../csharp/language-reference/keywords/try-catch.md) bloki są używane do obsługi wyjątków wynikowy. A [koniec](../../../csharp/language-reference/keywords/try-finally.md) blok zawiera kod, który jest uruchomiony niezależnie od tego, czy wyjątek jest zgłaszany `try` bloku, takich jak zwolnienia zasobów przydzielonych w `try` bloku. A `try` blok wymaga co najmniej jednego skojarzone `catch` bloków, lub `finally` bloku lub oba.  
  
 W poniższych przykładach pokazano `try-catch` instrukcji, `try-finally` instrukcji, a `try-catch-finally` instrukcji.  
  
 [!code-csharp[csProgGuideExceptions#6](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_1.cs)]  
  
 [!code-csharp[csProgGuideExceptions#7](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_2.cs)]  
  
 [!code-csharp[csProgGuideExceptions#8](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_3.cs)]  
  
 A `try` zablokować bez `catch` lub `finally` bloku powoduje błąd kompilatora.  
  
## <a name="catch-blocks"></a>Bloki catch  
 A `catch` bloku można określić typ wyjątku, aby wykryć. Specyfikacja typu jest nazywana *filtru wyjątków*. Typ wyjątku powinien pochodzić z <xref:System.Exception>. Ogólnie rzecz biorąc, nie należy określać <xref:System.Exception> jako filtr wyjątek, chyba że albo wiesz, jak obsługiwać wszystkie wyjątki, które może zostać zgłoszone w `try` bloku, lub wprowadzono [throw](../../../csharp/language-reference/keywords/throw.md) instrukcji na końcu Twojego`catch`bloku.  
  
 Wiele `catch` bloki z filtry wyjątków różnych można połączyć ze sobą. `catch` Są obliczane bloki od góry do dołu w kodzie, ale tylko jeden `catch` bloku jest wykonywane dla każdego zgłoszonego wyjątku. Pierwszy `catch` wykonaniu bloku, który określa dokładnie tego samego typu lub klasę podstawową zwrócony wyjątek. Jeśli nie `catch` bloku określa filtr wyjątków pasujących `catch` bloku, który nie ma filtru jest zaznaczone, jeśli występuje w instrukcji. Ważne jest, aby umieścić `catch` bloki z najbardziej (to znaczy najbardziej pochodnej) określonego wyjątku najpierw typów.  
  
 Należy przechwytywać wyjątki, gdy są spełnione następujące warunki:  
  
-   Masz dobrej zrozumieć dlaczego może zostać zgłoszony wyjątek i można zaimplementować określonego odzyskiwania, takich jak monitowanie użytkownika o wprowadź nową nazwę pliku, gdy zostaną wychwycone <xref:System.IO.FileNotFoundException> obiektu.  
  
-   Można tworzyć i zgłoszenie wyjątku nowe, bardziej szczegółowych.  
  
     [!code-csharp[csProgGuideExceptions#9](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_4.cs)]  
  
-   Chcesz częściowo obsługi wyjątku przed przekazaniem go potrzeby obsługi dodatkowych. W poniższym przykładzie `catch` bloku należy dodać wpis dziennik błędów, aby przed ponownym zgłoszeniem wyjątku.  
  
     [!code-csharp[csProgGuideExceptions#10](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_5.cs)]  
  
## <a name="finally-blocks"></a>Bloki finally  
 A `finally` bloku umożliwia czyszczenie akcje, które są wykonywane w `try` bloku. Jeśli jest obecny, `finally` bloku wykonuje ostatniego, po `try` blok i wszystkie dopasowane `catch` bloku. A `finally` zablokować zawsze działa, na niezależnie od tego, czy jest zwracany wyjątek, czy `catch` bloku odpowiadał typowi wyjątek został znaleziony.  
  
 `finally` Bloku mogą być używane do zwolnienia zasobów, takich jak plik strumieni, połączenia z bazą danych i obsługuje grafiki bez oczekiwania na moduł zbierający elementy bezużyteczne w czasie wykonywania w celu sfinalizowania obiektów. Zobacz [za pomocą instrukcji](../../../csharp/language-reference/keywords/using-statement.md) Aby uzyskać więcej informacji.  
  
 W poniższym przykładzie `finally` umożliwia zamknięcie pliku, który jest otwarty w bloku `try` bloku. Należy zauważyć, że stan dojście do pliku jest zaznaczone, przed zamknięciem pliku. Jeśli `try` bloku nie można otworzyć pliku, dojście do pliku nadal ma wartość `null` i `finally` bloku nie będzie próbował go zamknąć. Alternatywnie Jeśli plik jest otwarty pomyślnie w `try` bloku `finally` bloku Zamyka otwarty plik.  
  
 [!code-csharp[csProgGuideExceptions#11](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_6.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wyjątki i obsługa wyjątków](../../../csharp/programming-guide/exceptions/index.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)  
 [using, instrukcja](../../../csharp/language-reference/keywords/using-statement.md)
