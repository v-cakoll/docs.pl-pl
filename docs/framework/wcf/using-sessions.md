---
title: Korzystanie z sesji
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sessions [WCF]
ms.assetid: 864ba12f-3331-4359-a359-6d6d387f1035
caps.latest.revision: 32
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 172ef71bd3ae09e3c9f15cb0bdb48728a587605e
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="using-sessions"></a>Korzystanie z sesji
W [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikacji, *sesji* są powiązane z grupą wiadomości do konwersacji. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sesje są inne niż dostępna w obiekcie sesji [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplikacji, obsługuje różne zachowania i są kontrolowane na różne sposoby. W tym temacie opisano funkcje, które sesji umożliwiają w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacji i sposobu ich używania.  
  
## <a name="sessions-in-windows-communication-foundation-applications"></a>Sesje w aplikacjach programu Windows Communication Foundation  
 Gdy kontrakt usługi określa, że wymaga ona sesji, umowy jest określenie, że wszystkie wywołania (to znaczy podstawowej wymiany komunikatów obsługujących wywołania) musi być częścią jednej konwersacji. Jeśli kontrakt Określa, że umożliwia sesji, ale nie wymaga jednego, klienci mogą łączyć się i albo ustanowienia sesji lub nie ustanowienia sesji. Jeśli sesja zakończy się oraz komunikat jest wysyłany za pośrednictwem tego samego kanału, który jest zwracany wyjątek.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sesje mają następujące funkcje koncepcyjnej główne:  
  
-   Jawnie są inicjowane i został przerwany przez wywołanie aplikacji (klienta WCF).  
  
-   Komunikaty dostarczone podczas sesji są przetwarzane w kolejności, w którym są odbierane.  
  
-   Sesje skorelowania grupy wiadomości w konwersacji. Możliwe są różnego rodzaju korelacji. Na przykład jeden kanał opartymi na sesji mogą mieć związek wiadomości opartych na połączenie sieciowe udostępnionych podczas innego opartymi na sesji kanału może skorelować wiadomości opartych na udostępnionych tagu w treści wiadomości. Funkcje, które mogą być uzyskane z sesji są zależne od charakteru korelacji.  
  
-   Brak ma skojarzone z magazynu danych ogólnych [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sesji.  
  
 Jeśli znasz <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> klasy w [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplikacji i funkcji umożliwia, można zauważyć następujące różnice między tego rodzaju sesji i [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sesji:  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sesje są zawsze inicjowanych przez serwer.  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sesje są niejawnie nieuporządkowaną.  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sesje udostępniają mechanizm magazynu danych ogólnych żądań.  
  
 W tym temacie opisano:  
  
-   Domyślne wykonywania zachowanie przy użyciu powiązań opartymi na sesji w warstwy modelu usług.  
  
-   Typy funkcji [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Podaj powiązania opartymi na sesji, dostarczane przez system.  
  
-   Jak utworzyć kontrakt, który deklaruje wymóg sesji.  
  
-   Jak zrozumieć i kontrolować tworzenia i zakończenia sesji i ich relacji z sesji do wystąpienia usługi.  
  
## <a name="default-execution-behavior-using-sessions"></a>Domyślne wykonywania zachowanie przy użyciu sesji  
 Nosi nazwę powiązania, które próbuje zainicjować sesję *opartymi na sesji* powiązania. Kontrakty usług określić, że ich wymagają, zezwolić lub odmówić powiązania opartymi na sesji przez ustawienie <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> właściwości interfejsu kontraktu usługi (lub klasy) do jednego z <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> wartości wyliczenia. Domyślna wartość tej właściwości to <xref:System.ServiceModel.SessionMode.Allowed>, co oznacza, że jeśli klient używa powiązania opartymi na sesji z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] implementacji usługi Usługa ustanawia i używa sesji podane.  
  
 Gdy [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługa akceptuje sesji klienta, są domyślnie włączone następujące funkcje:  
  
1.  Wszystkie wywołania między [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obiektu klienta są obsługiwane przez tego samego wystąpienia usługi.  
  
2.  Różne powiązania opartymi na sesji oferują dodatkowe funkcje.  
  
## <a name="system-provided-session-types"></a>Typy sesji dostarczane przez system  
 Powiązanie opartymi na sesji obsługuje domyślne skojarzenie wystąpienia usługi z określoną sesją. Jednak różnych powiązania opartymi na sesji obsługuje różne funkcje oprócz włączenia opartymi na sesji sterowania wystąpień opisany wcześniej.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] udostępnia następujące rodzaje zachowanie aplikacji opartych na sesji:  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType> Obsługuje sesji na podstawie zabezpieczeń, w których oba końce elementu komunikacji przyjmują określonej bezpiecznej konwersacji. Aby uzyskać więcej informacji, zobacz [zabezpieczania usług](../../../docs/framework/wcf/securing-services.md). Na przykład <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType> powiązanie, który zawiera pomocy technicznej dla sesji zabezpieczeń i sesje niezawodne, domyślnie używa tylko bezpiecznej sesji i podpisaniu wiadomości.  
  
-   <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> Powiązanie obsługuje opartych na protokole TCP/IP sesji, aby upewnić się, skorelowanych wszystkie komunikaty dla tego połączenia na poziomie gniazda.  
  
-   <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> Element, który implementuje specyfikacji WS-ReliableMessaging, zapewnia obsługę niezawodne sesje, w których można skonfigurować komunikaty mają być dostarczone w kolejności i dokładnie, po sprawdzeniu, nawet wtedy, gdy są przesyłane komunikaty są odbierane wiadomości w wielu węzłach podczas konwersacji. Aby uzyskać więcej informacji, zobacz [sesji niezawodnej](../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
-   <xref:System.ServiceModel.NetMsmqBinding?displayProperty=nameWithType> Powiązanie obsługuje sesje datagramu MSMQ. Aby uzyskać więcej informacji, zobacz [kolejki programu WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
 Ustawienie <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> właściwość nie określa typ sesji kontrakt wymaga, tylko że wymaga jednego.  
  
## <a name="creating-a-contract-that-requires-a-session"></a>Tworzenie kontraktu wymagającego sesji  
 Tworzenie kontraktu, który wymaga sesji stwierdza, że grupy działań, które deklaruje kontraktu usługi musi wszystkie można wykonać w obrębie tej samej sesji i że wiadomości musi być dostarczane w kolejności. Do potwierdzenia poziom obsługi sesji, która wymaga kontraktu usługi, należy ustawić <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> właściwości interfejsu kontraktu usługi lub klasy do wartości <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> wyliczeniu, aby określić, czy kontrakt:  
  
-   Wymaga sesji.  
  
-   Umożliwia klientowi ustanowienia sesji.  
  
-   Zabrania używania sesji.  
  
 Ustawienie <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> właściwości, jednak określić typ zachowania opartymi na sesji kontrakt wymaga. Informuje [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] o potwierdzenie w czasie wykonywania który skonfigurowane powiązanie (tworzącej kanał komunikacyjny) usługa, nie obsługuje lub można ustanowić sesji podczas wdrażania usługi. Ponownie, powiązania spełnia tego wymagania w przypadku każdego typu opartymi na sesji zachowanie wybiera — zabezpieczeń, transport, niezawodnych lub kombinację. Dokładne zachowanie zależy od <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> wybranej wartości. Jeśli skonfigurowanego powiązania usługi nie jest zgodny z wartością <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A>, jest zgłaszany wyjątek. Powiązania i kanały tworzenia czy sesji pomocy technicznej są określane jako opartymi na sesji.  
  
 Następujące kontrakt usługi określa, że wszystkie operacje w `ICalculatorSession` muszą być wymieniane w ramach sesji. Żadna z operacji zwraca wartość do wywołującego, z wyjątkiem `Equals` metody. Jednak `Equals` — metoda nie przyjmuje żadnych parametrów i, w związku z tym może zwracać tylko wartości niezerowej, wewnątrz sesji, w którym dane już został przekazany do innych operacji. Ten kontrakt wymaga elementu session działać prawidłowo. Bez sesji skojarzonego z określonym kliencie wystąpienie usługi nie ma możliwości otrzymuje żadnej informacji o poprzedniej danych wysłał tego klienta.  
  
 [!code-csharp[S_Service_Session#1](../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
 Jeśli usługa umożliwia sesji, następnie sesji jest ustanowić i używane, jeśli klient jest inicjowany w przeciwnym razie nie ustanowiono.  
  
## <a name="sessions-and-service-instances"></a>Sesje i wystąpień usługi  
 Jeśli użytkownik korzysta z domyślnych wystąpień zachowanie w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], wszystkie wywołania między [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obiektu klienta są obsługiwane przez tego samego wystąpienia usługi. W związku z tym na poziomie aplikacji, można traktować sesji jako włączenie zachowanie aplikacji podobne do zachowania połączenia lokalnego. Na przykład podczas tworzenia obiektu lokalnego:  
  
-   Konstruktor jest wywoływana.  
  
-   Wszystkie kolejne wywołania [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] odwołanie do obiektu klienta są przetwarzane przez to samo wystąpienie obiektu.  
  
-   Destruktora jest wywoływane, gdy odwołanie do obiektu zostanie zniszczony.  
  
 Sesje Włącz podobne zachowanie między klientami i usługami tak długo, jak jest używane domyślne zachowanie wystąpienia usługi. Jeśli kontrakt usługi wymaga lub obsługuje sesji, co najmniej jeden kontrakt operacji może być oznaczony jako inicjowanie lub zakończenia sesji przez ustawienie <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A> i <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A> właściwości.  
  
 *Inicjowanie operacji* to takie, które musi zostać wywołana jako pierwszą operacją nowej sesji. Operacje inicjowania nie można wywołać tylko wtedy, gdy co najmniej jedną operację inicjujący została wywołana. W związku z tym można utworzyć typu konstruktora sesji usługi przez zadeklarowanie inicjujący działania mające na celu pobrać dane wejściowe z klientów odpowiednie na początku wystąpienia usługi. (Stan jest skojarzony z sesji i nie obiekt usługi).  
  
 *Kończenie operacji*, natomiast to takie, które musi zostać wywołana jako ostatnią wiadomością w istniejącej sesji. W przypadku domyślnej [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] po zamknięciu sesji, z którym usługa została powiązana jest odtwarzana obiekt usługi i jego kontekstu. W związku z tym można utworzyć rodzaj destruktora przez zadeklarowanie przerywania działania mające na celu wykonywania funkcji odpowiednie do końca wystąpienia usługi.  
  
> [!NOTE]
>  Domyślne zachowanie nosi podobieństwa do lokalnego konstruktory i destruktory, ale jest tylko wynik. Wszelkie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Operacja usługi może być inicjowanie zakończenia operacji i/lub w tym samym czasie. Ponadto w przypadku domyślne Inicjowanie operacji można wywołać dowolną liczbę razy w dowolnej kolejności. nie dodatkowych sesji są tworzone po ustanowić sesję i skojarzone z wystąpieniem, chyba że jawnie zarządzają okresem istnienia wystąpienia usługi (przez manipulowanie <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> obiektu). Na koniec stan jest skojarzony z sesji, a nie obiektu usługi.  
  
 Na przykład `ICalculatorSession` kontraktu użyty w poprzednim przykładzie wymaga, aby [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] pierwsze wywołanie obiektu klienta `Clear` operacji przed innej operacji i że sesji z tym [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] powinien obiektu klienta Kiedy wywołuje `Equals` operacji. Poniższy przykład kodu pokazuje kontraktu, która wymusza te wymagania. `Clear` Najpierw należy wywołać do zainicjowania sesji, i że kończenia sesji, gdy `Equals` jest wywoływana.  
  
 [!code-csharp[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.isinitiatingisterminating/cs/service.cs#1)]
 [!code-vb[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.isinitiatingisterminating/vb/service.vb#1)]  
  
 Usługi nie są uruchamiane sesje z klientami. W [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacje klienckie bezpośrednie relację między okres istnienia kanału opartymi na sesji i okresem istnienia sesji sam. Tak klienci tworzenia nowej sesji przez utworzenie nowych kanałów opartymi na sesji i zniszcz istniejące sesje, zamykając bezpiecznie kanały opartymi na sesji. Klient uruchamia sesję z punktem końcowym usługi wywołując jedną z następujących czynności:  
  
-   <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> w kanale zwrócony przez wywołanie do <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>.  
  
-   <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> na [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] generowanych przez obiekt klient [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
-   Operacja inicjujący w obu typów [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obiektu klienta (domyślnie wszystkie operacje są Inicjowanie). Po pierwszej operacji [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obiektu klienta automatycznie otwiera kanału i inicjuje sesję.  
  
 Zazwyczaj klient kończy sesję przy użyciu punktu końcowego usługi wywołując jedną z następujących czynności:  
  
-   <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> w kanale zwrócony przez wywołanie do <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>.  
  
-   <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType> na [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] generowane przez Svcutil.exe obiektu klienta.  
  
-   Trwa przerywanie działania operacji na obu typów [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obiektu klienta (domyślnie żadne operacje nie są przerywanie; kontrakt musi zawierać jawnie zakończenia operacji). Po pierwszej operacji [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obiektu klienta automatycznie otwiera kanału i inicjuje sesję.  
  
 Przykłady można znaleźć [porady: Tworzenie usługi czy wymaga sesji](../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md) , jak również [domyślne zachowanie usługi](../../../docs/framework/wcf/samples/default-service-behavior.md) i [Instancing](../../../docs/framework/wcf/samples/instancing.md) próbek.  
  
 Aby uzyskać więcej informacji dotyczących klientów i sesji, zobacz [dostęp do usług za pomocą klienta WCF](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Sesje interakcję z ustawieniami InstanceContext  
 Brak interakcji między <xref:System.ServiceModel.SessionMode> wyliczenia w umowie i <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> właściwość, która określa skojarzenie między kanałów i obiektów określonej usługi. Aby uzyskać więcej informacji, zobacz [sesji, Instancing i współbieżność](../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md).  
  
### <a name="sharing-instancecontext-objects"></a>Udostępnianie obiektów InstanceContext  
 Można również sterować kanał opartymi na sesji lub połączenia jest skojarzony z którym <xref:System.ServiceModel.InstanceContext> obiektu przez siebie wykonanie tego skojarzenia. Pełny przykład, zobacz [InstanceContextSharing](http://msdn.microsoft.com/library/4a6a46d7-b7d7-4bb5-a0dd-03ffa3cbc230).  
  
## <a name="sessions-and-streaming"></a>Sesje i przesyłania strumieniowego  
 Jeśli masz dużą ilość danych do przesłania tryb strumieniowy transfer w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] jest możliwe alternatywą do domyślne zachowanie buforowania i przetwarzanie komunikatów w pamięci w całości. Mogą wystąpić nieoczekiwane zachowanie podczas przesyłania strumieniowego wywołania z powiązaniem opartymi na sesji. Wszystkie wywołania przesyłania strumieniowego są nawiązywane przy użyciu jednego kanału (kanale datagramowym), który nie obsługuje sesji, nawet jeśli powiązania, używany jest skonfigurowana do używania sesji. Jeśli wielu klientów wywołań przesyłania strumieniowego do tego samego obiektu usługi za pośrednictwem powiązania opartymi na sesji i tryb współbieżności obiekt usługi jest ustawiony na jednym i jej wystąpienia kontekstu tryb ustawiono `PerSession`, wywołania musi przechodzić przez kanał datagram i dlatego tylko jedno wywołanie są przetwarzane pojedynczo. Co najmniej jeden klient następnie może upłynął limit czasu. Można obejść ten problem, ustawiając obiektu usługi `InstanceContextMode` do `PerCall` lub współbieżności do wielu.  
  
> [!NOTE]
>  MaxConcurrentSessions nie obowiązują w takim przypadku ponieważ jest dostępna tylko jedna "sesja".  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A>
