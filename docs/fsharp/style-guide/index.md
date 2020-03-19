---
title: F# — przewodnik dotyczący stylu
description: Poznaj pięć zasad dobrego kodu F#.
ms.date: 12/10/2018
ms.openlocfilehash: 9f47257626e04b09b546de2ae315d48d791678be
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400268"
---
# <a name="f-style-guide"></a>F# — przewodnik dotyczący stylu

W poniższych artykułach opisano wskazówki dotyczące formatowania kodu F# i aktualne wskazówki dotyczące funkcji języka i sposobu ich użycia.

Te wskazówki zostały sformułowane na podstawie użycia Języka F# w dużych bazach kodu z różnorodną grupą programistów. Te wskazówki zazwyczaj prowadzi do pomyślnego użycia Języka F# i minimalizuje frustracje, gdy wymagania dotyczące programów zmieniają się wraz z uchwa.

## <a name="five-principles-of-good-f-code"></a>Pięć zasad dobrego kodu F#

Należy pamiętać o następujących zasadach za każdym razem, gdy piszesz kod F#, szczególnie w systemach, które będą się zmieniać wraz z urazem. Każdy element wskazówek w dalszych artykułach wynika z tych pięciu punktów.

1. **Dobry kod F# jest zwięzły, wyrazisty i komposable**

    F# ma wiele funkcji, które umożliwiają wyrażanie akcji w mniejszej liczbie wierszy kodu i ponowne użycie funkcji ogólnych. Biblioteka rdzenia F# zawiera również wiele przydatnych typów i funkcji do pracy z typowymi zbiorami danych. Skład własnych funkcji i tych w bibliotece podstawowej F# (lub innych bibliotek) jest częścią rutynowego programowania idiomatycznego F#. Z reguły, jeśli można wyrazić rozwiązanie problemu w mniejszej liczbie wierszy kodu, inni deweloperzy (lub twoja przyszła ja) będą doceniać. Zaleca się również użycie biblioteki, takiej jak FSharp.Core, [rozległe biblioteki .NET,](../../../api/index.md) na których działa F#, lub pakietu innej firmy na [NuGet,](https://www.nuget.org/) gdy trzeba wykonać zadanie nietrywialne.

2. **Dobry kod F# jest interoperacyjny**

    Współdziałanie może przybrać wiele form, w tym używanie kodu w różnych językach. Granice kodu, z którymi współpracują inne obiekty wywołujące, są krytyczne elementy, aby uzyskać prawo, nawet jeśli obiekty wywołujące są również w F#. Podczas pisania F#, zawsze należy myśleć o tym, jak inny kod wywoła kod piszesz, w tym jeśli robią to z innego języka, takich jak C#. [Wytyczne dotyczące projektowania składników F#](component-design-guidelines.md) szczegółowo opisują współdziałanie.

3. **Dobry kod F# korzysta z programowania obiektów, a nie orientacji obiektu**

    F# ma pełną obsługę programowania z obiektami w .NET, w tym [klas](../language-reference/classes.md), [interfejsów](../language-reference/interfaces.md), [modyfikatorów dostępu](../language-reference/access-control.md), [klas abstrakcyjnych](../language-reference/abstract-classes.md)i tak dalej. Dla bardziej skomplikowanego kodu funkcjonalnego, takich jak funkcje, które muszą być zgodne z kontekstem, obiekty można łatwo hermetyzować informacje kontekstowe w sposób, który nie może. Funkcje, takie jak [parametry opcjonalne](../language-reference/members/methods.md#optional-arguments) i ostrożne korzystanie z [przeciążenia](../language-reference/members/methods.md#overloaded-methods) może ułatwić korzystanie z tej funkcji dla rozmówców.

4. **Dobry kod F# działa dobrze bez narażania mutacji**

    Nie jest tajemnicą, że aby napisać kod o wysokiej wydajności, należy użyć mutacji. W końcu tak działają komputery. Taki kod jest często podatny na błędy i trudno jest uzyskać prawo. Unikaj narażania mutacji na osoby dzwoniące. Zamiast tego [należy utworzyć interfejs funkcjonalny, który ukrywa implementacji opartej na mutacji,](conventions.md#performance) gdy wydajność jest krytyczna.

5. **Dobry kod F# jest toolable**

    Narzędzia są nieocenione do pracy w dużych baz kodu i można napisać kod F#, tak aby można go było używać bardziej efektywnie z języka F#tooling. Jednym z przykładów jest upewnienie się, że nie przesadzasz z bezpunktowym stylem programowania, dzięki czemu wartości pośrednie mogą być kontrolowane za pomocą debugera. Innym przykładem jest użycie [komentarzy dokumentacji XML](../language-reference/xml-documentation.md) opisujących konstrukcje, które etykietki narzędzi w edytorach mogą wyświetlać te komentarze w witrynie wywołania. Zawsze pomyśl o tym, jak kod będzie odczytywany, nawigowany, debugowany i manipulowany przez innych programistów za pomocą ich narzędzi.

## <a name="next-steps"></a>Następne kroki

[Wskazówki dotyczące formatowania kodu F#](formatting.md) zawierają wskazówki dotyczące formatowania kodu, dzięki czemu jest łatwy do odczytania.

[Konwencje kodowania F#](conventions.md) zawierają wskazówki dotyczące idiomów programowania F#, które pomogą w długoterminowej konserwacji większych baz kodu F#.

[Wskazówki dotyczące projektowania składników F#](component-design-guidelines.md) zawierają wskazówki dotyczące tworzenia składników F#, takich jak biblioteki.
