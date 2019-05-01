---
title: Usługa routingu
ms.date: 03/30/2017
ms.assetid: ca7c216a-5141-4132-8193-102c181d2eba
ms.openlocfilehash: 905c84d801a27e588e2c539f987d6280aae7b994
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991059"
---
# <a name="routing-service"></a>Usługa routingu
Usługa routingu jest ogólny pośredniczącego protokołu SOAP, działającego jako router wiadomości. Podstawowe funkcje usług routingu jest możliwość przesyłania wiadomości, na podstawie zawartości wiadomości, co pozwala wiadomości były przekazywane do endpoint klienta, na podstawie wartości w wiadomości, w nagłówku lub w treści wiadomości.  
  
 <xref:System.ServiceModel.Routing.RoutingService> Jest implementowany jako usługi Windows Communication Foundation (WCF) w <xref:System.ServiceModel.Routing> przestrzeni nazw. Usługa routingu udostępnia jeden lub więcej punktów końcowych usługi, które odbierają wiadomości i następnie trasy każdy komunikat do punktów końcowych klienta na podstawie zawartości komunikatu. Usługa zapewnia następujące funkcje:  
  
- Routing oparty na zawartość  
  
    - Usługi agregacji  
  
    - Przechowywanie wersji usługi  
  
    - Priorytet routingu  
  
    - Dynamiczna konfiguracja  
  
- Mostkowanie protokołu  
  
- Przetwarzanie protokołu SOAP  
  
- Zaawansowana obsługa błędów  
  
- Punkty końcowe kopii zapasowej  
  
 Jest możliwość tworzenia pośredniczące usługa, która wykonuje co najmniej jedną z tych celów, często takie wdrożenie jest powiązany z konkretnego scenariusza lub rozwiązania i nie można łatwo zastosować nowych aplikacji.  
  
 Usługa routingu zapewnia ogólne, dynamiczną konfigurację, podłączanych pośredniczącego protokołu SOAP, jest zgodny z modelami usługi WCF i kanału, który umożliwia przeprowadzanie na podstawie zawartości routingu opartego na protokole SOAP komunikatów.  
  
> [!NOTE]
>  Usługa routingu aktualnie nie obsługuje routingu usług REST programu WCF.  Aby przekierować wywołania REST, należy rozważyć użycie <xref:System.Web.Routing> lub [Routing żądań aplikacji](https://go.microsoft.com/fwlink/?LinkId=164589).  
  
## <a name="content-based-routing"></a>Routing oparty na zawartość  
 Routing zawartości oparty na to zdolność do rozsyłania wiadomości, na podstawie co najmniej wartości zawartych w wiadomości. Usługa routingu sprawdza każdy komunikat i tras do docelowego punktu końcowego na podstawie treść wiadomości i logikę routingu, które można utworzyć. Routing zawartości oparty na stanowi podstawę dla agregacji usługi, przechowywanie wersji usługi i priorytet routingu.  
  
 Aby zaimplementować, routingu opartego na zawartości, usługa routingu opiera się na <xref:System.ServiceModel.Dispatcher.MessageFilter> implementacji, które są używane do pasuje do wartości określonej w wiadomościach przesłana. Jeśli **MessageFilter** dopasowania komunikatu, komunikat jest kierowany do docelowego punktu końcowego skojarzone z **MessageFilter**.  Filtry komunikatów są zgrupowane w tabelach filtru (<xref:System.ServiceModel.Routing.Configuration.FilterTableCollection>) do utworzenia złożonej logiki routingu. Na przykład filtr tabeli może zawierać pięć filtry wzajemnie się wykluczają komunikatów, które komunikaty można kierować do tylko jeden z pięciu docelowych punktów końcowych.  
  
 Usługa routingu umożliwia skonfigurowanie logikę, która jest używana do wykonywania, routingu opartego na zawartości, jak również dynamiczne aktualizowanie logikę routingu w czasie wykonywania.  
  
 Przez grupowanie komunikatów filtry do filtrowania tabel routingu logiki można skonstruować, który umożliwia obsługę wielu scenariuszy routingu, takich jak:  
  
- Usługi agregacji  
  
- Przechowywanie wersji usługi  
  
- Priorytet routingu  
  
- Dynamiczna konfiguracja  
  
 Aby uzyskać więcej informacji na informacje o filtrach wiadomości i tabel filtrów, zobacz [routingu wprowadzenie](../../../../docs/framework/wcf/feature-details/routing-introduction.md) i [filtry komunikatów](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
### <a name="service-aggregation"></a>Usługi agregacji  
 Przy użyciu routingu opartego na zawartości, należy udostępnić jeden punkt końcowy, który odbiera komunikaty z aplikacji klienckich zewnętrznych, a następnie przekierowuje każdy komunikat do odpowiedniego wewnętrznego punktu końcowego, na podstawie wartości w komunikacie. Jest to przydatne, oferują jednego określonego punktu końcowego dla wielu aplikacji zaplecza, a także prezentować jeden punkt końcowy aplikacji dla klientów podczas wyprowadzenie aplikacji do różnych usług.  
  
### <a name="service-versioning"></a>Przechowywanie wersji usługi  
 Podczas migracji do nowej wersji rozwiązania, może być konieczne Obsługa starej wersji równolegle do obsługi istniejących klientów. Często wymaga klientów łączących się z nowszej wersji należy użyć innego adresu podczas komunikowania się z rozwiązaniem. Usługa routingu umożliwia udostępnianie jeden punkt końcowy usługi służący obie wersje rozwiązania poprzez wiadomości routingu do odpowiedniego rozwiązania oparte na informacjach specyficznych dla wersji zawartego w wiadomości. Na przykład takich realizacji zobacz [How to: Przechowywanie wersji usługi](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md).  
  
### <a name="priority-routing"></a>Priorytet routingu  
 Podczas tworzenia usługi dla wielu klientów, może być Umowa dotycząca poziomu usług (SLA) z partnerami, niektóre wymagane przez wszystkie dane z tych partnerów, które mają być przetwarzane niezależnie od tego dla innych klientów. Za pomocą filtru, który wyszukuje informacje specyficzne dla klienta, zawarte w komunikacie, łatwo komunikaty można kierować do określonych partnerów do punktu końcowego, który został utworzony w celu spełnienie rządowych wymagań dotyczących umowy SLA.  
  
## <a name="dynamic-configuration"></a>Dynamiczna konfiguracja  
 Do obsługi systemów krytycznych dla działalności, którym wiadomości muszą być przetwarzane bez żadnych przerw w świadczeniu usługi, ważne jest, można zmodyfikować konfigurację składników w systemie w czasie wykonywania. Aby obsługiwać te potrzeby, udostępnia usługi routingu <xref:System.ServiceModel.IExtension%601> implementacji <xref:System.ServiceModel.Routing.RoutingExtension>, co umożliwia dynamiczne aktualizowanie konfiguracji usługa routingu w czasie wykonywania.  
  
 Aby uzyskać więcej informacji na temat dynamiczną konfigurację usługi Routing zobacz [routingu wprowadzenie](../../../../docs/framework/wcf/feature-details/routing-introduction.md).  
  
## <a name="protocol-bridging"></a>Mostkowanie protokołu  
 Jednym z wyzwań w scenariuszach pośredniczące jest wewnętrznych punktów końcowych może innego transportu lub niż punkt końcowy, który wiadomości są odbierane na, wymagania dotyczące wersji protokołu SOAP. Aby zapewnić obsługę tego scenariusza, usługa routingu może mostkować protokołów, w tym przetwarzanie komunikatu protokołu SOAP do <xref:System.ServiceModel.Channels.MessageVersion> wymagany przez punkty końcowe: docelowy. W ten sposób jeden protokół może służyć do komunikacji wewnętrznej, podczas gdy inny może służyć do komunikacji zewnętrznych.  
  
 Aby obsługiwać routing wiadomości między punktami końcowymi za pomocą innego transportu, usługa routingu używa powiązania dostarczane przez system, które umożliwiają usłudze zestawiania różnych protokołów. Występuje to automatycznie, gdy punkt końcowy usługi udostępniane przez usługę Routing używa protokołu innego niż punktów końcowych klienta, które komunikaty są kierowane do.  
  
## <a name="soap-processing"></a>Przetwarzanie protokołu SOAP  
 Typowym wymogiem routingu jest możliwość przesyłania wiadomości między punktami końcowymi z różnymi wymaganiami protokołu SOAP. W celu spełnienia tego wymagania, udostępnia usługi routingu <xref:System.ServiceModel.Routing.SoapProcessingBehavior> , automatycznie tworzy nową **element MessageVersion** spełnia wymagania docelowego punktu końcowego, zanim komunikat jest kierowany do niego. To zachowanie wzrasta, powstaje nowy **element MessageVersion** dla dowolnego komunikatu odpowiedzi przed zwróceniem jej do żądania aplikacji klienckiej, upewnij się, że **element MessageVersion** odpowiedzi jest zgodny z typem oryginalne żądanie.  
  
 Aby uzyskać więcej informacji na temat przetwarzania protokołu SOAP, zobacz [routingu wprowadzenie](../../../../docs/framework/wcf/feature-details/routing-introduction.md).  
  
## <a name="error-handling"></a>Obsługa błędów  
 W systemie składa się z usług rozproszonych, korzystających z komunikacji sieciowej jest ważne, aby upewnić się, że komunikacja w danym systemie są odporne na błędy przejściowe problemy z siecią.  Usługa routingu implementuje obsługę błędów, która umożliwia obsługę wielu scenariuszy awarii komunikacji, które w przeciwnym razie może to spowodować awarię usług.  
  
 Jeśli usługa routingu napotka <xref:System.ServiceModel.CommunicationException> podczas próby wykonania do wysyłania komunikatów, obsługa błędów będą miały miejsce.  Wyjątki te zwykle sygnalizuje Napotkano problem podczas próby skomunikowania się z punktem końcowym zdefiniowanych klienta, takich jak <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, lub <xref:System.ServiceModel.CommunicationObjectFaultedException>.  Kodu obsługi błędu zostanie też przechwytywać i podjął próbę podczas wysyłania **TimeoutException** problem wystąpi, który jest inny wspólnej wyjątek, który nie pochodzi od **communicationexception —**.  
  
 Aby uzyskać więcej informacji na temat obsługi błędów, zobacz [routingu wprowadzenie](../../../../docs/framework/wcf/feature-details/routing-introduction.md).  
  
## <a name="backup-endpoints"></a>Punkty końcowe kopii zapasowej  
 Oprócz miejsce docelowe punkty końcowe klienta skojarzonego z definicją filtru, każdy w tabeli filtru możesz również utworzyć listę kopii zapasowych punktów końcowych, które wiadomości będą kierowane do awarii transmisji. Jeśli wystąpi błąd, a listy kopii zapasowych jest zdefiniowany dla filtru zapisu, usługa routingu spróbuje wysłać wiadomość do pierwszego punktu końcowego zdefiniowanym na liście. Jeśli ta transmisji próba zakończy się niepowodzeniem, usługa spróbuj następnego punktu końcowego i kontynuować ten proces, dopóki nie zakończy się pomyślnie próby transmisji, zwróci błąd powiązane innych transmisji lub wszystkie punkty końcowe na liście kopii zapasowych zwróciły błąd transmisji.  
  
 Aby uzyskać więcej informacji na temat tworzenia kopii zapasowych punktów końcowych, zobacz [routingu wprowadzenie](../../../../docs/framework/wcf/feature-details/routing-introduction.md) i [filtry komunikatów](../../../../docs/framework/wcf/feature-details/message-filters.md).  
  
## <a name="streaming"></a>Przesyłanie strumieniowe  
 Usługa routingu może pomyślnie strumienia komunikatów, jeśli ustawisz powiązania do obsługi przesyłania strumieniowego.  Istnieją jednak niektóre warunki, na jakich komunikatów może być konieczne buforowane:  
  
- Multiemisji (bufor do tworzenia kopii dodatkowych komunikatów)  
  
- Tryb failover (buforu w przypadku, gdy wiadomości musi być wysyłana do kopii zapasowej)  
  
- System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly ma wartość false (bufor do przedstawienia MessageFilterTable przy użyciu elementu MessageBuffer tak, aby sprawdzić filtry treści)  
  
- Dynamiczna konfiguracja  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do routingu](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
- [Kontrakty routingu](../../../../docs/framework/wcf/feature-details/routing-contracts.md)
- [Filtry komunikatów](../../../../docs/framework/wcf/feature-details/message-filters.md)
