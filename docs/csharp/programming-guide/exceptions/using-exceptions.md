---
title: Używanie wyjątków - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: 64e62d9c6cfcffb9ea5c0b0e05a546753278e186
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240193"
---
# <a name="using-exceptions-c-programming-guide"></a>Używanie wyjątków (Przewodnik programowania w języku C#)
W języku C# błędów w programie w czasie wykonywania są propagowane przez program za pomocą mechanizmu o nazwie wyjątków. Wyjątki są zgłaszane przez kod, który wystąpi błąd i przechwycony przez kod, który można rozwiązać problem. Wyjątki mogą zostać wygenerowane przez .NET Framework środowisko uruchomieniowe języka wspólnego (CLR) lub kodu w programie. Gdy wyjątek jest generowany, rozprzestrzenia się górę stosu wywołań, dopóki `catch` znajduje się instrukcji, dla wyjątku. Nieobsłużone wyjątki są obsługiwane przez wyjątek ogólny program obsługi, dostarczone przez system, który wyświetla okno dialogowe.  
  
 Wyjątki są reprezentowane przez klasy pochodne <xref:System.Exception>. Ta klasa identyfikuje typ wyjątku i zawiera właściwości, które będzie zawierał szczegółowe informacje o wyjątku. Zostanie zgłoszony wyjątek dotyczy tworzenia wystąpienia klasy pochodnej wyjątek, opcjonalnie konfigurowania właściwości wyjątku i następnie zgłaszanie obiektu za pomocą `throw` — słowo kluczowe. Na przykład:  
  
 [!code-csharp[csProgGuideExceptions#1](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_1.cs)]  
  
 Po jest zgłaszany wyjątek, środowisko uruchomieniowe sprawdza bieżącą instrukcję, aby zobaczyć, czy znajduje się w `try` bloku. Jeśli tak jest, dowolny `catch` bloki skojarzony `try` bloku jest sprawdzenie, czy ich może przechwycić wyjątek. `Catch` bloki zazwyczaj określenie typów wyjątków. Jeśli typ `catch` blok jest taki sam typ co wyjątek lub klasa bazowa wyjątku, `catch` bloku mogą obsługiwać metody. Na przykład:  
  
 [!code-csharp[csProgGuideExceptions#2](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_2.cs)]  
  
 Jeśli instrukcja, która zgłosiła wyjątek nie jest w ramach `try` bloku lub jeśli `try` blok, który otacza go nie ma odpowiadającego `catch` bloku, środowisko uruchomieniowe sprawdza wywoływania metody dla `try` instrukcji i `catch` bloków. Środowisko uruchomieniowe kontynuuje wywołania stosu, wyszukiwanie zgodnych `catch` bloku. Po `catch` blok zostanie odnaleziony i wykonywane, kontrola przechodzi do następnej instrukcji po tym `catch` bloku.  
  
 A `try` instrukcji może zawierać więcej niż jedną `catch` bloku. Pierwszy `catch` zostaje wykonana instrukcja, która może obsłużyć wyjątek; wszystkie następujące `catch` instrukcji, nawet jeśli są one zgodne, są ignorowane. W związku z tym, catch bloki zawsze powinny być uporządkowane od najbardziej określonego (lub najbardziej pochodnego) do najmniej specyficznych. Na przykład:  
  
 [!code-csharp[csProgGuideExceptions#3](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_3.cs)]  
  
 Przed `catch` blok jest wykonywany, środowisko uruchomieniowe sprawdza, czy `finally` bloków. `Finally` bloki Włącz programisty wyczyścić stan niejednoznaczny, który może pozostać za pośrednictwem z przerwane `try` bloku, lub zwolnij wszystkie zasoby zewnętrzne (na przykład grafiki obsługuje połączenia z bazą danych lub strumieni plików) bez konieczności oczekiwania na wyrzucanie elementów Moduł zbierający w środowisku uruchomieniowym do sfinalizowania obiektów. Na przykład:  
  
 [!code-csharp[csProgGuideExceptions#4](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_4.cs)]  
  
 Jeśli `WriteByte()` zgłosiło wyjątek, kod w drugim `try` blok, który próbuje ponownie otworzyć plik może zakończyć się niepowodzeniem, jeśli `file.Close()` nie jest wywoływana, a plik pozostanie zablokowany. Ponieważ `finally` bloki są wykonywane nawet wtedy, gdy wyjątek jest generowany, `finally` bloku w poprzednim przykładzie pozwala na plik Aby zostać poprawnie zamknięty i pomaga uniknąć błąd.  
  
 Jeśli zgodnego `catch` bloku znajduje się w stosie wywołań po wyjątek wystąpi jedno z trzech zdarzeń:  
  
-   Jeśli wyjątek znajduje się w finalizator, finalizator został przerwany, a podstawowy finalizator, nosi nazwę.  
  
-   Jeśli zawiera stos wywołań w konstruktorze statycznym lub inicjatorze pola statycznego <xref:System.TypeInitializationException> jest generowany przy użyciu oryginalnego wyjątku, które są przypisane do <xref:System.Exception.InnerException%2A> właściwość nowy wyjątek.  
  
-   Po osiągnięciu początek wątek, wątek jest zakończony.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Wyjątki i obsługa wyjątków](../../../csharp/programming-guide/exceptions/index.md)
