---
title: Nazwy przestrzeni nazw
ms.date: 03/30/2017
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d68966f60c5039fd67195a03facc1586b9ed154
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44097012"
---
# <a name="names-of-namespaces"></a>Nazwy przestrzeni nazw
Jako przy użyciu innych zasadach nazywania celem podczas nadawania nazw przestrzeni nazw jest utworzenie przejrzystości wystarczające do programisty należy od razu wiedzieć, co to jest prawdopodobnie zawartości przestrzeni nazw przy użyciu platformy. Następujący szablon określa zasady nazewnictwa przestrzeni nazw:  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 Poniżej przedstawiono przykłady:  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 **✓ DO** prefiksu nazwy przestrzeni nazw o nazwie firmy, aby zapobiec przestrzenie nazw różnych firm z o tej samej nazwie.  
  
 **✓ DO** użyć nazwy stabilny, niezależny od wersji produktu w drugiej nazwy przestrzeni nazw.  
  
 **X DO NOT** Użyj hierarchii organizacji na podstawie nazw w hierarchii obszaru nazw, ponieważ nazwy grup w ramach firmy mogą być krótkotrwały. Organizuj hierarchii przestrzenie nazw wokół grup powiązanych technologii.  
  
 **✓ DO** PascalCasing i składniki oddzielne przestrzeni nazw za pomocą kropek (np. `Microsoft.Office.PowerPoint`). Jeśli swoją markę wykorzystuje nietradycyjnych wielkości liter, powinien być zgodny definicją Twojej marki wielkości liter, nawet wtedy, gdy odbiega od wielkość liter w wyrazie normalne przestrzeni nazw.  
  
 **✓ CONSIDER** przy użyciu nazwy przestrzeni nazw w liczbie mnogiej, gdzie jest to odpowiednie.  
  
 Na przykład użyć `System.Collections` zamiast `System.Collection`. Nazw marek i akronimów są jednak wyjątki od tej reguły. Na przykład użyć `System.IO` zamiast `System.IOs`.  
  
 **X DO NOT** Użyj takiej samej nazwy przestrzeni nazw i typ w tej przestrzeni nazw.  
  
 Na przykład nie używaj `Debug` jako przestrzeń nazw nazwę, a także podać klasę o nazwie `Debug` w tej samej przestrzeni nazw. Kompilatory kilka wymagają takich typów być w pełni kwalifikowana.  
  
### <a name="namespaces-and-type-name-conflicts"></a>Przestrzenie nazw i typ konflikty nazw  
 **X DO NOT** wprowadzenie nazwy typu ogólnego, takich jak `Element`, `Node`, `Log`, i `Message`.  
  
 Istnieje wysokie prawdopodobieństwo, że w ten sposób doprowadzi do wpisz nazwę powoduje konflikt w typowych scenariuszy. Należy kwalifikowania nazwy typów ogólnych (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).  
  
 Istnieją konkretne wskazówki dotyczące unikanie konflikt nazw typu różne kategorie przestrzeni nazw.  
  
-   **Przestrzenie nazw modelu aplikacji**  
  
     Przestrzenie nazw należących do modelu jednej aplikacji są bardzo często używane ze sobą, ale prawie nigdy nie są one używane przestrzenie nazw innych modeli aplikacji. Na przykład <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw jest bardzo rzadko używana razem z <xref:System.Web.UI?displayProperty=nameWithType> przestrzeni nazw. Oto lista aplikacji dobrze znanego modelu przestrzeni nazw grup:  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X DO NOT** nadać tej samej nazwy dla typów w przestrzeniach nazw w obrębie modelu pojedynczej aplikacji.  
  
     Na przykład, należy dodawać typu o nazwie `Page` do <xref:System.Web.UI.Adapters?displayProperty=nameWithType> przestrzeni nazw, ponieważ <xref:System.Web.UI?displayProperty=nameWithType> przestrzeń nazw zawiera już typ o nazwie `Page`.  
  
-   **Przestrzenie nazw infrastruktury**  
  
     Ta grupa zawiera przestrzenie nazw, które rzadko są importowane podczas tworzenia typowych aplikacji. Na przykład `.Design` przestrzenie nazw są używane głównie podczas tworzenia programowania narzędzi. Unikanie konfliktów z typami w tych obszarach nazw nie jest krytyczny.  
  
-   **Przestrzenie nazw Core**  
  
     Przestrzenie nazw Core obejmuje wszystkie `System` przestrzeni nazw, z wyłączeniem przestrzeni nazw modeli aplikacji i infrastruktury przestrzeni nazw. Przestrzenie nazw Core należą między innymi, `System`, `System.IO`, `System.Xml`, i `System.Net`.  
  
     **X DO NOT** zapewnia typy nazw, które spowodowałoby to konflikt z dowolnego typu w przestrzeniach nazw Core.  
  
     Na przykład nie wolno używać `Stream` jako nazwy typu. Spowodowałoby to konflikt z <xref:System.IO.Stream?displayProperty=nameWithType>, bardzo często używane typu.  
  
-   **Technologia przestrzeni nazw grup**  
  
     Ta kategoria zawiera wszystkie przestrzenie nazw przy użyciu tego samego pierwsze dwa węzły przestrzeni nazw `(<Company>.<Technology>*`), takie jak `Microsoft.Build.Utilities` i `Microsoft.Build.Tasks`. Należy pamiętać, że typy należące do pojedynczego technologia nie kolidują ze sobą.  
  
     **X DO NOT** przypisać nazwy typów, które spowodowałoby to konflikt z innymi typami w ramach pojedynczego technologii.  
  
     **X DO NOT** wprowadzenie typu konfliktów nazw między typami w przestrzeniach nazw technologii i przestrzeń nazw modelu aplikacji (chyba że technologii nie jest przeznaczona do użycia z modelem aplikacji).  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
- [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
