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
ms.openlocfilehash: 9e0b6c5ac60474cfe984b3802e880eb58b017722
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576435"
---
# <a name="names-of-namespaces"></a>Nazwy przestrzeni nazw
Jako z innych nazw wytycznymi celem w nazwach obszarów nazw jest tworzenie wystarczająco jasno dla programisty od razu wiedzieć, co zawartość obszaru nazw jest prawdopodobnie za pomocą środowiska. Następujący szablon określa zasady nazewnictwa przestrzeni nazw:  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 Poniżej przedstawiono przykłady:  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 **✓ DO** prefiksu nazwy przestrzeni nazw o nazwie firmy, aby zapobiec przestrzenie nazw różnych firm z o tej samej nazwie.  
  
 **✓ DO** użyć nazwy stabilny, niezależny od wersji produktu w drugiej nazwy przestrzeni nazw.  
  
 **X DO NOT** Użyj hierarchii organizacji na podstawie nazw w hierarchii obszaru nazw, ponieważ nazwy grup w ramach firmy mogą być krótkotrwały. Organizowanie hierarchii przestrzenie nazw wokół grupy powiązanych technologii.  
  
 **✓ DO** PascalCasing i składniki oddzielne przestrzeni nazw za pomocą kropek (np. `Microsoft.Office.PowerPoint`). Jeśli oznakowanie wykorzystuje nietradycyjnych wielkości liter, należy wykonać wielkość liter, zdefiniowane przez użytkownika marki, nawet wtedy, gdy odbiega od wielkości liter normalne przestrzeni nazw.  
  
 **✓ CONSIDER** przy użyciu nazwy przestrzeni nazw w liczbie mnogiej, gdzie jest to odpowiednie.  
  
 Na przykład użyć `System.Collections` zamiast `System.Collection`. Firmowe i akronimów są jednak wyjątki od tej reguły. Na przykład użyć `System.IO` zamiast `System.IOs`.  
  
 **X DO NOT** Użyj takiej samej nazwy przestrzeni nazw i typ w tej przestrzeni nazw.  
  
 Na przykład nie używaj `Debug` jako obszar nazw name, a także podać klasę o nazwie `Debug` w tej samej przestrzeni nazw. Kompilatory kilka wymagają takich typów być w pełni kwalifikowana.  
  
### <a name="namespaces-and-type-name-conflicts"></a>Obszary nazw i typ konflikty nazw  
 **X DO NOT** wprowadzenie nazwy typu ogólnego, takich jak `Element`, `Node`, `Log`, i `Message`.  
  
 Istnieje wysokie prawdopodobieństwo, że to spowoduje, że nazwa powoduje konflikt wspólnych scenariuszy. Powinny kwalifikować się nazwy typu ogólnego (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).  
  
 Brak określonego wytyczne dotyczące unikanie konfliktów nazw typu dla różnych kategorii przestrzeni nazw.  
  
-   **Przestrzenie nazw modelu aplikacji**  
  
     Przestrzenie nazw należących do modelu pojedynczej aplikacji są bardzo często używane razem, ale prawie nigdy nie są używane z przestrzeni nazw innych modeli aplikacji. Na przykład <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw jest bardzo rzadko używane razem z <xref:System.Web.UI?displayProperty=nameWithType> przestrzeni nazw. Oto lista grup przestrzeń nazw modelu dobrze znanych aplikacji:  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X DO NOT** nadać tej samej nazwy dla typów w przestrzeniach nazw w obrębie modelu pojedynczej aplikacji.  
  
     Na przykład, nie dodawaj typu o nazwie `Page` do <xref:System.Web.UI.Adapters?displayProperty=nameWithType> przestrzeni nazw, ponieważ <xref:System.Web.UI?displayProperty=nameWithType> przestrzeń nazw już zawiera typ o nazwie `Page`.  
  
-   **Przestrzenie nazw infrastruktury**  
  
     Ta grupa zawiera przestrzenie nazw, które są rzadko zaimportowane podczas tworzenia typowych aplikacji. Na przykład `.Design` przestrzenie nazw są używane głównie podczas opracowywania programowania narzędzi. Unikanie konfliktów z typami w tych obszarach nazw nie jest konieczne.  
  
-   **Przestrzenie nazw Core**  
  
     Przestrzenie nazw Core obejmują wszystkie `System` przestrzeni nazw, z wyłączeniem przestrzeni nazw modeli aplikacji i przestrzeni nazw infrastruktury. Przestrzenie nazw Core należą między innymi, `System`, `System.IO`, `System.Xml`, i `System.Net`.  
  
     **X DO NOT** zapewnia typy nazw, które spowodowałoby to konflikt z dowolnego typu w przestrzeniach nazw Core.  
  
     Na przykład, nigdy nie używaj `Stream` jako nazwę typu. Spowodowałoby to konflikt z <xref:System.IO.Stream?displayProperty=nameWithType>, bardzo często używane typu.  
  
-   **Grupy przestrzeni nazw technologii**  
  
     Ta kategoria zawiera wszystkie przestrzenie nazw z tej samej pierwszych dwóch węzłów przestrzeni nazw `(<Company>.<Technology>*`), takich jak `Microsoft.Build.Utilities` i `Microsoft.Build.Tasks`. Należy pamiętać, że typy należące do pojedynczego technologii nie powodują konflikt.  
  
     **X DO NOT** przypisać nazwy typów, które spowodowałoby to konflikt z innymi typami w ramach pojedynczego technologii.  
  
     **X DO NOT** wprowadzenie typu konfliktów nazw między typami w przestrzeniach nazw technologii i przestrzeń nazw modelu aplikacji (chyba że technologii nie jest przeznaczona do użycia z modelem aplikacji).  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
 [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
