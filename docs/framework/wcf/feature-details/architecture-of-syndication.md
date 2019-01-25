---
title: Architektura syndykacji
ms.date: 03/30/2017
ms.assetid: ed4ca86e-e3d8-4acb-87aa-1921fbc353be
ms.openlocfilehash: b07fc03fd11c794d804b6bcd1813010965365e43
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623446"
---
# <a name="architecture-of-syndication"></a>Architektura syndykacji
Syndykacja interfejs API umożliwiający niezależny od formatu model programowania, który umożliwia syndykowany zawartość do zapisania się do sieci w różnych formatach. Abstrakcyjny model danych zawiera następujące klasy:  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 W ramach tych zajęć mapować ściśle konstrukcje specyfikacją Atom 1.0, mimo że niektóre nazwy są różne.  
  
 W Windows Communication Foundation (WCF), zespolone kanały informacyjne są modelowane jako inny rodzaj operacji usługi, jeden typ zwracany w przypadku jednej z klas pochodnych <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. Pobieranie kanału informacyjnego ma formę wymianę komunikatów żądań i odpowiedzi. Klient wysyła żądanie do usługi i odpowiada. Komunikat żądania ma wartość protokołu infrastruktury (na przykład pierwotne HTTP), a komunikat odpowiedzi zawiera ładunek, który składa się z często rozpoznawanych syndykacji formatu (RSS 2.0 i Atom 1.0). Usługi, które implementują te wymianę komunikatów są określane jako usługi syndykacji.  
  
 Kontrakt usługi syndykacji składa się z zestawu działań, które zwraca wystąpienie <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> klasy. W poniższym przykładzie pokazano deklaracji interfejsu usługi syndykacji.  
  
 [!code-csharp[S_UE_SyndicationBoth#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_syndicationboth/cs/service.cs#0)]  
  
 Syndykacja informacji o pomocy technicznej jest oparty na modelu programowania REST programu WCF, która definiuje <xref:System.ServiceModel.WebHttpBinding> powiązania, który jest używany w połączeniu z <xref:System.ServiceModel.Description.WebHttpBehavior> udostępnić źródła danych jako usługi. Aby uzyskać więcej informacji o modelu programowania REST programu WCF, zobacz [Programming Overview modelu WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md).  
  
> [!NOTE]
>  Specyfikacja Atom 1.0 umożliwia ułamków sekund, należy określić w jednym z jej konstrukcji daty. Podczas serializacji i deserializacji implementacji WCF ignoruje ułamków sekund.  
  
## <a name="object-model"></a>Model obiektów  
 Model obiektów dla syndykacji składa się z grup klas w poniższych tabelach.  
  
 Formatowanie klasy:  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Syndication.Atom10FeedFormatter>|Klasa, która wykonuje serializację <xref:System.ServiceModel.Syndication.SyndicationFeed> wystąpienia do formatu Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Atom10FeedFormatter%601>|Klasa, która wykonuje serializację <xref:System.ServiceModel.Syndication.SyndicationFeed> klas pochodnych do formatu Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Atom10ItemFormatter>|Klasa, która wykonuje serializację <xref:System.ServiceModel.Syndication.SyndicationItem> wystąpienia do formatu Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Atom10ItemFormatter%601>|Klasa, która wykonuje serializację <xref:System.ServiceModel.Syndication.SyndicationItem> klas pochodnych do formatu Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Rss20FeedFormatter>|Klasa, która wykonuje serializację <xref:System.ServiceModel.Syndication.SyndicationFeed> wystąpienia do formatu RSS 2.0.|  
|<xref:System.ServiceModel.Syndication.Rss20FeedFormatter%601>|Klasa, która wykonuje serializację <xref:System.ServiceModel.Syndication.SyndicationFeed> klas pochodnych do formatu RSS 2.0.|  
|<xref:System.ServiceModel.Syndication.Rss20ItemFormatter>|Klasa, która wykonuje serializację <xref:System.ServiceModel.Syndication.SyndicationItem> wystąpienia do formatu RSS 2.0.|  
|<xref:System.ServiceModel.Syndication.Rss20ItemFormatter%601>|Klasa, która wykonuje serializację <xref:System.ServiceModel.Syndication.SyndicationItem> klas pochodnych do formatu RSS 2.0.|  
  
 Klasy modelu obiektu:  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Syndication.SyndicationCategory>|Klasa, która reprezentuje kategorię Kanał informacyjny syndykacji.|  
|<xref:System.ServiceModel.Syndication.SyndicationContent>|Klasa bazowa reprezentuje zawartość syndykacji.|  
|<xref:System.ServiceModel.Syndication.SyndicationElementExtension>|Klasa, która reprezentuje rozszerzenie element syndykacji.|  
|<xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection>|Kolekcja <xref:System.ServiceModel.Syndication.SyndicationElementExtension> obiektów.|  
|<xref:System.ServiceModel.Syndication.SyndicationFeed>|Klasa, która reprezentuje obiekt źródła najwyższego poziomu.|  
|<xref:System.ServiceModel.Syndication.SyndicationItem>|Klasa, która reprezentuje element kanału informacyjnego.|  
|<xref:System.ServiceModel.Syndication.SyndicationLink>|Klasa, która reprezentuje łącze w zespolonego źródła danych lub element.|  
|<xref:System.ServiceModel.Syndication.SyndicationPerson>|Klasa, która reprezentuje konstrukcja osoby Atom.|  
|<xref:System.ServiceModel.Syndication.SyndicationVersions>|Klasa, która reprezentuje protokołów obsługiwanych syndykacji.|  
|<xref:System.ServiceModel.Syndication.TextSyndicationContent>|Klasa, która reprezentuje dowolny <xref:System.ServiceModel.Syndication.SyndicationItem> zawartości ma być wyświetlany użytkownikowi końcowemu.|  
|<xref:System.ServiceModel.Syndication.TextSyndicationContentKind>|Wyliczenie reprezentuje różne rodzaje tekstu syndykacja informacji o zawartości obsługiwane.|  
|<xref:System.ServiceModel.Syndication.UrlSyndicationContent>|Klasa, która reprezentuje syndykacji zawartość, która składa się z adresu URL do innego zasobu.|  
|<xref:System.ServiceModel.Syndication.XmlSyndicationContent>|Klasa, która reprezentuje zawartość syndykacji, która nie ma być wyświetlany w przeglądarce.|  
  
 Abstrakcje danych podstawowych w modelu obiektów są źródła danych i elementów, które odpowiadają <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem> klasy. Źródło danych udostępnia niektóre metadane poziomie źródła danych (na przykład, tytuł, opis i autor), lokalizację do przechowywania nieznane rozszerzenia oraz zestaw elementów, które tworzą pozostałej części źródła informacji o zawartości. Elementu udostępnia niektóre metadane poziomie elementu (na przykład, Title, Summary i PublicationDate), lokalizację do przechowywania nieznane rozszerzenia i zawartość elementu, który zawiera resztę zawartość informacji elementu. Abstrakcje podstawowe źródło danych i elementów są obsługiwane przez dodatkowych klas reprezentujących typowe konstrukcje danych, do którego odwołuje się do specyfikacji Atom 1.0 i RSS.  
  
 Informacje w wystąpieniu źródła danych można przekonwertować na wiele formatów XML. Proces konwersji do i z pliku XML jest zarządzana przez <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> klasy. Ta klasa jest abstrakcyjna; konkretne implementacje są dostarczane dla Atom 1.0 i RSS 2.0 <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> i <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>. Aby używać klasy pochodne źródła danych, należy użyć <xref:System.ServiceModel.Syndication.Atom10FeedFormatter%601> lub <xref:System.ServiceModel.Syndication.Rss20FeedFormatter%601> zgodnie z ich pozwalają na określenie klasy pochodnej źródła danych. Aby użyć klasy pochodnej elementu należy użyć <xref:System.ServiceModel.Syndication.Atom10ItemFormatter%601> lub <xref:System.ServiceModel.Syndication.Rss20ItemFormatter%601> jako pozwala użytkownikowi na określenie klasy pochodnej elementu trzecim może pochodzić zapewniali własną implementację <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> do obsługi syndykacji różnych formatów.  
  
## <a name="extensibility"></a>Rozszerzalność  
  
-   Kluczową cechą protokołów syndykacji jest rozszerzalności. RSS 2.0 i Atom 1.0 umożliwiają dodawanie atrybuty i elementy do zespolone kanały informacyjne, które nie są zdefiniowane w specyfikacji. Model programowania syndykacji programu WCF zapewnia dwa sposoby pracy z atrybutami niestandardowymi i rozszerzenia: wyprowadzanie nową klasę i typowaniem luźnym dostępu. Aby uzyskać więcej informacji, zobacz [rozszerzalność syndykacji](../../../../docs/framework/wcf/feature-details/syndication-extensibility.md).  
  
## <a name="see-also"></a>Zobacz także
- [Omówienie syndykacji WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)
- [Sposób mapowania modelu obiektu syndykacji programu WCF na kanały informacyjne Atom i RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)
- [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
