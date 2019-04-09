---
title: Kolejki i sesje niezawodne
ms.date: 03/30/2017
ms.assetid: 7e794d03-141c-45ed-b6b1-6c0e104c1464
ms.openlocfilehash: 1fb7d7db36aa51c63789b6daf0ac3689c87ace5c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196830"
---
# <a name="queues-and-reliable-sessions"></a>Kolejki i sesje niezawodne
Kolejki i sesje niezawodne są funkcje Windows Communication Foundation (WCF), które implementują niezawodną obsługę komunikatów. Tematy zawarte w tej sekcji omówiono w nim niezawodne funkcje obsługi komunikatów WCF.  
  
 Niezawodna obsługa komunikatów jest sposobu wiarygodnego źródła wiadomości (nazywane źródła) przesyłania komunikatów niezawodnie niezawodnej obsługi komunikatów miejsca docelowego (nazywane miejsce docelowe).  
  
 Niezawodna obsługa komunikatów ma następujące kluczowe aspekty:  
  
-   Przenieś gwarancji dla komunikatów wysyłanych ze źródła do miejsca docelowego, niezależnie od tego, czy niepowodzenie transferu wiadomości lub błędów transportu.  
  
-   Rozdzielenie źródłowych i docelowych, które ze sobą, co zapewnia niezależnie od awarii i odzyskiwania dla źródła i miejsca docelowego oraz również tak niezawodna transferu dostarczania wiadomości, nawet, jeśli źródłowy lub docelowy jest niedostępny.  
  
 Niezawodna obsługa komunikatów jest dostarczany często kosztem duże opóźnienie. Opóźnienie to czas potrzebny do miejsca docelowego ze źródła wiadomości. Usługi WCF, w związku z tym, zawiera następujące typy niezawodną obsługę komunikatów:  
  
-   [Niezawodne sesje](../../../../docs/framework/wcf/feature-details/reliable-sessions.md), które oferują niezawodne przesyłanie bez ponoszenia kosztów duże opóźnienie  
  
-   [Kolejki programu WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md), które oferują niezawodne transferu i separacji między źródłową i docelową.  
  
## <a name="reliable-sessions"></a>Niezawodne sesje  
 Niezawodne sesje zapewniają end-to-end niezawodne przesyłanie wiadomości między źródłem i miejsca docelowego przy użyciu protokołu WS-ReliableMessaging niezależnie od liczby i typu pośredników, których punkty końcowe komunikatów (źródłowy i docelowy). Dotyczy to również wszelkich pośredników transportu, które nie korzystają z protokołu SOAP (na przykład serwera proxy HTTP) lub pośredników, które używają protokołu SOAP (na przykład opartego na protokole SOAP routery lub mostków), które są wymagane dla komunikatów przepływ między punktami końcowymi. Niezawodne sesje okno transfer w pamięci na awarie poziom komunikatu protokołu SOAP maski i ponownie ustanowić połączenia w przypadku błędów transportu.  
  
 Niezawodne sesje zapewniają transfery wiarygodnych wiadomości o małych opóźnieniach. Zapewniają one komunikaty protokołu SOAP za pośrednictwem serwerów proxy ani pośredników, równoważna jakiego protokołu TCP zapewnia pakietów przez mostków adresów IP. Aby uzyskać więcej informacji o sesjach niezawodnych, zobacz [sesje niezawodnej](../../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>kolejki  
 Kolejki programu WCF zapewnia zarówno niezawodne transferu wiadomości i separacji między źródeł i miejsc docelowych kosztem duże opóźnienie. Usługi WCF w kolejce komunikacji jest zbudowana na usługi kolejkowania komunikatów (MSMQ).  
  
 Usługa MSMQ jest dostarczany jako opcję z Windows, która działa jako usługa NT. Ona przechwytuje wiadomości do przesłania w kolejce transmisji w imieniu źródła i dostarczy go do kolejki docelowej. Kolejka docelowa akceptuje komunikaty o imieniu docelowym w celu późniejszego dostarczenia zawsze wtedy, gdy miejsce docelowe żądań dla wiadomości. Menedżerami kolejki usługi MSMQ zaimplementować protokół transferu komunikatów w niezawodny, dzięki czemu komunikaty nie zostaną utracone podczas transmisji. Protokół może być lokalny lub opartego na protokole SOAP, np. Soap Reliable Messaging Protocol (SRMP).  
  
 Oddzielenie połączone z przeniesienia niezawodnych komunikatów między kolejek umożliwia aplikacji, które są luźno powiązane niezawodnie komunikować się. W przeciwieństwie do sesji niezawodnych źródłowym i docelowym nie musi być uruchomiona w tym samym czasie. Dzięki temu niejawnie scenariuszy, w którym kolejki w efekcie służą jako mechanizm wyrównywania obciążenia w przypadku niezgodności między za produkcji wiadomości według źródeł oraz stawkę za użycie komunikatu przez miejsce docelowe. Aby uzyskać więcej informacji na temat kolejek, zobacz [kolejki programu WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Zobacz także

- [Kolejki programu WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [Tworzenie kolejek w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [Niezawodne sesje](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
- [Omówienie sesji niezawodnych](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)
