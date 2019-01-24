---
title: Niezawodne usługi
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], reliable messaging
- Windows Communication Foundation [WCF], reliable messaging
- WCF [WCF], reliable sessions
- Windows Communication Foundation [WCF], reliable sessions
- service contracts [WCF], reliable services
ms.assetid: 07814ed0-0775-47f2-987b-d8134fdd5099
ms.openlocfilehash: a3a53cb26ffb0e5934982c1c9f367115177b9b59
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559401"
---
# <a name="reliable-services"></a>Niezawodne usługi
Kolejki i sesje niezawodne są funkcje Windows Communication Foundation (WCF), które implementują niezawodną obsługę komunikatów. W tym temacie opisano niezawodne funkcje komunikatów WCF.  
  
 *Niezawodna obsługa komunikatów* jest jak wiarygodnego źródła wiadomości (o nazwie *źródła*) niezawodnie przesyła komunikaty niezawodnej obsługi komunikatów miejsca docelowego (o nazwie *docelowy*).  
  
 Niezawodna obsługa komunikatów wykonuje następujące funkcje:  
  
-   Przesyła gwarancji dla komunikatów wysyłanych ze źródła do miejsca docelowego, niezależnie od awarii przenoszenia lub transportu wiadomości.  
  
-   Oddziela źródło i miejsce docelowe, od siebie nawzajem. Dzięki temu można niezależnie od awarii i odzyskiwania źródło i miejsce docelowe, jak również transferu niezawodne i dostarczanie wiadomości, nawet wtedy, gdy źródłowy lub docelowy jest niedostępny.  
  
 Niezawodna obsługa komunikatów jest dostarczany często kosztem duże opóźnienie. *Opóźnienie* to czas potrzebny do miejsca docelowego ze źródła wiadomości. Usługi WCF, w związku z tym, zawiera następujące typy niezawodną obsługę komunikatów:  
  
-   [Niezawodne sesje](../../../docs/framework/wcf/feature-details/reliable-sessions.md), która zapewnia niezawodne przesyłanie bez ponoszenia kosztów duże opóźnienie.  
  
-   [Kolejki programu WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md), które oferuje niezawodny transferu i separacji między źródłową i docelową.  
  
## <a name="reliable-sessions"></a>Niezawodne sesje  
 Niezawodne sesje zapewniają end-to-end niezawodne przesyłanie wiadomości między źródłem i miejsca docelowego przy użyciu protokołu elementy usługi WS-Reliable Messaging, niezależnie od liczby i typu pośredników, których punkty końcowe komunikatów (źródłowy i docelowy). Dotyczy to również wszelkich pośredników transportu, które nie korzystają z protokołu SOAP (na przykład serwera proxy HTTP) lub pośredników, które używają protokołu SOAP (na przykład opartego na protokole SOAP routery lub mostków), które są wymagane dla komunikatów przepływ między punktami końcowymi. Niezawodne sesje okno transfer w pamięci na awarie poziom komunikatu protokołu SOAP maski i ponownie ustanowić połączenia w przypadku błędów transportu.  
  
 Niezawodne sesje zapewniają transfery wiarygodnych wiadomości o małych opóźnieniach. Zapewniają one komunikaty protokołu SOAP za pośrednictwem serwerów proxy ani pośredników, równoważna jakiego protokołu TCP zapewnia pakietów przez mostków adresów IP. Aby uzyskać więcej informacji o sesjach niezawodnych, zobacz [sesje niezawodnej](../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>kolejki  
 Kolejki programu WCF zapewnia zarówno niezawodne transferu wiadomości i separacji między źródeł i miejsc docelowych kosztem duże opóźnienie. Usługi WCF w kolejce komunikacji jest zbudowany na podstawie usługi kolejkowania komunikatów (MSMQ).  
  
 Usługa MSMQ jest dostarczany jako opcjonalny składnik z Windows. Usługa MSMQ jest uruchamiana jako usługa Windows. Ona przechwytuje wiadomości do przesłania w kolejce transmisji w imieniu źródła i dostarczy go do kolejki docelowej. Kolejka docelowa akceptuje komunikaty o imieniu docelowym w celu późniejszego dostarczenia zawsze wtedy, gdy miejsce docelowe żądań wiadomości. Menedżerowie MSMQ zaimplementować protokół transferu komunikatów w niezawodny, dzięki czemu komunikaty nie zostaną utracone podczas transmisji. Protokół może być natywne lub opartego na protokole SOAP protokołu SOAP Reliable Messaging Protocol (SRMP).  
  
 Oddzielenie połączone z przeniesienia niezawodnych komunikatów między kolejek umożliwia aplikacji, które są luźno powiązane niezawodnie komunikować się. W przeciwieństwie do sesji niezawodnych źródłowym i docelowym nie musi być uruchomiona w tym samym czasie. Dzięki temu niejawnie scenariuszach, gdzie kolejek w praktyce używana jako mechanizm wyrównywania obciążenia, gdy współczynnik źródła wiadomości w środowisku produkcyjnym i miejsca docelowego stopień wykorzystania wiadomości nie są zgodne. Aby uzyskać więcej informacji na temat kolejek, zobacz [kolejki programu WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Zobacz także
- [Omówienie sesji niezawodnych](../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)
- [Tworzenie kolejek w programie WCF](../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
