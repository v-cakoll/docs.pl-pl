---
title: Tworzenie kolejek w programie WCF
ms.date: 03/30/2017
ms.assetid: e98d76ba-1acf-42cd-b137-0f8214661112
ms.openlocfilehash: e6608a3d556b546660be904eb8c853243e833d2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184560"
---
# <a name="queuing-in-wcf"></a>Tworzenie kolejek w programie WCF
W tej sekcji opisano sposób używania komunikacji w kolejce w programie Windows Communication Foundation (WCF).  
  
## <a name="queues-as-a-wcf-transport-binding"></a>Kolejki jako powiązanie transportu WCF  
 W WCF kontrakty określają, co jest wymieniane. Kontrakty są zależne od firmy lub specyficzne dla aplikacji wymiany komunikatów. Mechanizm używany do wymiany komunikatów (lub "jak") jest określony w powiązaniach. Powiązania w WCF hermetyzują szczegóły wymiany komunikatów. Uwidaczniają one pokrętła konfiguracji dla użytkownika do kontrolowania różnych aspektów transportu lub protokołu, który reprezentują powiązania. Kolejkowanie w WCF jest traktowane jak każde inne powiązanie transportowe, co jest dużą zaletą dla wielu aplikacji kolejkowania. Obecnie wiele aplikacji kolejkowania jest zapisywanych inaczej niż inne aplikacje rozproszone w stylu zdalnego wywoływania procedur (RPC), co utrudnia śledzenie i konserwację. Z WCF styl pisania aplikacji rozproszonej jest znacznie taka sama, dzięki czemu łatwiej śledzić i obsługiwać. Ponadto, poprzez uwzględnienie mechanizmu wymiany oddzielnie od logiki biznesowej, łatwiej jest skonfigurować transport lub wprowadzić w nim zmiany bez wpływu na kod specyficzny dla aplikacji. Poniższy rysunek ilustruje strukturę usługi WCF i klienta przy użyciu usługi MSMQ jako transportu.  
  
 ![Diagram aplikacji w kolejce](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Liczba rozproszonych kolejek")  
  
 Jak widać na powyższej ilustracji, klient i usługa musi zdefiniować tylko semantyka aplikacji, czyli umowy i implementacji. Usługa konfiguruje powiązanie w kolejce z preferowanymi ustawieniami. Klient używa [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania klienta WCF do usługi i do generowania pliku konfiguracji, który opisuje powiązania używane do wysyłania wiadomości do usługi. W związku z tym, aby wysłać wiadomość w kolejce, klient wywołuje klienta WCF i wywołuje operację na nim. Powoduje to, że wiadomość ma zostać wysłana do kolejki transmisji i przeniesiona do kolejki docelowej. Wszystkie zawiłości komunikacji w kolejce są ukryte przed aplikacją, która wysyła i odbiera wiadomości.  
  
 Zastrzeżenia dotyczące powiązania w kolejce w WCF obejmują:  
  
- Wszystkie operacje usługi muszą być jednokierunkowe, ponieważ domyślne powiązanie w kolejce w WCF nie obsługuje komunikacji dupleksowej przy użyciu kolejek. Przykład komunikacji dwukierunkowej[(Dwukierunkowa komunikacja)](../../../../docs/framework/wcf/samples/two-way-communication.md)ilustruje sposób używania dwóch kontraktów jednokierunkowych do implementacji komunikacji dupleksowej przy użyciu kolejek.  
  
- Aby wygenerować klienta WCF przy użyciu wymiany metadanych wymaga dodatkowego punktu końcowego HTTP w usłudze, dzięki czemu można zbadać bezpośrednio do generowania klienta WCF i uzyskać informacje o powiązaniach odpowiednio skonfigurować komunikację w kolejce.  
  
- Na podstawie powiązania w kolejce wymagana jest dodatkowa konfiguracja poza WCF. Na przykład <xref:System.ServiceModel.NetMsmqBinding> klasa, która jest dostarczana z WCF wymaga skonfigurowania powiązań, a także minimalnie skonfigurować usługę kolejkowania wiadomości (MSMQ).  
  
 W poniższych sekcjach opisano określone powiązania w kolejce dostarczane z WCF, które są oparte na msmq.  
  
### <a name="msmq"></a>Usługa MSMQ  
 Transport w kolejce w WCF używa usługi MSMQ do komunikacji w kolejce.  
  
 Usługa MSMQ jest dostarczany jako opcjonalny składnik z systemem Windows i działa jako usługa NT. Przechwytuje wiadomości do transmisji w kolejce transmisji i do dostarczania w kolejce docelowej. Menedżery kolejek usługi MSMQ implementują niezawodny protokół transferu wiadomości, dzięki czemu wiadomości nie są tracone podczas transmisji. Protokół może być natywny lub oparty na pogrodówce, na przykład protokół SOAP Reliable Message Protocol (SRMP).  
  
 W ujmijce MSMQ kolejki mogą być transakcyjne lub nietransakcyjne. Kolejka transakcyjna umożliwia przechwytywanie i dostarczanie wiadomości w transakcji, a następnie trwale przechowywane w kolejce. Wiadomości wysyłane do kolejki transakcyjnej są przesyłane dokładnie raz w kolejności. Kolejki nietransakcyjnej można używać do wysyłania zarówno wiadomości nietrwałych, jak i trwałych. Wiadomość wysłana do kolejki nietransakcyjnej nie zawiera żadnych wiarygodnych gwarancji przeniesienia; w ten sposób wiadomości mogą zostać utracone.  
  
 Kolejki usługi MSMQ można również zabezpieczyć przy użyciu tożsamości systemu Windows zarejestrowanej w usłudze katalogowej Active Directory. Podczas instalowania usługi MSMQ można zainstalować integrację usługi Active Directory, która wymaga, aby komputer był częścią sieci domeny systemu Windows.  
  
 Aby uzyskać więcej informacji na temat usługi MSMQ, zobacz [Instalowanie usługi kolejkowania wiadomości (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md).  
  
### <a name="netmsmqbinding"></a>Netmsmqbinding  
 NetMsmqBinding>jest w kolejce powiązania WCF zapewnia dwa punkty końcowe WCF do komunikowania się przy użyciu usługi MSMQ. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) Powiązanie, w związku z tym udostępnia właściwości, które są specyficzne dla usługi MSMQ. Jednak nie wszystkie funkcje i właściwości usługi `NetMsmqBinding`MSMQ są widoczne w pliku . Kompaktowy `NetMsmqBinding` został zaprojektowany z optymalnym zestawem funkcji, które większość klientów powinna znaleźć wystarczające.  
  
 Manifesty `NetMsmqBinding` podstawowe koncepcje kolejkowania omówione do tej pory w postaci właściwości na powiązaniach. Te właściwości z kolei komunikują się z usługą MSMQ, jak przesyłać i dostarczać wiadomości. Omówienie kategorii właściwości znajduje się w poniższych sekcjach. Aby uzyskać więcej informacji, zobacz tematy koncepcyjne, które opisują określone właściwości bardziej całkowicie.  
  
#### <a name="exactlyonce-and-durable-properties"></a>DokładnieNachu i trwałe właściwości  
 Właściwości `ExactlyOnce` `Durable` i właściwości wpływają na sposób przesyłania wiadomości między kolejkami:  
  
- `ExactlyOnce`: Po `true` ustawieniu (domyślnie) kanał w kolejce zapewnia, że wiadomość, jeśli zostanie dostarczona, nie zostanie zduplikowana. Zapewnia również, że wiadomość nie zostanie utracona. Jeśli wiadomość nie może zostać dostarczona lub wiadomość Time-To Live wygaśnie przed dostarczeniem wiadomości, wiadomość nie powiodła się wraz z przyczyną niepowodzenia dostarczania jest rejestrowana w kolejce utraconych wiadomości. Po ustawieniu `false`na kanał w kolejce podejmuje próbę przeniesienia wiadomości. W takim przypadku można opcjonalnie wybrać kolejkę utraconych wiadomości.  
  
- `Durable:`Po ustawieniu `true` (domyślnie) kanał w kolejce zapewnia, że usługa MSMQ przechowuje wiadomość trwale na dysku. W związku z tym jeśli usługa MSMQ miały zatrzymać i ponownie uruchomić, wiadomości na dysku są przenoszone do kolejki docelowej lub dostarczane do usługi. Po ustawieniu `false`na , wiadomości są przechowywane w magazynie nietrwałych i są tracone podczas zatrzymywania i ponownego uruchamiania usługi MSMQ.  
  
 W `ExactlyOnce` przypadku transferu niezawodnego usługa MSMQ wymaga, aby kolejka była transakcyjna. Ponadto usługa MSMQ wymaga transakcji do odczytu z kolejki transakcyjnej. W związku z tym `NetMsmqBinding`podczas korzystania z programu , należy pamiętać, że transakcja jest wymagana do wysyłania lub odbierania wiadomości, gdy `ExactlyOnce` jest ustawiona na `true`. Podobnie usługa MSMQ wymaga, aby kolejka nie była transakcyjna w `ExactlyOnce` `false` celu zapewnienia najlepszego wysiłku, na przykład kiedy jest i dla nietrwałej obsługi wiadomości. W związku `ExactlyOnce` z `false` tym `false`podczas ustawiania lub trwałe do , nie można wysyłać lub odbierać przy użyciu transakcji.  
  
> [!NOTE]
> Upewnij się, że prawidłowa kolejka (transakcyjnych lub nietransakcyjnych) jest tworzony na podstawie ustawień w powiązaniach. Jeśli `ExactlyOnce` `true`tak, użyj kolejki transakcyjnej; w przeciwnym razie należy użyć kolejki nietransakcyjnej.  
  
#### <a name="dead-letter-queue-properties"></a>Właściwości kolejki utraconych wiadomości  
 Kolejka utraconych wiadomości służy do przechowywania wiadomości, które nie dostarczają. Użytkownik może napisać logikę kompensacją, która odczytuje wiadomości z kolejki utraconych wiadomości.  
  
 Wiele systemów kolejkowania zapewnia ogólnosystemową kolejkę utraconych wiadomości. Usługa MSMQ udostępnia ogólnosystemową kolejkę utraconych wiadomości nietransakcyjnych dla wiadomości, które nie są dostarczane do kolejek nietransakcyjnych, oraz ogólnosystemową kolejkę utraconych wiadomości dla wiadomości, które nie dostarczają do kolejek transakcyjnych.  
  
 Jeśli wielu klientów wysyłających wiadomości do różnych kolejek docelowych współużytkuje usługę MSMQ, wszystkie wiadomości wysyłane przez klientów przechodzą do tej samej kolejki utraconych wiadomości. Nie zawsze jest to preferowane. Aby uzyskać lepszą izolację, WCF i MSMQ w systemie Windows Vista zapewniają niestandardową kolejkę utraconych wiadomości (lub kolejkę utraconych wiadomości specyficznych dla aplikacji), którą użytkownik może określić do przechowywania wiadomości, które nie powiedzie się. W związku z tym różnych klientów nie współużytkują tę samą kolejkę utraconych wiadomości.  
  
 Powiązanie ma dwie właściwości zainteresowania:  
  
- `DeadLetterQueue`: Ta właściwość jest wyliczeniem, które wskazuje, czy żądana jest kolejka utraconych wiadomości. Wyliczenie zawiera również rodzaj kolejki utraconych wiadomości, jeśli jest to wymagane. Wartości to `None` `System`, `Custom`i . Aby uzyskać więcej informacji na temat interpretacji tych właściwości, zobacz [Używanie kolejek utraconych do obsługi błędów transferu wiadomości](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
  
- `CustomDeadLetterQueue`: Ta właściwość jest adresem identyfikatora URI (Uniform Resource Identifier) kolejki utraconych wiadomości specyficznych dla aplikacji. Jest to wymagane, jeśli `DeadLetterQueue`.`Custom` zostanie wybrana.  
  
#### <a name="poison-message-handling-properties"></a>Właściwości obsługi trujących wiadomości  
 Gdy usługa odczytuje wiadomości z kolejki docelowej w ramach transakcji, usługa może nie przetwarzać komunikatu z różnych powodów. Wiadomość jest następnie umieszczana z powrotem w kolejce do odczytu ponownie. Aby poradzić sobie z komunikatami, które nie wielokrotnie, zestaw właściwości obsługi wiadomości poison można skonfigurować w powiązaniu. Istnieją cztery właściwości: `ReceiveRetryCount` `MaxRetryCycles`, `RetryCycleDelay`, `ReceiveErrorHandling`, i . Aby uzyskać więcej informacji na temat tych właściwości, zobacz [Trująca obsługa wiadomości](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
#### <a name="security-properties"></a>Właściwości zabezpieczeń  
 Usługa MSMQ udostępnia własny model zabezpieczeń, taki jak listy kontroli dostępu (Listy kontroli dostępu) w kolejce lub wysyłanie uwierzytelnionych wiadomości. Udostępnia `NetMsmqBinding` te właściwości zabezpieczeń w ramach ustawień zabezpieczeń transportu. Istnieją dwie właściwości w powiązaniu `MsmqAuthenticationMode` dla `MsmqProtectionLevel`zabezpieczeń transportu: i . Ustawienia w tych właściwościach zależą od konfiguracji usługi MSMQ. Aby uzyskać więcej informacji, zobacz [zabezpieczanie wiadomości przy użyciu zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
 Oprócz zabezpieczeń transportu, rzeczywisty komunikat SOAP sam może być zabezpieczony przy użyciu zabezpieczeń wiadomości. Aby uzyskać więcej informacji, zobacz [zabezpieczanie wiadomości przy użyciu zabezpieczeń wiadomości](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md).  
  
 `MsmqTransportSecurity`również udostępnia dwie właściwości `MsmqEncryptionAlgorithm` `MsmqHashAlgorithm`i . Są to wyliczenia różnych algorytmów do wyboru dla szyfrowania transferu kolejka do kolejki wiadomości i mieszania podpisów.  
  
#### <a name="other-properties"></a>Inne właściwości  
 Oprócz poprzednich właściwości inne właściwości specyficzne dla usługi MSMQ widoczne w powiązaniu obejmują:  
  
- `UseSourceJournal`: Właściwość wskazująca, że rejestrowanie źródłowe jest włączone. Rejestrowanie źródłowe to funkcja usługi MSMQ, która śledzi wiadomości, które zostały pomyślnie przesłane z kolejki transmisji.  
  
- `UseMsmqTracing`: Właściwość wskazująca, że śledzenie usługi MSMQ jest włączone. Śledzenie usługi MSMQ wysyła wiadomości raportu do kolejki raportów za każdym razem, gdy wiadomość opuszcza lub dociera do komputera obsługującego menedżera kolejek usługi MSMQ.  
  
- `QueueTransferProtocol`: Wyliczenie protokołu używanego do przesyłania wiadomości kolejka do kolejki. Usługa MSMQ implementuje natywny protokół transferu kolejka do kolejki oraz protokół oparty na potajemnym protokół o nazwie SOAP Reliable Messaging Protocol (SRMP). Protokół SRMP jest używany podczas korzystania z transportu HTTP do transferów kolejka do kolejki. SRMP secure jest używany podczas korzystania z protokołu HTTPS do transferów kolejka do kolejki.  
  
- `UseActiveDirectory`: Wartość logiczna wskazująca, czy usługa Active Directory musi być używana do rozpoznawania adresów kolejki. Domyślnie jest to wyłączone. Aby uzyskać więcej informacji, zobacz [Punkty końcowe usługi i Adresowanie kolejek](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
### <a name="msmqintegrationbinding"></a>Msmqintegrationbinding  
 Jest `MsmqIntegrationBinding` używany, gdy punkt końcowy WCF do komunikowania się z istniejącą aplikacją MSMQ napisane w C, C++, COM lub System.Messaging interfejsów API.  
  
 Właściwości wiązania są takie same `NetMsmqBinding`jak dla . Obowiązują jednak następujące różnice:  
  
- Kontrakt operacyjny `MsmqIntegrationBinding` dla jest ograniczona do podjęcia <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> jednego parametru typu, gdzie parametr typu jest typem treści.  
  
- Wiele właściwości wiadomości natywnych usługi MSMQ są widoczne w <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> do użytku.  
  
- Aby pomóc w serializacji i deserializacji treści wiadomości, serializatory, takie jak XML i ActiveX są dostarczane.  
  
### <a name="sample-code"></a>Przykładowy kod  
 Aby uzyskać instrukcje krok po kroku dotyczące pisania usług WCF korzystających z usługi MSMQ, zobacz następujące tematy:  
  
- [Instrukcje: wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
  
- [Instrukcje: wymiana komunikatów znajdujących się w kolejce z punktami końcowymi WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
  
 W przypadku ukończonego przykładu kodu ilustrującego użycie usługi MSMQ w WCF zobacz następujące tematy:  
  
- [Transakcyjne powiązanie MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
  
- [Komunikacja za pomocą nietrwałych kolejek](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
  
- [Kolejki utraconych komunikatów](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
  
- [Sesje i kolejki](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
  
- [Komunikacja dwukierunkowa](../../../../docs/framework/wcf/samples/two-way-communication.md)
  
- [SRMP](../../../../docs/framework/wcf/samples/srmp.md)  
  
- [Zabezpieczenia komunikatów w ramach kolejkowania komunikatów](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
  
## <a name="see-also"></a>Zobacz też

- [Punkty końcowe usługi i adresowanie kolejki](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)
- [Sieć Web hostująca aplikację zakolejkowaną](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
