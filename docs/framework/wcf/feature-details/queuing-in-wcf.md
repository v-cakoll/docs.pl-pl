---
title: Tworzenie kolejek w programie WCF
ms.date: 03/30/2017
ms.assetid: e98d76ba-1acf-42cd-b137-0f8214661112
ms.openlocfilehash: c390970d66e442eb413d238691896608dcf27e03
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64643509"
---
# <a name="queuing-in-wcf"></a>Tworzenie kolejek w programie WCF
W tej sekcji opisano sposób użycia komunikacji z obsługą kolejek w Windows Communication Foundation (WCF).  
  
## <a name="queues-as-a-wcf-transport-binding"></a>Kolejki jako WCF transportu powiązania  
 W WCF — umowy Określ, co wymianie. Kontrakty są wymianę komunikatów zależnych od firm lub specyficzne dla aplikacji. Mechanizm służący do wymiany wiadomości (lub "jak") jest określona w powiązaniach. Powiązania WCF hermetyzować szczegółowe informacje o wymianie wiadomości. Eksponowanie pokrętła konfiguracji dla użytkownika kontrolować różne aspekty transportu lub protokół, który reprezentuje powiązania. Usługa kolejkowania w programie WCF jest traktowany jak inne powiązania transportu, która jest dużą zaletą dla wielu aplikacji usługi kolejkowania. Dzisiaj wiele aplikacji kolejkowania są zapisywane inaczej od innych zdalnego wywołania procedury (RPC)-style aplikacji rozproszonych, co utrudnia stosować i obsługa. Za pomocą usługi WCF styl pisania aplikacji rozproszonej jest bardzo podobne do, ułatwiając stosować i obsługa. Ponadto, uwzględniając się mechanizm programu exchange, niezależnie od logiki biznesowej, łatwiej jest skonfigurować transportu lub go zmienić bez wpływu na kod określonych aplikacji. Na poniższym rysunku przedstawiono strukturę usługi i klienta WCF przy użyciu usługi MSMQ jako transportu.  
  
 ![Diagram aplikacji w kolejce](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "rozproszonych kolejka rysunek")  
  
 Jak widać na poprzednim rysunku, klient i usługa należy zdefiniować tylko aplikacji semantykę, oznacza to, gdy kontrakt i implementacja. Usługa umożliwia skonfigurowanie Zakolejkowane powiązanie odpowiednie ustawienia. Klient używa [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) Generowanie klienta programu WCF do usługi oraz generowanie pliku konfiguracji, który opisuje powiązania do użycia, aby wysyłać komunikaty do usługi. W związku z tym aby wysłać wiadomość w kolejce, klient tworzy klienta programu WCF i wywołuje operację. Powoduje to, że komunikat, który ma być wysyłany do kolejki transmisji i przeniesiona do kolejki docelowej. Złożoności komunikacji z obsługą kolejek są ukryte przed aplikacji, która wysyła i odbiera wiadomości.  
  
 Ostrzeżenia dotyczące Zakolejkowane powiązanie w usłudze WCF obejmują:  
  
- Wszystkie usługi, musi być jednokierunkowe operacji, ponieważ domyślnie umieszczane w kolejce powiązanie w usłudze WCF nie obsługuje komunikację dupleksową przy użyciu funkcji kolejek. Przykładowe komunikacja dwukierunkowa ([komunikacji dwustronny](../../../../docs/framework/wcf/samples/two-way-communication.md)) pokazano, jak wdrożyć paradygmacie komunikacji przy użyciu funkcji kolejek za pomocą kontraktów jednokierunkowych dwa.  
  
- Do generowania WCF klienta za pomocą wymiany metadanych wymaga dodatkowego punktu końcowego HTTP usługi mogą być wyszukiwane w bezpośrednio do generowania klienta WCF i uzyskać informacje o powiązaniu, aby odpowiednio skonfigurować komunikacji z obsługą kolejek.  
  
- Oparty na umieszczonych w kolejce powiązania, dodatkowe poza WCF jest wymagana konfiguracja. Na przykład <xref:System.ServiceModel.NetMsmqBinding> klasy, który jest dostarczany z programem WCF, musisz skonfigurować powiązania, a także nieznacznego skonfigurowania usługi kolejkowania komunikatów (MSMQ).  
  
 W poniższych sekcjach opisano określonych umieszczonych w kolejce powiązania dostarczane z programem WCF, które są oparte na usłudze MSMQ.  
  
### <a name="msmq"></a>Usługa MSMQ  
 Transport umieszczonych w kolejce w programie WCF używa usługi MSMQ komunikacie w kolejce.  
  
 Usługa MSMQ jest dostarczany jako opcjonalny składnik z Windows i działa jako usługa NT. Przechwytuje wiadomości do przesłania w kolejce transmisji i dostarczania w kolejce docelowej. Menedżerami kolejki usługi MSMQ zaimplementować protokół transferu komunikatów w niezawodny, dzięki czemu komunikaty nie zostaną utracone podczas transmisji. Protokół może być lokalny lub opartego na protokole SOAP, takich jak Reliable protokołu komunikatu (SRMP) protokołu SOAP.  
  
 W usłudze MSMQ kolejki może być transakcyjna lub nietransakcyjnej. Kolejka transakcyjna pozwala być przechwytywane i dostarczane w ramach transakcji i następnie trwale przechowywane w kolejce. Wiadomości wysłanych do kolejki transakcyjne są przesyłane dokładnie jeden raz w kolejności. Kolejka nietransakcyjna służy do wysyłania komunikatów trwałe i nietrwałe. Komunikat wysyłany do kolejki nietransakcyjnej nie zawiera żadnych gwarancji niezawodne przesyłanie; w związku z tym komunikaty mogą zostać utracone.  
  
 Kolejki usługi MSMQ również mogą być chronione przy użyciu tożsamości Windows zarejestrowanych przy użyciu usługi katalogowej Active Directory. Podczas instalowania usługi MSMQ, można zainstalować integracji usługi Active Directory, która wymaga komputera jako część sieci z domeną Windows.  
  
 Aby uzyskać więcej informacji na temat usługi MSMQ, zobacz [instalowanie komunikatów usługi kolejkowania wiadomości (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md).  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 [ \<NetMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) jest Zakolejkowane powiązanie WCF zapewnia dwa punktami końcowymi programu WCF do komunikowania się za pomocą usługi MSMQ. Wiązanie, w związku z tym, udostępnia właściwości, które są specyficzne dla usługi MSMQ. Jednak nie wszystkie funkcje usługi MSMQ i właściwości, które są widoczne w `NetMsmqBinding`. Kompaktowania `NetMsmqBinding` zaprojektowano z optymalny zestaw zasobów wystąpień funkcji, które większość klientów powinien znajdować się wystarczające.  
  
 `NetMsmqBinding` Manifesty podstawowe koncepcje kolejkowania na powiązania, a następnie omówiono tej pory w formie właściwości. Te właściwości, z kolei komunikują się do usługi MSMQ jak przenieść i dostarczanie komunikatów. Dyskusję na temat kategorii właściwości znajduje się w poniższych sekcjach. Aby uzyskać więcej informacji zobacz koncepcyjne tematy, które opisują konkretne właściwości więcej całkowicie.  
  
#### <a name="exactlyonce-and-durable-properties"></a>ExactlyOnce i trwałe właściwości  
 `ExactlyOnce` i `Durable` właściwości wpływają na sposób przekazywania komunikatów pomiędzy kolejki:  
  
- `ExactlyOnce`: Po ustawieniu `true` (ustawienie domyślne), zwrócony gwarantuje, że komunikat, jeśli dostarczony, nie jest zduplikowany. Gwarantuje również, że komunikat nie zostanie utracony. Jeśli nie można dostarczyć komunikatu lub komunikat do czasu na żywo wygaśnie przed wiadomości, które mogą być dostarczane, nie powiodło się komunikat i odtworzy dostarczania Przyczyna niepowodzenia jest rejestrowana w kolejki utraconych wiadomości. Po ustawieniu `false`, zwrócony sprawia, że zmierzających do transferu wiadomości. W takim przypadku możesz opcjonalnie wybrać kolejki utraconych wiadomości.  
  
- `Durable:` Po ustawieniu `true` (ustawienie domyślne), zwrócony gwarantuje, że usługi MSMQ przechowuje komunikat trwale na dysku. W związku z tym jeśli usługa MSMQ udało się zatrzymać i uruchomić ponownie, wiadomości na dysku jest przeniesiona do kolejki docelowej lub dostarczane do usługi. Po ustawieniu `false`, komunikaty są przechowywane w magazynie volatile i zostaną utracone na zatrzymanie i ponowne uruchomienie usługi MSMQ.  
  
 Aby uzyskać `ExactlyOnce` transferu niezawodnej usługi MSMQ wymaga kolejki transakcyjnej. Ponadto usługi MSMQ wymaga transakcji można odczytać z kolejką transakcyjną. W efekcie zastosowania `NetMsmqBinding`, należy pamiętać, że transakcja jest wymagany do wysyłania i odbierania komunikatów podczas `ExactlyOnce` ustawiono `true`. Podobnie, usługa MSMQ wymaga się nietransakcyjnej dla zapewnienia optymalnych, takie jak czas w kolejce `ExactlyOnce` jest `false` i volatile komunikatów. W związku z tym podczas ustawiania `ExactlyOnce` do `false` lub trwałe do `false`, użytkownik nie może wysłać lub odebrać, przy użyciu transakcji.  
  
> [!NOTE]
>  Upewnij się, czy poprawny kolejki (transakcyjna lub nietransakcyjna) został utworzony zgodnie z ustawieniami w powiązaniach. Jeśli `ExactlyOnce` jest `true`, użyj kolejkę transakcyjną; w przeciwnym razie użyj nietransakcyjnej kolejki.  
  
#### <a name="dead-letter-queue-properties"></a>Właściwości kolejki utraconych wiadomości  
 Kolejki utraconych wiadomości jest używany do przechowywania komunikatów, które nie spełniają dostarczania. Użytkownik może zapisać logiki wyrównującej, która odczytuje komunikaty z kolejki utraconych wiadomości.  
  
 Wiele systemów kolejkowania zapewnia kolejki utraconych wiadomości całego systemu. Usługi MSMQ zapewnia systemowe nietransakcyjnej kolejki utraconych wiadomości dla wiadomości, które się nie powieść dostarczania nietransakcyjnej kolejkach i systemowe transakcyjnej kolejki utraconych wiadomości dla wiadomości, które nie spełniają dostarczania do kolejek transakcyjnych.  
  
 Jeśli wielu klientów, wysyłanie komunikatów do kolejki inną docelową udostępniają usługi MSMQ, wszystkie komunikaty wysyłane przez klientów przejdź do tej samej kolejki utraconych wiadomości. Nie zawsze jest to pożądane. Dla lepszej izolacji, WCF i usługi MSMQ w [!INCLUDE[wv](../../../../includes/wv-md.md)] podać niestandardowy kolejki utraconych wiadomości (lub kolejki utraconych wiadomości specyficzne dla aplikacji), użytkownik może określić do przechowywania komunikatów, które nie spełniają dostarczania. W związku z tym różni klienci nie korzystają z tej samej kolejki utraconych wiadomości.  
  
 Powiązanie ma dwie właściwości zainteresowania:  
  
- `DeadLetterQueue`: Ta właściwość jest wyliczeniem, która wskazuje, czy kolejka utraconych wiadomości jest wymagane. Wyliczenie zawiera także rodzaj kolejki utraconych wiadomości, jeśli wymagana jest jeden. Wartości są `None`, `System`, i `Custom`. Aby uzyskać więcej informacji na temat interpretacji tych właściwości, zobacz [przy użyciu kolejki utraconych wiadomości, do obsługi błędów transferu](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
  
- `CustomDeadLetterQueue`: Ta właściwość jest adresem identyfikator (URI) kolejki utraconych wiadomości specyficzne dla aplikacji. Jest to wymagane, jeśli `DeadLetterQueue`.`Custom` jest wybierany.  
  
#### <a name="poison-message-handling-properties"></a>Właściwości Obsługa komunikatów zanieczyszczonych  
 Usługa odczytuje komunikaty z kolejki docelowej, w ramach transakcji, usługa może zakończyć się niepowodzeniem przetworzyć komunikatu z różnych powodów. Komunikat jest następnie odłożyć do kolejki, aby ponownie odczytać. Aby poradzić sobie z wiadomości, które nie są regularnie, zbiór Obsługa komunikatów poison właściwości można skonfigurować w powiązaniu. Istnieją cztery właściwości: `ReceiveRetryCount`, `MaxRetryCycles`, `RetryCycleDelay`, i `ReceiveErrorHandling`. Aby uzyskać więcej informacji o tych właściwościach, zobacz [Obsługa komunikatów zanieczyszczonych](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
#### <a name="security-properties"></a>Właściwości zabezpieczeń  
 Usługa MSMQ udostępnia własny model zabezpieczeń, takie jak listy kontroli dostępu (ACL) w kolejce lub wysyłania uwierzytelnione komunikaty. `NetMsmqBinding` Udostępnia te właściwości zabezpieczeń jako część jej ustawienia zabezpieczeń transportu. Istnieją dwie właściwości powiązanie dla zabezpieczeń transportu: `MsmqAuthenticationMode` i `MsmqProtectionLevel`. Ustawienia w ramach tych właściwości zależą od tego, jak usługa MSMQ jest skonfigurowana. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie komunikatów za pomocą zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
 Oprócz zabezpieczeń transportu rzeczywiste samej wiadomości protokołu SOAP mogą być chronione, korzystanie z zabezpieczeń komunikatów. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie komunikatów za pomocą zabezpieczeń wiadomości](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md).  
  
 `MsmqTransportSecurity` udostępnia również dwie właściwości `MsmqEncryptionAlgorithm` i `MsmqHashAlgorithm`. Są to wyliczenia różnych algorytmów szyfrowania transferu kolejki do kolejki komunikatów i wyznaczania wartości skrótu podpisów.  
  
#### <a name="other-properties"></a>Inne właściwości  
 Oprócz poprzedniego właściwości inne właściwości specyficzne dla usługi MSMQ ujawnione podczas dołączania powiązania:  
  
- `UseSourceJournal`: Właściwości, aby wskazać, że źródłowa jest wyłączona. Źródłowa to funkcja usługi MSMQ, która przechowuje informacje o wiadomości, które zostały pomyślnie przekazane z kolejki transmisji.  
  
- `UseMsmqTracing`: Właściwości, aby wskazać, czy śledzenie usługi MSMQ jest włączona. Śledzenie usługi MSMQ wysyła komunikaty raportu do kolejki raportu, za każdym razem wiadomości pozostawia lub dociera komputer, na którym Menedżer kolejki usługi MSMQ.  
  
- `QueueTransferProtocol`: Wyliczenie protokół do użycia dla transferów kolejki do kolejki komunikatów. Usługa MSMQ implementuje protokół transmisji w trybie macierzystym kolejki do kolejki i opartego na protokole SOAP protokołu SOAP Reliable Messaging Protocol (SRMP). SRMP jest używany, gdy za pomocą transportu HTTP transferów kolejki do kolejki. SRMP bezpieczne jest używana w przypadku używania protokołu HTTPS dla kolejki do kolejki transferu.  
  
- `UseActiveDirectory`: Wartość logiczna, aby wskazać, czy usługi Active Directory muszą być używane do rozpoznawania adresów kolejki. Domyślnie jest wyłączona. Aby uzyskać więcej informacji, zobacz [punkty końcowe usługi i adresowanie kolejki](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 `MsmqIntegrationBinding` Jest używany, gdy punkt końcowy usługi WCF do komunikowania się z istniejącą aplikacją usługi MSMQ napisanych w C, C++, COM lub System.Messaging interfejsów API.  
  
 Wiązanie właściwości są takie same jak w przypadku `NetMsmqBinding`. Jednak mają zastosowanie następujące różnice:  
  
- Kontrakt operacji dla `MsmqIntegrationBinding` jest ograniczony do przełączania jeden parametr typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> gdzie parametr typu jest typem treści.  
  
- Wiele właściwości natywnej wiadomości usługi MSMQ są widoczne w <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> do użycia.  
  
- Aby ułatwić serializacji i deserializacji treści komunikatu, znajdują się serializatory, takich jak XML i ActiveX.  
  
### <a name="sample-code"></a>Przykładowy kod  
 Aby uzyskać instrukcje krok po kroku dotyczące pisania WCF usług korzystających z usługi MSMQ, zobacz następujące tematy:  
  
- [Instrukcje: Wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
  
- [Instrukcje: Wymiana zakolejkowanych komunikatów z punktami końcowymi programu WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
  
 Aby uzyskać kompletny kod przykładowy pokazujący użycie usługi MSMQ w usłudze WCF, zobacz następujące tematy:  
  
- [Transakcyjne powiązanie MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
  
- [Komunikacja za pomocą nietrwałych kolejek](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
  
- [Kolejki utraconych komunikatów](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
  
- [Sesje i kolejki](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
  
- [Komunikacja dwukierunkowa](../../../../docs/framework/wcf/samples/two-way-communication.md) 
  
- [SRMP](../../../../docs/framework/wcf/samples/srmp.md)  
  
- [Zabezpieczenia komunikatów w ramach kolejkowania komunikatów](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
  
## <a name="see-also"></a>Zobacz także

- [Punkty końcowe usługi i adresowanie kolejki](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)
- [Sieć Web hostująca aplikację zakolejkowaną](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
