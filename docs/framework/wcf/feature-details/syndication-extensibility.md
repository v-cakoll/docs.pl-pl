---
title: Rozszerzalność syndykacji
ms.date: 03/30/2017
ms.assetid: 4d941175-74a2-4b15-81b3-086e8a95d25f
ms.openlocfilehash: 5e8f47b45897f46e15847c793c986e953523e66b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600727"
---
# <a name="syndication-extensibility"></a>Rozszerzalność syndykacji
Interfejs API zespalania został zaprojektowany z myślą o udostępnianiu modelu programowania neutralnego za pomocą formatu, który umożliwia zapisywanie zespolonej zawartości w sieci w różnych formatach. Abstrakcyjny model danych składa się z następujących klas:  
  
- <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
- <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
- <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
- <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 Te klasy są mapowane blisko konstrukcji zdefiniowanych w specyfikacji Atom 1,0, chociaż niektóre nazwy są różne.  
  
 Kluczową funkcją protokołów zespalania jest rozszerzalność. Atom 1,0 i RSS 2,0, Dodaj atrybuty i elementy do źródeł zespolonych, które nie są zdefiniowane w specyfikacjach. Model programowania zespalania w Windows Communication Foundation (WCF) oferuje następujące sposoby pracy z atrybutami i rozszerzeniami niestandardowymi, swobodny dostęp do danych i wyprowadzanie nowej klasy.  
  
## <a name="loosely-typed-access"></a>Dostęp swobodny do określonego  
 Dodanie rozszerzeń przez wytworzenie nowej klasy wymaga napisania dodatkowego kodu. Inna opcja uzyskuje dostęp do rozszerzeń w sposób swobodny. Wszystkie typy zdefiniowane w abstrakcyjnym modelu danych zespolonych zawierają właściwości o nazwie `AttributeExtensions` i `ElementExtensions` (z jednym wyjątkiem, <xref:System.ServiceModel.Syndication.SyndicationContent> ma `AttributeExtensions` Właściwość, ale nie ma `ElementExtensions` Właściwości). Te właściwości są kolekcjami rozszerzeń nieprzetwarzanych `TryParseAttribute` `TryParseElement` odpowiednio metodami i. Możesz uzyskać dostęp do tych rozszerzeń nieprzetworzonych <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection.ReadElementExtensions%2A?displayProperty=nameWithType> `ElementExtensions` , wywołując Właściwość <xref:System.ServiceModel.Syndication.SyndicationFeed> ,,, <xref:System.ServiceModel.Syndication.SyndicationItem> <xref:System.ServiceModel.Syndication.SyndicationLink> <xref:System.ServiceModel.Syndication.SyndicationPerson> , i <xref:System.ServiceModel.Syndication.SyndicationCategory> . Ten zestaw metod znajduje wszystkie rozszerzenia o określonej nazwie i przestrzeni nazw, deserializacji je pojedynczo do wystąpień `TExtension` i zwraca je jako kolekcję `TExtension` obiektów.  
  
## <a name="deriving-a-new-class"></a>Wyprowadzanie nowej klasy  
 Można utworzyć nową klasę z dowolnej istniejącej klasy abstrakcyjnych modeli danych. Zrób to podczas implementowania aplikacji, w której większość kanałów roboczych, z którymi pracujesz, ma określone rozszerzenie. W tym temacie większość kanałów informacyjnych, z którymi działa program, zawiera `MyExtension` rozszerzenie. Aby zapewnić Ulepszone środowisko programistyczne, wykonaj następujące czynności:  
  
- Utwórz klasę, aby przechowywać dane rozszerzenia. W takim przypadku należy utworzyć klasę o nazwie "noextension".  
  
- Utwórz klasę o nazwie MyExtensionItem z <xref:System.ServiceModel.Syndication.SyndicationItem> , aby uwidocznić właściwość typu "rozszerzenie" dla celów programistycznych.  
  
- Przesłoń <xref:System.ServiceModel.Syndication.SyndicationItem.TryParseElement%28System.Xml.XmlReader%2CSystem.String%29> w klasie MyExtensionItem, aby utworzyć wystąpienie nowego wystąpienia rozszerzenia, gdy rozszerzenie jest odczytane.  
  
- Przesłoń <xref:System.ServiceModel.Syndication.SyndicationItem.WriteElementExtensions%28System.Xml.XmlWriter%2CSystem.String%29> w klasie MyExtensionItem, aby zapisać zawartość właściwości webextension w składniku zapisywania XML.  
  
- Utwórz klasę o nazwie MyExtensionFeed z <xref:System.ServiceModel.Syndication.SyndicationFeed> .  
  
- Przesłoń <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateItem> w klasie MyExtensionFeed, aby utworzyć wystąpienie elementu MyExtensionItem zamiast domyślnego <xref:System.ServiceModel.Syndication.SyndicationItem> . Seria metod jest definiowana w i, <xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem> które mogą tworzyć <xref:System.ServiceModel.Syndication.SyndicationLink> obiekty, <xref:System.ServiceModel.Syndication.SyndicationCategory> , i <xref:System.ServiceModel.Syndication.SyndicationPerson> (na przykład,, <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateLink> <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateCategory> i <xref:System.ServiceModel.Syndication.SyndicationFeed.CreatePerson> ). Wszystko to można zastąpić, aby utworzyć niestandardową klasę pochodną.  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie syndykacji WCF](wcf-syndication-overview.md)
- [Architektura syndykacji](architecture-of-syndication.md)
