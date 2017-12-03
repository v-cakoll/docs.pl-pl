---
title: Kolejki i sesje niezawodne
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e794d03-141c-45ed-b6b1-6c0e104c1464
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9b2ad869e8127bcaf513bee82e3175b35349d922
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="queues-and-reliable-sessions"></a>Kolejki i sesje niezawodne
Kolejki i sesje niezawodne są [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] funkcje, które implementują niezawodna obsługa komunikatów. Tematy zawarte w tej sekcji omówiono w nim [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] niezawodnej funkcji obsługi komunikatów.  
  
 Niezawodna obsługa komunikatów jest sposobu wiarygodnego źródła wiadomości (nazywane źródła) przesyłania komunikatów niezawodnie do niezawodnej obsługi komunikatów miejsca docelowego (nazywane miejsce docelowe).  
  
 Niezawodna obsługa komunikatów ma następujące kluczowe aspekty:  
  
-   Gwarancje transferu komunikatów wysyłanych z źródła do miejsca docelowego, niezależnie od awarii transportu lub niepowodzenie transferu komunikatów.  
  
-   Rozdzielenie źródłowego i docelowego ze sobą, co zapewnia niezależnie od awarii i odzyskiwania źródłowy i docelowy jako również tak niezawodna transfer i dostarczania wiadomości nawet, jeśli źródłowy lub docelowy jest niedostępny.  
  
 Często niezawodna obsługa komunikatów odbywa się kosztem duże opóźnienie. Opóźnienie to czas potrzebny do miejsca docelowego ze źródła wiadomości. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], w związku z tym zapewnia następujące typy niezawodnej obsługi komunikatów:  
  
-   [Niezawodne sesje](../../../../docs/framework/wcf/feature-details/reliable-sessions.md), które oferują niezawodnej transfer bez kosztów duże opóźnienie  
  
-   [Kolejki programu WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md), które oferują zarówno transferów niezawodnych i separacji między serwerem źródłowym a docelowym.  
  
## <a name="reliable-sessions"></a>Niezawodne sesje  
 Niezawodne sesje Podaj end-to-end niezawodnej transferu wiadomości między źródłem a miejscem docelowym przy użyciu protokołu WS-ReliableMessaging, niezależnie od liczby i typ pośredników, których punkty końcowe wiadomości (źródłowego i docelowego). Dotyczy to również wszelkich pośredników transportu, które nie korzystają z protokołu SOAP (na przykład serwera proxy HTTP) lub pośredników korzystających z protokołu SOAP (np. routery opartego na protokole SOAP lub mostków), które są wymagane dla komunikatów przepływ między punktami końcowymi. Niezawodne sesje okno transfer w pamięci na awarie poziom wiadomości SOAP maski i ponownie ustanowić połączenia w przypadku awarii transportu.  
  
 Niezawodne sesje Podaj transferów komunikatów niezawodnej małe opóźnienia. Udostępniają one wiadomości SOAP za pośrednictwem serwerów proxy ani pośredników, odpowiednik jakiego protokołu TCP zapewnia pakietów przez mostków IP. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]niezawodne sesje, zobacz [sesji niezawodnej](../../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>Kolejki  
 Kolejki w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zapewniają zarówno niezawodnej transferów komunikatów i separacji między źródłami a miejsc docelowych kosztem duże opóźnienie. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Komunikacja z obsługą kolejek jest oparty na usługi kolejkowania komunikatów (MSMQ).  
  
 Usługa MSMQ jest dostarczany jako opcja z systemem Windows, który działa jako usługa NT. On przechwytuje wiadomości do przesłania z kolejki transmisji w imieniu źródła i dostarcza go do kolejki docelowej. Kolejka docelowa akceptuje wiadomości w imieniu docelowego w celu późniejszego dostarczenia zawsze, gdy żąda miejsce docelowe dla wiadomości. Menedżerami kolejki usługi MSMQ implementacji protokołu niezawodnych transferu komunikatów, dzięki czemu komunikaty nie zostaną utracone podczas transmisji. Protokół może być lokalny lub opartego na protokole SOAP, takich jak Soap Reliable Messaging Protocol (SRMP).  
  
 Separacji, w połączeniu z komunikatu niezawodnej transferu między kolejek umożliwia aplikacji, które są luźno powiązane do komunikowania się niezawodnie. W przeciwieństwie do sesji niezawodnej źródłowym i docelowym nie masz działa w tym samym czasie. Dzięki temu niejawnie scenariuszy, w którym kolejki w efekcie służą jako mechanizm wyrównywanie obciążenia w przypadku niezgodności między szybkości produkcji wiadomości przez źródłowego i szybkość zużycia wiadomości przez miejsce docelowe. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]kolejki, zobacz [kolejki programu WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kolejki programu WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Usługi kolejkowania wiadomości w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Niezawodne sesje](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)  
 [Omówienie sesji niezawodnych](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)
