---
title: Sesje, tworzenie wystąpień i współbieżność
ms.date: 03/30/2017
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
ms.openlocfilehash: d780488f7bb0bd46a22ef205b3954b6b4614cae0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969214"
---
# <a name="sessions-instancing-and-concurrency"></a>Sesje, tworzenie wystąpień i współbieżność
*Sesja* jest korelacją wszystkich komunikatów wysyłanych między dwoma punktami końcowymi. Tworzenie *wystąpień* odnosi się do kontrolowania okresu istnienia obiektów usługi zdefiniowanej przez <xref:System.ServiceModel.InstanceContext> użytkownika i powiązanych z nimi obiektów. *Współbieżność* to termin nadawany kontroli nad liczbą wątków wykonywanych w <xref:System.ServiceModel.InstanceContext> tym samym czasie.  
  
 W tym temacie opisano te ustawienia, sposób ich używania oraz różne interakcje między nimi.  
  
## <a name="sessions"></a>Kategoria Sessions  
 Gdy kontrakt usługi ustawia <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> właściwość na <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>, ten kontrakt mówi, że wszystkie wywołania (czyli podstawowe wymiany komunikatów, które obsługują wywołania) muszą być częścią tej samej konwersacji. Jeśli kontrakt Określa, że zezwala na sesje, ale go nie wymaga, klienci mogą łączyć się i ustanawiać sesję. Jeśli sesja zostanie zakończona, a wiadomość jest wysyłana za pośrednictwem tego samego kanału opartego na sesji, zgłaszany jest wyjątek.  
  
 Sesje WCF mają następujące główne funkcje koncepcyjne:  
  
- Są one jawnie inicjowane i kończone przez aplikację wywołującą.  
  
- Komunikaty dostarczane podczas sesji są przetwarzane w kolejności, w jakiej zostały odebrane.  
  
- Sesje są skorelowane z grupą komunikatów w konwersacji. Znaczenie tej korelacji jest abstrakcyjne. Na przykład jeden kanał oparty na sesji może skorelować komunikaty na podstawie udostępnionego połączenia sieciowego, podczas gdy inny kanał oparty na sesji może skorelować komunikaty na podstawie tagu udostępnionego w treści komunikatu. Funkcje, które mogą pochodzić z sesji, zależą od charakteru korelacji.  
  
- Brak ogólnego magazynu danych skojarzonego z sesją WCF.  
  
 W przypadku znajomości <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> klasy w aplikacjach ASP.NET i udostępnianej przez nią funkcji, można zauważyć następujące różnice między tym rodzajem sesji a sesjami programu WCF:  
  
- Sesje ASP.NET są zawsze inicjowane przez serwer.  
  
- Sesje ASP.NET są niejawnie nieuporządkowane.  
  
- Sesje ASP.NET zapewniają ogólny mechanizm magazynowania danych między żądaniami.  
  
 Aplikacje klienckie i aplikacje usług współpracują z sesjami na różne sposoby. Aplikacje klienckie inicjują sesje, a następnie odbierają i przetwarzają komunikaty wysyłane w ramach sesji. Aplikacje usług mogą używać sesji jako punktu rozszerzalności, aby dodać dodatkowe zachowanie. Jest to realizowane przez pracę bezpośrednio z <xref:System.ServiceModel.InstanceContext> lub implementacją niestandardowego dostawcy kontekstu wystąpienia.  
  
## <a name="instancing"></a>Tworzenie wystąpienia  
 Zachowanie tworzenia wystąpienia (ustawiane przy użyciu <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> właściwości) kontroluje, <xref:System.ServiceModel.InstanceContext> w jaki sposób jest tworzony w odpowiedzi na komunikaty przychodzące. Domyślnie każda <xref:System.ServiceModel.InstanceContext> z nich jest skojarzona z jednym obiektem zdefiniowanym przez użytkownika, więc (w domyślnym przypadku) <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> ustawienie właściwości również kontroluje tworzenie obiektów usługi zdefiniowane przez użytkownika. <xref:System.ServiceModel.InstanceContextMode> Wyliczenie definiuje tryby wystąpienia.  
  
 Dostępne są następujące tryby wystąpienia:  
  
- <xref:System.ServiceModel.InstanceContextMode.PerCall>: Nowy <xref:System.ServiceModel.InstanceContext> (i ten obiekt usługi) jest tworzony dla każdego żądania klienta.  
  
- <xref:System.ServiceModel.InstanceContextMode.PerSession>: Nowy <xref:System.ServiceModel.InstanceContext> (i w związku z tym obiekt usługi) jest tworzony dla każdej nowej sesji klienta i utrzymywany przez okres istnienia tej sesji (wymaga to powiązania, które obsługuje sesje).  
  
- <xref:System.ServiceModel.InstanceContextMode.Single>: Pojedynczy <xref:System.ServiceModel.InstanceContext> (i w związku z tym obiekt usługi) obsługuje wszystkie żądania klientów w okresie istnienia aplikacji.  
  
 Poniższy przykład kodu pokazuje wartość domyślną <xref:System.ServiceModel.InstanceContextMode> , <xref:System.ServiceModel.InstanceContextMode.PerSession> która jest jawnie ustawiana w klasie usługi.  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]   
public class CalculatorService : ICalculatorInstance   
{   
    ...  
}  
```  
  
 A podczas gdy <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> Właściwość kontroluje, jak <xref:System.ServiceModel.InstanceContext> często jest wydawana <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> , <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> a właściwości i kontroluje, kiedy obiekt usługi jest wydawany.  
  
### <a name="well-known-singleton-services"></a>Dobrze znane usługi pojedyncze  
 Jedna odmiana obiektów usługi pojedynczego wystąpienia jest czasami przydatna: można utworzyć obiekt usługi samodzielnie i utworzyć hosta usługi za pomocą tego obiektu. W tym celu należy również ustawić <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> właściwość na <xref:System.ServiceModel.InstanceContextMode.Single> lub wyjątek jest zgłaszany podczas otwierania hosta usługi.  
  
 Użyj konstruktora <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> , aby utworzyć taką usługę. Jest to alternatywa dla wdrożenia niestandardowego <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> , gdy chcesz podać konkretne wystąpienie obiektu do użycia przez pojedynczą usługę. Można użyć tego przeciążenia, gdy typ implementacji usługi jest trudny do skonstruowania (na przykład jeśli nie implementuje domyślnego konstruktora publicznego bez parametrów).  
  
 Należy pamiętać, że gdy obiekt jest dostarczany do tego konstruktora, niektóre funkcje związane z zachowaniem wystąpienia Windows Communication Foundation (WCF) działają inaczej. Na przykład wywoływanie <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> nie ma wpływu na wystąpienie pojedynczego obiektu. Podobnie wszystkie inne mechanizmy zwalniania wystąpień są ignorowane. Zawsze zachowuje się tak, <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> jakby właściwość została ustawiona na <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> dla wszystkich operacji. <xref:System.ServiceModel.ServiceHost>  
  
### <a name="sharing-instancecontext-objects"></a>Udostępnianie obiektów InstanceContext  
 Można również kontrolować, które kanały sesji lub wywołania są skojarzone z <xref:System.ServiceModel.InstanceContext> tym obiektem przez wykonanie tego skojarzenia samodzielnie.  
  
## <a name="concurrency"></a>Współbieżność  
 Współbieżność to kontrola liczby wątków aktywnych w <xref:System.ServiceModel.InstanceContext> dowolnym momencie. Jest to kontrolowane przy użyciu <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ConcurrencyMode> z wyliczeniem.  
  
 Dostępne są następujące trzy tryby współbieżności:  
  
- <xref:System.ServiceModel.ConcurrencyMode.Single>: Każdy kontekst wystąpienia może mieć maksymalnie jeden komunikat przetwarzania wątku w danym momencie. Inne wątki, które chcą korzystać z tego samego kontekstu wystąpienia, muszą blokować do momentu opuszczenia kontekstu wystąpienia przez oryginalny wątek.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Multiple>: Każde wystąpienie usługi może mieć wiele wątków przetwarzających komunikaty współbieżnie. Implementacja usługi musi być bezpieczna wątkowo, aby można było używać tego trybu współbieżności.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant>: Każde wystąpienie usługi przetwarza jeden komunikat w danym momencie, ale akceptuje wywołania operacji ponownego wykonania. Usługa akceptuje te wywołania tylko wtedy, gdy jest wywoływany przez obiekt klienta WCF.  
  
> [!NOTE]
> Zrozumienie i Programowanie kodu, który bezpiecznie korzysta z więcej niż jednego wątku może być trudne do zapisania. Przed użyciem <xref:System.ServiceModel.ConcurrencyMode.Multiple> lub <xref:System.ServiceModel.ConcurrencyMode.Reentrant> wartości upewnij się, że usługa została prawidłowo zaprojektowana dla tych trybów. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>.  
  
 Użycie współbieżności jest związane z trybem wystąpienia. W <xref:System.ServiceModel.InstanceContextMode.PerCall> przypadku wystąpienia, współbieżność nie jest istotna, ponieważ każdy komunikat jest przetwarzany przez nowy <xref:System.ServiceModel.InstanceContext> i, dlatego nigdy więcej niż jeden <xref:System.ServiceModel.InstanceContext>wątek jest aktywny w.  
  
 Poniższy przykład kodu demonstruje ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> właściwości na. <xref:System.ServiceModel.ConcurrencyMode.Multiple>  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]   
public class CalculatorService : ICalculatorConcurrency   
{   
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Sesje współpracują z ustawieniami InstanceContext  
 Sesje i <xref:System.ServiceModel.InstanceContext> współdziałanie w zależności od kombinacji wartości <xref:System.ServiceModel.SessionMode> wyliczenia <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> w kontrakcie i właściwości implementacji usługi, która kontroluje skojarzenie między kanałami i konkretną obiekty usługi.  
  
 W poniższej tabeli przedstawiono wynik przychodzącego kanału obsługującego sesje lub nieobsługujący sesji, które podano kombinację wartości <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> właściwości <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> i właściwości.  
  
|Wartość InstanceContextmode|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|PerCall|-Zachowanie przy użyciu kanału sesji: Sesja i <xref:System.ServiceModel.InstanceContext> dla każdego wywołania.<br />-Zachowanie przy użyciu kanału bez sesji: Zgłaszany jest wyjątek.|-Zachowanie przy użyciu kanału sesji: Sesja i <xref:System.ServiceModel.InstanceContext> dla każdego wywołania.<br />-Zachowanie przy użyciu kanału bez sesji: <xref:System.ServiceModel.InstanceContext> Dla każdego wywołania.|-Zachowanie przy użyciu kanału sesji: Zgłaszany jest wyjątek.<br />-Zachowanie przy użyciu kanału bez sesji: <xref:System.ServiceModel.InstanceContext> Dla każdego wywołania.|  
|PerSession|-Zachowanie przy użyciu kanału sesji: Sesja i <xref:System.ServiceModel.InstanceContext> dla każdego kanału.<br />-Zachowanie przy użyciu kanału bez sesji: Zgłaszany jest wyjątek.|-Zachowanie przy użyciu kanału sesji: Sesja i <xref:System.ServiceModel.InstanceContext> dla każdego kanału.<br />-Zachowanie przy użyciu kanału bez sesji: <xref:System.ServiceModel.InstanceContext> Dla każdego wywołania.|-Zachowanie przy użyciu kanału sesji: Zgłaszany jest wyjątek.<br />-Zachowanie przy użyciu kanału bez sesji: <xref:System.ServiceModel.InstanceContext> Dla każdego wywołania.|  
|Single|-Zachowanie przy użyciu kanału sesji: Sesja i jeden <xref:System.ServiceModel.InstanceContext> dla wszystkich wywołań.<br />-Zachowanie przy użyciu kanału bez sesji: Zgłaszany jest wyjątek.|-Zachowanie przy użyciu kanału sesji: Sesja i <xref:System.ServiceModel.InstanceContext> dla pojedynczych utworzonych lub określonych przez użytkownika.<br />-Zachowanie przy użyciu kanału bez sesji: Dla <xref:System.ServiceModel.InstanceContext> obiektu utworzonego lub określonego przez użytkownika.|-Zachowanie przy użyciu kanału sesji: Zgłaszany jest wyjątek.<br />-Zachowanie przy użyciu kanału bez sesji: <xref:System.ServiceModel.InstanceContext> Dla każdego utworzonego pojedynczego lub dla pojedynczego użytkownika.|  
  
## <a name="see-also"></a>Zobacz także

- [Korzystanie z sesji](../../../../docs/framework/wcf/using-sessions.md)
- [Instrukcje: Tworzenie usługi wymagającej sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
- [Instrukcje: Kontrola wystąpień usług](../../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
- [Współbieżność](../../../../docs/framework/wcf/samples/concurrency.md)
- [Tworzenie wystąpienia](../../../../docs/framework/wcf/samples/instancing.md)
- [Sesja](../../../../docs/framework/wcf/samples/session.md)
