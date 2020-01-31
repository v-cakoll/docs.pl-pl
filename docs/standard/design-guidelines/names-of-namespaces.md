---
title: Nazwy przestrzeni nazw
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
ms.openlocfilehash: 52fee0dfaff284c2c1a6afcb8aa7530c28a60d65
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744142"
---
# <a name="names-of-namespaces"></a>Nazwy przestrzeni nazw
Podobnie jak w przypadku innych wytycznych dotyczących nazewnictwa, celem podczas nazewnictwa przestrzeni nazw jest utworzenie wystarczającej przejrzystości dla programisty korzystającego z platformy, aby natychmiast znać zawartość przestrzeni nazw. Następujący szablon określa ogólną regułę nazewnictwa przestrzeni nazw:

 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`

 Oto przykłady:

 `Fabrikam.Math` `Litware.Security`

 ✔️ NALEŻY prefiksować nazwy przestrzeni nazw z nazwą firmy, aby zapobiec istnieniu przez obszary nazw różnych firm.

 ✔️ Użyj stabilnej, niezależnej od wersji nazwy produktu na drugim poziomie nazwy przestrzeni nazw.

 ❌ nie używaj hierarchii organizacyjnych jako podstawy nazw w hierarchiach przestrzeni nazw, ponieważ nazwy grup w firmach mają być krótkotrwałe. Organizuj hierarchię przestrzeni nazw wokół grup powiązanych technologii.

 ✔️ używać PascalCasing i oddzielaj składniki przestrzeni nazw z okresami (np. `Microsoft.Office.PowerPoint`). Jeśli Marka używa nietradycyjnej wielkości liter, należy postępować zgodnie z wielkością liter zdefiniowaną przez markę, nawet jeśli odbiega od normalnej wielkości liter przestrzeni nazw.

 ✔️ ROZWAŻYĆ użycie nazw w liczbie mnogiej nazw, tam gdzie to konieczne.

 Na przykład użyj `System.Collections`, a nie `System.Collection`. Jednak nazwy marki i akronimy są wyjątkami od tej reguły. Na przykład użyj `System.IO`, a nie `System.IOs`.

 ❌ nie należy używać tej samej nazwy dla przestrzeni nazw i typu w tej przestrzeni nazw.

 Na przykład nie należy używać `Debug` jako nazwy przestrzeni nazw, a następnie dostarczać klasę o nazwie `Debug` w tej samej przestrzeni nazw. Kilka kompilatorów wymaga, aby te typy były w pełni kwalifikowane.

### <a name="namespaces-and-type-name-conflicts"></a>Konflikty nazw i nazw typów
 ❌ nie należy wprowadzać nazw typów ogólnych, takich jak `Element`, `Node`, `Log`i `Message`.

 Istnieje bardzo wysokie prawdopodobieństwo, że spowoduje to powstanie konfliktów nazw typu w typowych scenariuszach. Należy zakwalifikować nazwy typów ogólnych (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).

 Istnieją szczegółowe wskazówki dotyczące unikania konfliktów nazw typów dla różnych kategorii przestrzeni nazw.

- **Przestrzenie nazw modelu aplikacji**

     Przestrzenie nazw należące do pojedynczego modelu aplikacji są często używane razem, ale są prawie nigdy nieużywane z przestrzeniami nazw innych modeli aplikacji. Na przykład przestrzeń nazw <xref:System.Windows.Forms?displayProperty=nameWithType> jest bardzo rzadko używana razem z przestrzenią nazw <xref:System.Web.UI?displayProperty=nameWithType>. Poniżej znajduje się lista dobrze znanych grup przestrzeni nazw modelu aplikacji:

     `System.Windows*` `System.Web.UI*`

     ❌ nie dają takiej samej nazwy do typów w przestrzeniach nazw w ramach jednego modelu aplikacji.

     Na przykład nie należy dodawać typu o nazwie `Page` do przestrzeni nazw <xref:System.Web.UI.Adapters?displayProperty=nameWithType>, ponieważ przestrzeń nazw <xref:System.Web.UI?displayProperty=nameWithType> zawiera już typ o nazwie `Page`.

- **Przestrzenie nazw infrastruktury**

     Ta grupa zawiera przestrzenie nazw, które są rzadko importowane podczas opracowywania typowych aplikacji. Na przykład `.Design` przestrzenie nazw są używane głównie podczas opracowywania narzędzi programistycznych. Unikanie konfliktów z typami w tych obszarach nazw nie jest krytyczne.

- **Podstawowe przestrzenie nazw**

     Podstawowe przestrzenie nazw obejmują wszystkie `System` przestrzenie nazw, z wyłączeniem przestrzeni nazw modeli aplikacji i przestrzeni nazw infrastruktury. Podstawowe przestrzenie nazw obejmują między innymi `System`, `System.IO`, `System.Xml`i `System.Net`.

     ❌ nie należy przyznawać nazw typów, które mogłyby powodować konflikt z dowolnym typem w podstawowych obszarach nazw.

     Na przykład nigdy nie używaj `Stream` jako nazwy typu. Wystąpił konflikt z <xref:System.IO.Stream?displayProperty=nameWithType>, bardzo często używanym typem.

- **Grupy przestrzeni nazw technologii**

     Ta kategoria zawiera wszystkie przestrzenie nazw zawierające te same dwa węzły przestrzeni nazw `(<Company>.<Technology>*`), takie jak `Microsoft.Build.Utilities` i `Microsoft.Build.Tasks`. Ważne jest, aby typy należące do jednej technologii nie powodowały konfliktów ze sobą.

     ❌ nie przypisuj nazw typów, które mogłyby powodować konflikt z innymi typami w ramach jednej technologii.

     ❌ nie należy wprowadzać nazw typów w zależności od typów w przestrzeni nazw technologii i przestrzeni nazw modelu aplikacji (chyba że technologia nie jest przeznaczona do użycia z modelem aplikacji).

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
