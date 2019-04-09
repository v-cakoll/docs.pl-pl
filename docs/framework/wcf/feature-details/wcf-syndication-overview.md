---
title: Omówienie syndykacji WCF
ms.date: 03/30/2017
ms.assetid: af6d4c39-e5e8-4099-aee6-5261feff9107
ms.openlocfilehash: ef62c4460ff5dd4890de174afda671facee97f2e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189838"
---
# <a name="wcf-syndication-overview"></a>Omówienie syndykacji WCF
Windows Communication Foundation (WCF) obsługuje udostępnianie zespolone kanały informacyjne usługi WCF. Syndykacja jest mechanizm integracji aplikacji, w którym serwer udostępnia dane aplikacji w formie międzyoperacyjnych, znane jako źródła danych. Źródło danych to zbiór danych aplikacji, która zawiera trochę metadanych źródła danych na poziomie (tytuł, autor, adres URL i inne metadane) i szereg elementów kanału informacyjnego. Źródła wiadomości program elementów kanału informacyjnego są zazwyczaj uporządkowanej w czasie w odwrotnej kolejności chronologicznej. Element kanału informacyjnego zawiera standardowy zestaw metadanych poziomie elementu (tytuł, adres URL, Data utworzenia, kategorii i inne metadane na poziomie elementu) oraz dowolnej liczby dane specyficzne dla aplikacji. Dwa najbardziej powszechne typy zespolone kanały informacyjne są naprawdę proste syndykacji (RSS) w wersji 2.0 i Atom 1.0, które są obsługiwane przez architekturę WCF.  
  
## <a name="object-model"></a>Model obiektów  
 Usługi WCF definiuje zestaw klas specyficznych dla syndykacji, które pozwalają pracować z kanałami informacyjnymi, elementów kanału informacyjnego i powiązanych metadanych w sposób niezależny od formatu: <xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, <xref:System.ServiceModel.Syndication.SyndicationPerson>, <xref:System.ServiceModel.Syndication.SyndicationLink>i inne klasy specyficzne dla syndykacji. Usługi WCF definiuje również klasy infrastruktury, które są kompilowane w modelu programowania REST programu WCF zapewnienie syndykacja informacji o pomocy technicznej w tym: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter>, i <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>. Klasy program formatujący kanału informacyjnego obsługują serializację modelu obiektów do i z RSS 2.0 i Atom 1.0.  
  
## <a name="scenarios"></a>Scenariusze  
 Zazwyczaj syndykacji już dziś jest używane do obsługi blogów, gdzie autora bloga okresowo publikuje jakieś informacje. Może to być tekst, obrazy, audio lub inne informacje. Wiele gazet i czasopism publikować historii wiadomości lub artykułów z wykorzystaniem syndykacji. Po zasubskrybowaniu kanału informacyjnego, użytkownik może na bieżąco o nowe informacje pochodzące z takich witryn. Mimo że najczęściej skojarzony, blogów i wydawców syndykacji może służyć za pomocą dowolnej aplikacji, która udostępnia zbierania informacji. na przykład błędów bazy danych, którą chcesz udostępnić, za pomocą zespolonego źródła danych. Można utworzyć usługi WCF, która udostępnia operacji o nazwie `CodeDefects`. Ta operacja może potrwać parametr, który określa adres e-mail osoby, usterek, którego chcesz pobrać. Klient może używać następującego adresu URL do wywołania operacji: `http://someserver/bugDatabase/CodeDefects?user=johndoe`.  
  
## <a name="syndication-formats"></a>Formaty syndykacji  
 Platforma syndykacji WCF obsługuje RSS 2.0 i Atom 1.0.  
  
## <a name="see-also"></a>Zobacz także

- [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
