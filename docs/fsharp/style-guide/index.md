---
title: 'Przewodnik po stylu F #'
description: 'Dowiedz się pięć zasadami dobrej kodzie języka F #.'
ms.date: 05/14/2018
ms.openlocfilehash: 6d8c1336ca991040a8f6e13290d209cb3b70054d
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34235908"
---
# <a name="f-style-guide"></a>Przewodnik po stylu F #

Poniższe artykuły zawierają wskazówki dotyczące formatowania kodu F # i miejscowego wskazówki dotyczące funkcji języka i jak powinny być używane.

W tych wskazówkach został opracowany na podstawie użycia języka F # w dużych codebases z różnych grupy programistów. W tych wskazówkach zwykle prowadzi do pomyślnego użycia języka F # i minimalizuje frustrations zmiany wymogów dla programów wraz z upływem czasu.

## <a name="five-principles-of-good-f-code"></a>Pięć zasadami dobrej kodzie języka F #

Następujące zasady należy mieć na uwadze za każdym razem zapisu kodzie języka F #, szczególnie w systemach, które zmieni się wraz z upływem czasu. Każdą wskazówki w artykułach dalsze wynika z tych punktów pięć.

1. **Dobrym kodzie języka F # jest zwięzły i obszerne**

    F # ma wiele funkcji, które umożliwiają express działaniami w mniej wierszy kodu i ponowne użycie funkcji ogólnego. Biblioteki podstawowej F # zawiera także wiele przydatne typy i funkcje do pracy z typowych kolekcji danych. Jako ogólną regułę Jeśli rozwiązanie problemu w mniej wierszy kodu można wyrazić inni deweloperzy (lub użytkownika samoobsługowego przyszłych) będzie znaczących. Również zdecydowanie zaleca się, że używasz biblioteki, takich jak plikiem FSharp.Core, [przeważająca bibliotek .NET](https://docs.microsoft.com/dotnet/api/) uruchomioną F #, lub innych firm pakietu na [NuGet](https://www.nuget.org/) kiedy trzeba wykonać zadanie proste.

2. **Współdziałanie jest dobrym kodzie języka F #**

    Współdziałanie może zająć wiele formy, wykorzystywanie kodu w różnych językach. Granice swój kod, który jest współpraca z innych klientów są najistotniejsze uzyskać prawo. Podczas zapisywania F # możesz powinien zawsze pomyśleć o jak inny kod wywoła do kodu, który pisania, w tym, jeśli w tym celu w innym języku, takich jak C#. [F # składnika zaleceń dotyczących projektowania](component-design-guidelines.md) współdziałanie szczegółowo opisano.

3. **Dobrym kodzie języka F # sprawia, że Użyj programowania obiektu, ponieważ obiekt nie orientacji**

    F # ma pełną obsługę programowania z obiektami w środowisku .NET, w tym [klasy](../language-reference/classes.md), [interfejsów](../language-reference/interfaces.md), [modyfikatorów dostępu](../language-reference/access-control.md), [klasyabstrakcyjne](../language-reference/abstract-classes.md)i tak dalej. Dla bardziej złożonego kodu funkcjonalności, takich jak funkcje, które muszą być kontekstu obsługujący obiekty łatwo umożliwiająca Hermetyzowanie informacje kontekstowe w sposób, w którym nie funkcji. Funkcje, takie jak [następujące parametry opcjonalne](../language-reference/members/methods.md#optional-arguments) i [przeładowanie](../language-reference/members/methods.md#overloaded-methods) również pomocy użycie tej funkcji dla wywoływania.

4. **Wykonuje dobrej kodzie języka F # nie udostępnianie mutacji**

    Nie jest brak tajne, że aby napisać kod wysokiej wydajności, należy użyć mutacji. Jest komputerów działania, po wszystkich. Taki kod jest często podatne na błędy i trudne do pobrania prawo. Unikaj udostępnianie mutacji wywołań. Wyszukiwanie funkcjonalności interfejsu na podstawie mutacji implementacji.

5. **Biorąc to dobry kodzie języka F #**

    Narzędzia są cenne dla pracy w dużych codebases, można napisać kod w języku F # tak, aby mógł być używany w bardziej efektywnie z narzędziami języka F #. Przykładem jest upewnienie się, że możesz nie nadużywać stylem bez punktu programowania, dzięki czemu można sprawdzić wartości pośrednich z debugera. Innym przykładem jest przy użyciu [komentarze dokumentacji XML](../language-reference/xml-documentation.md) opisujące konstrukcje tak, aby etykietki narzędzi w edytorach można wyświetlać te komentarze na miejsce wywołania. Zawsze traktować jak kodu będzie można odczytać, przejście debugowania i manipulować innych programistów z ich narzędzi.

## <a name="next-steps"></a>Następne kroki

[Wskazówki dotyczące formatowania kodu języka F #](formatting.md) zawierają wskazówki dotyczące formatowania kodu, dzięki czemu jest łatwy do odczytania.

[F # konwencje kodowania](conventions.md) zawierają wskazówki dla codebases idioms pomagających długoterminowej obsługi większych języka F # programowania w języku F #.

[F # składnika zaleceń dotyczących projektowania](component-design-guidelines.md) zawierają wskazówki dotyczące tworzenia F # składniki, takie jak biblioteki.
