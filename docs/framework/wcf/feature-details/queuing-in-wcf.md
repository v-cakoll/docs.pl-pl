---
title: Tworzenie kolejek w programie WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e98d76ba-1acf-42cd-b137-0f8214661112
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 64a66b1ce04f6c644eef266fee1c89366f1fb707
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="queuing-in-wcf"></a>Tworzenie kolejek w programie WCF
W tej sekcji opisano sposób użycia komunikacji z obsługą kolejek w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="queues-as-a-wcf-transport-binding"></a>Powiązania transportu kolejki jako WCF  
 W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], określ umów co wymiany. Kontrakty są wymiany komunikatów zależne od firm lub specyficzne dla aplikacji. Mechanizm służący do wymiany wiadomości (lub "jak") jest określona w powiązaniach. Powiązania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hermetyzowanie szczegółowe informacje o wymianie wiadomości. Udostępniają pokrętła konfiguracji dla użytkownika kontrolować różne aspekty transportu lub protokół, który reprezentuje powiązania. Tworzenie kolejek w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest traktowany jak wszelkie inne powiązania transportu, czyli duże korzyści w wielu aplikacjach kolejkowania wiadomości. Obecnie wiele aplikacji kolejkowania wiadomości są zapisywane inaczej z innych zdalnego wywołania procedury (RPC) — styl aplikacji rozproszonych, dzięki czemu trudniej wykonaj i obsługa. Z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], styl pisania aplikacji rozproszonej jest znacznie takie same, co ułatwia wykonaj i konserwacji. Ponadto przez factoring limit mechanizmu programu exchange, niezależnie od logiki biznesowej, łatwiej skonfigurować transportu lub go zmienić bez wpływu na kodu określonych aplikacji. Na poniższym rysunku przedstawiono struktury usług WCF i klienta przy użyciu usługi MSMQ do ich przenoszenia.  
  
 ![Diagram aplikacji w kolejce](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "rozproszonych kolejki — rysunek")  
  
 Jak widać na poprzedniej ilustracji, klient i usługa muszą być zdefiniowane tylko aplikacji semantykę, oznacza to, gdy kontrakt i implementacja. Usługa umożliwia skonfigurowanie Zakolejkowane powiązanie odpowiednie ustawienia. Klient używa [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta do usługi i generowania pliku konfiguracji, który opisuje powiązania służące do wysyłania komunikatów do usługi. W związku z tym, aby wysłać wiadomość w kolejce, klient tworzy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, a następnie wywołuje operację. Powoduje to, że komunikat, który ma zostać wysłane do kolejki transmisji i przeniesienia uprawnień do kolejki docelowej. Złożonością komunikatu w kolejce są ukryte przed aplikacji, która wysyła i odbiera komunikaty.  
  
 Ostrzeżenia o kolejce wiąże w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obejmują:  
  
-   Wszystkie operacje usługi musi być jednokierunkowe, ponieważ powiązanie w kolejce domyślne [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie obsługuje komunikację dupleksową korzystanie z kolejek. Przykładowe komunikacja dwukierunkowa ([komunikacji dwustronny](../../../../docs/framework/wcf/samples/two-way-communication.md)) ilustruje sposób używania dwa kontrakty jednokierunkowe do zaimplementowania komunikację dupleksową korzystanie z kolejek.  
  
-   Aby wygenerować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta przy użyciu wymiany metadanych wymaga dodatkowy punkt końcowy HTTP w usłudze, dzięki czemu mogą być przeszukiwane bezpośrednio do generowania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta i uzyskać informacje o powiązaniu odpowiednio skonfigurować w kolejce komunikacji.  
  
-   Oparte na powiązanie umieszczonych w kolejce, dodatkowej konfiguracji poza [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest wymagana. Na przykład <xref:System.ServiceModel.NetMsmqBinding> klasy, która jest dostarczana razem z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wymaga skonfigurowania powiązań, a także skonfigurować migrację usługi kolejkowania komunikatów (MSMQ).  
  
 W poniższych sekcjach opisano określonych w kolejce powiązania dostarczane z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], które są oparte na usługi MSMQ.  
  
### <a name="msmq"></a>Usługa MSMQ  
 Transport z kolejką w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa usługi MSMQ do komunikacji z jej w kolejce.  
  
 Usługa MSMQ jest dostarczany jako opcjonalny składnik z systemem Windows i działa jako usługa NT. Zarejestrowaniu wiadomości do przesłania w kolejce transmisji i dostarczenie w kolejce docelowej. Menedżerami kolejki usługi MSMQ implementacji protokołu niezawodnych transferu komunikatów, dzięki czemu komunikaty nie zostaną utracone podczas transmisji. Protokół może być lokalny lub opartego na protokole SOAP, takich jak Reliable protokołu komunikatu (SRMP) protokołu SOAP.  
  
 W usłudze MSMQ kolejek można transakcyjnej lub nietransakcyjnej. Kolejką transakcyjną umożliwia komunikaty, aby przechwycić i dostarczane w transakcji i następnie trwale przechowywane w kolejce. Komunikaty wysyłane do kolejką transakcyjną są przekazywane tylko raz w kolejności. Kolejki nietransakcyjnej służy do wysyłania wiadomości jednocześnie nietrwałe i trwałe. Wiadomość wysłana do kolejki nietransakcyjnej nie zawiera żadnych gwarancji niezawodnej transferu; w związku z tym komunikaty mogą zostać utracone.  
  
 Kolejki usługi MSMQ mogą również chronione, za pomocą tożsamości systemu Windows, w zarejestrowany w usłudze katalogowej Active Directory. Podczas instalowania usługi MSMQ, należy zainstalować integracji usługi Active Directory, która wymaga komputera, jako część sieci domeny systemu Windows.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Usługa MSMQ, zobacz [usługi kolejkowania komunikatów instalowanie (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md).  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 [ \<NetMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) jest Zakolejkowane powiązanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zapewnia dwa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktów końcowych do komunikowania się przy użyciu usługi MSMQ. Wiązanie, w związku z tym udostępnia właściwości, które są specyficzne dla usługi MSMQ. Jednak nie wszystkie funkcje usługi MSMQ i właściwości są widoczne w `NetMsmqBinding`. CD `NetMsmqBinding` zaprojektowano z optymalny zestaw funkcji, które większość klientów stwierdzi, że wystarczające.  
  
 `NetMsmqBinding` Manifesty podstawowe koncepcje kolejkowania omówione w związku z tym daleko w formie właściwości na powiązania. Te właściwości, komunikują się z usługi MSMQ z kolei, jak przenieść i dostarczania komunikatów. Omówienie kategorii właściwości jest w poniższych sekcjach. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]Tematy dotyczące pojęć opisujących właściwości specyficzne dla bardziej całkowicie.  
  
#### <a name="exactlyonce-and-durable-properties"></a>ExactlyOnce i trwałe właściwości  
 `ExactlyOnce` i `Durable` właściwości mają wpływ na sposób wiadomości są przesyłane między kolejki:  
  
-   `ExactlyOnce`: Jeśli równa `true` (domyślnie) umieszczonych w kolejce kanał zapewnia, że komunikat, jeśli dostarczane, nie jest zduplikowany. Gwarantuje również, że komunikat nie zostaną utracone. Jeśli nie można dostarczyć wiadomości lub wiadomości do czasu wygaśnięcia wygasa przed wiadomości mogą być dostarczane, wiadomości nie powiodło się wraz z przyczyną niepowodzenia dostarczenia jest rejestrowana w kolejki utraconych wiadomości. Jeśli wartość `false`, zwrócony sprawia, że ramach działań zmierzających do transferowania wiadomości. W takim przypadku można opcjonalnie kolejki utraconych wiadomości.  
  
-   `Durable:`Jeśli wartość `true` (ustawienie domyślne), umieszczonych w kolejce kanał zapewnia, że usługa MSMQ przechowuje wiadomości trwale na dysku. W związku z tym jeżeli zatrzymać i uruchomić ponownie usługę MSMQ, wiadomości na dysku jest przenoszona do kolejki docelowej lub dostarczone do usługi. Jeśli wartość `false`, komunikaty są przechowywane w magazynie nietrwałe i zostaną utracone na zatrzymując i uruchamiając ponownie usługę MSMQ.  
  
 Aby uzyskać `ExactlyOnce` niezawodnej transfer MSMQ wymaga kolejki transakcyjnej. Ponadto usługi MSMQ wymaga transakcji można odczytać z kolejką transakcyjną. Tak, jeśli używasz `NetMsmqBinding`, należy pamiętać, że transakcja jest wymagana do wysyłania i odbierania wiadomości gdy `ExactlyOnce` ma ustawioną wartość `true`. Podobnie, MSMQ wymaga kolejki z systemem innym niż transakcyjnej dla zapewnienia optymalnych, takie jak kiedy `ExactlyOnce` jest `false` i nietrwałe obsługi wiadomości. W związku z tym podczas ustawiania `ExactlyOnce` do `false` lub trwałe do `false`, nie można wysyłać ani odbierać przy użyciu transakcji.  
  
> [!NOTE]
>  Upewnij się, czy prawidłowa kolejki (transakcyjna lub nietransakcyjna) został utworzony zgodnie z ustawieniami w powiązaniach. Jeśli `ExactlyOnce` jest `true`, użyj kolejką transakcyjną; w przeciwnym razie użyj kolejki nietransakcyjnej.  
  
#### <a name="dead-letter-queue-properties"></a>Właściwości kolejki utraconych wiadomości  
 Kolejki utraconych wiadomości jest używany do przechowywania komunikatów, które nie są dostawy. Użytkownik może zapisać kompensacyjnych logikę, która odczytuje wiadomości z kolejki utraconych wiadomości.  
  
 Wiele systemów kolejkowania Podaj kolejki utraconych wiadomości całego systemu. Usługa MSMQ zapewnia systemowe nietransakcyjnej kolejki utraconych wiadomości dla wiadomości, które nie są dostawy do kolejki nietransakcyjnej i systemowe transakcyjnej kolejki utraconych wiadomości dla wiadomości, które nie są dostawy do kolejek transakcyjnych.  
  
 Jeśli wielu klientów, wysyłanie komunikatów do kolejki inny element docelowy korzystają usługi MSMQ, wszystkie wiadomości wysyłane przez klientów przejdź do tej samej kolejki utraconych wiadomości. Nie zawsze jest preferowanym. Dla lepszej izolacji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] i usługi MSMQ w [!INCLUDE[wv](../../../../includes/wv-md.md)] Podaj niestandardowej kolejki utraconych wiadomości (lub kolejki utraconych wiadomości specyficzne dla aplikacji) czy użytkownika można określić do przechowywania komunikatów, które nie są dostawy. W związku z tym różnych klientów nie mają tej samej kolejki utraconych wiadomości.  
  
 Powiązanie ma dwie właściwości odsetek:  
  
-   `DeadLetterQueue`: Ta właściwość jest wyliczeniem, która wskazuje, czy kolejka utraconych wiadomości jest wymagane. Wyliczenie zawiera także rodzaj kolejki utraconych wiadomości, jeśli wymagane jest jeden. Wartości są `None`, `System`, i `Custom`. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Interpretacja te właściwości, zobacz [przy użyciu kolejki utraconych wiadomości do obsługi błędów transferu](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
  
-   `CustomDeadLetterQueue`: Ta właściwość jest adresem identyfikator URI (Uniform Resource) specyficzne dla aplikacji kolejki utraconych wiadomości. Jest to wymagane, jeśli `DeadLetterQueue`.`Custom` zostanie wybrany.  
  
#### <a name="poison-message-handling-properties"></a>Właściwości Obsługa komunikatów zanieczyszczonych  
 Usługa odczytuje wiadomości z kolejki docelowej, w ramach transakcji, usługa może zakończyć się niepowodzeniem przetworzyć komunikatu z różnych przyczyn. Komunikat jest następnie przywracane do kolejki, aby ponownie odczytać. Na wypadek wiadomości, które nie są często zestaw poison komunikat — Obsługa właściwości można skonfigurować w powiązaniu. Istnieją cztery właściwości: `ReceiveRetryCount`, `MaxRetryCycles`, `RetryCycleDelay`, i `ReceiveErrorHandling`. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]te właściwości, zobacz [Obsługa komunikatów zanieczyszczonych](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
#### <a name="security-properties"></a>Właściwości zabezpieczeń  
 MSMQ udostępnia własny model zabezpieczeń, takie jak listy kontroli dostępu (ACL) w kolejce lub wysyłania uwierzytelnione komunikaty. `NetMsmqBinding` Opisuje te właściwości zabezpieczeń jako część jej ustawienia zabezpieczeń transportu. Istnieją dwie właściwości powiązanie dla zabezpieczeń transportu: `MsmqAuthenticationMode` i `MsmqProtectionLevel`. Ustawienia te właściwości są zależne od konfiguracji usługi MSMQ. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Zabezpieczanie komunikatów za pomocą zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
 Oprócz zabezpieczeń transportu korzystanie z zabezpieczeń komunikatów być zabezpieczona rzeczywiste samej wiadomości SOAP. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Korzystanie z zabezpieczeń wiadomości](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md).  
  
 `MsmqTransportSecurity`udostępnia również dwie właściwości `MsmqEncryptionAlgorithm` i `MsmqHashAlgorithm`. Są to wyliczenia różne algorytmy, aby wybrać szyfrowania transferu kolejki do kolejki komunikatów i tworzenia skrótów podpisów.  
  
#### <a name="other-properties"></a>Inne właściwości  
 Oprócz powyższych właściwości innych właściwości specyficzne dla usługi MSMQ w include powiązania:  
  
-   `UseSourceJournal`: Właściwość, aby wskazać, że źródłowa jest włączona. Źródłowa jest funkcją usługi MSMQ, który śledzi wiadomości, które zostały pomyślnie przekazane z kolejki transmisji.  
  
-   `UseMsmqTracing`: Właściwość wskazująca, czy usługa MSMQ śledzenia jest włączona. Śledzenie MSMQ wysyła komunikaty raport do kolejki raportu, zawsze pozostawia lub nadejściu wiadomości we komputer, na którym menedżera kolejki usługi MSMQ.  
  
-   `QueueTransferProtocol`: Wyliczenie protokół do użycia podczas transferu wiadomości do kolejki do kolejki. Usługa MSMQ implementuje protokół transmisji w trybie macierzystym kolejki do kolejki i opartego na protokole SOAP protokołu SOAP Reliable Messaging Protocol (SRMP). SRMP jest używany podczas transferów kolejki do kolejki przy użyciu transportu HTTP. Bezpieczne SRMP jest używany podczas transferów kolejki do kolejki przy użyciu protokołu HTTPS.  
  
-   `UseActiveDirectory`: Wartość logiczna wskazująca, czy usługi Active Directory muszą być używane do rozpoznawania adresów kolejki. Domyślnie jest wyłączona. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Punktów końcowych i adresowanie kolejki usługi service](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 `MsmqIntegrationBinding` Jest używany, gdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktu końcowego do komunikowania się z istniejącej aplikacji usługi MSMQ napisana C, C++, COM lub System.Messaging interfejsów API.  
  
 Właściwości powiązania są takie same, jak w przypadku `NetMsmqBinding`. Jednakże Zastosuj następujące różnice:  
  
-   Kontrakt operacji dla `MsmqIntegrationBinding` jest ograniczona do podjęcia pojedynczy parametr typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> gdzie parametr typu jest typem treści.  
  
-   Większość właściwości macierzystych wiadomości usługi MSMQ są widoczne w <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> do użycia.  
  
-   Do serializacji i deserializacji treści wiadomości, znajdują się serializatorów, takich jak XML i ActiveX.  
  
### <a name="sample-code"></a>Przykładowy kod  
 Aby uzyskać instrukcje krok po kroku dotyczące programowania WCF usług używających usługi MSMQ, zobacz następujące tematy:  
  
-   [Porady: wymiana komunikatów z punktami końcowymi WCF i aplikacji usługi kolejkowania komunikatów](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
  
-   [Porady: wymiana komunikatów z punktami końcowymi WCF umieszczonych w kolejce](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
  
 Kompletny kod przykładowy pokazujący korzystanie z usługi MSMQ w programie WCF, zobacz następujące tematy:  
  
-   [Transakcyjne powiązanie MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
  
-   [Komunikacja za pomocą nietrwałych kolejek](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
  
-   [Kolejki utraconych wiadomości](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
  
-   [Sesje i kolejki](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
  
-   [Komunikacja dwukierunkowa](../../../../docs/framework/wcf/samples/two-way-communication.md)  
  
-   [Nietransakcyjnego przetwarzanie wsadowe](../../../../docs/framework/wcf/samples/transacted-batching.md)  
  
-   [SRMP](../../../../docs/framework/wcf/samples/srmp.md)  
  
-   [Zabezpieczenia komunikatów w ramach usługi kolejkowania komunikatów](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty końcowe usługi i adresowanie kolejki](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)  
 [Sieć Web hostująca aplikację Zakolejkowaną](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
