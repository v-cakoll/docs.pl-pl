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
ms.openlocfilehash: 78f492c7a7c5abd7b72c40fc5695b8d56003f822
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319888"
---
# <a name="reliable-services"></a>Niezawodne usługi
Kolejki i niezawodne sesje to funkcje Windows Communication Foundation (WCF), które implementują niezawodne komunikaty. W tym temacie opisano funkcje niezawodnej obsługi komunikatów w programie WCF.  
  
 *Niezawodna obsługa* komunikatów polega na tym, że niezawodne źródło komunikatów (nazywane *źródłem*) przesyła komunikaty niezawodne do niezawodnego miejsca docelowego obsługi komunikatów (nazywanego *miejscem docelowym*).  
  
 Niezawodne komunikaty są wykonywane przy użyciu następujących funkcji:  
  
- Przekazuje gwarancje dotyczące komunikatów wysyłanych ze źródła do miejsca docelowego niezależnie od transferu komunikatów lub niepowodzeń transportu.  
  
- Oddziela źródło i miejsce docelowe od siebie. Zapewnia to niezależną awarię i odzyskiwanie źródła i miejsca docelowego, a także niezawodny transfer i dostarczanie komunikatów, nawet jeśli źródło lub miejsce docelowe są niedostępne.  
  
 Niezawodne komunikaty często mają koszt dużego opóźnienia. *Opóźnienie* to czas, jaki zajmuje komunikat docierania do miejsca docelowego ze źródła. W związku z tym program obsługuje następujące typy niezawodnej obsługi komunikatów:  
  
- [Niezawodne sesje](./feature-details/reliable-sessions.md), które oferują niezawodny transfer bez kosztu dużego opóźnienia.  
  
- [Kolejki w programie WCF](./feature-details/queues-in-wcf.md), które oferują niezawodne transfery i rozdzielenie między źródłem a miejscem docelowym.  
  
## <a name="reliable-sessions"></a>Niezawodne sesje  
 Niezawodne sesje zapewniają kompleksowy, niezawodny transfer komunikatów między źródłem a miejscem docelowym przy użyciu protokołu obsługi komunikatów w usłudze WS-niezawodny, niezależnie od liczby lub typu pośredników, które oddzielają punkty końcowe komunikatów (źródłowych i docelowych). Dotyczy to wszystkich pośredników transportu, które nie używają protokołu SOAP (na przykład proxy HTTP) ani pośredników korzystających z protokołu SOAP (na przykład routerów lub mostków opartych na protokole SOAP), które są wymagane do przepływu komunikatów między punktami końcowymi. Niezawodne sesje używają okna transferu w pamięci do maskowania błędów na poziomie komunikatu protokołu SOAP i ponownego ustanawiania połączeń w przypadku awarii transportu.  
  
 Niezawodne sesje zapewniają niezawodne przesyłanie komunikatów o małym opóźnieniu. Zapewniają one komunikaty protokołu SOAP za pośrednictwem dowolnych serwerów proxy lub pośredników, równoważne z protokołem TCP zapewnianym przez pakiety przez mosty IP. Aby uzyskać więcej informacji na temat sesji niezawodnych, zobacz [Sesje niezawodne](./feature-details/reliable-sessions.md).  
  
### <a name="queues"></a>tworzone  
 Kolejki w programie WCF zapewniają niezawodne transfery komunikatów i separację między źródłami i miejscami docelowymi kosztem dużego opóźnienia. Komunikacja z kolejką WCF została utworzona na podstawie usługi kolejkowania komunikatów (MSMQ).  
  
 Usługa MSMQ jest dostarczana jako składnik opcjonalny z systemem Windows. Usługa MSMQ działa jako usługa systemu Windows. Przechwytuje komunikaty do transmisji w kolejce transmisji w imieniu źródła i dostarcza je do kolejki docelowej. Kolejka docelowa akceptuje komunikaty w imieniu miejsca docelowego w celu późniejszego dostarczenia przy każdym zalogowaniu. Menedżerowie MSMQ implementują niezawodny protokół transferu komunikatów, dzięki czemu komunikaty nie są tracone w transmisji. Protokół może być natywny lub protokołu opartego na protokole SOAP o nazwie protokołu SOAP niezawodnej obsługi komunikatów (SRMP).  
  
 Separacja, w połączeniu z niezawodnymi transferami komunikatów między kolejkami, umożliwia niezawodną komunikację z aplikacjami, które są luźno połączone. W przeciwieństwie do sesji niezawodnych, źródło i miejsce docelowe nie muszą być uruchomione w tym samym czasie. To niejawnie włącza scenariusze, w których kolejki są stosowane jako mechanizm poziomu obciążenia, gdy wskaźnik źródła produkcji komunikatów i szybkość użycia wiadomości nie są zgodne. Aby uzyskać więcej informacji o kolejkach, zobacz [kolejki w programie WCF](./feature-details/queues-in-wcf.md).  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie sesji niezawodnych](./feature-details/reliable-sessions-overview.md)
- [Tworzenie kolejek w programie WCF](./feature-details/queuing-in-wcf.md)
