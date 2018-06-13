---
title: Rozszerzalność syndykacji
ms.date: 03/30/2017
ms.assetid: 4d941175-74a2-4b15-81b3-086e8a95d25f
ms.openlocfilehash: 8182aee9d8a526d995ab1266e5c654f29f4af3d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498582"
---
# <a name="syndication-extensibility"></a>Rozszerzalność syndykacji
Interfejs API zespolonego umożliwia model programowania niezależny od formatu, który umożliwia zawartości zespolonej do zapisania danych przesyłanych w sieci w różnych formatach. Model danych abstrakcyjny składa się z następujących klas:  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 Te klasy mapowania ściśle konstrukcje specyfikacją Atom 1.0, mimo że niektóre nazwy są różne.  
  
 Kluczowy element zespolony protokołów jest rozszerzalności. Zarówno Atom 1.0 i RSS 2.0, należy dodać atrybuty i elementy do zespolonego źródła danych, które nie są zdefiniowane w specyfikacji. Model programowania zespolonego Windows Communication Foundation (WCF) zapewnia następujące sposoby pracy z atrybutów niestandardowych i rozszerzeń, typowaniem luźnym dostępu i wyprowadzanie nową klasę.  
  
## <a name="loosely-typed-access"></a>Słabo Typizowana dostępu  
 Dodawanie rozszerzeń przez wyprowadzanie nową klasę wymaga zapisywania dodatkowy kod. Inną opcją uzyskuje dostęp do rozszerzeń w taki sposób, typowaniem luźnym. Wszystkie typy zdefiniowanego w modelu danych abstrakcyjny zespolonego zawiera właściwości o nazwie `AttributeExtensions` i `ElementExtensions` (z jednym wyjątkiem <xref:System.ServiceModel.Syndication.SyndicationContent> ma `AttributeExtensions` właściwość, ale nie `ElementExtensions` właściwości). Te właściwości są kolekcjami rozszerzeń nie są przetwarzane przez `TryParseAttribute` i `TryParseElement` metody odpowiednio. Dostęp do tych rozszerzeń nieprzetworzone wywołując <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection.ReadElementExtensions%2A?displayProperty=nameWithType> na `ElementExtensions` właściwość <xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, <xref:System.ServiceModel.Syndication.SyndicationLink>, <xref:System.ServiceModel.Syndication.SyndicationPerson>, i <xref:System.ServiceModel.Syndication.SyndicationCategory>. Ten zestaw metod znajduje wszystkie rozszerzenia o określonej nazwie i przestrzeni nazw, deserializuje je oddzielnie do wystąpienia `TExtension` i zwraca je jako kolekcja `TExtension` obiektów.  
  
## <a name="deriving-a-new-class"></a>Wyprowadzanie nowej klasy  
 Nowe klasy mogą dziedziczyć po wszelkie istniejące klasy abstrakcyjnej danych w modelu. W tym przypadku wdrażania aplikacji, w której większość źródeł danych, z którym pracujesz z ma określonego rozszerzenia. W tym temacie zawierają większość źródła danych, które program działa z `MyExtension` rozszerzenia. Aby zapewnić lepszą obsługę programowania, wykonaj następujące czynności:  
  
-   Utwórz klasę do przechowywania danych rozszerzenia. W przypadku tworzenia klasy o nazwie MyExtension.  
  
-   Pochodzi z klasy o nazwie MyExtensionItem z <xref:System.ServiceModel.Syndication.SyndicationItem> do udostępnienia właściwości typu MyExtension do celów programowania.  
  
-   Zastąpienie <xref:System.ServiceModel.Syndication.SyndicationItem.TryParseElement%28System.Xml.XmlReader%2CSystem.String%29> w klasie MyExtensionItem można utworzyć nowego wystąpienia MyExtension, została przeczytana MyExtension.  
  
-   Zastąpienie <xref:System.ServiceModel.Syndication.SyndicationItem.WriteElementExtensions%28System.Xml.XmlWriter%2CSystem.String%29> w klasie MyExtensionItem można zapisać właściwości MyExtension zawartość do edytora XML.  
  
-   Pochodzi z klasy o nazwie MyExtensionFeed z <xref:System.ServiceModel.Syndication.SyndicationFeed>.  
  
-   Zastąpienie <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateItem> w klasie MyExtensionFeed można utworzyć wystąpienia MyExtensionItem zamiast domyślnej <xref:System.ServiceModel.Syndication.SyndicationItem>. Szereg metod są zdefiniowane w <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem> który można utworzyć <xref:System.ServiceModel.Syndication.SyndicationLink>, <xref:System.ServiceModel.Syndication.SyndicationCategory>, i <xref:System.ServiceModel.Syndication.SyndicationPerson> obiektów (na przykład <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateLink>, <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateCategory>, i <xref:System.ServiceModel.Syndication.SyndicationFeed.CreatePerson>). Które może zostać zastąpiona w celu tworzenie niestandardowej klasy pochodnej.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie syndykacji WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)  
 [Architektura syndykacji](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)
