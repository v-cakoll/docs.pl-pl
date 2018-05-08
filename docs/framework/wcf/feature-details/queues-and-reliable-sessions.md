---
title: Kolejki i sesje niezawodne
ms.date: 03/30/2017
ms.assetid: 7e794d03-141c-45ed-b6b1-6c0e104c1464
ms.openlocfilehash: a60f409a0f5c237c372fe3303d67ef979950eab4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="queues-and-reliable-sessions"></a>Kolejki i sesje niezawodne
Kolejki i sesje niezawodne są funkcji Windows Communication Foundation (WCF), które implementują niezawodna obsługa komunikatów. Tematy zawarte w tej sekcji omówiono w nim niezawodnej funkcji obsługi komunikatów usługi WCF.  
  
 Niezawodna obsługa komunikatów jest sposobu wiarygodnego źródła wiadomości (nazywane źródła) przesyłania komunikatów niezawodnie do niezawodnej obsługi komunikatów miejsca docelowego (nazywane miejsce docelowe).  
  
 Niezawodna obsługa komunikatów ma następujące kluczowe aspekty:  
  
-   Gwarancje transferu komunikatów wysyłanych z źródła do miejsca docelowego, niezależnie od awarii transportu lub niepowodzenie transferu komunikatów.  
  
-   Rozdzielenie źródłowego i docelowego ze sobą, co zapewnia niezależnie od awarii i odzyskiwania źródłowy i docelowy jako również tak niezawodna transfer i dostarczania wiadomości nawet, jeśli źródłowy lub docelowy jest niedostępny.  
  
 Często niezawodna obsługa komunikatów odbywa się kosztem duże opóźnienie. Opóźnienie to czas potrzebny do miejsca docelowego ze źródła wiadomości. Usługi WCF, w związku z tym zawiera następujące typy niezawodna obsługa komunikatów:  
  
-   [Niezawodne sesje](../../../../docs/framework/wcf/feature-details/reliable-sessions.md), które oferują niezawodnej transfer bez kosztów duże opóźnienie  
  
-   [Kolejki programu WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md), które oferują zarówno transferów niezawodnych i separacji między serwerem źródłowym a docelowym.  
  
## <a name="reliable-sessions"></a>Niezawodne sesje  
 Niezawodne sesje Podaj end-to-end niezawodnej transferu wiadomości między źródłem a miejscem docelowym przy użyciu protokołu WS-ReliableMessaging, niezależnie od liczby i typ pośredników, których punkty końcowe wiadomości (źródłowego i docelowego). Dotyczy to również wszelkich pośredników transportu, które nie korzystają z protokołu SOAP (na przykład serwera proxy HTTP) lub pośredników korzystających z protokołu SOAP (np. routery opartego na protokole SOAP lub mostków), które są wymagane dla komunikatów przepływ między punktami końcowymi. Niezawodne sesje okno transfer w pamięci na awarie poziom wiadomości SOAP maski i ponownie ustanowić połączenia w przypadku awarii transportu.  
  
 Niezawodne sesje Podaj transferów komunikatów niezawodnej małe opóźnienia. Udostępniają one wiadomości SOAP za pośrednictwem serwerów proxy ani pośredników, odpowiednik jakiego protokołu TCP zapewnia pakietów przez mostków IP. Aby uzyskać więcej informacji na temat niezawodnej sesji, zobacz [sesji niezawodnej](../../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>Kolejki  
 Kolejki programu WCF zawierają zarówno niezawodnej transferów komunikatów i separacji między źródłami a miejsc docelowych kosztem duże opóźnienie. Usługi WCF w kolejce komunikacji jest oparty na usługi kolejkowania komunikatów (MSMQ).  
  
 Usługa MSMQ jest dostarczany jako opcja z systemem Windows, który działa jako usługa NT. On przechwytuje wiadomości do przesłania z kolejki transmisji w imieniu źródła i dostarcza go do kolejki docelowej. Kolejka docelowa akceptuje wiadomości w imieniu docelowego w celu późniejszego dostarczenia zawsze, gdy żąda miejsce docelowe dla wiadomości. Menedżerami kolejki usługi MSMQ implementacji protokołu niezawodnych transferu komunikatów, dzięki czemu komunikaty nie zostaną utracone podczas transmisji. Protokół może być lokalny lub opartego na protokole SOAP, takich jak Soap Reliable Messaging Protocol (SRMP).  
  
 Separacji, w połączeniu z komunikatu niezawodnej transferu między kolejek umożliwia aplikacji, które są luźno powiązane do komunikowania się niezawodnie. W przeciwieństwie do sesji niezawodnej źródłowym i docelowym nie masz działa w tym samym czasie. Dzięki temu niejawnie scenariuszy, w którym kolejki w efekcie służą jako mechanizm wyrównywanie obciążenia w przypadku niezgodności między szybkości produkcji wiadomości przez źródłowego i szybkość zużycia wiadomości przez miejsce docelowe. Aby uzyskać więcej informacji na temat kolejek, zobacz [kolejki programu WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kolejki programu WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Tworzenie kolejek w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Niezawodne sesje](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)  
 [Omówienie sesji niezawodnych](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)
