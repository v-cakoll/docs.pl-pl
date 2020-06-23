---
title: Interfejs API sieci Web programu WCF i platformy ASP.NET
description: Dowiedz się, czy interfejs API sieci Web WCF lub ASP.NET jest lepiej dostosowany do Twoich potrzeb, porównując główne funkcje poszczególnych technologii.
ms.date: 03/30/2017
ms.assetid: 08ceded3-fd9a-4467-9715-c4cbd9c7228e
ms.openlocfilehash: de8d1905866c860da96983c2f3d52599e3342403
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245970"
---
# <a name="wcf-and-aspnet-web-api"></a>Interfejs API sieci Web programu WCF i platformy ASP.NET
WCF to ujednolicony model programowania firmy Microsoft służący do tworzenia aplikacji zorientowanych na usługę. Umożliwia ona deweloperom tworzenie bezpiecznych, niezawodnych, transakcyjnych rozwiązań, które integrują się między platformami i współdziałają z istniejącymi inwestycjami. [Interfejs API sieci Web ASP.NET](https://www.asp.net/web-api) to struktura, która ułatwia tworzenie usług http, które docierają do szerokiego zakresu klientów, w tym przeglądarek i urządzeń przenośnych. Interfejs API sieci Web ASP.NET to idealna platforma służąca do tworzenia aplikacji RESTful na .NET Framework. W tym temacie przedstawiono wskazówki ułatwiające podjęcie decyzji, która technologia najlepiej spełnia Twoje potrzeby.  
  
## <a name="choosing-which-technology-to-use"></a>Wybieranie technologii do użycia  
 W poniższej tabeli opisano główne funkcje poszczególnych technologii.  
  
|WCF|Internetowy interfejs API platformy ASP.NET|  
|---------|---------------------|  
|Umożliwia tworzenie usług, które obsługują wiele protokołów transportu (HTTP, TCP, UDP i transporty niestandardowe) i umożliwia przełączanie między nimi.|Tylko HTTP. Model programowania pierwszej klasy dla protokołu HTTP. Jest to bardziej odpowiednie w przypadku dostępu z różnych przeglądarek, urządzeń przenośnych itd.|  
|Umożliwia tworzenie usług, które obsługują wiele kodowań (text, MTOM i Binary) tego samego typu komunikatu i umożliwia przełączanie między nimi.|Umożliwia tworzenie interfejsów API sieci Web, które obsługują szeroką gamę typów multimediów, w tym XML, JSON itp.|  
|Obsługuje tworzenie usług przy użyciu standardów WS-*, takich jak niezawodne komunikaty, transakcje i zabezpieczenia komunikatów.|Używa podstawowego protokołu i formatów, takich jak HTTP, WebSockets, SSL, JSON i XML. Nie ma żadnego wsparcia dla protokołów wyższego poziomu, takich jak niezawodne komunikaty lub transakcje.|  
|Obsługuje wzorce wymiany komunikatów Request-reply, jednokierunkowe i dwustronne.|Protokół HTTP jest żądaniem/odpowiedzi, ale mogą być obsługiwane dodatkowe wzorce za pośrednictwem integracji [sygnałów](https://github.com/SignalR/SignalR) i obiektów WebSockets.|  
|W języku WSDL można opisać usługi SOAP WCF umożliwiające zautomatyzowanym narzędziom Generowanie serwerów proxy klientów nawet dla usług z złożonymi schematami.|Istnieją różne sposoby opisywania internetowego interfejsu API w zakresie od automatycznie generowanej strony pomocy HTML zawierającej fragmenty kodu do metadanych strukturalnych dla zintegrowanych interfejsów API OData.|  
|Jest dostarczany z .NET Frameworką.|Program jest dostarczany z .NET Framework, ale jest typu open source i jest również dostępny poza pasmem jako niezależnym do pobrania.|  
  
 Używaj programu WCF do tworzenia niezawodnych, bezpiecznych usług sieci Web, które są dostępne w różnych transportach. Użyj interfejsu API sieci Web ASP.NET do tworzenia usług opartych na protokole HTTP, które są dostępne dla wielu klientów. Korzystanie z interfejsu API sieci Web ASP.NET w przypadku tworzenia i projektowania nowych usług w stylu REST. Mimo że WCF zapewnia obsługę pisania usług w stylu REST, obsługa protokołu REST w interfejsie Web API ASP.NET jest bardziej kompletna, a wszystkie przyszłe ulepszenia funkcji REST zostaną wprowadzone w ASP.NET Web API. Jeśli masz istniejącą usługę WCF i chcesz uwidocznić dodatkowe punkty końcowe REST, użyj programu WCF i <xref:System.ServiceModel.WebHttpBinding> .  
  
## <a name="see-also"></a>Zobacz też

- [Co to jest program Windows Communication Foundation](whats-wcf.md)
- [Podstawowe pojęcia programu Windows Communication Foundation](fundamental-concepts.md)
