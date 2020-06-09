---
title: Usługa routingu
ms.date: 03/30/2017
ms.assetid: ca7c216a-5141-4132-8193-102c181d2eba
ms.openlocfilehash: 833c824e17d70a982a2f7bb13fe388b9b2b0dec1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590452"
---
# <a name="routing-service"></a>Usługa routingu

Usługa routingu to ogólna pośrednik protokołu SOAP, który działa jako router komunikatów. Podstawowe funkcje usługi routingu umożliwiają kierowanie komunikatów na podstawie zawartości komunikatów, co umożliwia przekazywanie komunikatów do punktu końcowego klienta na podstawie wartości w wiadomości, w nagłówku lub w treści wiadomości.

Funkcja <xref:System.ServiceModel.Routing.RoutingService> jest zaimplementowana jako usługa Windows Communication Foundation (WCF) w <xref:System.ServiceModel.Routing> przestrzeni nazw. Usługa routingu udostępnia jeden lub więcej punktów końcowych usługi, które odbierają komunikaty, a następnie kieruje każdy komunikat do co najmniej jednego punktu końcowego klienta na podstawie zawartości komunikatu. Usługa udostępnia następujące funkcje:

- Routing oparty na zawartości

  - Agregacja usług

  - Przechowywanie wersji usługi

  - Routing oparty na priorytetach

  - Konfiguracja dynamiczna

- Mostkowanie protokołów

- Przetwarzanie SOAP

- Zaawansowana obsługa błędów

- Punkty końcowe kopii zapasowej

Chociaż istnieje możliwość utworzenia usługi pośredniczącej, która wykonuje co najmniej jeden z tych celów, często taka implementacja jest związana z konkretnym scenariuszem lub rozwiązaniem i nie można jej łatwo zastosować do nowych aplikacji.

Usługa routingu zapewnia ogólne, dynamicznie konfigurowalne, podłączane elementy pośredniczące protokołu SOAP, które są zgodne z modelami usługi WCF i kanałów oraz umożliwiają kierowanie na podstawie zawartości komunikatów opartych na protokole SOAP.

> [!NOTE]
> Usługa routingu nie obsługuje obecnie routingu usług REST WCF.  Aby kierować wywołania REST, należy rozważyć użycie <xref:System.Web.Routing> lub [Routing żądań aplikacji](https://go.microsoft.com/fwlink/?LinkId=164589).

## <a name="content-based-routing"></a>Routing oparty na zawartości

Funkcja routingu opartego na zawartości umożliwia kierowanie komunikatów na podstawie co najmniej jednej wartości zawartej w komunikacie. Usługa routingu sprawdza każdy komunikat i kieruje go do docelowego punktu końcowego w oparciu o zawartość wiadomości i utworzoną logikę routingu. Routing oparty na zawartości stanowi podstawę do agregacji usług, przechowywania wersji usług i routingu priorytetów.

W celu zaimplementowania routingu opartego na zawartości Usługa routingu opiera się na <xref:System.ServiceModel.Dispatcher.MessageFilter> implementacjach, które są używane do dopasowywania określonych wartości w wiadomościach do rozesłania. Jeśli **MessageFilter** dopasowuje komunikat, komunikat jest kierowany do docelowego punktu końcowego skojarzonego z **MessageFilter**.  Filtry komunikatów są pogrupowane w tabele filtrów ( <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection> ) w celu skonstruowania złożonej logiki routingu. Na przykład tabela filtrów może zawierać pięć wzajemnie wykluczających się filtrów komunikatów, które powodują kierowanie komunikatów do jednego z pięciu docelowych punktów końcowych.

Usługa routingu umożliwia skonfigurowanie logiki, która jest używana do przeprowadzania routingu opartego na zawartości, a także dynamiczne aktualizowanie logiki routingu w czasie wykonywania.

Za pomocą grupowania filtrów komunikatów w tabelach filtrów można utworzyć logikę routingu, która umożliwia obsługę wielu scenariuszy routingu, takich jak:

- Agregacja usług

- Przechowywanie wersji usługi

- Routing oparty na priorytetach

- Konfiguracja dynamiczna

Aby uzyskać więcej informacji o filtrach komunikatów i tabelach filtrów, zobacz [wprowadzenie routingu](routing-introduction.md) i [filtry komunikatów](message-filters.md).

### <a name="service-aggregation"></a>Agregacja usług

Korzystając z routingu opartego na zawartości, można uwidocznić jeden punkt końcowy, który odbiera wiadomości z zewnętrznych aplikacji klienckich, a następnie kieruje każdy komunikat do odpowiedniego wewnętrznego punktu końcowego na podstawie wartości w komunikacie. Jest to przydatne do oferowania jednego określonego punktu końcowego dla różnych aplikacji zaplecza, a także do prezentowania jednego punktu końcowego aplikacji klientom przy jednoczesnym obsłużeniu aplikacji w różnych usługach.

### <a name="service-versioning"></a>Przechowywanie wersji usługi

W przypadku migrowania do nowej wersji rozwiązania może być konieczne zachowanie starszej wersji równolegle, aby zapewnić istniejącym klientom. Często wymaga się, aby klienci łączący się z nowszą wersją muszą używać innego adresu podczas komunikowania się z rozwiązaniem. Usługa routingu umożliwia uwidocznienie jednego punktu końcowego usługi, który obsługuje obie wersje rozwiązania przez kierowanie komunikatów do odpowiedniego rozwiązania na podstawie informacji specyficznych dla wersji zawartych w komunikacie. Przykład takiej implementacji można znaleźć w temacie [How to: Versioning Service](how-to-service-versioning.md).

### <a name="priority-routing"></a>Priorytetowe kierowanie

W przypadku świadczenia usługi dla wielu klientów może istnieć umowa dotycząca poziomu usług (SLA) z niektórymi partnerami, którzy muszą przetwarzać wszystkie dane od tych partnerów niezależnie od innych klientów. Korzystając z filtru, który wyszukuje informacje specyficzne dla klienta zawarte w komunikacie, można łatwo kierować komunikaty od określonych partnerów do punktu końcowego, który został utworzony w celu spełnienia wymagań umowy SLA.

## <a name="dynamic-configuration"></a>Konfiguracja dynamiczna

Aby obsługiwać systemy o znaczeniu krytycznym, w przypadku których komunikaty muszą być przetwarzane bez przerw w świadczeniu usług, należy koniecznie zmodyfikować konfigurację składników w systemie w czasie wykonywania. Aby to umożliwić, usługa routingu udostępnia <xref:System.ServiceModel.IExtension%601> implementację, <xref:System.ServiceModel.Routing.RoutingExtension> która umożliwia dynamiczne aktualizowanie konfiguracji usługi routingu w czasie wykonywania.

Aby uzyskać więcej informacji na temat dynamicznej konfiguracji usługi routingu, zobacz [wprowadzenie do routingu](routing-introduction.md).

## <a name="protocol-bridging"></a>Mostkowanie protokołów

Jednym z wyzwań w scenariuszach pośrednich jest to, że wewnętrzne punkty końcowe mogą mieć różne wymagania dotyczące wersji transportu lub protokołu SOAP niż punkt końcowy, w którym są odbierane komunikaty. Aby obsłużyć ten scenariusz, usługa routingu może mostkować protokoły, w tym przetwarzanie komunikatu protokołu SOAP do <xref:System.ServiceModel.Channels.MessageVersion> wymaganych przez docelowe punkty końcowe. W ten sposób jeden protokół może być używany do komunikacji wewnętrznej, podczas gdy inna może być używana do komunikacji zewnętrznej.

Aby zapewnić obsługę routingu komunikatów między punktami końcowymi z różnymi transportami, usługa routingu używa powiązań dostarczonych przez system, które umożliwiają usłudze łączenie się z niepodobnymi protokołami. Jest to wykonywane automatycznie, gdy punkt końcowy usługi udostępniany przez usługę routingu używa innego protokołu niż punkty końcowe, do których są kierowane komunikaty.

## <a name="soap-processing"></a>Przetwarzanie SOAP

Typowym wymaganiem routingu jest możliwość kierowania komunikatów między punktami końcowymi z różnymi wymaganiami protokołu SOAP. Aby zapewnić obsługę tego wymagania, usługa routingu zapewnia, <xref:System.ServiceModel.Routing.SoapProcessingBehavior> że program automatycznie tworzy nową wartość **MessageVersion** , która spełnia wymagania docelowego punktu końcowego, zanim komunikat zostanie rozesłany do niego. To zachowanie powoduje także utworzenie nowego elementu **MessageVersion** dla dowolnego komunikatu odpowiedzi przed zwróceniem go do żądającej aplikacji klienta, aby upewnić się, że element **MessageVersion** odpowiedzi jest zgodny z oryginalnym żądaniem.

Aby uzyskać więcej informacji na temat przetwarzania protokołu SOAP, zobacz [wprowadzenie do routingu](routing-introduction.md).

## <a name="error-handling"></a>Obsługa błędów

W systemie złożonym z usług rozproszonych, które opierają się na komunikacji sieciowej, należy upewnić się, że komunikacja w systemie jest odporna na awarie sieci.  Usługa routingu implementuje obsługę błędów, która umożliwia obsługę wielu scenariuszy błędów komunikacji, które mogłyby spowodować awarię usługi.

Jeśli usługa routingu napotyka <xref:System.ServiceModel.CommunicationException> błąd podczas próby wysłania wiadomości, zostanie przeprowadzona obsługa błędów.  Te wyjątki zwykle wskazują, że wystąpił problem podczas próby komunikowania się ze zdefiniowanym punktem końcowym klienta, na przykład <xref:System.ServiceModel.EndpointNotFoundException> , <xref:System.ServiceModel.ServerTooBusyException> lub <xref:System.ServiceModel.CommunicationObjectFaultedException> .  Kod obsługi błędu również przechwytuje i próbuje ponowić próbę wysłania, gdy wystąpi wyjątek **timeout** , który jest innym typowym wyjątkiem, który nie pochodzi od **CommunicationException**.

Aby uzyskać więcej informacji na temat obsługi błędów, zobacz [wprowadzenie routingu](routing-introduction.md).

## <a name="backup-endpoints"></a>Punkty końcowe kopii zapasowej

Poza docelowymi punktami końcowymi skojarzonymi z każdą definicją filtru w tabeli filtrów można także utworzyć listę punktów końcowych kopii zapasowych, do których zostanie rozesłany komunikat w przypadku niepowodzenia transmisji. W przypadku wystąpienia błędu i zdefiniowania listy kopii zapasowych dla wpisu filtru usługa routingu podejmie próbę wysłania komunikatu do pierwszego punktu końcowego zdefiniowanego na liście. Jeśli ta próba transmisji nie powiedzie się, usługa podejmie próbę następnego punktu końcowego i kontynuuje ten proces do momentu pomyślnej próby transmisji, zwróci błąd związany z nietransmisjami lub wszystkie punkty końcowe na liście kopii zapasowych zwróciły błąd transmisji.

Aby uzyskać więcej informacji na temat punktów końcowych kopii zapasowych, zobacz [wprowadzenie routingu](routing-introduction.md) i [filtry komunikatów](message-filters.md).

## <a name="streaming"></a>Przesyłanie strumieniowe

Usługa routingu może pomyślnie przesyłać strumieniowo komunikaty w przypadku ustawienia powiązania do obsługi przesyłania strumieniowego.  Istnieją jednak pewne warunki, w których komunikaty mogą być niezbędne do buforowania:

- Multiemisja (bufor w celu utworzenia dodatkowych kopii komunikatów)

- Tryb failover (bufor w przypadku, gdy wiadomość musi zostać wysłana do kopii zapasowej)

- System. ServiceModel. Routing. zastosowano. RouteOnHeadersOnly ma wartość false (bufor, aby przedstawić obiektem za pomocą Element MessageBuffer, tak aby filtry mogły zbadać treść)

- Konfiguracja dynamiczna

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do routingu](routing-introduction.md)
- [Kontrakty routingu](routing-contracts.md)
- [Filtry komunikatów](message-filters.md)
