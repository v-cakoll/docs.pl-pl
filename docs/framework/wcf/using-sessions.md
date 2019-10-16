---
title: Korzystanie z sesji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sessions [WCF]
ms.assetid: 864ba12f-3331-4359-a359-6d6d387f1035
ms.openlocfilehash: aea26c3a814a34c9d2985bb1bf02dbb80d32ef12
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320288"
---
# <a name="using-sessions"></a>Korzystanie z sesji
W aplikacjach Windows Communication Foundation (WCF) *sesja* korelacji grupy komunikatów w konwersacji. Sesje WCF są inne niż w przypadku obiektów sesji dostępnych w aplikacjach ASP.NET, obsługują różne zachowania i są kontrolowane na różne sposoby. W tym temacie opisano funkcje, które są włączane przez sesje w aplikacjach WCF i jak z nich korzystać.  
  
## <a name="sessions-in-windows-communication-foundation-applications"></a>Sesje w Windows Communication Foundation aplikacji  
 Gdy kontrakt usługi określa, że wymaga sesji, ten kontrakt Określa, że wszystkie wywołania (czyli podstawowe wymiany komunikatów, które obsługują wywołania) muszą być częścią tej samej konwersacji. Jeśli kontrakt Określa, że zezwala na sesje, ale go nie wymaga, klienci mogą nawiązywać połączenia i ustanawiać sesję lub nie ustanawiają sesji. Jeśli sesja zostanie zakończona i zostanie wysłany komunikat za pośrednictwem tego samego kanału, zgłaszany jest wyjątek.  
  
 Sesje WCF mają następujące główne funkcje koncepcyjne:  
  
- Są one jawnie inicjowane i kończone przez aplikację wywołującą (klienta WCF).  
  
- Komunikaty dostarczane podczas sesji są przetwarzane w kolejności, w jakiej zostały odebrane.  
  
- Sesje są skorelowane z grupą komunikatów w konwersacji. Możliwe są różne typy korelacji. Na przykład jeden kanał oparty na sesji może skorelować komunikaty na podstawie udostępnionego połączenia sieciowego, podczas gdy inny kanał oparty na sesji może skorelować komunikaty na podstawie tagu udostępnionego w treści komunikatu. Funkcje, które mogą pochodzić z sesji, zależą od charakteru korelacji.  
  
- Brak ogólnego magazynu danych skojarzonego z sesją WCF.  
  
 W przypadku znajomości klasy <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> w aplikacjach ASP.NET i udostępnianej przez nią funkcji, można zauważyć następujące różnice między tym rodzajem sesji a sesjami programu WCF:  
  
- Sesje ASP.NET są zawsze inicjowane przez serwer.  
  
- Sesje ASP.NET są niejawnie nieuporządkowane.  
  
- Sesje ASP.NET zapewniają ogólny mechanizm magazynowania danych między żądaniami.  
  
 W tym temacie opisano:  
  
- Domyślne zachowanie wykonywania w przypadku korzystania z powiązań opartych na sesji w warstwie modelu usług.  
  
- Typy funkcji, które zapewnia oparty na sesji WCF, powiązania dostarczone przez system.  
  
- Jak utworzyć kontrakt, który deklaruje wymaganie sesji.  
  
- Jak zrozumieć i kontrolować tworzenie i zakończenie sesji oraz relacje między sesją a wystąpieniem usługi.  
  
## <a name="default-execution-behavior-using-sessions"></a>Domyślne zachowanie wykonywania przy użyciu sesji  
 Powiązanie, które próbuje zainicjować sesję, nazywa się powiązaniem *opartym na sesji* . Kontrakty usługi określają, że wymagają, zezwalają lub odmawiają odmowy powiązań opartych na sesji przez ustawienie właściwości <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> w interfejsie (lub klasy) kontraktu usługi na jedną z wartości wyliczenia <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>. Domyślnie wartość tej właściwości to <xref:System.ServiceModel.SessionMode.Allowed>, co oznacza, że jeśli klient używa powiązań opartych na sesji z implementacją usługi WCF, usługa ustanawia i używa udostępnionej sesji.  
  
 Gdy usługa WCF akceptuje sesję klienta, domyślnie włączone są następujące funkcje:  
  
1. Wszystkie wywołania między obiektem klienta WCF są obsługiwane przez to samo wystąpienie usługi.  
  
2. Różne powiązania oparte na sesji zapewniają dodatkowe funkcje.  
  
## <a name="system-provided-session-types"></a>Typy sesji dostarczone przez system  
 Powiązanie oparte na sesji obsługuje domyślne skojarzenie wystąpienia usługi z określoną sesją. Jednak różne powiązania oparte na sesji obsługują różne funkcje oprócz włączania opisanej wcześniej kontrolki dotyczącej wystąpienia opartego na sesji.  
  
 Funkcja WCF udostępnia następujące typy zachowań aplikacji opartych na sesji:  
  
- @No__t-0 obsługuje sesje oparte na zabezpieczeniach, w których oba punkty końcowe komunikacji zgadzają się na konkretną bezpieczną konwersację. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie usług](securing-services.md). Na przykład powiązanie <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>, które zawiera obsługę zarówno dla sesji zabezpieczeń, jak i sesji niezawodnych, domyślnie używa tylko bezpiecznej sesji, która szyfruje i cyfrowo podpisuje komunikaty.  
  
- Powiązanie <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> obsługuje sesje oparte na protokole TCP/IP, aby upewnić się, że wszystkie komunikaty są skorelowane przez połączenie na poziomie gniazda.  
  
- Element <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType>, który implementuje specyfikację WS-ReliableMessaging, zapewnia obsługę niezawodnych sesji, w których można skonfigurować dostarczanie komunikatów w kolejności i dokładnie jeden raz, co zapewnia otrzymywanie komunikatów nawet w przypadku przesyłania komunikatów między wiele węzłów podczas konwersacji. Aby uzyskać więcej informacji, zobacz [niezawodne sesje](./feature-details/reliable-sessions.md).  
  
- Powiązanie <xref:System.ServiceModel.NetMsmqBinding?displayProperty=nameWithType> udostępnia sesje datagramu usługi MSMQ. Aby uzyskać więcej informacji, zobacz [kolejki w programie WCF](./feature-details/queues-in-wcf.md).  
  
 Ustawienie właściwości <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> nie określa typu sesji wymaganej przez umowę.  
  
## <a name="creating-a-contract-that-requires-a-session"></a>Tworzenie kontraktu wymagającego sesji  
 Utworzenie kontraktu wymagającego podania stanu sesji, że Grupa operacji deklarujących kontrakt usługi musi być wykonywana w ramach tej samej sesji, a komunikaty muszą zostać dostarczone w pożądanej kolejności. Aby zapewnić obsługę sesji wymaganej przez kontrakt usługi, ustaw właściwość <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> w interfejsie lub klasie kontraktu usługi na wartość wyliczenia <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>, aby określić, czy kontrakt:  
  
- Wymaga sesji.  
  
- Zezwala klientowi na ustanawianie sesji.  
  
- Zabrania sesji.  
  
 Ustawienie właściwości <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> nie określa jednak typu zachowania wymaganego przez kontrakt. Powoduje to, że program WCF sprawdza w czasie wykonywania, że skonfigurowane powiązanie (które tworzy kanał komunikacyjny) dla usługi, nie lub może ustanowić sesję podczas implementowania usługi. Po ponownym rozwiązaniu można spełnić to wymaganie przy użyciu dowolnego typu zachowań opartych na sesji, które wybiera — zabezpieczenia, transport, niezawodne lub kilka kombinacji. Dokładne zachowanie zależy od wybranej wartości <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>. Jeśli skonfigurowane powiązanie usługi nie jest zgodne z wartością <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A>, zgłaszany jest wyjątek. Powiązania i kanały tworzone przez siebie do sesji obsługi są określane jako oparte na sesji.  
  
 Następujący kontrakt usługi określa, że wszystkie operacje w `ICalculatorSession` muszą być wymieniane w ramach sesji. Żadna z operacji nie zwraca wartości do obiektu wywołującego, z wyjątkiem metody `Equals`. Jednak Metoda `Equals` nie przyjmuje żadnych parametrów i dlatego może zwracać wartość różną od zera w sesji, w której dane zostały już przesłane do innych operacji. Ten kontrakt wymaga poprawnego działania sesji. Bez sesji skojarzonej z określonym klientem wystąpienie usługi nie ma wpływu na to, jakie poprzednie dane wysłał ten klient.  
  
 [!code-csharp[S_Service_Session#1](../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
 Jeśli usługa zezwala na sesję, sesja zostanie nawiązana i użyta, jeśli klient ją zainicjuje. w przeciwnym razie nie zostanie ustanowiona żadna sesja.  
  
## <a name="sessions-and-service-instances"></a>Sesje i wystąpienia usługi  
 W przypadku korzystania z domyślnego zachowania podczas wystąpienia programu WCF wszystkie wywołania między obiektem klienta WCF są obsługiwane przez to samo wystąpienie usługi. W związku z tym na poziomie aplikacji można myśleć o sesji, co umożliwia zachowanie aplikacji podobnej do zachowania połączenia lokalnego. Na przykład podczas tworzenia obiektu lokalnego:  
  
- Konstruktor jest wywoływany.  
  
- Wszystkie kolejne wywołania w odwołaniu do obiektu klienta WCF są przetwarzane przez to samo wystąpienie obiektu.  
  
- Destruktor jest wywoływany, gdy odwołanie do obiektu jest niszczone.  
  
 Sesje umożliwiają podobne zachowanie między klientami i usługami, o ile jest używane domyślne zachowanie wystąpienia usługi. Jeśli kontrakt usługi wymaga lub obsługuje sesje, co najmniej jedna operacja kontraktu może być oznaczona jako inicjująca lub kończąca sesję przez ustawienie właściwości <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A> i <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A>.  
  
 *Operacje inicjujące* to te, które muszą być wywoływane jako pierwsza operacja nowej sesji. Operacje nieinicjujące mogą być wywoływane tylko po wywołaniu co najmniej jednej operacji inicjującej. W związku z tym można utworzyć rodzaj konstruktora sesji dla swojej usługi, deklarując operacje inicjowania, które umożliwiają przejęcie danych z klientów odpowiednich do początku wystąpienia usługi. (Stan jest skojarzony z sesją, ale nie z obiektem usługi).  
  
 *Przerywanie operacji*, jest to te, które muszą być wywoływane jako ostatni komunikat w istniejącej sesji. W przypadku domyślnego przypadku usługa WCF odtwarza obiekt usługi i jego kontekst po zamknięciu sesji, z którą usługa została skojarzona. W związku z tym można utworzyć Rodzaj destruktora, deklarując operacje kończące, które umożliwiają wykonanie funkcji odpowiedniej dla końca wystąpienia usługi.  
  
> [!NOTE]
> Chociaż domyślne zachowanie nosi podobieństwo do lokalnych konstruktorów i destruktorów, jest to tylko podobieństwo. Każda operacja usługi WCF może być operacją inicjującą lub kończącą lub jednocześnie. Ponadto w przypadku domyślnego przypadku operacje inicjujące mogą być wywoływane dowolną liczbę razy w dowolnej kolejności; Po ustanowieniu sesji i skojarzeniu jej z wystąpieniem nie są tworzone żadne dodatkowe sesje, chyba że jawnie kontrolujesz okres istnienia wystąpienia usługi (przez manipulowanie obiektem <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>). Na koniec stan jest skojarzony z sesją, a nie z obiektem usługi.  
  
 Na przykład kontrakt `ICalculatorSession` użyty w poprzednim przykładzie wymaga, aby obiekt klienta WCF najpierw wywoływał operację `Clear` przed żadną inną operacją i że sesja z tym obiektem klienta WCF powinna zakończyć się po wywołaniu operacji `Equals`. Poniższy przykład kodu przedstawia kontrakt, który wymusza te wymagania. `Clear` musi być wywoływana jako pierwsza, aby zainicjować sesję i że sesja zostanie zakończona, gdy zostanie wywołana `Equals`.  
  
 [!code-csharp[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.isinitiatingisterminating/cs/service.cs#1)]
 [!code-vb[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.isinitiatingisterminating/vb/service.vb#1)]  
  
 Usługi nie uruchamiają sesji z klientami programu. W aplikacjach klienckich WCF istnieje relacja bezpośrednia między okresem istnienia kanału opartego na sesji i okresem istnienia sesji. W związku z tym klienci tworzą nowe sesje przez utworzenie nowych kanałów opartych na sesji i rozbicie istniejących sesji przez zamknięcie kanałów opartych na sesji. Klient uruchamia sesję z punktem końcowym usługi, wywołując jedną z następujących czynności:  
  
- <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> w kanale zwróconym przez wywołanie do <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>.  
  
- <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> w obiekcie klienta WCF wygenerowanym przez [Narzędzie narzędzia metadanych ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
- Operacja inicjująca dla każdego typu obiektu klienta WCF (domyślnie wszystkie operacje są inicjowane). Po wywołaniu pierwszej operacji obiekt klienta WCF automatycznie otwiera kanał i inicjuje sesję.  
  
 Zwykle klient zamyka sesję z punktem końcowym usługi, wywołując jedną z następujących czynności:  
  
- <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> w kanale zwróconym przez wywołanie do <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>.  
  
- <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType> w obiekcie klienta WCF wygenerowanym przez Svcutil. exe.  
  
- Operacja przerywania dla każdego typu obiektu klienta WCF (domyślnie nie kończy się żadna operacja; kontrakt musi jawnie określić operację kończącą). Po wywołaniu pierwszej operacji obiekt klienta WCF automatycznie otwiera kanał i inicjuje sesję.  
  
 Przykłady można znaleźć w temacie [How to: Create a Service, która wymaga sesji](./feature-details/how-to-create-a-service-that-requires-sessions.md) oraz [domyślne zachowanie usługi](./samples/default-service-behavior.md) i przykłady tworzenia [wystąpień](./samples/instancing.md) .  
  
 Więcej informacji o klientach i sesjach znajduje się w temacie [Uzyskiwanie dostępu do usług za pomocą klienta WCF](./feature-details/accessing-services-using-a-client.md).  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Sesje współpracują z ustawieniami InstanceContext  
 Istnieje interakcja między wyliczeniem <xref:System.ServiceModel.SessionMode> w kontrakcie i właściwością <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType>, która kontroluje skojarzenie między kanałami i określonymi obiektami usługi. Aby uzyskać więcej informacji, zobacz [sesje, Tworzenie wystąpień i współbieżność](./feature-details/sessions-instancing-and-concurrency.md).  
  
### <a name="sharing-instancecontext-objects"></a>Udostępnianie obiektów InstanceContext  
 Można również kontrolować, który kanał lub połączenie oparte na sesji jest skojarzone z tym obiektem <xref:System.ServiceModel.InstanceContext> przez wykonanie tego skojarzenia samodzielnie. 
  
## <a name="sessions-and-streaming"></a>Sesje i przesyłanie strumieniowe  
 W przypadku transferu dużej ilości danych, tryb transferu przesyłania strumieniowego w programie WCF jest możliwym rozwiązaniem alternatywnym dla domyślnego zachowania buforowania i przetwarzania komunikatów w pamięci. Podczas przesyłania strumieniowego do wywołań opartych na sesji może wystąpić nieoczekiwane zachowanie. Wszystkie wywołania przesyłania strumieniowego są realizowane za pośrednictwem pojedynczego kanału (kanału datagramu), który nie obsługuje sesji, nawet jeśli używane powiązanie jest skonfigurowane do korzystania z sesji. Jeśli wielu klientów przesyła strumieniowo wywołania do tego samego obiektu usługi za pośrednictwem powiązań opartych na sesji, a tryb współbieżności obiektu usługi jest ustawiony na wartość Single, a jego tryb kontekstu wystąpienia jest ustawiony na `PerSession`, wszystkie wywołania muszą przechodzić przez kanał datagramu i tylko jeden wywołanie jest przetwarzane w czasie. Co najmniej jeden klient może przekroczyć limit czasu. Ten problem można obejść, ustawiając wartość `InstanceContextMode` obiektu usługi na `PerCall` lub współbieżność do wielu.  
  
> [!NOTE]
> MaxConcurrentSessions nie ma wpływu w tym przypadku, ponieważ jest dostępna tylko jedna "sesja".  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A>
- <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A>
