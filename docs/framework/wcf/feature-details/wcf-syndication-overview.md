---
title: Omówienie syndykacji WCF
ms.date: 03/30/2017
ms.assetid: af6d4c39-e5e8-4099-aee6-5261feff9107
ms.openlocfilehash: c059ca3ee33b254a60d6b8596b02e1f995fd2ca1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498247"
---
# <a name="wcf-syndication-overview"></a>Omówienie syndykacji WCF
Windows Communication Foundation (WCF) zapewnia obsługę udostępnianie zespolonego źródła usługi WCF. Syndykacja jest mechanizm integracji aplikacji, w którym serwer przedstawia niektóre dane aplikacji w formacie interoperacyjne znany jako źródło danych. Źródło danych to kolekcja danych aplikacji, która składa się z niektórych metadanych źródła danych na poziomie (tytuł, autora, adres URL i innych metadanych) i szereg elementów strumieniowego źródła danych. W źródle danych elementów strumieniowego źródła danych są zwykle czas uporządkowanych w odwrotnej kolejności. Element źródła składa się ze standardowego zestawu metadanych poziomie elementu (tytuł, adres URL, Data utworzenia, kategorii i innych metadanych elementu poziom) oraz dowolnej liczby dane specyficzne dla aplikacji. Dwa najczęściej używane typy zespolonego źródła danych są naprawdę proste Syndication (RSS) 2.0 i Atom 1.0, które są obsługiwane przez usługę WCF.  
  
## <a name="object-model"></a>Model obiektu  
 Usługi WCF definiuje zestaw klas zespolonego specyficzne, które umożliwiają pracę ze źródłami, elementów strumieniowego źródła danych i pokrewne metadane w sposób niezależny od formatu: <xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, <xref:System.ServiceModel.Syndication.SyndicationPerson>, <xref:System.ServiceModel.Syndication.SyndicationLink>i inne klasy specyficzne dla zespolonego. WCF definiuje również klasy infrastruktury, wykorzystujących Model programowania interfejsu REST usługi WCF aby zapewnić tym obsługa zespolonego: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter>, i <!--zz <xref:System.ServiceModel.Syndication.RSS20FeedFormatter>--> `RSS20FeedFormatter`. Program formatujący kanału informacyjnego klasy obsługuje serializowania obiektu modelu do i z RSS 2.0 i Atom 1.0.  
  
## <a name="scenarios"></a>Scenariusze  
 Zazwyczaj jest używane, syndykacji dzisiaj obsługi blogów, gdy autor blogu okresowo publikuje jakieś informacje. Może to być tekst, obrazy, audio lub inne informacje. Wiele gazetach i magazyny również publikować wiadomości lub artykułów za pomocą zespolonego. Subskrybuj takich źródeł danych, użytkownik może zapewnić aktualność przy użyciu nowych informacji pochodzących z tych witryn. Mimo że zespolonego jest najczęściej skojarzony z blogów i wydawców, można łączyć z dowolnej aplikacji, która przedstawia zbierania informacji. na przykład błąd bazy danych, który ma zostać udostępniona za pomocą zespolonego źródła danych. Można utworzyć usługi WCF, która uwidacznia operacji o nazwie `CodeDefects`. Ta operacja może potrwać parametr, który określa adres e-mail osoby, których usterki, które ma zostać pobrane. Klient może używać następującego adresu URL do wywołania operacji: http://someserver/bugDatabase/CodeDefects?user=johndoe.  
  
## <a name="syndication-formats"></a>Formaty syndykacji  
 Platforma syndykacji WCF obsługuje RSS 2.0 i Atom 1.0.  
  
## <a name="see-also"></a>Zobacz też  
 [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
