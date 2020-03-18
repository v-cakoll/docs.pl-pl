---
title: Korzystanie z wyjątków — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: 4012027dc1a9bd2543d0a4195360e5f7e0586fe1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705265"
---
# <a name="using-exceptions-c-programming-guide"></a>Używanie wyjątków (Przewodnik programowania w języku C#)
W języku C#, błędy w programie w czasie wykonywania są propagowane za pośrednictwem programu przy użyciu mechanizmu o nazwie wyjątki. Wyjątki są generowane przez kod, który napotka błąd i przechwycone przez kod, który może poprawić błąd. Wyjątki mogą być generowane przez program runtime wspólnego języka .NET Framework (CLR) lub przez kod w programie. Po wymażeniu wyjątku propaguje `catch` stos wywołań, dopóki nie zostanie znaleziona instrukcja dla wyjątku. Nieprzechwycone wyjątki są obsługiwane przez ogólny program obsługi wyjątków dostarczonyprzez system, który wyświetla okno dialogowe.  
  
 Wyjątki są reprezentowane przez klasy <xref:System.Exception>pochodzące z . Ta klasa identyfikuje typ wyjątku i zawiera właściwości, które mają szczegółowe informacje o wyjątku. Zgłaszanie wyjątku polega na utworzeniu wystąpienia klasy pochodnej wyjątku, opcjonalnie konfigurowania właściwości wyjątku, `throw` a następnie zgłaszanie obiektu przy użyciu słowa kluczowego. Przykład:  
  
 [!code-csharp[csProgGuideExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#1)]  
  
 Po wyjątek wyjątek, czas wykonywania sprawdza bieżącą instrukcję, `try` aby zobaczyć, czy znajduje się w bloku. Jeśli tak, `catch` wszystkie bloki `try` skojarzone z blokiem są sprawdzane, aby zobaczyć, czy mogą przechwycić wyjątek. `Catch`bloki zazwyczaj określają typy wyjątków; Jeśli typ `catch` bloku jest tego samego typu co wyjątek lub klasy podstawowej wyjątku, `catch` blok może obsługiwać metodę. Przykład:  
  
 [!code-csharp[csProgGuideExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#2)]  
  
 Jeśli instrukcja, która zgłasza wyjątek `try` nie jest `try` w bloku lub jeśli blok, który otacza nie ma pasującego `catch` bloku, czas wykonywania sprawdza metodę wywoływania `try` dla instrukcji i `catch` bloków. Środowiska uruchomieniowego kontynuuje stos wywoławczy, szukając zgodnego `catch` bloku. Po `catch` znalezieniu i wykonaniu bloku kontrola jest przekazywana `catch` do następnej instrukcji po tym bloku.  
  
 Instrukcja `try` może zawierać `catch` więcej niż jeden blok. Pierwsza `catch` instrukcja, która może obsłużyć wyjątek jest wykonywana; wszelkie `catch` następujące instrukcje, nawet jeśli są one zgodne, są ignorowane. W związku z tym catch bloki powinny być zawsze uporządkowane z najbardziej specyficznych (lub najbardziej pochodnych) do najmniej szczegółowych. Przykład:  
  
 [!code-csharp[csProgGuideExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#3)]  
  
 Przed `catch` wykonaniem bloku, w czasie `finally` wykonywania sprawdza bloki. `Finally`bloki umożliwiają programisty, aby oczyścić wszelkie niejednoznaczne stan, który może być pozostawiony z przerwanego `try` bloku lub zwolnić żadnych zasobów zewnętrznych (takich jak uchwyty grafiki, połączenia z bazą danych lub strumieni plików) bez oczekiwania na moduł zbierający elementy bezużyteczne w czasie wykonywania, aby sfinalizować obiekty. Przykład:  
  
 [!code-csharp[csProgGuideExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#4)]  
  
 Jeśli `WriteByte()` zgłosił wyjątek, kod w `try` drugim bloku, który próbuje ponownie `file.Close()` otworzyć plik zakończy się niepowodzeniem, jeśli nie zostanie wywołana, a plik pozostanie zablokowany. Ponieważ `finally` bloki są wykonywane, nawet `finally` jeśli wyjątek jest wyjątek, blok w poprzednim przykładzie pozwala na plik do zamknięcia poprawnie i pomaga uniknąć błędu.  
  
 Jeśli nie `catch` zostanie znaleziony żaden zgodny blok na stosie wywołań po wygenerowaniu wyjątku, występuje jedna z trzech rzeczy:  
  
- Jeśli wyjątek znajduje się w finalizatora, finalizator jest przerywany i finalizator bazy, jeśli istnieje, jest wywoływana.  
  
- Jeśli stos wywołań zawiera konstruktora statycznego <xref:System.TypeInitializationException> lub inicjatora pola <xref:System.Exception.InnerException%2A> statycznego, a jest zgłaszany, z oryginalnym wyjątkiem przypisanym do właściwości nowego wyjątku.  
  
- Jeśli zostanie osiągnięty początek wątku, wątek zostanie zakończony.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Wyjątki i obsługa wyjątków](./index.md)
