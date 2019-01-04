---
title: F#Przewodnik po stylu
description: Dowiedz się, zasady pięciu dobrze F# kodu.
ms.date: 12/10/2018
ms.openlocfilehash: 9f47257626e04b09b546de2ae315d48d791678be
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54030272"
---
# <a name="f-style-guide"></a>F#Przewodnik po stylu

Następujące artykuły opisano wskazówki dotyczące formatowania F# kod i wskazówek istotna dla funkcji języka i jak powinna być używana.

Te wskazówki zostały sformułowane oparte na korzystanie z F# w dużych ścieżek bazowych kodów z różnych grupa programistów. Wskazówki te zwykle prowadzi do pomyślnego użycia F# i minimalizuje frustrations, gdy zmienią się wymagania dla programów wraz z upływem czasu.

## <a name="five-principles-of-good-f-code"></a>Zasady pięciu dobrze F# kodu

Pamiętać o następujących zasadach ilekroć pisania F# kod, szczególnie w przypadku systemów, które zostaną zmienione wraz z upływem czasu. Każdy element ze wskazówkami zawartymi w dalsze artykuły wynika z tych pięciu punktów.

1. **Dobre F# kod jest zwięzły, ekspresyjny i konfigurowalna**

    F#oferuje wiele funkcji umożliwiających express akcje w mniejszej liczby linii kodu i ponowne użycie ogólną funkcję. F# Biblioteka podstawowa zawiera również wiele typów przydatne i funkcje do pracy z typowych kolekcji danych. Tworzenie własnych funkcji i znajdującymi się na F# Biblioteka podstawowa (lub inne biblioteki) jest częścią standardowego idiomatyczną F# programowania. Zgodnie z ogólną zasadą Jeśli rozwiązanie problemu w mniejszą liczbę wierszy kodu można wyrazić innym deweloperom (lub z własnym przyszłych) będzie przynosi. Również zdecydowanie zaleca się, że używasz biblioteki, takie jak elementu FSharp.Core, [ogromnej biblioteki .NET](../../../api/index.md) , F# działa, lub pakiet innych firm na [NuGet](https://www.nuget.org/) kiedy trzeba będzie wykonać proste zadanie.

2. **Dobre F# kodu jest współpracujący**

    Współdziałanie można Przybieranie wielu form, w tym korzystanie z kodu w różnych językach. Granice swój kod, który współdziałać inne obiekty wywołujące są najistotniejsze można pobrać po prawej stronie, nawet jeśli funkcja wywołująca są również w F#. Podczas zapisywania F#, użytkownik powinien zawsze pomyśleć o jak inny kod będzie wywoływać kod, pisząc, w tym, jeśli to zrobią z innego języka, takich jak C#. [ F# Wytyczne dotyczące projektowania składnika](component-design-guidelines.md) współdziałanie szczegółowo opisano.

3. **Dobre F# kod sprawia, że używają programowania obiektu, obiekt nie orientacji**

    F#ma pełne wsparcie dla programowania przy użyciu obiektów na platformie .NET, w tym [klasy](../language-reference/classes.md), [interfejsów](../language-reference/interfaces.md), [modyfikatorach dostępu](../language-reference/access-control.md), [klasyabstrakcyjne](../language-reference/abstract-classes.md)i tak dalej. Dla bardziej skomplikowanego kodu funkcjonalności, takich jak funkcje, które muszą być oparte na kontekście obiekty można łatwo hermetyzować informacje kontekstowe w sposób, który nie funkcji. Funkcje, takie jak [następujące parametry opcjonalne](../language-reference/members/methods.md#optional-arguments) i dokładnej użytkowania [przeciążenie](../language-reference/members/methods.md#overloaded-methods) ułatwia użycie tej funkcji dla obiektów wywołujących.

4. **Dobre F# kod wykonuje się dobrze, bez narażania mutacji**

    Nie jest tajemnicą, aby napisać kod o wysokiej wydajności, należy użyć mutacji. To, jak komputery działają, gdy wszystkie. Taki kod jest często podatne na błędy i problemy z uzyskaniem prawo. Należy unikać udostępnianie mutacji dotyczące obiektów wywołujących. Zamiast tego [tworzenie funkcjonalności interfejsu, która ukrywa implementacji opartej na mutacji](conventions.md#performance) Jeśli wydajność ma kluczowe znaczenie.

5. **Dobre F# kod jest biorąc**

    Narzędzia są nieocenieni dla pracy w dużych bazach kodu, a następnie można napisać F# kodu w taki sposób, że można efektywniej przy użyciu F# narzędzi języka. Przykładem jest upewnienie się, że użytkownik nie nadużywać stylem bezpłatne punktu programowania, tak, aby wartości pośrednich mogą być kontrolowane za pomocą debugera. Innym przykładem jest przy użyciu [komentarze dokumentacji XML](../language-reference/xml-documentation.md) opisujące konstrukcje w taki sposób, że etykietki narzędzi w edytorach można wyświetlać te komentarze w witrynie wywołania. Zawsze zastanowić, jak kod będzie można odczytać, przejście, debugowania i zmieniane przez innych programistów przy użyciu swoich narzędzi.

## <a name="next-steps"></a>Następne kroki

[ F# Wskazówki dotyczące formatowania kodu](formatting.md) zawierają wskazówki dotyczące formatowania kodu, aby była łatwa do odczytania.

[ F# Konwencje kodowania](conventions.md) zawierają wskazówki dotyczące F# programowania idiomy pomagających długoterminowej obsługi większych F# bazach kodu.

[ F# Wytyczne dotyczące projektowania składnika](component-design-guidelines.md) zawierają wskazówki dotyczące tworzenia F# składników, takich jak biblioteki.
