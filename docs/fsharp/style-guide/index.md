---
title: 'Przewodnik stylistyczny F #'
description: 'Dowiedz się pięciu zasady dobrej kodzie języka F #.'
ms.date: 05/14/2018
ms.openlocfilehash: 1d0f4e2a946f0cc91f376ba624f847549a830bc7
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "34235908"
---
# <a name="f-style-guide"></a>Przewodnik stylistyczny F #

Następujące artykuły opisano wskazówki dotyczące formatowania kodu F # i miejscowego wskazówki dotyczące funkcji języka i jak powinna być używana.

Niniejsze wskazówki został opracowany na podstawie użycia języka F # w dużych ścieżek bazowych kodów z różnych grupa programistów. Niniejsze wskazówki zwykle prowadzi do pomyślnego użycia języka F # i minimalizuje frustrations, gdy zmienią się wymagania dla programów wraz z upływem czasu.

## <a name="five-principles-of-good-f-code"></a>Pięć zasadami dobrej kodzie języka F #

Następujące zasady należy mieć na uwadze każdym razem, gdy piszesz kod F #, szczególnie w przypadku systemów, które zostaną zmienione wraz z upływem czasu. Każdy element ze wskazówkami zawartymi w dalsze artykuły wynika z tych pięciu punktów.

1. **Dobre kodzie języka F # jest zwięzły i obszerne strategie**

    F # zawiera wiele funkcji, które umożliwiają express akcje w mniejszej liczby linii kodu i ponowne użycie ogólną funkcję. Biblioteka core F # zawiera również wiele typów przydatne i funkcje do pracy z typowych kolekcji danych. Zgodnie z ogólną zasadą Jeśli rozwiązanie problemu w mniejszą liczbę wierszy kodu można wyrazić innym deweloperom (lub z własnym przyszłych) będzie przynosi. Również zdecydowanie zaleca się, że używasz biblioteki, takie jak elementu FSharp.Core, [ogromnej biblioteki .NET](https://docs.microsoft.com/dotnet/api/) uruchomionym F #, lub pakiet innych firm na [NuGet](https://www.nuget.org/) kiedy trzeba będzie wykonać proste zadanie.

2. **Dobre kodzie języka F # jest współpracujący**

    Współdziałanie można Przybieranie wielu form, w tym korzystanie z kodu w różnych językach. Granice swój kod, który współdziałać inne obiekty wywołujące są najistotniejsze, aby uzyskać odpowiednie. Podczas pisania F #, możesz powinien zawsze pomyśleć o jak inny kod wywoła do kodu, którą piszesz, w tym, jeśli to zrobią z innego języka C#. [F # składnika wytyczne dotyczące projektowania](component-design-guidelines.md) współdziałanie szczegółowo opisano.

3. **Dobre kodzie języka F # sprawia, że używają programowania obiektu, obiekt nie orientacji**

    F # zawiera pełne wsparcie dla programowania przy użyciu obiektów na platformie .NET, w tym [klasy](../language-reference/classes.md), [interfejsów](../language-reference/interfaces.md), [modyfikatorach dostępu](../language-reference/access-control.md), [klasyabstrakcyjne](../language-reference/abstract-classes.md)i tak dalej. Dla bardziej skomplikowanego kodu funkcjonalności, takich jak funkcje, które muszą być oparte na kontekście obiekty można łatwo hermetyzować informacje kontekstowe w sposób, który nie funkcji. Funkcje, takie jak [następujące parametry opcjonalne](../language-reference/members/methods.md#optional-arguments) i dokładnej użytkowania [przeciążenie](../language-reference/members/methods.md#overloaded-methods) ułatwia użycie tej funkcji dla obiektów wywołujących.

4. **Dobre kodzie języka F # wykonuje się dobrze, bez narażania mutacji**

    Nie jest tajemnicą, aby napisać kod o wysokiej wydajności, należy użyć mutacji. To, jak komputery działają, gdy wszystkie. Taki kod jest często podatne na błędy i problemy z uzyskaniem prawo. Należy unikać udostępnianie mutacji dotyczące obiektów wywołujących. Zamiast tego [tworzenie funkcjonalności interfejsu, która ukrywa implementacji opartej na mutacji](conventions.md#performance) Jeśli wydajność ma kluczowe znaczenie.

5. **Biorąc to dobry kodzie języka F #**

    Narzędzia są nieocenieni dla pracy w dużych bazach kodu, a następnie można napisać kod F # w taki sposób, aby mogły być używane w bardziej wydajnie za pomocą narzędzi języka F #. Przykładem jest upewnienie się, że użytkownik nie nadużywać stylem bezpłatne punktu programowania, tak, aby wartości pośrednich mogą być kontrolowane za pomocą debugera. Innym przykładem jest przy użyciu [komentarze dokumentacji XML](../language-reference/xml-documentation.md) opisujące konstrukcje w taki sposób, że etykietki narzędzi w edytorach można wyświetlać te komentarze w witrynie wywołania. Zawsze zastanowić, jak kod będzie można odczytać, przejście, debugowania i zmieniane przez innych programistów przy użyciu swoich narzędzi.

## <a name="next-steps"></a>Następne kroki

[Wskazówki dotyczące formatowania kodu F #](formatting.md) zawierają wskazówki dotyczące formatowania kodu, aby była łatwa do odczytania.

[Konwencje kodowania F #](conventions.md) zapewniają wskazówki dotyczące programowania idiomy pomagających długoterminowej obsługi większych języka F # F # bazach kodu.

[F # składnika wytyczne dotyczące projektowania](component-design-guidelines.md) zawierają wskazówki dotyczące tworzenia F # składników, takich jak biblioteki.
