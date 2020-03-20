---
title: Korzystanie z sesji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sessions [WCF]
ms.assetid: 864ba12f-3331-4359-a359-6d6d387f1035
ms.openlocfilehash: a879e90aeab7b40529df1f1a60cd1f879c39720a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143177"
---
# <a name="using-sessions"></a>Korzystanie z sesji
W aplikacjach Windows Communication Foundation (WCF) *sesja* koreluje grupę wiadomości do konwersacji. Sesje WCF różnią się od obiektu sesji dostępnego w ASP.NET aplikacji, obsługują różne zachowania i są kontrolowane na różne sposoby. W tym temacie opisano funkcje, które sesje włączyć w aplikacjach WCF i jak z nich korzystać.  
  
## <a name="sessions-in-windows-communication-foundation-applications"></a>Sesje w aplikacjach programu Windows Communication Foundation  
 Gdy umowa serwisowa określa, że wymaga sesji, że umowa określa, że wszystkie wywołania (czyli podstawowe wymiany komunikatów, które obsługują wywołania) musi być częścią tej samej konwersacji. Jeśli umowa określa, że zezwala na sesje, ale nie wymaga jednego, klienci mogą łączyć się i ustanawiać sesję lub nie ustanawiać sesji. Jeśli sesja kończy się i wiadomość jest wysyłana za pośrednictwem tego samego kanału wyjątek.  
  
 Sesje WCF mają następujące główne funkcje koncepcyjne:  
  
- Są one jawnie inicjowane i zakończone przez aplikację wywołującą (klienta WCF).  
  
- Wiadomości dostarczane podczas sesji są przetwarzane w kolejności, w jakiej są odbierane.  
  
- Sesje skorelować grupę wiadomości do konwersacji. Możliwe są różne rodzaje korelacji. Na przykład jeden kanał oparty na sesji może skorelować wiadomości na podstawie udostępnionego połączenia sieciowego, podczas gdy inny kanał oparty na sesji może skorelować wiadomości na podstawie udostępnionego tagu w treści wiadomości. Funkcje, które mogą pochodzić z sesji zależą od charakteru korelacji.  
  
- Nie ma ogólnego magazynu danych skojarzonego z sesją WCF.  
  
 Jeśli znasz <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> klasę w ASP.NET aplikacji i funkcji, które zapewnia, można zauważyć następujące różnice między tego rodzaju sesji i WCF sesji:  
  
- ASP.NET sesje są zawsze inicjowane przez serwer.  
  
- ASP.NET sesje są niejawnie nieuiarszane.  
  
- ASP.NET sesji zapewniają ogólny mechanizm przechowywania danych między żądaniami.  
  
 W tym temacie opisano:  
  
- Domyślne zachowanie wykonywania podczas korzystania z powiązań opartych na sesji w warstwie modelu usługi.  
  
- Typy funkcji, które WCF sesji oparte, systemowe powiązania zapewniają.  
  
- Jak utworzyć kontrakt, który deklaruje wymaganie sesji.  
  
- Jak zrozumieć i kontrolować tworzenie i zakończenie sesji i relacji sesji do wystąpienia usługi.  
  
## <a name="default-execution-behavior-using-sessions"></a>Domyślne zachowanie wykonania przy użyciu sesji  
 Powiązanie, które próbuje zainicjować sesję, jest nazywane powiązaniem *opartym na sesji.* Umowy serwisowe określają, że wymagają, zezwalają lub <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> odmawiają powiązania oparte na sesji, ustawiając <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> właściwość w interfejsie umowy serwisowej (lub klasie) na jedną z wartości wyliczenia. Domyślnie wartość tej właściwości <xref:System.ServiceModel.SessionMode.Allowed>jest , co oznacza, że jeśli klient używa powiązania opartego na sesji z implementacją usługi WCF, usługa ustanawia i używa dostarczonej sesji.  
  
 Gdy usługa WCF akceptuje sesję klienta, następujące funkcje są domyślnie włączone:  
  
1. Wszystkie wywołania między obiektem klienta WCF są obsługiwane przez to samo wystąpienie usługi.  
  
2. Różne powiązania oparte na sesji zapewniają dodatkowe funkcje.  
  
## <a name="system-provided-session-types"></a>Typy sesji dostarczonych przez system  
 Powiązanie oparte na sesji obsługuje domyślne skojarzenie wystąpienia usługi z określoną sesją. Jednak różne powiązania oparte na sesji obsługują różne funkcje oprócz włączania formantu instancing opartego na sesji wcześniej opisane.  
  
 WCF udostępnia następujące typy zachowań aplikacji opartych na sesji:  
  
- Obsługuje <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType> sesje oparte na zabezpieczeniach, w których oba końce komunikacji uzgodniły konkretną bezpieczną rozmowę. Aby uzyskać więcej informacji, zobacz [zabezpieczanie usług](securing-services.md). Na przykład <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType> powiązanie, które zawiera obsługę zarówno sesji zabezpieczeń, jak i niezawodnych sesji, domyślnie używa tylko bezpiecznej sesji, która szyfruje i podpisuje wiadomości cyfrowo.  
  
- Powiązanie <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> obsługuje sesje oparte na protokół TCP/IP, aby upewnić się, że wszystkie komunikaty są skorelowane przez połączenie na poziomie gniazda.  
  
- Element, <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> który implementuje specyfikację WS-ReliableMessaging, zapewnia obsługę niezawodnych sesji, w których wiadomości mogą być skonfigurowane do dostarczania w kolejności i dokładnie raz, zapewniając odbieranie wiadomości nawet podczas podróży wiadomości przez wiele węzłów podczas konwersacji. Aby uzyskać więcej informacji, zobacz [Niezawodne sesje](./feature-details/reliable-sessions.md).  
  
- Powiązanie <xref:System.ServiceModel.NetMsmqBinding?displayProperty=nameWithType> zapewnia sesje datagramu usługi MSMQ. Aby uzyskać więcej informacji, zobacz [Kolejki w WCF](./feature-details/queues-in-wcf.md).  
  
 Ustawienie <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> właściwości nie określa typu sesji, jakiej wymaga kontrakt, tylko tego wymaga.  
  
## <a name="creating-a-contract-that-requires-a-session"></a>Tworzenie kontraktu, który wymaga sesji  
 Tworzenie umowy, która wymaga sesji stwierdza, że grupa operacji, które deklaruje umowa serwisowa muszą być wykonywane w ramach tej samej sesji i że wiadomości muszą być dostarczane w kolejności. Aby potwierdzić poziom obsługi sesji, który wymaga <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> umowy serwisowej, ustaw właściwość <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> w interfejsie umowy serwisowej lub klasy do wartości wyliczenia, aby określić, czy umowa:  
  
- Wymaga sesji.  
  
- Umożliwia klientowi ustanowienie sesji.  
  
- Zabrania sesji.  
  
 Ustawienie <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> właściwości nie określa jednak typu zachowania opartego na sesji, które wymaga od umowy. Nakazuje WCF potwierdzić w czasie wykonywania, że skonfigurowane powiązanie (który tworzy kanał komunikacji) dla usługi nie, nie lub można ustanowić sesji podczas implementowania usługi. Ponownie powiązanie może spełnić to wymaganie za pomocą dowolnego typu zachowania opartego na sesji, które wybierze — zabezpieczeń, transportu, niezawodne lub niektóre kombinacje. Dokładne zachowanie zależy <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> od wybranej wartości. Jeśli skonfigurowane powiązanie usługi nie jest zgodne <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A>z wartością , zostanie zgłoszony wyjątek. Powiązania i kanały, które tworzą, że sesje pomocy technicznej są uważane za oparte na sesji.  
  
 Poniższa umowa serwisowa określa, `ICalculatorSession` że wszystkie operacje w sesji muszą być wymieniane w ramach sesji. Żadna z operacji zwraca wartość do `Equals` wywołującego z wyjątkiem metody. Jednak `Equals` metoda nie przyjmuje żadnych parametrów i w związku z tym można zwrócić tylko wartość niezerową wewnątrz sesji, w której dane zostały już przekazane do innych operacji. Ten kontrakt wymaga sesji do poprawnego działania. Bez sesji skojarzonej z określonym klientem wystąpienie usługi nie ma możliwości poznania, jakie poprzednie dane wysłał ten klient.  
  
 [!code-csharp[S_Service_Session#1](../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
 Jeśli usługa zezwala na sesję, sesja jest ustanawiana i używana, jeśli klient inicjuje jedną; w przeciwnym razie nie zostanie ustanowiona żadna sesja.  
  
## <a name="sessions-and-service-instances"></a>Sesje i wystąpienia usługi  
 Jeśli używasz domyślnego zachowania instancing w WCF, wszystkie wywołania między obiektem klienta WCF są obsługiwane przez to samo wystąpienie usługi. W związku z tym na poziomie aplikacji można myśleć o sesji jako włączenie zachowania aplikacji podobne do zachowania wywołania lokalnego. Na przykład podczas tworzenia obiektu lokalnego:  
  
- Konstruktor jest wywoływana.  
  
- Wszystkie kolejne wywołania do odwołania do obiektu klienta WCF są przetwarzane przez to samo wystąpienie obiektu.  
  
- Destruktor jest wywoływany, gdy odwołanie do obiektu jest niszczony.  
  
 Sesje włączyć podobne zachowanie między klientami i usługami, tak długo, jak domyślne zachowanie wystąpienia usługi jest używany. Jeśli umowa serwisowa wymaga lub obsługuje sesje, co najmniej jedna operacja umowy może <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A> <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A> być oznaczona jako inicjująca lub kończąca sesję przez ustawienie właściwości i.  
  
 *Inicjowanie operacji* to te, które muszą być wywoływane jako pierwsza operacja nowej sesji. Operacje nie inicjujące można wywołać tylko po wywołaniu co najmniej jednej operacji inicjującej. W związku z tym można utworzyć rodzaj konstruktora sesji dla usługi, deklarując inicjując operacje przeznaczone do podjęcia danych wejściowych od klientów odpowiednich do początku wystąpienia usługi. (Stan jest skojarzony z sesją, jednak, a nie obiekt usługi.)  
  
 *Kończenie operacji*, odwrotnie, to te, które muszą być wywoływane jako ostatnia wiadomość w istniejącej sesji. W przypadku domyślnego WCF odtwarza obiekt usługi i jego kontekst po sesji, z którą usługa została skojarzona jest zamknięta. W związku z tym można utworzyć rodzaj destruktora, deklarując zakończenia operacji przeznaczonych do wykonywania funkcji odpowiednich do końca wystąpienia usługi.  
  
> [!NOTE]
> Chociaż domyślne zachowanie nosi podobieństwo do lokalnych konstruktorów i destruktorów, jest tylko podobieństwo. Każda operacja usługi WCF może być operacją inicjującą lub kończącą lub obie jednocześnie. Ponadto w przypadku domyślnym inicjowanie operacji można wywołać dowolną liczbę razy w dowolnej kolejności; żadne dodatkowe sesje nie są tworzone po ustanowieniu sesji i skojarzeniu z wystąpieniem, chyba że <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> jawnie kontrolujesz okres istnienia wystąpienia usługi (manipulując obiektem). Na koniec stan jest skojarzony z sesją, a nie z obiektem usługi.  
  
 Na przykład `ICalculatorSession` kontrakt używany w poprzednim przykładzie wymaga, aby obiekt `Clear` klienta WCF najpierw wywołać operację przed inną operacją i że `Equals` sesja z tym obiektem klienta WCF należy zakończyć, gdy wywołuje operację. Poniższy przykład kodu przedstawia kontrakt, który wymusza te wymagania. `Clear`musi być wywoływana najpierw, aby zainicjować `Equals` sesję, a sesja kończy się, gdy jest wywoływana.  
  
 [!code-csharp[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.isinitiatingisterminating/cs/service.cs#1)]
 [!code-vb[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.isinitiatingisterminating/vb/service.vb#1)]  
  
 Usługi nie rozpoczynają sesji z klientami. W aplikacjach klienckich WCF istnieje bezpośrednia relacja między okresem istnienia kanału opartego na sesji a okresem istnienia samej sesji. W związku z tym klienci tworzą nowe sesje, tworząc nowe kanały oparte na sesji i zburzyć istniejące sesje, zamykając bezpiecznie kanały oparte na sesji. Klient rozpoczyna sesję z punktem końcowym usługi, wywołując jedną z następujących czynności:  
  
- <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType>na kanale zwróconym przez <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>połączenie do .  
  
- <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType>na obiekcie klienta WCF wygenerowanym przez [narzędzie narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
- Operacja inicjująca na każdym typie obiektu klienta WCF (domyślnie wszystkie operacje są inicjujące). Po wywołaniu pierwszej operacji obiekt klienta WCF automatycznie otwiera kanał i inicjuje sesję.  
  
 Zazwyczaj klient kończy sesję z punktem końcowym usługi, wywołując jedną z następujących czynności:  
  
- <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType>na kanale zwróconym przez <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>połączenie do .  
  
- <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType>na obiekcie klienta WCF generowanym przez program Svcutil.exe.  
  
- Zakończenie operacji na każdym typie obiektu klienta WCF (domyślnie żadne operacje nie kończą działalności; umowa musi jawnie określać operację zakończenia). Po wywołaniu pierwszej operacji obiekt klienta WCF automatycznie otwiera kanał i inicjuje sesję.  
  
 Na przykład zobacz [Jak: Tworzenie usługi, która wymaga sesji,](./feature-details/how-to-create-a-service-that-requires-sessions.md) a także [domyślne zachowanie usługi](./samples/default-service-behavior.md) i [instancing](./samples/instancing.md) przykłady.  
  
 Aby uzyskać więcej informacji o klientach i sesjach, zobacz [Uzyskiwanie dostępu do usług przy użyciu klienta WCF](./feature-details/accessing-services-using-a-client.md).  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Sesje współdziałają z ustawieniami intertekstu wystąpienia  
 Istnieje interakcja <xref:System.ServiceModel.SessionMode> między wyliczeniem w <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> umowie i właściwości, która kontroluje skojarzenie między kanałami i określonych obiektów usługi. Aby uzyskać więcej informacji, zobacz [Sesje, Instancing i Współbieżność](./feature-details/sessions-instancing-and-concurrency.md).  
  
### <a name="sharing-instancecontext-objects"></a>Udostępnianie obiektów instancjowych  
 Można również kontrolować, który kanał oparty na sesji <xref:System.ServiceModel.InstanceContext> lub wywołanie jest skojarzony z który obiekt, wykonując to skojarzenie samodzielnie.
  
## <a name="sessions-and-streaming"></a>Sesje i przesyłanie strumieniowe  
 Gdy masz dużą ilość danych do transferu, tryb przesyłania strumieniowego w WCF jest wykonalną alternatywą dla domyślnego zachowania buforowania i przetwarzania wiadomości w pamięci w całości. Może wystąpić nieoczekiwane zachowanie podczas przesyłania strumieniowego wywołań z powiązaniem opartym na sesji. Wszystkie wywołania przesyłania strumieniowego są dokonywane za pośrednictwem jednego kanału (kanału datagram), który nie obsługuje sesji, nawet jeśli używane powiązanie jest skonfigurowane do używania sesji. Jeśli wielu klientów dokonuje wywołań przesyłania strumieniowego do tego samego obiektu usługi za pośrednictwem powiązania opartego na sesji, `PerSession`a tryb współbieżności obiektu usługi jest ustawiony na jeden, a jego tryb kontekstowy wystąpienia jest ustawiony na , wszystkie wywołania muszą przejść przez kanał datagramu, a więc tylko jedno wywołanie jest przetwarzane w danym momencie. Jeden lub więcej klientów może następnie limit czasu. Można obejść ten problem, ustawiając obiekt `InstanceContextMode` usługi `PerCall` do lub współbieżności do wielu.  
  
> [!NOTE]
> MaxConcurrentSessions nie mają wpływu w tym przypadku, ponieważ istnieje tylko jedna "sesja" dostępne.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A>
- <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A>
