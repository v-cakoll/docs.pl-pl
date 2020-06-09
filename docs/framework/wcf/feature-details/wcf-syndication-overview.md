---
title: Omówienie syndykacji WCF
ms.date: 03/30/2017
ms.assetid: af6d4c39-e5e8-4099-aee6-5261feff9107
ms.openlocfilehash: 4f72a6d797f195108401a361cc73d74d309d5602
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600961"
---
# <a name="wcf-syndication-overview"></a>Omówienie syndykacji WCF
Windows Communication Foundation (WCF) zapewnia obsługę udostępniania źródeł zespolonych z poziomu usługi WCF. Zespalanie to mechanizm integracji aplikacji, w którym serwer uwidacznia niektóre dane aplikacji w formacie interoperacyjnym znanym jako źródło danych. Kanał informacyjny to kolekcja danych aplikacji, która składa się z niektórych metadanych na poziomie kanału informacyjnego (tytułu, autora, adresu URL i innych metadanych) oraz serii elementów źródła danych. W ramach kanału informacyjnego elementy kanału informacyjnego są zwykle uporządkowane w odwrotnej kolejności chronologicznej. Element kanału informacyjnego składa się z standardowego zestawu metadanych na poziomie elementu (tytułu, adresu URL, daty utworzenia, kategorii i innych metadanych na poziomie elementu) oraz dowolnej ilości danych specyficznych dla aplikacji. Dwa najpopularniejsze typy źródeł zespolonych to naprawdę proste zespalanie (RSS) 2,0 i Atom 1,0, które są obsługiwane przez platformę WCF.  
  
## <a name="object-model"></a>Model obiektów  
 Funkcja WCF definiuje zestaw klas specyficznych dla zespalania, które umożliwiają współpracę ze źródłami danych, elementami kanału informacyjnego i powiązanymi metadanymi w sposób niezależny od formatu: <xref:System.ServiceModel.Syndication.SyndicationFeed> , <xref:System.ServiceModel.Syndication.SyndicationItem> ,, <xref:System.ServiceModel.Syndication.SyndicationPerson> <xref:System.ServiceModel.Syndication.SyndicationLink> i innych klas specyficznych dla zespalania. Funkcja WCF definiuje również klasy infrastruktury, które kompilują w modelu programowania REST WCF w celu zapewnienia wsparcia zespolonego, w tym: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> , i <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> . Klasy programu formatującego źródła danych obsługują Serializowanie modelu obiektów do i z kanałów RSS 2,0 i Atom 1,0.  
  
## <a name="scenarios"></a>Scenariusze  
 Typowym zastosowaniem zespalania jest zablogowanie, gdzie autor blogu okresowo publikuje pewne informacje. Może to być tekst, obrazy, audio lub inne typy informacji. Wiele gazet i czasopism publikuje także historie lub artykuły z wiadomościami przy użyciu zespalania. Dzięki subskrybowaniu takiego źródła danych użytkownik może aktualizować wszystkie nowe informacje pochodzące z tych witryn. Chociaż zespalanie jest najczęściej skojarzone ze blogami i wydawcami, może być używana z każdą aplikacją, która uwidacznia zbiór informacji; na przykład baza danych usterek, którą chcesz uwidocznić przy użyciu źródła zespolonego. Można utworzyć usługę WCF, która uwidacznia operację o nazwie `CodeDefects` . Ta operacja może potrwać parametr, który określa adres e-mail osoby, której błędy chcesz pobrać. Klient może użyć następującego adresu URL do wywołania operacji: `http://someserver/bugDatabase/CodeDefects?user=johndoe` .  
  
## <a name="syndication-formats"></a>Formaty zespolone  
 Platforma zespalania programu WCF obsługuje funkcję RSS 2,0 i Atom 1,0.  
  
## <a name="see-also"></a>Zobacz też

- [Model programowania protokołu HTTP sieci Web w programie WCF](wcf-web-http-programming-model.md)
