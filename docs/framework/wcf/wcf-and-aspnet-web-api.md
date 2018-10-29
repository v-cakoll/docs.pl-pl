---
title: Interfejs API sieci Web programu WCF i platformy ASP.NET
ms.date: 03/30/2017
ms.assetid: 08ceded3-fd9a-4467-9715-c4cbd9c7228e
ms.openlocfilehash: 9ff974ca59b5a6448a140cbb1e7d6e8114840bdf
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198422"
---
# <a name="wcf-and-aspnet-web-api"></a>Interfejs API sieci Web programu WCF i platformy ASP.NET
Usługi WCF jest jednolity model programowania firmy Microsoft do budowania aplikacji usługowych. Umożliwia deweloperom tworzenie rozwiązań bezpieczne, niezawodne i transakcyjnych, które integrują się na platformach oraz współpraca z istniejących inwestycji. [ASP.NET Web API](https://www.asp.net/web-api) to struktura, która ułatwia tworzenie usług HTTP, docierających do szerokiej gamy klientów, w tym przeglądarek i urządzeń przenośnych. Web API platformy ASP.NET jest idealną platformą do tworzenia aplikacji typu RESTful na .NET Framework. W tym temacie przedstawiono wskazówki pomagające w podjęciu decyzji, technologii, które będzie najlepiej odpowiadać potrzebom użytkownika.  
  
## <a name="choosing-which-technology-to-use"></a>Wybór technologii  
 W poniższej tabeli opisano główne funkcje poszczególnych technologii.  
  
|WCF|ASP.NET Web API|  
|---------|---------------------|  
|Włącza usług budynku, które obsługują wiele protokołów (HTTP, TCP, UDP i niestandardowe transportu) i pozwala na przełączanie się między nimi.|Tylko protokół HTTP. Najwyższej klasy modelu programowania protokołu HTTP. Bardziej odpowiednie dla dostępu z różnych przeglądarek, etc Włączanie szeroki zasięg urządzeń przenośnych.|  
|Umożliwia tworzenie usług, które obsługują wiele kodowania tego samego komunikatu (tekst, MTOM i danych binarnych) wpisz i pozwala na przełączanie się między nimi.|Umożliwia tworzenie interfejsów API sieci Web, która obsługuje wiele różnych typów nośników, w tym XML, JSON itp.|  
|Obsługuje tworzenie usług przy użyciu usługi WS-* standardów, takich jak niezawodną obsługę komunikatów, transakcje, zabezpieczenia wiadomości.|Używa protokołu podstawowego i formatów, takich jak HTTP, funkcja WebSockets, protokołu SSL, JSON i XML. Nie jest obsługiwane dla protokołów wyższego poziomu, takie jak niezawodna obsługa komunikatów lub transakcji.|  
|Obsługuje żądanie-odpowiedź, jeden sposób i komunikacja dwukierunkowa wzorców wymiany komunikatów.|Protokół HTTP jest żądań/odpowiedzi, ale dodatkowe wzorce mogą być obsługiwane za pośrednictwem [SignalR](https://github.com/SignalR/SignalR) i integrację funkcji WebSockets.|  
|Usług WCF SOAP można opisać w WSDL, dzięki czemu zautomatyzowanych narzędzi Generowanie serwerów proxy klientów nawet w przypadku usług za pomocą złożonych schematów.|Istnieje szereg sposobów w celu opisania interfejsu API sieci Web — od generowanych automatycznie HTML strony Pomocy opisujące fragmentów kodu, aby metadane strukturalne dla protokołu OData zintegrowane interfejsy API.|  
|Dostarczany z .NET framework.|Jest dostarczany z .NET framework, ale jest typu open source i jest również dostępna out-of-band jako niezależne do pobrania.|  
  
 Użyj usługi WCF do tworzenia usług niezawodnej, bezpiecznej sieci web, które są dostępne za pośrednictwem różnych transportów. Do tworzenia usług opartych na protokole HTTP, które są dostępne z szerokiej gamy klientów, należy użyć interfejsu API sieci Web platformy ASP.NET. Jeśli tworzenie i projektowanie nowych usług opartego na interfejsie REST, należy użyć interfejsu API sieci Web platformy ASP.NET. Chociaż WCF niektóre pomocy technicznej dotyczące pisania usługi typu REST, obsługa PRZECHOWYWANYCH na interfejs API sieci Web platformy ASP.NET jest bardziej szczegółowy, a wszystkie przyszłe ulepszenia funkcji REST, które zostaną wprowadzone w Web API platformy ASP.NET. Jeśli masz istniejącą usługę WCF i chcesz udostępnić dodatkowe punkty końcowe REST, należy użyć programu WCF i <xref:System.ServiceModel.WebHttpBinding>.  
  
## <a name="see-also"></a>Zobacz też  
 [Co to jest program Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)  
 [Podstawowe pojęcia programu Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md)  
