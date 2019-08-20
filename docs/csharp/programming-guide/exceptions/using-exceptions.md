---
title: Korzystanie z wyjątków C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: 8d0fe4b8c2ba3e64aa7ee34fc9d02b29bda5c017
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590171"
---
# <a name="using-exceptions-c-programming-guide"></a>Używanie wyjątków (Przewodnik programowania w języku C#)
W C#programie błędy w programie w czasie wykonywania są propagowane za pośrednictwem programu przy użyciu mechanizmu nazywanego wyjątkami. Wyjątki są zgłaszane przez kod, który napotka błąd i przechwycony przez kod, który może poprawić błąd. Wyjątki mogą być zgłaszane przez .NET Framework środowisko uruchomieniowe języka wspólnego (CLR) lub kod w programie. Gdy wyjątek jest zgłaszany, propaguje stos wywołań do momentu `catch` znalezienia instrukcji dla wyjątku. Nieprzechwycone wyjątki są obsługiwane przez ogólną procedurę obsługi wyjątków dostarczoną przez system, który wyświetla okno dialogowe.  
  
 Wyjątki są reprezentowane przez klasy pochodne od <xref:System.Exception>. Ta klasa identyfikuje typ wyjątku i zawiera właściwości, które zawierają szczegółowe informacje o wyjątku. Zgłaszanie wyjątku obejmuje utworzenie wystąpienia klasy pochodnej wyjątku, opcjonalnie skonfigurowanie właściwości wyjątku, a następnie wygenerowanie obiektu za pomocą `throw` słowa kluczowego. Na przykład:  
  
 [!code-csharp[csProgGuideExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#1)]  
  
 Po zgłoszeniu wyjątku środowisko uruchomieniowe sprawdza bieżącą instrukcję, aby sprawdzić, czy znajduje się w `try` bloku. Jeśli tak jest, wszystkie `catch` bloki skojarzone `try` z blokiem są sprawdzane w celu sprawdzenia, czy mogą przechwytywać wyjątek. `Catch`bloki zwykle określają typy wyjątków; Jeśli typ `catch` bloku jest tego samego typu co wyjątek lub Klasa bazowa wyjątku `catch` , blok może obsłużyć metodę. Przykład:  
  
 [!code-csharp[csProgGuideExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#2)]  
  
 Jeśli instrukcja `try` zwracająca wyjątek nie znajduje się w bloku lub `try` Jeśli blok, który go zawiera, nie ma pasującego `catch` bloku, środowisko uruchomieniowe sprawdza metodę wywołującą dla `try` instrukcji i `catch` bloków. Środowisko uruchomieniowe kontynuuje wywoływanie stosu, wyszukując zgodny `catch` blok. Po znalezieniu i wykonaniu `catch` bloku,kontrolajestprzenoszonadonastępnejinstrukcjipotymbloku.`catch`  
  
 Instrukcja może zawierać więcej niż jeden `catch` blok. `try` Pierwsza `catch` instrukcja, która może obsłużyć wyjątek, jest wykonywana; `catch` wszelkie poniższe instrukcje, nawet jeśli są zgodne, są ignorowane. W związku z tym bloki catch powinny zawsze być uporządkowane z najbardziej specyficznych (lub najbardziej pochodnych) do najmniej określonych. Na przykład:  
  
 [!code-csharp[csProgGuideExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#3)]  
  
 Przed wykonaniem `finally`blokuprogram sprawdza bloki w czasie wykonywania. `catch` `Finally`bloki umożliwiają programistom czyszczenie dowolnego niejednoznacznego stanu, który może być pozostawiony przez przerwany `try` blok, lub do zwolnienia zasobów zewnętrznych (takich jak uchwyty grafiki, połączenia bazy danych lub strumienie plików) bez oczekiwania na śmieci Moduł zbierający w środowisku uruchomieniowym umożliwia finalizowanie obiektów. Na przykład:  
  
 [!code-csharp[csProgGuideExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#4)]  
  
 W `WriteByte()` przypadku wypełniania wyjątku kod w drugim `try` bloku próbujący ponownie otworzyć plik mógłby się nie powieść `file.Close()` , jeśli nie zostanie wywołany, a plik pozostanie zablokowany. Ponieważ `finally` bloki są wykonywane nawet `finally` w przypadku zgłoszenia wyjątku, blok w poprzednim przykładzie umożliwia poprawne zamknięcie pliku i pomaga uniknąć błędu.  
  
 Jeśli nie odnaleziono zgodnego `catch` bloku w stosie wywołań po zgłoszeniu wyjątku, wystąpi jedno z trzech rzeczy:  
  
- Jeśli wyjątek znajduje się w obrębie finalizatora, finalizator zostanie przerwany i zostanie wywołany podstawowy finalizator, jeśli istnieje.  
  
- Jeśli stos wywołań zawiera statyczny Konstruktor lub <xref:System.TypeInitializationException> zostaje zgłoszony inicjator pola statycznego, z pierwotnym wyjątkiem przypisanym <xref:System.Exception.InnerException%2A> do właściwości nowego wyjątku.  
  
- Jeśli początek wątku zostanie osiągnięty, wątek zostanie zakończony.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Wyjątki i obsługa wyjątków](./index.md)
