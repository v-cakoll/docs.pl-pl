---
title: Korzystanie z wyjątków C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: 4012027dc1a9bd2543d0a4195360e5f7e0586fe1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705265"
---
# <a name="using-exceptions-c-programming-guide"></a>Używanie wyjątków (Przewodnik programowania w języku C#)
W C#programie błędy w programie w czasie wykonywania są propagowane za pośrednictwem programu przy użyciu mechanizmu nazywanego wyjątkami. Wyjątki są zgłaszane przez kod, który napotka błąd i przechwycony przez kod, który może poprawić błąd. Wyjątki mogą być zgłaszane przez .NET Framework środowisko uruchomieniowe języka wspólnego (CLR) lub kod w programie. Gdy wyjątek jest zgłaszany, propaguje stos wywołań do momentu znalezienia instrukcji `catch` dla wyjątku. Nieprzechwycone wyjątki są obsługiwane przez ogólną procedurę obsługi wyjątków dostarczoną przez system, który wyświetla okno dialogowe.  
  
 Wyjątki są reprezentowane przez klasy pochodne <xref:System.Exception>. Ta klasa identyfikuje typ wyjątku i zawiera właściwości, które zawierają szczegółowe informacje o wyjątku. Zgłaszanie wyjątku obejmuje utworzenie wystąpienia klasy pochodnej wyjątku, opcjonalnie skonfigurowanie właściwości wyjątku, a następnie wygenerowanie obiektu za pomocą słowa kluczowego `throw`. Na przykład:  
  
 [!code-csharp[csProgGuideExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#1)]  
  
 Po zgłoszeniu wyjątku środowisko uruchomieniowe sprawdza bieżącą instrukcję, aby sprawdzić, czy znajduje się w bloku `try`. Jeśli tak, wszystkie `catch` bloki skojarzone z blokiem `try` są sprawdzane w celu sprawdzenia, czy mogą przechwytywać wyjątek. bloki `Catch` zwykle określają typy wyjątków; Jeśli typ bloku `catch` jest tego samego typu co wyjątek lub Klasa bazowa wyjątku, blok `catch` może obsłużyć metodę. Na przykład:  
  
 [!code-csharp[csProgGuideExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#2)]  
  
 Jeśli instrukcja zwracająca wyjątek nie znajduje się w bloku `try` lub jeśli blok `try` zawierający go nie ma pasującego bloku `catch`, środowisko uruchomieniowe sprawdzi metodę wywołującą dla instrukcji `try` i bloków `catch`. Środowisko uruchomieniowe kontynuuje wywoływanie stosu, wyszukując zgodny blok `catch`. Po znalezieniu i wykonaniu bloku `catch` sterowanie jest przenoszona do następnej instrukcji po tym bloku `catch`.  
  
 Instrukcja `try` może zawierać więcej niż jeden blok `catch`. Zostanie wykonana Pierwsza instrukcja `catch`, która może obsłużyć wyjątek; wszystkie poniższe instrukcje `catch`, nawet jeśli są zgodne, są ignorowane. W związku z tym bloki catch powinny zawsze być uporządkowane z najbardziej specyficznych (lub najbardziej pochodnych) do najmniej określonych. Na przykład:  
  
 [!code-csharp[csProgGuideExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#3)]  
  
 Przed wykonaniem bloku `catch` środowisko uruchomieniowe sprawdzi `finally` bloków. bloki `Finally` umożliwiają programistom czyszczenie dowolnego niejednoznacznego stanu, który może być pozostawiony z przerwania `try` bloku, lub do zwolnienia zasobów zewnętrznych (takich jak uchwyty grafiki, połączenia z bazą danych lub strumienie plików) bez czekania na zakończenie działania modułu zbierającego elementy bezużyteczne w środowisku uruchomieniowym. Na przykład:  
  
 [!code-csharp[csProgGuideExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#4)]  
  
 Jeśli `WriteByte()` wywołał wyjątek, kod w drugim bloku `try`, który próbuje ponownie otworzyć plik, będzie kończyć się niepowodzeniem, jeśli `file.Close()` nie zostanie wywołana, a plik pozostanie zablokowany. Ponieważ `finally` bloki są wykonywane nawet w przypadku zgłoszenia wyjątku, blok `finally` w poprzednim przykładzie umożliwia poprawne zamknięcie pliku i pomaga uniknąć błędu.  
  
 Jeśli nie odnaleziono zgodnego bloku `catch` w stosie wywołań po zgłoszeniu wyjątku, wystąpi jedno z trzech rzeczy:  
  
- Jeśli wyjątek znajduje się w obrębie finalizatora, finalizator zostanie przerwany i zostanie wywołany podstawowy finalizator, jeśli istnieje.  
  
- Jeśli stos wywołań zawiera statyczny Konstruktor lub Inicjator pola statycznego, zgłaszany jest <xref:System.TypeInitializationException>, z oryginalnym wyjątek przypisany do właściwości <xref:System.Exception.InnerException%2A> nowego wyjątku.  
  
- Jeśli początek wątku zostanie osiągnięty, wątek zostanie zakończony.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Wyjątki i obsługa wyjątków](./index.md)
