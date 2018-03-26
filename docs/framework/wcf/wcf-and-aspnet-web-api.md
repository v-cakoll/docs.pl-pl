---
title: Interfejs API sieci Web programu WCF i platformy ASP.NET
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08ceded3-fd9a-4467-9715-c4cbd9c7228e
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1270eb202a1e8cbf1a297a13593dd0aa6046cb6c
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="wcf-and-aspnet-web-api"></a>Interfejs API sieci Web programu WCF i platformy ASP.NET
Usługi WCF jest firmy Microsoft ujednolicony model programowania do tworzenia aplikacji korzystających z usług. Umożliwia ona deweloperom tworzenie rozwiązań bezpieczne, niezawodne i transakcyjne, zintegrowanie na różnych platformach, które współdziałają z dotychczasowych inwestycji. [ASP.NET Web API](http://www.asp.net/web-api) to platforma, która ułatwia tworzenie usług HTTP, które są używane przez szeroki wachlarz klientów, w tym przeglądarki i urządzenia przenośne. Interfejs API sieci Web ASP.NET jest idealną platformą do tworzenia RESTful aplikacji w programie .NET Framework. W tym temacie przedstawiono pewne wskazówki ułatwiające podjęcie technologii, które będzie najlepiej odpowiadać potrzebom użytkownika.  
  
## <a name="choosing-which-technology-to-use"></a>Wybór technologii  
 W poniższej tabeli opisano najważniejszych funkcji poszczególnych technologii.  
  
|WCF|ASP.NET Web API|  
|---------|---------------------|  
|Umożliwia tworzenie usług, które obsługują wiele protokołów (HTTP, TCP, UDP i niestandardowych transportów) oraz pozwala na przełączanie się między nimi.|Tylko protokół HTTP. Najwyższej jakości modelu programowania protokołu HTTP. Bardziej odpowiednie dla dostępu z różnych przeglądarek, etc włączenie całego osiągnąć urządzeń przenośnych.|  
|Umożliwia tworzenie usług, które obsługują wiele kodowań ten sam komunikat (tekst, MTOM i Binary) wpisz i pozwala na przełączanie się między nimi.|Umożliwia tworzenie interfejsów API sieci Web, która obsługuje wiele różnych typów nośników, w tym XML, JSON itp.|  
|Obsługuje tworzenie usług za pomocą usługi WS-* zabezpieczenia komunikatów niezawodnej obsługi komunikatów, transakcje, takie jak standardów.|Używa protokołu podstawowego i formatuje np. HTTP, protokół WebSockets SSL, JSON i XML. Nie jest obsługiwane dla protokołów wyższego poziomu, takich jak niezawodna obsługa komunikatów lub transakcji.|  
|Obsługuje żądanie-odpowiedź, jeden sposób i dupleks wzorce wymiany wiadomości.|HTTP jest żądanie/odpowiedź, ale dodatkowe wzorce mogą być obsługiwane za pośrednictwem [SignalR](https://github.com/SignalR/SignalR) i integracja protokołu WebSockets.|  
|Usług WCF SOAP można przedstawić w języku WSDL umożliwiające automatyczne narzędzia do generowania proxy klienta, nawet w przypadku usług o schematach złożonych.|Brak na różne sposoby do opisu interfejsu API sieci Web — od automatycznie generowanej HTML strony Pomocy opisujące wstawki metadanych strukturalnych dla interfejsów API zintegrowane OData.|  
|Jest dostarczany z programu .NET framework.|Dostarczany z programem .NET framework, ale jest open source i jest również dostępny poza pasmem jako niezależne pobierania.|  
  
 Używają WCF do tworzenia usług sieci web niezawodne, bezpieczne to dostępne za pośrednictwem różnych transportów. Użyj interfejsu API sieci Web platformy ASP.NET, aby utworzyć oparte na protokole HTTP usług, które są dostępne w różnych klientów. Jeśli są tworzone i projektowanie nowych usług typu REST, należy użyć interfejsu API sieci Web platformy ASP.NET. Mimo że WCF zapewnia obsługę niektórych pisanie usługi typu REST, obsługa REST w interfejsie API sieci Web ASP.NET jest bardziej szczegółowy i wszystkie przyszłe ulepszenia funkcji REST zostaną wprowadzone w interfejsie API sieci Web ASP.NET. Jeśli masz istniejącą usługę WCF i chcesz udostępnić dodatkowe punkty końcowe REST, użyj programu WCF i <xref:System.ServiceModel.WebHttpBinding>.  
  
## <a name="see-also"></a>Zobacz też  
 [Co to jest program Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)  
 [Podstawowe pojęcia programu Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md)  
