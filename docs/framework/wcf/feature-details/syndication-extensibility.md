---
title: Rozszerzalność syndykacji
ms.date: 03/30/2017
ms.assetid: 4d941175-74a2-4b15-81b3-086e8a95d25f
ms.openlocfilehash: 226ea682d8b17a818e6d5be2097a19315d106bda
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170810"
---
# <a name="syndication-extensibility"></a>Rozszerzalność syndykacji
Syndykacja interfejs API umożliwiający niezależny od formatu model programowania, który umożliwia syndykowany zawartość do zapisania podczas transmisji w różnych formatach. Abstrakcyjny model danych zawiera następujące klasy:  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 W ramach tych zajęć mapować ściśle konstrukcje specyfikacją Atom 1.0, mimo że niektóre nazwy są różne.  
  
 Kluczową cechą protokołów syndykacji jest rozszerzalności. RSS 2.0 i Atom 1.0 Dodaj atrybuty i elementy do zespolone kanały informacyjne, które nie są zdefiniowane w specyfikacji. Model programowania syndykacji usługi Windows Communication Foundation (WCF) zapewnia następujące sposoby pracy z atrybutami niestandardowymi i rozszerzenia, dostęp z typowaniem luźnym i elementu pochodnego dla nowej klasy.  
  
## <a name="loosely-typed-access"></a>Co słabo Typizowana dostępu  
 Dodawanie rozszerzeń, Nowa Klasa pochodząca wymaga tworzenia dodatkowego kodu. Inną opcją uzyskuje dostęp do rozszerzeń w taki sposób, typowaniem luźnym. Wszystkie typy zdefiniowane w syndykacji abstrakcyjny model danych zawiera właściwości o nazwie `AttributeExtensions` i `ElementExtensions` (z jednym wyjątkiem <xref:System.ServiceModel.Syndication.SyndicationContent> ma `AttributeExtensions` właściwość, ale nie `ElementExtensions` właściwości). Te właściwości są kolekcjami rozszerzeń, które nie są przetwarzane przez `TryParseAttribute` i `TryParseElement` metody odpowiednio. Dostęp do tych rozszerzeń nieprzetworzonych przez wywołanie metody <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection.ReadElementExtensions%2A?displayProperty=nameWithType> na `ElementExtensions` właściwość <xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, <xref:System.ServiceModel.Syndication.SyndicationLink>, <xref:System.ServiceModel.Syndication.SyndicationPerson>, i <xref:System.ServiceModel.Syndication.SyndicationCategory>. Ten zestaw metod znajdzie wszystkie rozszerzenia o określonej nazwie i przestrzeni nazw, deserializuje je pojedynczo do wystąpień `TExtension` i zwraca je jako kolekcja `TExtension` obiektów.  
  
## <a name="deriving-a-new-class"></a>Nowa Klasa pochodząca  
 Nowa klasa może pochodzić z dowolnego z istniejącej klasy abstrakcyjnej danych w modelu. W tym podczas wdrażania aplikacji, w którym większość źródeł danych, którą pracujesz z ma określonego rozszerzenia. W tym temacie zawierają większość źródeł, w których działa program z `MyExtension` rozszerzenia. Aby zapewnić lepszą obsługę programowania, wykonaj następujące czynności:  
  
-   Utwórz klasę do przechowywania danych rozszerzenia. W takim przypadku należy utworzyć klasę o nazwie MyExtension.  
  
-   Pochodną klasę o nazwie MyExtensionItem z <xref:System.ServiceModel.Syndication.SyndicationItem> do udostępnienia właściwość typu MyExtension do celów programowania.  
  
-   Zastąp <xref:System.ServiceModel.Syndication.SyndicationItem.TryParseElement%28System.Xml.XmlReader%2CSystem.String%29> w klasie MyExtensionItem w celu utworzenia wystąpienia nowego wystąpienia MyExtension została przeczytana MyExtension.  
  
-   Zastąp <xref:System.ServiceModel.Syndication.SyndicationItem.WriteElementExtensions%28System.Xml.XmlWriter%2CSystem.String%29> w klasie MyExtensionItem w celu zapisywania zawartości właściwość MyExtension do usługi składnika zapisywania XML.  
  
-   Pochodną klasę o nazwie MyExtensionFeed z <xref:System.ServiceModel.Syndication.SyndicationFeed>.  
  
-   Zastąp <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateItem> w klasie MyExtensionFeed w celu utworzenia wystąpienia MyExtensionItem zamiast domyślnego <xref:System.ServiceModel.Syndication.SyndicationItem>. Szereg metod są zdefiniowane w <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem> , można utworzyć <xref:System.ServiceModel.Syndication.SyndicationLink>, <xref:System.ServiceModel.Syndication.SyndicationCategory>, i <xref:System.ServiceModel.Syndication.SyndicationPerson> obiektów (na przykład <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateLink>, <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateCategory>, i <xref:System.ServiceModel.Syndication.SyndicationFeed.CreatePerson>). Wszystkie z nich może zostać zastąpiona w celu utworzenie klasy pochodnej niestandardowej.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie syndykacji WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)
- [Architektura syndykacji](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)
