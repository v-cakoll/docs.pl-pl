---
ms.openlocfilehash: ca369c4e3f78648c6e8e0bcb5d54711d3009a769
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174269"
---
### <a name="blazor-insignificant-whitespace-trimmed-from-components-at-compile-time"></a>Blazor: nieznaczące odstępy są obcinane ze składników w czasie kompilacji

Począwszy od ASP.NET Core 5,0 w wersji zapoznawczej 7 kompilator Razor pomija nieznaczące odstępy w składnikach Blazor (pliki*Razor* ) w czasie kompilacji. Aby zapoznać się z omówieniem, zobacz temat Issue [dotnet/aspnetcore # 23568](https://github.com/dotnet/aspnetcore/issues/23568).

#### <a name="version-introduced"></a>Wprowadzona wersja

5,0 wersja zapoznawcza 7

#### <a name="old-behavior"></a>Stare zachowanie

W 3. x wersjach Blazor Server i Blazor webassembly biały znak jest uznawany za kod źródłowy składnika. Odstępy — tylko węzły tekstowe są renderowane w Document Object Model przeglądarki (DOM), nawet jeśli nie ma efektów wizualnych.

Rozważmy następujący kod składnika Blazor:

```razor
<ul>
    @foreach (var item in Items)
    {
        <li>
            @item.Text
        </li>
    }
</ul>
```

W poprzednim przykładzie renderowane są dwa węzły odstępu:

* Poza `@foreach` blokiem kodu.
* Wokół `<li>` elementu.
* Wokół `@item.Text` danych wyjściowych.

Lista zawierająca 100 elementów skutkuje w węzłach o 402. Jest to ponad połowę wszystkich wyrenderowanych węzłów, nawet jeśli żaden z węzłów odstępu nie ma wizualnie wpływu na renderowane dane wyjściowe.

Podczas renderowania statycznego kodu HTML dla składników, odstęp wewnątrz tagu nie został zachowany. Na przykład Wyświetl źródło następującego składnika:

```razor
<foo        bar="baz"     />
```

Biały znak nie jest zachowywany. Wstępnie renderowane dane wyjściowe to:

```razor
<foo bar="baz" />
```

#### <a name="new-behavior"></a>Nowe zachowanie

O ile `@preservewhitespace` dyrektywa nie jest używana z wartością `true` , węzły odstępu są usuwane, jeśli:

* Są wiodące lub końcowe w obrębie elementu.
* Są wiodące lub końcowe w obrębie `RenderFragment` parametru. Na przykład zawartość podrzędna jest przesyłana do innego składnika.
* Należy użyć bloku kodu w języku C#, takiego jak `@if` i `@foreach` .

#### <a name="reason-for-change"></a>Przyczyna zmiany

Celem Blazor w ASP.NET Core 5,0 jest poprawa wydajności renderowania i różnicowania. Nieznaczące węzły drzewa odstępów zużywają do 40% czasu renderowania w testach porównawczych.

#### <a name="recommended-action"></a>Zalecana akcja

W większości przypadków nie ma to żadnego oddziaływania na układ wizualizacji renderowanego składnika. Jednak usunięcie odstępu może mieć wpływ na renderowane dane wyjściowe w przypadku używania reguły CSS, takiej jak `white-space: pre` . Aby wyłączyć tę optymalizację wydajności i zachować odstęp, wykonaj jedną z następujących czynności:

* Dodaj `@preservewhitespace true` dyrektywę w górnej części pliku *Razor* , aby zastosować preferencję do określonego składnika.
* Dodaj `@preservewhitespace true` dyrektywę wewnątrz pliku *_Imports. Razor* , aby zastosować preferencję do całego podkatalogu lub całego projektu.

W większości przypadków żadna akcja nie jest wymagana, ponieważ aplikacje zwykle nadal zachowują się normalnie (ale szybciej). W przypadku wyłączania odstępów powoduje wszelkie problemy dotyczące określonego składnika, użyj `@preservewhitespace true` w tym składniku, aby wyłączyć tę optymalizację.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!--

#### Affected APIs

Not detectable via API analysis

-->
