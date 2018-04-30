---
title: Usługa routingu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ca7c216a-5141-4132-8193-102c181d2eba
caps.latest.revision: 13
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8ff2a99bc06ab0de2aedce98ea029f484e47053f
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="routing-service"></a>Usługa routingu
Usługa routingu jest ogólny pośrednik SOAP, który działa jako router wiadomości. Do podstawowych funkcji usługi routingu jest możliwość przesyłania wiadomości, na podstawie zawartości komunikatu, dzięki czemu wiadomości do przekazania do punktu końcowego klienta na podstawie wartości w wiadomości, w nagłówku lub w treści wiadomości.  
  
 <xref:System.ServiceModel.Routing.RoutingService> Jest zaimplementowany jako [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] w <xref:System.ServiceModel.Routing> przestrzeni nazw. Usługa routingu przedstawia jedną lub więcej punktów końcowych usługi który odbiera komunikaty, a następnie trasy każdy komunikat do punktów końcowych klienta na podstawie zawartości wiadomości. Usługa zawiera następujące funkcje:  
  
-   Routing na podstawie zawartości  
  
    -   Usługi agregacji  
  
    -   Przechowywanie wersji usługi  
  
    -   Priorytet routingu  
  
    -   Konfiguracji dynamicznej  
  
-   Mostkowanie protokołu  
  
-   Przetwarzania protokołu SOAP  
  
-   Zaawansowana obsługa błędów  
  
-   Punkty końcowe kopii zapasowej  
  
 Istnieje możliwość tworzenia usługi pośredniczącej, która wykonuje co najmniej jednego z tych celów, często takie implementacja jest związany z konkretnych sytuacji lub rozwiązanie i nie można łatwo zastosować do nowych aplikacji.  
  
 Usługa routingu umożliwia ogólny, można dynamicznie konfigurować, podłączane pośrednik SOAP, który jest zgodny z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi i kanału modeli i umożliwia wykonywanie na podstawie zawartości routingu opartego na protokole SOAP komunikatów.  
  
> [!NOTE]
>  Usługa routingu nie obsługuje obecnie routing [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi REST.  Aby rozesłać wywołań REST, należy rozważyć użycie <xref:System.Web.Routing> lub [Routing żądań aplikacji](http://go.microsoft.com/fwlink/?LinkId=164589) (http://go.microsoft.com/fwlink/?LinkId=164589).  
  
## <a name="content-based-routing"></a>Routing na podstawie zawartości  
 Na podstawie zawartości routingu jest możliwość kierowania wiadomości na podstawie jednego lub więcej wartości zawartych w komunikacie. Usługa routingu sprawdza każdego komunikatów i tras go do docelowego punktu końcowego na podstawie treść wiadomości i logiki routingu, którą utworzysz. Routing na podstawie zawartości stanowi podstawę dla usługi agregacji, przechowywanie wersji usługi i priorytet routingu.  
  
 Do wdrożenia na podstawie zawartości routingu, zależy od usługi routingu <xref:System.ServiceModel.Dispatcher.MessageFilter> implementacji, które są używane do pasuje do wartości określonej w komunikatach przesłana. Jeśli **MessageFilter** dopasowań komunikatu, komunikat jest kierowane do docelowego punktu końcowego skojarzonego z **MessageFilter**.  Filtry komunikatów są pogrupowane w tabelach filtru (<xref:System.ServiceModel.Routing.Configuration.FilterTableCollection>) do utworzenia złożonej logiki routingu. Na przykład tabela filtr może zawierać pięć filtry wykluczają się wzajemnie komunikatów, które komunikaty kierowane do tylko jeden z punktów końcowych pięć docelowego.  
  
 Usługa routingu umożliwia konfigurowanie logiki, który służy do wykonywania na podstawie zawartości routingu, jak również dynamicznie Aktualizuj logiki routingu w czasie wykonywania.  
  
 Za pomocą grupowania filtry komunikatów do filtrów tabel, logiki routingu można skonstruować, który umożliwia obsługę wielu scenariuszy routingu, takich jak:  
  
-   Usługi agregacji  
  
-   Przechowywanie wersji usługi  
  
-   Priorytet routingu  
  
-   Konfiguracji dynamicznej  
  
 Aby uzyskać więcej informacji na temat filtry komunikatów i tabele filtru, zobacz [routingu wprowadzenie](../../../../docs/framework/wcf/feature-details/routing-introduction.md) i [filtry komunikatów](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
### <a name="service-aggregation"></a>Usługi agregacji  
 Przy użyciu routingu na podstawie zawartości, może narazić jeden punkt końcowy, który odbiera komunikaty z aplikacji zewnętrznych klienta, a następnie przekierowuje każdy komunikat do odpowiednich wewnętrzny punkt końcowy na podstawie wartości w komunikacie. Jest to przydatne, oferowanie jednego określonego punktu końcowego dla wielu aplikacji zaplecza i przekazać jeden punkt końcowy aplikacji do klientów podczas factoring aplikacji do różnych usług.  
  
### <a name="service-versioning"></a>Przechowywanie wersji usługi  
 Podczas migracji do nowej wersji rozwiązania, należy zachować starą wersję równolegle do obsługi istniejących klientów. Często wymaga klientów łączących się z nowszej wersji należy użyć innego adresu podczas komunikowania się z rozwiązaniem. Usługa routingu umożliwia uwidocznienie jeden punkt końcowy usługi pełniącą obie wersje rozwiązania poprzez wiadomości routingu do odpowiedniej rozwiązania na podstawie informacji o określonej wersji zawarte w wiadomości. Przykładem takiego wdrożenia dla [jak: przechowywanie wersji usługi](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md).  
  
### <a name="priority-routing"></a>Priorytet routingu  
 Podczas tworzenia usługi dla wielu klientów, może być Umowa dotycząca poziomu usług (SLA), niektórych partnerom, które wymaga wszystkich danych przez tych partnerów do przetworzenia oddzielnie od innych klientów. Przy użyciu filtru sprawdzający właściwe dla klienta informacje zawarte w wiadomości, można łatwo rozesłać komunikaty z określonym partnerów do punktu końcowego, który został utworzony w celu spełnienia wymagań SLA.  
  
## <a name="dynamic-configuration"></a>Konfiguracji dynamicznej  
 Do obsługi systemów krytycznym, gdzie wiadomości musi zostać przetworzona, bez żadnych przerw w działaniu usługi, jest istotne, że można zmodyfikować konfigurację składników w systemie w czasie wykonywania. Aby obsługiwać te wymagania, usługa routingu umożliwia <xref:System.ServiceModel.IExtension%601> implementacji <xref:System.ServiceModel.Routing.RoutingExtension>, co umożliwia dynamiczne aktualizowanie konfiguracji usługi routingu w czasie wykonywania.  
  
 Aby uzyskać więcej informacji o konfiguracji dynamicznej usługi routingu, zobacz [routingu wprowadzenie](../../../../docs/framework/wcf/feature-details/routing-introduction.md).  
  
## <a name="protocol-bridging"></a>Mostkowanie protokołu  
 Jedną z trudności w scenariuszach pośredniczące jest wewnętrznych punktów końcowych może innego transportu lub wymagania dotyczące wersji SOAP niż punktu końcowego, który są odbierane wiadomości. Aby obsługiwać ten scenariusz, usługa routingu może mostkować protokołów, w tym przetwarzanie wiadomości SOAP do <xref:System.ServiceModel.Channels.MessageVersion> wymagane przez punktów końcowych docelowego. W ten sposób jeden protokół może służyć do wewnętrznej komunikacji, podczas gdy inny może służyć do komunikacji zewnętrznej.  
  
 Aby obsługiwać routing wiadomości między punktami końcowymi z innego transportu, usługa routingu używa powiązania dostarczane przez system, umożliwiających usługi do zestawiania niepodobnych protokołów. Występuje to automatycznie, gdy punkt końcowy usługi udostępniane przez usługi routingu używa innego protokołu niż punkty końcowe klienta, które komunikaty są kierowane do.  
  
## <a name="soap-processing"></a>Przetwarzania protokołu SOAP  
 Typowe wymagania routingu jest możliwość przesyłania wiadomości między punktami końcowymi różne wymagania protokołu SOAP. W celu spełnienia tego wymagania, usługa routingu umożliwia <xref:System.ServiceModel.Routing.SoapProcessingBehavior> automatycznie tworzącą nowy **MessageVersion** spełnia wymagania docelowego punktu końcowego, zanim komunikat jest kierowany do niego. To zachowanie również tworzy nowy **MessageVersion** dla dowolnego komunikatu odpowiedzi przed zwróceniem jej do żądania aplikacji klienckiej, upewnij się, że **MessageVersion** odpowiedzi zgodny z oryginalne żądanie.  
  
 Aby uzyskać więcej informacji na temat przetwarzania protokołu SOAP, zobacz [routingu wprowadzenie](../../../../docs/framework/wcf/feature-details/routing-introduction.md).  
  
## <a name="error-handling"></a>Obsługa błędów  
 W systemie składa się z usługi rozproszone, które opierają się na komunikacji sieciowej jest ważne upewnić się, że komunikacji w danym systemie są odporne na awarie sieci.  Usługa routingu implementuje obsługi błędów, który umożliwia obsługę wielu scenariuszy awarii łączności, które w przeciwnym razie może spowodować awarię usług.  
  
 Jeśli usługi routingu napotkał <xref:System.ServiceModel.CommunicationException> podczas próby wysłania wiadomości, odbędzie się obsługi błędów.  Tych wyjątków zwykle oznaczają, że wystąpił problem podczas próby komunikacji z punktem końcowym zdefiniowanych klienta, takich jak <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, lub <xref:System.ServiceModel.CommunicationObjectFaultedException>.  Kod obsługi błędów utworzy również catch i spróbuj ponowić próbę, gdy wysyłanie **TimeoutException** występuje, który jest inny wspólnej wyjątek, który nie pochodzi od **communicationexception —**.  
  
 Aby uzyskać więcej informacji na temat obsługi błędów, zobacz [routingu wprowadzenie](../../../../docs/framework/wcf/feature-details/routing-introduction.md).  
  
## <a name="backup-endpoints"></a>Punkty końcowe kopii zapasowej  
 Oprócz docelowego klienta punkty końcowe skojarzone z każdej definicji filtru w tablicy filtrów można tworzyć również listę kopii zapasowych punkty końcowe, które wiadomości będą kierowane do awarii transmisji. Jeśli wystąpi błąd i listy kopii zapasowych jest zdefiniowany dla wpisu filtru, usługa routingu będzie podejmować próby wysłania wiadomości do pierwszego punktu końcowego zdefiniowane na liście. Jeśli ten transmisji próba nie powiedzie się, usługa spróbuj następnego punktu końcowego i kontynuować ten proces, dopóki próba transmisji kończy się powodzeniem, zwróci błąd powiązany z systemem innym niż transmisji lub wszystkie punkty końcowe na liście kopii zapasowej zwrócono błąd transmisji.  
  
 Aby uzyskać więcej informacji dotyczących tworzenia kopii zapasowej punktów końcowych, zobacz [routingu wprowadzenie](../../../../docs/framework/wcf/feature-details/routing-introduction.md) i [filtry komunikatów](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
## <a name="streaming"></a>przesyłanie strumieniowe  
 Usługa routingu pomyślnie można strumienia komunikatów, jeśli ustawisz powiązania w celu obsługi przesyłania strumieniowego.  Istnieją jednak niektóre warunki, w których wiadomości może być konieczne buforowane:  
  
-   Multiemisji (bufor do tworzenia kopii dodatkowe wiadomości)  
  
-   Tryb failover (buforu w przypadku, gdy wiadomość musi być wysyłana do kopii zapasowej)  
  
-   System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly ma wartość false (bufor do prezentowania obiektu MessageFilterTable z elementu MessageBuffer, aby sprawdzić filtry treści)  
  
-   Konfiguracji dynamicznej  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do routingu](../../../../docs/framework/wcf/feature-details/routing-introduction.md)  
 [Kontrakty routingu](../../../../docs/framework/wcf/feature-details/routing-contracts.md)  
 [Filtry komunikatów](../../../../docs/framework/wcf/feature-details/message-filters.md)
