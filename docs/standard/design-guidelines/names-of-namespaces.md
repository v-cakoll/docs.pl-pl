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
ms.openlocfilehash: 0678f695e3ae7c40660031862c9073a21fd72491
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709234"
---
# <a name="names-of-namespaces"></a>Nazwy przestrzeni nazw
Podobnie jak w przypadku innych wytycznych dotyczących nazewnictwa, celem podczas nazewnictwa przestrzeni nazw jest utworzenie wystarczającej przejrzystości dla programisty korzystającego z platformy, aby natychmiast znać zawartość przestrzeni nazw. Następujący szablon określa ogólną regułę nazewnictwa przestrzeni nazw:  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 Oto przykłady:  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 **✓ DO** prefiksu nazwy przestrzeni nazw o nazwie firmy, aby zapobiec przestrzenie nazw różnych firm z o tej samej nazwie.  
  
 **✓ DO** użyć nazwy stabilny, niezależny od wersji produktu w drugiej nazwy przestrzeni nazw.  
  
 **X DO NOT** Użyj hierarchii organizacji na podstawie nazw w hierarchii obszaru nazw, ponieważ nazwy grup w ramach firmy mogą być krótkotrwały. Organizuj hierarchię przestrzeni nazw wokół grup powiązanych technologii.  
  
 **✓ DO** PascalCasing i składniki oddzielne przestrzeni nazw za pomocą kropek (np. `Microsoft.Office.PowerPoint`). Jeśli Marka używa nietradycyjnej wielkości liter, należy postępować zgodnie z wielkością liter zdefiniowaną przez markę, nawet jeśli odbiega od normalnej wielkości liter przestrzeni nazw.  
  
 **✓ CONSIDER** przy użyciu nazwy przestrzeni nazw w liczbie mnogiej, gdzie jest to odpowiednie.  
  
 Na przykład użyj `System.Collections`, a nie `System.Collection`. Jednak nazwy marki i akronimy są wyjątkami od tej reguły. Na przykład użyj `System.IO`, a nie `System.IOs`.  
  
 **X DO NOT** Użyj takiej samej nazwy przestrzeni nazw i typ w tej przestrzeni nazw.  
  
 Na przykład nie należy używać `Debug` jako nazwy przestrzeni nazw, a następnie dostarczać klasę o nazwie `Debug` w tej samej przestrzeni nazw. Kilka kompilatorów wymaga, aby te typy były w pełni kwalifikowane.  
  
### <a name="namespaces-and-type-name-conflicts"></a>Konflikty nazw i nazw typów  
 **X DO NOT** wprowadzenie nazwy typu ogólnego, takich jak `Element`, `Node`, `Log`, i `Message`.  
  
 Istnieje bardzo wysokie prawdopodobieństwo, że spowoduje to powstanie konfliktów nazw typu w typowych scenariuszach. Należy zakwalifikować nazwy typów ogólnych (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).  
  
 Istnieją szczegółowe wskazówki dotyczące unikania konfliktów nazw typów dla różnych kategorii przestrzeni nazw.  
  
- **Przestrzenie nazw modelu aplikacji**  
  
     Przestrzenie nazw należące do pojedynczego modelu aplikacji są często używane razem, ale są prawie nigdy nieużywane z przestrzeniami nazw innych modeli aplikacji. Na przykład przestrzeń nazw <xref:System.Windows.Forms?displayProperty=nameWithType> jest bardzo rzadko używana razem z przestrzenią nazw <xref:System.Web.UI?displayProperty=nameWithType>. Poniżej znajduje się lista dobrze znanych grup przestrzeni nazw modelu aplikacji:  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X DO NOT** nadać tej samej nazwy dla typów w przestrzeniach nazw w obrębie modelu pojedynczej aplikacji.  
  
     Na przykład nie należy dodawać typu o nazwie `Page` do przestrzeni nazw <xref:System.Web.UI.Adapters?displayProperty=nameWithType>, ponieważ przestrzeń nazw <xref:System.Web.UI?displayProperty=nameWithType> zawiera już typ o nazwie `Page`.  
  
- **Przestrzenie nazw infrastruktury**  
  
     Ta grupa zawiera przestrzenie nazw, które są rzadko importowane podczas opracowywania typowych aplikacji. Na przykład `.Design` przestrzenie nazw są używane głównie podczas opracowywania narzędzi programistycznych. Unikanie konfliktów z typami w tych obszarach nazw nie jest krytyczne.  
  
- **Podstawowe przestrzenie nazw**  
  
     Podstawowe przestrzenie nazw obejmują wszystkie `System` przestrzenie nazw, z wyłączeniem przestrzeni nazw modeli aplikacji i przestrzeni nazw infrastruktury. Podstawowe przestrzenie nazw obejmują między innymi `System`, `System.IO`, `System.Xml`i `System.Net`.  
  
     **X DO NOT** zapewnia typy nazw, które spowodowałoby to konflikt z dowolnego typu w przestrzeniach nazw Core.  
  
     Na przykład nigdy nie używaj `Stream` jako nazwy typu. Wystąpił konflikt z <xref:System.IO.Stream?displayProperty=nameWithType>, bardzo często używanym typem.  
  
- **Grupy przestrzeni nazw technologii**  
  
     Ta kategoria zawiera wszystkie przestrzenie nazw zawierające te same dwa węzły przestrzeni nazw `(<Company>.<Technology>*`), takie jak `Microsoft.Build.Utilities` i `Microsoft.Build.Tasks`. Ważne jest, aby typy należące do jednej technologii nie powodowały konfliktów ze sobą.  
  
     **X DO NOT** przypisać nazwy typów, które spowodowałoby to konflikt z innymi typami w ramach pojedynczego technologii.  
  
     **X DO NOT** wprowadzenie typu konfliktów nazw między typami w przestrzeniach nazw technologii i przestrzeń nazw modelu aplikacji (chyba że technologii nie jest przeznaczona do użycia z modelem aplikacji).  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
