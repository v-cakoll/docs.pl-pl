---
title: Tworzenie kolejek w programie WCF
ms.date: 03/30/2017
ms.assetid: e98d76ba-1acf-42cd-b137-0f8214661112
ms.openlocfilehash: 6656ab0b2db88297e6ac9a28bb2ea18c0056d18c
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837327"
---
# <a name="queuing-in-wcf"></a>Tworzenie kolejek w programie WCF
W tej sekcji opisano sposób używania komunikacji kolejkowanej w programie Windows Communication Foundation (WCF).  
  
## <a name="queues-as-a-wcf-transport-binding"></a>Kolejki jako powiązanie transportu WCF  
 W programie WCF kontrakty określają, co jest wymieniane. Kontrakty są wymianą komunikatów zależnych od firmy lub aplikacji. Mechanizm używany do wymiany komunikatów (lub "How") jest określony w powiązaniach. Powiązania w programie WCF hermetyzują szczegóły wymiany komunikatów. Uwidaczniają pokrętła konfiguracyjne dla użytkownika w celu kontrolowania różnych aspektów transportu lub protokołu, które reprezentują powiązania. Kolejkowanie w programie WCF jest traktowane jak inne powiązania transportowe, które jest dużą korzyść dla wielu aplikacji obsługujących kolejkowanie. Obecnie wiele aplikacji obsługujących kolejkowanie jest pisanych inaczej niż inne aplikacje rozproszone w stylu zdalnego wywołania procedury (RPC), co utrudnia ich śledzenie i konserwowanie. Dzięki platformie WCF styl pisania aplikacji rozproszonej jest znacznie taki sam, co ułatwia ich wykonywanie i konserwowanie. Ponadto dzięki rozróżnieniu mechanizmu wymiany niezależnie od logiki biznesowej, łatwiej jest skonfigurować Transport lub wprowadzić w nim zmiany bez wpływu na kod aplikacji. Na poniższej ilustracji przedstawiono strukturę usługi i klienta programu WCF przy użyciu usługi MSMQ jako transportu.  
  
 ![Diagram aplikacji znajdujących się w kolejce](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Rozproszona-Queueed-Figure")  
  
 Jak widać na poprzedniej ilustracji, klient i usługa muszą definiować tylko semantykę aplikacji, czyli umowę i implementację. Usługa konfiguruje Powiązywanie w kolejce przy użyciu preferowanych ustawień. Klient korzysta z narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) , aby wygenerować klienta WCF w usłudze i wygenerować plik konfiguracji, który opisuje powiązania, które będą używane do wysyłania komunikatów do usługi. W tym celu wysłanie komunikatu w kolejce powoduje utworzenie wystąpienia klienta programu WCF i wywołanie na nim operacji. Spowoduje to wysłanie wiadomości do kolejki transmisji i przekazanie jej do kolejki docelowej. Wszystkie złożoności komunikacji kolejkowanej są ukryte w aplikacji wysyłającej i otrzymującej komunikaty.  
  
 Ostrzeżenia dotyczące umieszczania w kolejce powiązań w programie WCF obejmują:  
  
- Wszystkie operacje usługi muszą być jednokierunkowe, ponieważ domyślne powiązanie kolejkowane w programie WCF nie obsługuje komunikacji dwukierunkowej przy użyciu kolejek. Dwukierunkowa próbka komunikacji ([komunikacja dwukierunkowa](../../../../docs/framework/wcf/samples/two-way-communication.md)) przedstawia sposób użycia umów 2 1 w celu zaimplementowania komunikacji dupleksowej przy użyciu kolejek.  
  
- Aby wygenerować klienta WCF przy użyciu wymiany metadanych, wymagany jest dodatkowy punkt końcowy protokołu HTTP w usłudze, aby można było wykonywać zapytania bezpośrednio w celu wygenerowania klienta WCF i uzyskać informacje o powiązaniu, aby odpowiednio skonfigurować komunikację z kolejką.  
  
- W oparciu o powiązanie umieszczone w kolejce, wymagana jest dodatkowa konfiguracja poza programem WCF. Na przykład Klasa <xref:System.ServiceModel.NetMsmqBinding> dostarczana z usługą WCF wymaga skonfigurowania powiązań oraz minimalnego skonfigurowania usługi kolejkowania komunikatów (MSMQ).  
  
 W poniższych sekcjach opisano określone powiązania w kolejce dostarczone z programem WCF, które są oparte na usłudze MSMQ.  
  
### <a name="msmq"></a>Usługa MSMQ  
 Transport w kolejce w usłudze WCF używa usługi MSMQ do obsługi komunikacji znajdującej się w kolejce.  
  
 Usługa MSMQ jest dostarczana jako składnik opcjonalny z systemem Windows i działa jako usługa NT. Przechwytuje komunikaty do transmisji w kolejce transmisji oraz do dostarczania w kolejce docelowej. Menedżerowie kolejki MSMQ implementują niezawodny protokół transferu komunikatów, dzięki czemu komunikaty nie są tracone w transmisji. Protokół może być natywny lub oparty na protokole SOAP, taki jak protokół SOAP Message Protocol (SRMP).  
  
 W usłudze MSMQ kolejki mogą być transakcyjne lub nietransakcyjne. Kolejka transakcyjna umożliwia przechwytywanie i dostarczanie komunikatów w transakcji, a następnie przechowywanie trwale w kolejce. Komunikaty wysyłane do kolejki transakcyjnej są przesyłane dokładnie jeden raz w określonej kolejności. Kolejki nietransakcyjnej można użyć do wysyłania zarówno komunikatów nietrwałych, jak i trwałych. Komunikat wysłany do kolejki nietransakcyjnej nie zawiera żadnych wiarygodnych gwarancji transferu; w ten sposób komunikaty mogą być tracone.  
  
 Kolejki usługi MSMQ można także zabezpieczyć przy użyciu tożsamości systemu Windows zarejestrowanej w usłudze katalogowej Active Directory. Podczas instalowania usługi MSMQ można zainstalować integrację Active Directory, która wymaga, aby komputer był częścią sieci domeny systemu Windows.  
  
 Aby uzyskać więcej informacji na temat usługi MSMQ, zobacz [Instalowanie usługi kolejkowania komunikatów (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md).  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 [\<> usługi msmqbinding](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) to powiązane z kolejką WCF, który zapewnia dwa punkty końcowe WCF do komunikowania się przy użyciu usługi MSMQ. W związku z tym, uwidacznia właściwości, które są specyficzne dla usługi MSMQ. Jednak nie wszystkie funkcje i właściwości usługi MSMQ są uwidocznione w `NetMsmqBinding`. `NetMsmqBinding` kompaktowy jest zaprojektowana z optymalnym zestawem funkcji, które najlepiej znaleźć w większości klientów.  
  
 `NetMsmqBinding` manifestuje podstawowe koncepcje dotyczące kolejkowania omówione w tym zakresie w postaci właściwości powiązań. Te właściwości z kolei komunikują się z usługą MSMQ w celu przesyłania i dostarczania komunikatów. Dyskusje dotyczące kategorii właściwości znajdują się w poniższych sekcjach. Aby uzyskać więcej informacji, zobacz tematy dotyczące pojęć, które bardziej szczegółowo opisują określone właściwości.  
  
#### <a name="exactlyonce-and-durable-properties"></a>Właściwości ExactlyOnce i trwałe  
 Właściwości `ExactlyOnce` i `Durable` mają wpływ na sposób przesyłania komunikatów między kolejkami:  
  
- `ExactlyOnce`: po ustawieniu na `true` (domyślnie) kanał umieszczony w kolejce gwarantuje, że komunikat, jeśli został dostarczony, nie jest duplikowany. Gwarantuje również, że wiadomość nie zostanie utracona. Jeśli wiadomość nie może zostać dostarczona lub komunikat czasu wygaśnięcia komunikatu wygasa przed dostarczeniem komunikatu, komunikat o błędzie i Przyczyna niepowodzenia dostarczenia są rejestrowane w kolejce utraconych wiadomości. Po ustawieniu na `false`kanał umieszczony w kolejce sprawia, że jest to konieczne. W takim przypadku można opcjonalnie wybrać kolejkę utraconych wiadomości.  
  
- `Durable:` po ustawieniu na `true` (domyślnie) kanał umieszczony w kolejce gwarantuje, że usługa MSMQ zapisze komunikat trwale na dysku. W takim przypadku, jeśli usługa MSMQ została zatrzymana i ponownie uruchomiona, komunikaty na dysku są przesyłane do kolejki docelowej lub dostarczane do usługi. Po ustawieniu na `false`komunikaty są przechowywane w magazynie nietrwałym i są tracone po zatrzymywaniu i ponownym uruchomieniu usługi MSMQ.  
  
 W celu `ExactlyOnce` niezawodnego transferu Usługa MSMQ wymaga, aby Kolejka była transakcyjna. Ponadto usługa MSMQ wymaga transakcji do odczytu z kolejki transakcyjnej. W związku z tym podczas korzystania z `NetMsmqBinding`należy pamiętać, że transakcja jest wymagana do wysyłania i odbierania komunikatów, gdy `ExactlyOnce` jest ustawiona na `true`. Podobnie usługa MSMQ wymaga, aby Kolejka była nietransakcyjna dla najważniejszych gwarancji, na przykład gdy `ExactlyOnce` jest `false` i dla nieulotnych komunikatów. W tym przypadku, gdy ustawienie `ExactlyOnce` na `false` lub trwałe na `false`nie można wysłać ani odebrać przy użyciu transakcji.  
  
> [!NOTE]
> Upewnij się, że na podstawie ustawień w powiązaniach utworzono poprawną kolejkę (transakcyjną lub nietransakcyjną). Jeśli `ExactlyOnce` jest `true`, użyj kolejki transakcyjnej; w przeciwnym razie użyj kolejki nietransakcyjnej.  
  
#### <a name="dead-letter-queue-properties"></a>Właściwości kolejki utraconych wiadomości  
 Kolejka utraconych wiadomości służy do przechowywania komunikatów, które kończą się niepowodzeniem. Użytkownik może napisać logikę kompensowania, która odczytuje komunikaty z kolejki utraconych wiadomości.  
  
 Wiele systemów kolejkowania zapewnia kolejkę utraconych wiadomości w całej sieci. Usługa MSMQ zapewnia nietransakcyjną kolejkę utraconych wiadomości dla komunikatów, które kończą się nietransakcyjnymi kolejkami, oraz kolejką utraconych wiadomości transakcyjnych w całej systemie dla komunikatów, które kończą się niepowodzeniem w kolejkach transakcyjnych.  
  
 Jeśli wielu klientów wysyła komunikaty do różnych kolejek docelowych, współużytkują usługę MSMQ, wszystkie komunikaty wysyłane przez klientów przejdą do tej samej kolejki utraconych wiadomości. Nie zawsze jest to zalecane. W celu uzyskania lepszej izolacji Funkcja WCF i usługa MSMQ w systemie Windows Vista zapewniają niestandardową kolejkę utraconych wiadomości (lub kolejkę utraconych danych specyficznych dla aplikacji), którą użytkownik może określić do przechowywania wiadomości, które nie są dostarczane. W związku z tym różni klienci nie korzystają z tej samej kolejki utraconych wiadomości.  
  
 Powiązanie ma dwie właściwości zainteresowania:  
  
- `DeadLetterQueue`: Ta właściwość jest wyliczeniem wskazującym, czy zażądano kolejki utraconych wiadomości. Wyliczenie zawiera również rodzaj kolejki utraconych wiadomości, jeśli jest wymagana. Wartości to `None`, `System`i `Custom`. Aby uzyskać więcej informacji o interpretacji tych właściwości, zobacz [Korzystanie z kolejek utraconych w celu obsługi błędów transferu komunikatów](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
  
- `CustomDeadLetterQueue`: Ta właściwość jest adresem Uniform Resource Identifier (URI) kolejki utraconych wiadomości specyficznych dla aplikacji. Jest to wymagane, jeśli `DeadLetterQueue`.`Custom` jest wybierany.  
  
#### <a name="poison-message-handling-properties"></a>Właściwości obsługi skażonych komunikatów  
 Gdy usługa odczytuje komunikaty z kolejki docelowej w ramach transakcji, usługa może nie przetwarzać komunikatu z różnych powodów. Komunikat jest następnie ponownie umieszczany w kolejce, aby można go było odczytać. Aby zająć się niepowtarzalnymi komunikatami, zestaw właściwości obsługujących trującą wiadomość można skonfigurować w powiązaniu. Istnieją cztery właściwości: `ReceiveRetryCount`, `MaxRetryCycles`, `RetryCycleDelay`i `ReceiveErrorHandling`. Aby uzyskać więcej informacji o tych właściwościach, zobacz [Obsługa skażonych komunikatów](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
#### <a name="security-properties"></a>Właściwości zabezpieczeń  
 Usługa MSMQ uwidacznia własny model zabezpieczeń, taki jak listy kontroli dostępu (ACL) w kolejce lub wysyła uwierzytelnione komunikaty. `NetMsmqBinding` uwidacznia te właściwości zabezpieczeń w ramach swoich ustawień zabezpieczeń transportu. Istnieją dwie właściwości powiązania dla zabezpieczeń transportu: `MsmqAuthenticationMode` i `MsmqProtectionLevel`. Ustawienia w tych właściwościach zależą od konfiguracji usługi MSMQ. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie komunikatów za pomocą zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
 Oprócz zabezpieczeń transportu rzeczywisty komunikat protokołu SOAP może być zabezpieczony przy użyciu zabezpieczeń komunikatów. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie komunikatów przy użyciu zabezpieczeń komunikatów](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md).  
  
 `MsmqTransportSecurity` również uwidacznia dwie właściwości, `MsmqEncryptionAlgorithm` i `MsmqHashAlgorithm`. Są to wyliczenia różnych algorytmów, które umożliwiają wybranie opcji przenoszenia komunikatów i wyznaczania wartości skrótu sygnatur do kolejki.  
  
#### <a name="other-properties"></a>Inne właściwości  
 Oprócz powyższych właściwości inne właściwości specyficzne dla usługi MSMQ, które są widoczne w ramach powiązania, obejmują:  
  
- `UseSourceJournal`: Właściwość wskazująca, że rejestrowanie źródłowe jest włączone. Rejestrowanie źródłowe jest funkcją usługi MSMQ, która zachowuje śledzenie komunikatów, które zostały pomyślnie przesłane z kolejki transmisji.  
  
- `UseMsmqTracing`: Właściwość wskazująca, że śledzenie usługi MSMQ jest włączone. Śledzenie usługi MSMQ wysyła komunikaty raportu do kolejki raportu za każdym razem, gdy komunikat opuszcza lub dociera do komputera obsługującego Menedżera kolejki usługi MSMQ.  
  
- `QueueTransferProtocol`: Wyliczenie protokołu, który ma być używany do transferów komunikatów z kolejki. Usługa MSMQ implementuje natywny protokół przesyłania kolejek do kolejki i protokół oparty na protokole SOAP o nazwie SRMP. Protokół SRMP jest używany w przypadku przesyłania kolejek do kolejki przy użyciu protokołu HTTP. Protokół SRMP Secure jest używany w przypadku przesyłania kolejek do kolejki przy użyciu protokołu HTTPS.  
  
- `UseActiveDirectory`: wartość logiczna określająca, czy Active Directory musi być używana do rozpoznawania adresów w kolejce. Domyślnie to ustawienie jest wyłączone. Aby uzyskać więcej informacji, zobacz [punkty końcowe usługi i adresowanie kolejki](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 `MsmqIntegrationBinding` jest używany, gdy punkt końcowy WCF ma komunikować się z istniejącą aplikacją MSMQ zapisaną w interfejsie API C++języka C,, com lub system. Messaging.  
  
 Właściwości powiązania są takie same jak dla `NetMsmqBinding`. Jednak obowiązują następujące różnice:  
  
- Kontrakt operacji dla `MsmqIntegrationBinding` jest ograniczony do pobierania jednego parametru typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, gdzie parametr typu jest typem treści.  
  
- Wiele właściwości natywnych komunikatów usługi MSMQ jest dostępnych w <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> do użycia.  
  
- W celu ułatwienia serializacji i deserializacji treści wiadomości są udostępniane serializatory, takie jak XML i ActiveX.  
  
### <a name="sample-code"></a>Przykładowy kod  
 Instrukcje krok po kroku dotyczące pisania usług WCF korzystających z usługi MSMQ można znaleźć w następujących tematach:  
  
- [Instrukcje: wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
  
- [Instrukcje: wymiana komunikatów znajdujących się w kolejce z punktami końcowymi WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
  
 Aby uzyskać przykładowy kod ilustrujący użycie usługi MSMQ w programie WCF, zobacz następujące tematy:  
  
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
