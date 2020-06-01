---
title: Korzystanie z wyjątków — Przewodnik programowania w języku C#
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: a00259dfd5634ad9b9c951c3cd76da97afe5077d
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241698"
---
# <a name="use-exceptions-c-programming-guide"></a>Używanie wyjątków (Przewodnik programowania w języku C#)

W języku C# błędy w programie w czasie wykonywania są propagowane za pośrednictwem programu przy użyciu mechanizmu nazywanego wyjątkami. Wyjątki są zgłaszane przez kod, który napotka błąd i przechwycony przez kod, który może poprawić błąd. Wyjątki mogą być zgłaszane przez środowisko uruchomieniowe .NET lub kod w programie. Gdy wyjątek jest zgłaszany, propaguje stos wywołań do momentu `catch` znalezienia instrukcji dla wyjątku. Nieprzechwycone wyjątki są obsługiwane przez ogólną procedurę obsługi wyjątków dostarczoną przez system, który wyświetla okno dialogowe.  
  
 Wyjątki są reprezentowane przez klasy pochodne od <xref:System.Exception> . Ta klasa identyfikuje typ wyjątku i zawiera właściwości, które zawierają szczegółowe informacje o wyjątku. Zgłaszanie wyjątku obejmuje utworzenie wystąpienia klasy pochodnej wyjątku, opcjonalnie skonfigurowanie właściwości wyjątku, a następnie wygenerowanie obiektu za pomocą `throw` słowa kluczowego. Przykład:  
  
 [!code-csharp[csProgGuideExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#1)]  
  
 Po zgłoszeniu wyjątku środowisko uruchomieniowe sprawdza bieżącą instrukcję, aby sprawdzić, czy znajduje się w `try` bloku. Jeśli tak jest, wszystkie `catch` bloki skojarzone z `try` blokiem są sprawdzane w celu sprawdzenia, czy mogą przechwytywać wyjątek. `Catch`bloki zwykle określają typy wyjątków; Jeśli typ `catch` bloku jest tego samego typu co wyjątek lub Klasa bazowa wyjątku, `catch` blok może obsłużyć metodę. Przykład:  
  
 [!code-csharp[csProgGuideExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#2)]  
  
 Jeśli instrukcja zwracająca wyjątek nie znajduje się w `try` bloku lub jeśli `try` blok, który go zawiera, nie ma pasującego `catch` bloku, środowisko uruchomieniowe sprawdza metodę wywołującą dla `try` instrukcji i `catch` bloków. Środowisko uruchomieniowe kontynuuje wywoływanie stosu, wyszukując zgodny `catch` blok. Po `catch` znalezieniu i wykonaniu bloku, kontrola jest przenoszona do następnej instrukcji po tym `catch` bloku.  
  
 `try`Instrukcja może zawierać więcej niż jeden `catch` blok. Pierwsza `catch` instrukcja, która może obsłużyć wyjątek, jest wykonywana; wszelkie poniższe `catch` instrukcje, nawet jeśli są zgodne, są ignorowane. W związku z tym bloki catch powinny zawsze być uporządkowane z najbardziej specyficznych (lub najbardziej pochodnych) do najmniej określonych. Przykład:  
  
 [!code-csharp[csProgGuideExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#3)]  
  
 Przed `catch` wykonaniem bloku program sprawdza bloki w czasie wykonywania `finally` . `Finally`bloki umożliwiają programistom czyszczenie dowolnego niejednoznacznego stanu, który może być pozostawiony przez przerwany `try` blok, lub do zwolnienia zasobów zewnętrznych (takich jak uchwyty grafiki, połączenia bazy danych lub strumienie plików) bez oczekiwania na zakończenie działania modułu zbierającego elementy bezużyteczne w środowisku uruchomieniowym. Przykład:  
  
 [!code-csharp[csProgGuideExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#4)]  
  
 W przypadku wypełniania `WriteByte()` wyjątku kod w drugim `try` bloku próbujący ponownie otworzyć plik mógłby się nie powieść `file.Close()` , jeśli nie zostanie wywołany, a plik pozostanie zablokowany. Ponieważ `finally` bloki są wykonywane nawet w przypadku zgłoszenia wyjątku, `finally` blok w poprzednim przykładzie umożliwia poprawne zamknięcie pliku i pomaga uniknąć błędu.  
  
 Jeśli nie `catch` odnaleziono zgodnego bloku w stosie wywołań po zgłoszeniu wyjątku, wystąpi jedno z trzech rzeczy:  
  
- Jeśli wyjątek znajduje się w obrębie finalizatora, finalizator zostanie przerwany i zostanie wywołany podstawowy finalizator, jeśli istnieje.  
  
- Jeśli stos wywołań zawiera statyczny Konstruktor lub zostaje zgłoszony inicjator pola statycznego, <xref:System.TypeInitializationException> z pierwotnym wyjątkiem przypisanym do <xref:System.Exception.InnerException%2A> właściwości nowego wyjątku.  
  
- Jeśli początek wątku zostanie osiągnięty, wątek zostanie zakończony.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Wyjątki i obsługa wyjątków](./index.md)
