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
ms.openlocfilehash: f98da5db34686e3bf09cc14c42a2ff6b693201f6
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803757"
---
# <a name="reliable-services"></a>Niezawodne usługi
Kolejki i sesje niezawodne są funkcji Windows Communication Foundation (WCF), które implementują niezawodna obsługa komunikatów. W tym temacie opisano niezawodnej funkcji obsługi komunikatów usługi WCF.  
  
 *Niezawodna obsługa komunikatów* jest sposób wiarygodnego źródła komunikatów (o nazwie *źródła*) niezawodnie przekazuje komunikaty niezawodnej obsługi komunikatów miejsca docelowego (nazywane *docelowego*).  
  
 Niezawodna obsługa komunikatów wykonuje następujące funkcje:  
  
-   Transfery gwarancji komunikatów wysyłanych z źródła do miejsca docelowego, niezależnie od awarii przenoszenia lub transportu wiadomości.  
  
-   Oddziela źródłowego i docelowego od siebie. Zapewnia to niezależnie od awarii i odzyskiwanie źródło i miejsce docelowe, jak również transfer niezawodnych i dostarczanie komunikatów, nawet jeśli źródłowy lub docelowy jest niedostępny.  
  
 Często niezawodna obsługa komunikatów odbywa się kosztem duże opóźnienie. *Czas oczekiwania* to czas potrzebny do miejsca docelowego ze źródła wiadomości. Usługi WCF, w związku z tym zawiera następujące typy niezawodna obsługa komunikatów:  
  
-   [Niezawodne sesje](../../../docs/framework/wcf/feature-details/reliable-sessions.md), które oferuje niezawodny transfer bez kosztów duże opóźnienie.  
  
-   [Kolejki programu WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md), które oferuje zarówno transferów niezawodnych i separacji między serwerem źródłowym a docelowym.  
  
## <a name="reliable-sessions"></a>Niezawodne sesje  
 Niezawodne sesje Podaj end-to-end niezawodnej transferu wiadomości między źródłem a miejscem docelowym przy użyciu protokołu WS-niezawodny wiadomości, niezależnie od liczby i typ pośredników, których punkty końcowe wiadomości (źródłowego i docelowego). Dotyczy to również wszelkich pośredników transportu, które nie korzystają z protokołu SOAP (na przykład serwera proxy HTTP) lub pośredników korzystających z protokołu SOAP (np. routery opartego na protokole SOAP lub mostków), które są wymagane dla komunikatów przepływ między punktami końcowymi. Niezawodne sesje okno transfer w pamięci na awarie poziom wiadomości SOAP maski i ponownie ustanowić połączenia w przypadku awarii transportu.  
  
 Niezawodne sesje Podaj transferów komunikatów niezawodnej małe opóźnienia. Udostępniają one wiadomości SOAP za pośrednictwem serwerów proxy ani pośredników, odpowiednik jakiego protokołu TCP zapewnia pakietów przez mostków IP. Aby uzyskać więcej informacji na temat niezawodnej sesji, zobacz [sesji niezawodnej](../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>Kolejki  
 Kolejki programu WCF zawierają zarówno niezawodnej transferów komunikatów i separacji między źródłami a miejsc docelowych kosztem duże opóźnienie. Usługi WCF w kolejce komunikacji jest oparty na górze usługi kolejkowania komunikatów (MSMQ).  
  
 Usługa MSMQ jest dostarczany jako opcjonalny składnik z systemem Windows. Usługa MSMQ działa jako usługa systemu Windows. On przechwytuje wiadomości do przesłania z kolejki transmisji w imieniu źródła i dostarcza go do kolejki docelowej. Kolejka docelowa akceptuje wiadomości w imieniu docelowego w celu późniejszego dostarczenia zawsze, gdy miejsce docelowe żądań wiadomości. Menedżerów MSMQ implementuje protokołu niezawodnych transferu komunikatów, dzięki czemu komunikaty nie zostaną utracone podczas transmisji. Protokół może być natywne lub opartego na protokole SOAP protokołu SOAP Reliable Messaging Protocol (SRMP).  
  
 Separacji, w połączeniu z komunikatu niezawodnej transferu między kolejek umożliwia aplikacji, które są luźno powiązane do komunikowania się niezawodnie. W przeciwieństwie do sesji niezawodnej źródłowym i docelowym nie masz działa w tym samym czasie. Dzięki temu niejawnie scenariuszy, w którym kolejek w efekcie używanych jako mechanizm wyrównywanie obciążenia podczas stosownej źródła komunikatów i szybkość miejsca docelowego zużycia wiadomości nie są zgodne. Aby uzyskać więcej informacji na temat kolejek, zobacz [kolejki programu WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie sesji niezawodnych](../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)  
 [Tworzenie kolejek w programie WCF](../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
