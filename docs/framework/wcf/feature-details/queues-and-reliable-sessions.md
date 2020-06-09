---
title: Kolejki i sesje niezawodne
ms.date: 03/30/2017
ms.assetid: 7e794d03-141c-45ed-b6b1-6c0e104c1464
ms.openlocfilehash: af45fd86f673d0cc296f6593d9d5709d3e2b616e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596750"
---
# <a name="queues-and-reliable-sessions"></a>Kolejki i sesje niezawodne
Kolejki i niezawodne sesje to funkcje Windows Communication Foundation (WCF), które implementują niezawodne komunikaty. Tematy zawarte w tej sekcji omawiają funkcje niezawodnej obsługi komunikatów w programie WCF.  
  
 Niezawodna obsługa komunikatów polega na tym, że niezawodne źródło komunikatów (nazywane źródłem) przesyła komunikaty niezawodne do niezawodnego miejsca docelowego obsługi komunikatów (nazywanego miejscem docelowym).  
  
 Niezawodna obsługa komunikatów ma następujące kluczowe aspekty:  
  
- Gwarantuje transfer komunikatów wysyłanych ze źródła do miejsca docelowego bez względu na awarie transferu komunikatów lub błędy transportu.  
  
- Oddzielenie źródła i miejsca docelowego od siebie, które zapewnia niezależną awarię i odzyskiwanie źródła i miejsca docelowego, a także niezawodny transfer i dostarczanie komunikatów, nawet jeśli źródło lub miejsce docelowe są niedostępne.  
  
 Niezawodne komunikaty często mają koszt dużego opóźnienia. Opóźnienie to czas, jaki zajmuje komunikat docierania do miejsca docelowego ze źródła. W związku z tym program obsługuje następujące typy niezawodnej obsługi komunikatów:  
  
- [Niezawodne sesje](reliable-sessions.md), które oferują niezawodny transfer bez kosztu dużego opóźnienia  
  
- [Kolejki w programie WCF](queues-in-wcf.md), które oferują niezawodne transfery i rozdzielanie między źródłem a miejscem docelowym.  
  
## <a name="reliable-sessions"></a>Niezawodne sesje  
 Niezawodne sesje zapewniają kompleksowy, niezawodny transfer komunikatów między źródłem a miejscem docelowym przy użyciu protokołu WS-ReliableMessaging bez względu na liczbę lub typ pośredników, które oddzielają punkty końcowe komunikatów (źródłowych i docelowych). Dotyczy to wszystkich pośredników transportu, które nie używają protokołu SOAP (na przykład proxy HTTP) ani pośredników korzystających z protokołu SOAP (na przykład routerów lub mostków opartych na protokole SOAP), które są wymagane do przepływu komunikatów między punktami końcowymi. Niezawodne sesje używają okna transferu w pamięci do maskowania błędów na poziomie komunikatu protokołu SOAP i ponownego ustanawiania połączeń w przypadku awarii transportu.  
  
 Niezawodne sesje zapewniają niezawodne przesyłanie komunikatów o małym opóźnieniu. Zapewniają one komunikaty protokołu SOAP za pośrednictwem dowolnych serwerów proxy lub pośredników, równoważne z protokołem TCP zapewnianym przez pakiety przez mosty IP. Aby uzyskać więcej informacji na temat sesji niezawodnych, zobacz [Sesje niezawodne](reliable-sessions.md).  
  
## <a name="queues"></a>Kolejki  
 Kolejki w programie WCF zapewniają niezawodne transfery komunikatów i separację między źródłami i miejscami docelowymi kosztem dużego opóźnienia. Komunikacja w kolejce WCF jest oparta na usłudze kolejkowania komunikatów (znanej także jako MSMQ).  
  
 Usługa MSMQ jest dostarczana jako opcja systemu Windows, która działa jako usługa NT. Przechwytuje komunikaty do transmisji w kolejce transmisji w imieniu źródła i dostarcza je do kolejki docelowej. Kolejka docelowa akceptuje komunikaty w imieniu miejsca docelowego w celu późniejszego dostarczenia za każdym razem, gdy docelowe żądania komunikatów. Menedżerowie kolejki MSMQ implementują niezawodny protokół transferu komunikatów, dzięki czemu komunikaty nie są tracone w transmisji. Protokół może być natywny lub oparty na protokole SOAP, taki jak protokół SOAP unmessaging Protocol (SRMP).  
  
 Separacja, w połączeniu z niezawodnymi transferami komunikatów między kolejkami, umożliwia niezawodną komunikację z aplikacjami, które są luźno połączone. W przeciwieństwie do sesji niezawodnych, źródło i miejsce docelowe nie muszą być uruchomione w tym samym czasie. To niejawnie włącza scenariusze, w których kolejki są stosowane jako mechanizm poziomu obciążenia, gdy występuje niezgodność między szybkością produkcji komunikatów przez źródło i szybkością zużycia komunikatów przez miejsce docelowe. Aby uzyskać więcej informacji o kolejkach, zobacz [kolejki w programie WCF](queues-in-wcf.md).  
  
## <a name="see-also"></a>Zobacz też

- [Kolejki programu WCF](queues-in-wcf.md)
- [Tworzenie kolejek w programie WCF](queuing-in-wcf.md)
- [Niezawodne sesje](reliable-sessions.md)
- [Omówienie sesji niezawodnych](reliable-sessions-overview.md)
