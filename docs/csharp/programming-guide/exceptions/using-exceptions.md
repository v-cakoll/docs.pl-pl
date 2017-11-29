---
title: "Używanie wyjątków (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 55c2cc0c6a1f852bd286b98927cc69f81119aeee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-exceptions-c-programming-guide"></a>Używanie wyjątków (Przewodnik programowania w języku C#)
W języku C# błędów w programie w czasie wykonywania są propagowane za pośrednictwem programu przy użyciu mechanizmu o nazwie wyjątków. Wyjątki są zgłaszane przez kod, który wystąpi błąd i przechwycony przez kod, który może poprawić ten błąd. Wyjątki może zostać wygenerowany przez .NET Framework środowisko uruchomieniowe języka wspólnego (CLR) lub kodu w programie. Po wyjątku rozprzestrzenia się górę stosu wywołań do `catch` instrukcji dla wyjątku został znaleziony. Nieprzechwyconych wyjątków są obsługiwane przez program obsługi wyjątków ogólnych obsługiwanych przez system, który wyświetla okno dialogowe.  
  
 Wyjątki są reprezentowane przez klasy pochodzące od <xref:System.Exception>. Ta klasa zawiera typ wyjątku i zawiera właściwości, które zawierały wszystkie szczegółowe informacje o wyjątku. Zgłaszanie wyjątku obejmuje tworzenie wystąpienia klasy pochodnej wyjątek, opcjonalnie konfigurowania właściwości wyjątku i następnie zgłaszanie obiektu przy użyciu `throw` — słowo kluczowe. Na przykład:  
  
 [!code-csharp[csProgGuideExceptions#1](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_1.cs)]  
  
 Po wyjątek środowiska uruchomieniowego sprawdza bieżącej instrukcji, aby zobaczyć, czy znajduje się w `try` bloku. Jeśli tak jest, wszelkie `catch` bloki skojarzone z `try` bloku jest sprawdzenie, czy ich catch wyjątku. `Catch`bloki zazwyczaj określić typy wyjątków; Jeśli typ `catch` blok jest taki sam typ jak wyjątek lub klasę podstawową wyjątku, `catch` bloku może obsługiwać metodę. Na przykład:  
  
 [!code-csharp[csProgGuideExceptions#2](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_2.cs)]  
  
 Jeśli instrukcja, która zgłasza wyjątek, nie jest w `try` bloku lub, jeśli `try` bloku ograniczający go nie posiada odpowiadającego `catch` bloku, środowisko uruchomieniowe sprawdza wywołania metody `try` instrukcji i `catch` bloków. Środowisko uruchomieniowe nadal górę stosu wywołania, wyszukiwanie zgodnego `catch` bloku. Po `catch` blok jest znaleziono i wykonać, kontrola jest przekazywana do następnej instrukcji, po którym `catch` bloku.  
  
 A `try` instrukcji może zawierać więcej niż jedną `catch` bloku. Pierwszy `catch` instrukcji, która może obsłużyć wyjątek jest wykonywane; wszystkie następujące `catch` instrukcje, nawet jeśli są one zgodne, są ignorowane. W związku z tym catch bloki zawsze powinna być wyświetlana z najbardziej określonego (lub pochodnego większość) do najmniej specyficznych. Na przykład:  
  
 [!code-csharp[csProgGuideExceptions#3](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_3.cs)]  
  
 Przed `catch` wykonaniu bloku środowiska uruchomieniowego sprawdza, czy `finally` bloków. `Finally`bloki włączyć programisty wyczyścić niejednoznaczne stan może być pozostałe z przerwane `try` bloku, lub aby zwolnić dowolnych zasobów zewnętrznych (na przykład grafiki dojść, połączenia z bazą danych lub plików strumieni) bez oczekiwania na odzyskiwanie Moduł zbierający w środowisku uruchomieniowym finalize obiektów. Na przykład:  
  
 [!code-csharp[csProgGuideExceptions#4](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_4.cs)]  
  
 Jeśli `WriteByte()` zwrócił wyjątek, kod w ciągu sekundy `try` bloku, który próbuje ponownie otworzyć plik będą się kończyć niepowodzeniem, jeśli `file.Close()` nie jest wywoływany, a plik pozostanie zablokowane. Ponieważ `finally` bloki są wykonywane, nawet jeśli wyjątek `finally` umożliwia bloku w poprzednim przykładzie plik zostanie zamknięty poprawnie i pozwala uniknąć wystąpił błąd.  
  
 Jeśli zgodnego `catch` bloku znajduje się w stosie wywołań po wyjątek wystąpi jedno z trzech zdarzeń:  
  
-   Jeśli wyjątek jest w finalizator, finalizator zostało przerwane i podstawowej finalizator, jest wywoływana.  
  
-   Jeśli stos wywołań zawiera w konstruktorze statycznym lub inicjatorze pola statycznego <xref:System.TypeInitializationException> jest zgłaszany, z wyjątkiem oryginalnego przypisane do <xref:System.Exception.InnerException%2A> właściwości nowej wyjątek.  
  
-   Osiągnięto początek wątku zakończenia wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wyjątki i obsługa wyjątków](../../../csharp/programming-guide/exceptions/index.md)
