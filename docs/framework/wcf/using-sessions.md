---
title: Korzystanie z sesji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sessions [WCF]
ms.assetid: 864ba12f-3331-4359-a359-6d6d387f1035
ms.openlocfilehash: fc0bfec95e625c1433636fbe5e0fdb6cc1112b14
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645156"
---
# <a name="using-sessions"></a>Korzystanie z sesji
W aplikacjach Windows Communication Foundation (WCF) *sesji* koreluje grupę wiadomości do konwersacji. Sesje WCF są inne niż dostępne w obiekcie sesji [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplikacji obsługują różne zachowania i są kontrolowane na różne sposoby. W tym temacie opisano funkcje umożliwiające w sesji programu WCF aplikacji i sposobu ich używania.  
  
## <a name="sessions-in-windows-communication-foundation-applications"></a>Sesje w aplikacjach programu Windows Communication Foundation  
 Gdy kontrakt usługi określa, że wymaga sesji, kontrakt ten jest określenie, że wszystkie wywołania (czyli bazowego wymianę komunikatów, które obsługują wywołania) musi być częścią tej samej konwersacji. Jeśli kontrakt Określa, że zezwala na sesji, ale nie wymaga jednego, klienci mogą łączyć się i albo ustanowienia sesji lub nie ustanowienia sesji. Jeśli sesja zakończy się, a jeśli tak, to a wiadomość jest wysyłana za pośrednictwem tego samego kanału, który jest zwracany wyjątek.  
  
 Sesje WCF oferują następujące funkcje koncepcyjny główne:  
  
- Jawnie są inicjowane i został przerwany przez aplikacji wywołującej (klient WCF).  
  
- Wiadomości dostarczone w trakcie sesji są przetwarzane w kolejności, w której zostały odebrane.  
  
- Sesje skorelowania grupę wiadomości w konwersacji. Możliwe są różne rodzaje korelacji. Na przykład jeden kanał oparte na sesji mogą mieć związek komunikaty na podstawie sieci udostępnionego połączenia podczas inną drogą oparte na sesji mogą mieć związek wiadomości według znaczników udostępnionych w treści komunikatu. Funkcje, które mogą być uzyskane z sesji zależą od rodzaju korelacji.  
  
- Brak nie magazynu ogólnych danych skojarzonych z sesją usługi WCF.  
  
 Jeśli znasz <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> klasy w [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplikacji i funkcji zawiera, można zauważyć następujące różnice między tego rodzaju sesji i sesje WCF:  
  
- [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sesje są zawsze inicjowanych przez serwer.  
  
- [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sesje są niejawnie nieuporządkowane.  
  
- [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sesje udostępniają mechanizm magazynu danych ogólnych dla żądań.  
  
 W tym temacie opisano:  
  
- Wykonanie domyślnie podczas korzystania z powiązań oparte na sesji w warstwy modelu usług.  
  
- Typy funkcji zapewniających powiązaniami WCF opartego na sesji, dostarczane przez system.  
  
- Jak utworzyć kontraktu, który deklaruje wymóg sesji.  
  
- Jak zrozumieć i kontrolować utworzenia i zakończenia sesji oraz relacje sesji do wystąpienia usługi.  
  
## <a name="default-execution-behavior-using-sessions"></a>Domyślne wykonywania zachowanie przy użyciu sesji  
 Nosi nazwę powiązania, które podejmuje próbę zainicjowania sesji *oparte na sesji* powiązania. Określ kontraktów usług, że wymagają, zezwolić lub odmówić powiązania oparte na sesji, ustawiając <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> właściwość interfejsu kontraktu usługi (lub klasy) do jednego z <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> wartości wyliczenia. Domyślnie wartość tej właściwości jest <xref:System.ServiceModel.SessionMode.Allowed>, oznacza to, że jeśli klient używa powiązanie oparte na sesji z implementacji usługi WCF, usługa ustanawia i używa podanej sesji.  
  
 Gdy usługa WCF akceptuje sesji klienta, są domyślnie włączone następujące funkcje:  
  
1. Wszystkie wywołania między obiektem platformy WCF klienta są obsługiwane przez tego samego wystąpienia usługi.  
  
2. Różne powiązania oparte na sesji zapewniają dodatkowe funkcje.  
  
## <a name="system-provided-session-types"></a>Sesja dostarczane przez system typów  
 Powiązanie oparte na sesji obsługuje domyślne skojarzenie wystąpienia usługi w określonej sesji. Jednak różnych powiązania oparte na sesji obsługują różne funkcje oprócz włączenia oparte na sesji kontroli wystąpień opisany wcześniej.  
  
 Usługi WCF zawiera następujące typy zachowanie aplikacji opartych na sesji:  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType> Obsługuje oparty na zabezpieczeniach sesje, w których obu końcach komunikacji uzgodnionych określonej bezpiecznej konwersacji. Aby uzyskać więcej informacji, zobacz [zabezpieczania usług](../../../docs/framework/wcf/securing-services.md). Na przykład <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType> powiązania, który zawiera obsługę zarówno dla sesji bezpieczeństwa i sesje niezawodne, domyślnie używa tylko bezpiecznej sesji, który szyfruje i podpisuje cyfrowo wiadomości.  
  
- <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> Powiązanie obsługuje opartego na protokole IP sesji, aby upewnić się, że wszystkie komunikaty są powiązane przez połączenie na poziomie gniazd.  
  
- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> Element, który implementuje specyfikacji WS-ReliableMessaging, zapewnia obsługę dotyczące sesji niezawodnych, w których można skonfigurować wiadomości, aby być dostarczane w kolejności i dokładnie raz, zapewniając komunikaty są odbierane, nawet wtedy, gdy wiadomości przesyłane w wielu węzłach podczas rozmowy. Aby uzyskać więcej informacji, zobacz [sesje niezawodnej](../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
- <xref:System.ServiceModel.NetMsmqBinding?displayProperty=nameWithType> Powiązanie obsługuje sesje datagram usługi MSMQ. Aby uzyskać więcej informacji, zobacz [kolejki programu WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
 Ustawienie <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> właściwość nie określa typ sesji wymaga umowy, tylko jeden wymagane przez dział it.  
  
## <a name="creating-a-contract-that-requires-a-session"></a>Tworzenie kontraktu, który wymaga sesji  
 Tworzenie kontraktu, który wymaga sesję stwierdza, że grupy działań, które deklaruje kontraktu usługi musi wszystkie można wykonać w obrębie tej samej sesji i że wiadomości musi być dostarczane w kolejności. Do potwierdzenia poziom obsługi sesji, która wymaga kontraktu usługi, należy ustawić <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> właściwości na interfejsu kontraktu usługi lub klasy wartości <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> wyliczeniu, aby określić, czy kontrakt:  
  
- Wymaga sesji.  
  
- Umożliwia klienta w celu ustanowienia sesji.  
  
- Zabrania sesji.  
  
 Ustawienie <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> właściwości nie, jednak określić typ oparte na sesji zachowania kontrakt wymaga. Informuje WCF, aby upewnić się, w czasie wykonywania, skonfigurowane powiązanie (który tworzy kanał komunikacyjny) usługa, nie jest ani można ustanowić sesji podczas wdrażania usługi. Ponownie powiązanie może spełnić tego wymogu przy użyciu dowolnego typu na podstawie sesji zachowanie go wybierze — zabezpieczeń, transport, niezawodne lub kombinację. Dokładne zachowanie zależy <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> wybranej wartości. Jeśli skonfigurowanego powiązania usługi nie jest zgodny z wartością <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A>, zgłaszany jest wyjątek. Powiązania i kanałów mogą tworzyć, że sesji pomocy technicznej są określane jako oparte na sesji.  
  
 Następujące kontrakt usługi określa, że wszystkie operacje w `ICalculatorSession` muszą być wymieniane w ramach sesji. Brak operacji zwraca wartość do obiektu wywołującego, z wyjątkiem `Equals` metody. Jednak `Equals` metoda nie przyjmuje żadnych parametrów i dlatego może zwracać tylko wartość niezerową w ramach sesji, w którym danych został już przekazany do innych operacji. Ten kontrakt wymaga elementu session działać prawidłowo. Bez sesję skojarzone z określonego klienta wystąpienie usługi nie ma możliwości, wiedząc, jakie dane poprzedniego wysłał tego klienta.  
  
 [!code-csharp[S_Service_Session#1](../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
 Jeśli usługa umożliwia sesję, następnie sesji jest nawiązane i używane, jeśli klient inicjuje w przeciwnym razie sesja nie zostanie nawiązane.  
  
## <a name="sessions-and-service-instances"></a>Sesje i wystąpień usługi  
 Jeśli używasz domyślnego wystąpień zachowanie programu WCF, wszystkie wywołania między obiektem klienta platformy WCF są obsługiwane przez tego samego wystąpienia usługi. W związku z tym na poziomie aplikacji, można traktować sesji co włączenie zachowanie aplikacji, podobnie jak zachowanie połączenia lokalnego. Na przykład podczas tworzenia obiektu lokalnego:  
  
- Konstruktor jest wywoływana.  
  
- Wszystkie kolejne wywołania odwołanie do obiektu klienta programu WCF są przetwarzane przez tego samego wystąpienia obiektu.  
  
- Destruktor jest wywoływany, kiedy niszczony jest odwołanie do obiektu.  
  
 Sesje Włącz zachowanie podobne między klientami i usługami, tak długo, jak domyślne zachowanie wystąpienia usługi jest używana. Jeśli kontraktu usługi wymaga lub obsługuje sesji, co najmniej jednej operacji kontraktu może być oznaczona jako inicjowania lub zakończenia sesji, ustawiając <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A> i <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A> właściwości.  
  
 *Inicjowanie operacji* te, które musi zostać wywołana jako pierwszą operacją nowej sesji. Inicjowanie inne niż operacje można wywołać tylko wtedy, gdy została wywołana co najmniej jedną operację inicjujący. W związku z tym można utworzyć typu konstruktora sesji usługi przez zadeklarowanie zainicjować operacji projektowane w celu wejściowego od klientów odpowiednie do stanu sprzed wystąpienia usługi. (Stan jest skojarzony z sesji, jednak a nie obiekt usługi).  
  
 *Kończenie operacji*, z drugiej strony, to te, które musi zostać wywołana jako ostatni komunikat w istniejącej sesji. W przypadku domyślnej WCF jest odtwarzana obiekt usługi i jej kontekstu po zamknięciu sesji, z którą została skojarzona usługa. W związku z tym, można utworzyć rodzaj destruktor przez zadeklarowanie powodujący zakończenie operacji przeznaczony do wykonywania funkcji, które są odpowiednie do końca wystąpienia usługi.  
  
> [!NOTE]
>  Domyślne zachowanie nosi podobieństwo do lokalnego konstruktory i destruktory, ale jest tylko bardzo podobne. Inicjowanie powodujący zakończenie działania i/lub w tym samym czasie, może być żadnej operacji usługi WCF. Ponadto w przypadku domyślnej Inicjowanie operacji można wywołać dowolną liczbę razy w dowolnej kolejności. nie dodatkowych sesji są tworzone, gdy sesja zostanie ustanowione i skojarzone z wystąpieniem, chyba że jawnie kontrolować okres istnienia wystąpienia usługi (przez operacje <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> obiektu). Na koniec stanu jest skojarzony z sesji, a nie obiekt usługi.  
  
 Na przykład `ICalculatorSession` używane w poprzednim przykładzie kontrakt wymaga elementu czy klienta platformy WCF obiektu pierwsze wywołanie `Clear` operacji przed wszystkie inne czynności i który sesji z tym obiektem klienta WCF należy zakończyć, gdy wywołuje `Equals` operacji. Poniższy przykład kodu pokazuje kontraktu, który wymusza te wymagania. `Clear` musi zostać wywołane najpierw zainicjowania sesji, i że sesja zakończy się, kiedy `Equals` jest wywoływana.  
  
 [!code-csharp[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.isinitiatingisterminating/cs/service.cs#1)]
 [!code-vb[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.isinitiatingisterminating/vb/service.vb#1)]  
  
 Usługi nie są uruchamiane sesje z klientami. W aplikacjach klienckich usługi WCF bezpośrednią relację między istnieje okres istnienia kanału oparte na sesji i okres istnienia sesji sam. Jako takie klienci utworzyć nowej sesji, tworząc nowe kanały oparte na sesji i zatrzymywania istniejące sesje, zamykając bezpiecznie kanały oparte na sesji. Klient uruchamia sesję z punktem końcowym usługi, wywołując jedną z następujących czynności:  
  
- <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> w kanale zwracany przez wywołanie <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>.  
  
- <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> w obiekcie klienta WCF, generowane przez [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
- Zainicjować operacji na dowolnego typu obiektu klienta WCF (domyślnie, wszystkie operacje są Inicjowanie). Po wywołaniu pierwszą operacją obiektu klienta programu WCF automatycznie zostanie otwarty kanał i inicjuje sesję.  
  
 Zazwyczaj klient kończy sesję, korzystając z punktu końcowego usługi, wywołując jedną z następujących czynności:  
  
- <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> w kanale zwracany przez wywołanie <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>.  
  
- <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType> w obiekcie klienta WCF, generowane przez Svcutil.exe.  
  
- Trwa przerywanie działania operacji dla dowolnego typu obiektu klienta programu WCF (domyślnie są Kończenie żadnych operacji; kontrakt należy jawnie określić powodujący zakończenie działania). Po wywołaniu pierwszą operacją obiektu klienta programu WCF automatycznie zostanie otwarty kanał i inicjuje sesję.  
  
 Aby uzyskać przykłady, zobacz [jak: Tworzenie usługi, wymaga sesji](../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md) , jak również [domyślne zachowanie usługi](../../../docs/framework/wcf/samples/default-service-behavior.md) i [Instancing](../../../docs/framework/wcf/samples/instancing.md) przykłady.  
  
 Aby uzyskać więcej informacji na temat klientów i sesji, zobacz [uzyskiwanie dostępu do usług za pomocą klienta WCF](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Sesje wchodzić w interakcje przy użyciu typu InstanceContext ustawień  
 Brak interakcji między <xref:System.ServiceModel.SessionMode> wyliczenia w Umowie oraz <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> właściwość, która kontroluje skojarzenie między kanałów i obiektów określonej usługi. Aby uzyskać więcej informacji, zobacz [sesji, Instancing i współbieżności](../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md).  
  
### <a name="sharing-instancecontext-objects"></a>Udostępnianie obiektów typu InstanceContext  
 Można również sterować określające kanał oparte na sesji lub wywołanie jest skojarzone z którym <xref:System.ServiceModel.InstanceContext> obiektu, wykonując tego skojarzenia, samodzielnie. 
  
## <a name="sessions-and-streaming"></a>Sesje i przesyłania strumieniowego  
 W przypadku dużych ilości danych do przesłania strumieniowego tryb transferu programu WCF jest możliwe alternatywa domyślne zachowanie buforowania i przetwarzanie komunikatów w pamięci w całości. Podczas przesyłania strumieniowego wywołania z powiązaniem oparte na sesji, może wystąpić nieoczekiwane zachowanie. Wszystkie wywołania przesyłania strumieniowego są nawiązywane przy użyciu jednego kanału (kanał datagram), który nie obsługuje sesji, nawet jeśli powiązania, używany jest skonfigurowany do używania sesji. Jeśli wielu klientów wywołań przesyłania strumieniowego do tego samego obiektu usługi za pośrednictwem powiązania oparte na sesji i tryb współbieżności obiekt usługi jest ustawiony na jednym i jego wystąpienie kontekstu tryb jest ustawiony na `PerSession`, wywołania musi przechodzić przez kanał datagram, a tym samym tylko jedno wywołanie są przetwarzane w danym momencie. Co najmniej jeden klient może następnie limit czasu. Można obejść ten problem, ustawiając obiektu usługi `InstanceContextMode` do `PerCall` lub współbieżności do wielu.  
  
> [!NOTE]
>  MaxConcurrentSessions w tym przypadku przyniosło żadnego skutku, ponieważ istnieje tylko jeden "sesja".  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A>
- <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A>
