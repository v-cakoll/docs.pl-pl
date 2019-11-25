---
title: Sesje, tworzenie wystąpień i współbieżność
ms.date: 03/30/2017
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
ms.openlocfilehash: b8c0b40ca67de92f4f1b481298a8a26d96e887d4
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976089"
---
# <a name="sessions-instancing-and-concurrency"></a>Sesje, tworzenie wystąpień i współbieżność
*Sesja* jest korelacją wszystkich komunikatów wysyłanych między dwoma punktami końcowymi. Tworzenie *wystąpień* odnosi się do kontrolowania okresu istnienia obiektów usługi zdefiniowanej przez użytkownika i powiązanych z nimi obiektów <xref:System.ServiceModel.InstanceContext>. *Współbieżność* to termin nadawany kontroli liczby wątków wykonywanych w <xref:System.ServiceModel.InstanceContext> w tym samym czasie.  
  
 W tym temacie opisano te ustawienia, sposób ich używania oraz różne interakcje między nimi.  
  
## <a name="sessions"></a>Kategoria Sessions  
 Gdy kontrakt usługi ustawia właściwość <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>, ten kontrakt stwierdza, że wszystkie wywołania (czyli podstawowe wymiany komunikatów obsługujące wywołania) muszą być częścią tej samej konwersacji. Jeśli kontrakt Określa, że zezwala na sesje, ale go nie wymaga, klienci mogą łączyć się i ustanawiać sesję. Jeśli sesja zostanie zakończona, a wiadomość jest wysyłana za pośrednictwem tego samego kanału opartego na sesji, zgłaszany jest wyjątek.  
  
 Sesje WCF mają następujące główne funkcje koncepcyjne:  
  
- Są one jawnie inicjowane i kończone przez aplikację wywołującą.  
  
- Komunikaty dostarczane podczas sesji są przetwarzane w kolejności, w jakiej zostały odebrane.  
  
- Sesje są skorelowane z grupą komunikatów w konwersacji. Znaczenie tej korelacji jest abstrakcyjne. Na przykład jeden kanał oparty na sesji może skorelować komunikaty na podstawie udostępnionego połączenia sieciowego, podczas gdy inny kanał oparty na sesji może skorelować komunikaty na podstawie tagu udostępnionego w treści komunikatu. Funkcje, które mogą pochodzić z sesji, zależą od charakteru korelacji.  
  
- Brak ogólnego magazynu danych skojarzonego z sesją WCF.  
  
 W przypadku znajomości klasy <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> w aplikacjach ASP.NET i udostępnianej przez nią funkcji, można zauważyć następujące różnice między tym rodzajem sesji a sesjami programu WCF:  
  
- Sesje ASP.NET są zawsze inicjowane przez serwer.  
  
- Sesje ASP.NET są niejawnie nieuporządkowane.  
  
- Sesje ASP.NET zapewniają ogólny mechanizm magazynowania danych między żądaniami.  
  
 Aplikacje klienckie i aplikacje usług współpracują z sesjami na różne sposoby. Aplikacje klienckie inicjują sesje, a następnie odbierają i przetwarzają komunikaty wysyłane w ramach sesji. Aplikacje usług mogą używać sesji jako punktu rozszerzalności, aby dodać dodatkowe zachowanie. Jest to realizowane przez pracę bezpośrednio z <xref:System.ServiceModel.InstanceContext> lub implementacją niestandardowego dostawcy kontekstu wystąpień.  
  
## <a name="instancing"></a>Tworzenie wystąpienia  
 Zachowanie tworzenia wystąpień (ustawiane za pomocą właściwości <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType>) kontroluje sposób, w jaki <xref:System.ServiceModel.InstanceContext> jest tworzony w odpowiedzi na komunikaty przychodzące. Domyślnie każda <xref:System.ServiceModel.InstanceContext> jest skojarzona z jednym obiektem usługi zdefiniowanym przez użytkownika, więc (w przypadku domyślnym) ustawienie właściwości <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> również steruje tworzeniem obiektów usługi zdefiniowanych przez użytkownika. Wyliczenie <xref:System.ServiceModel.InstanceContextMode> definiuje tryby wystąpień.  
  
 Dostępne są następujące tryby wystąpienia:  
  
- <xref:System.ServiceModel.InstanceContextMode.PerCall>: dla każdego żądania klienta jest tworzony nowy <xref:System.ServiceModel.InstanceContext> (i ten obiekt usługi).  
  
- <xref:System.ServiceModel.InstanceContextMode.PerSession>: dla każdej nowej sesji klienta jest tworzony nowy <xref:System.ServiceModel.InstanceContext> (a w związku z tym obiekt usługi), który jest obsługiwany przez okres istnienia tej sesji (wymaga to powiązania, które obsługuje sesje).  
  
- <xref:System.ServiceModel.InstanceContextMode.Single>: pojedynczy <xref:System.ServiceModel.InstanceContext> (i w związku z tym obiekt usługi) obsługuje wszystkie żądania klientów w okresie istnienia aplikacji.  
  
 Poniższy przykład kodu pokazuje domyślną wartość <xref:System.ServiceModel.InstanceContextMode>, <xref:System.ServiceModel.InstanceContextMode.PerSession> być jawnie ustawiona w klasie usługi.  
  
```csharp  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]   
public class CalculatorService : ICalculatorInstance   
{   
    ...  
}  
```  
  
 Natomiast Właściwość <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> kontroluje, jak często <xref:System.ServiceModel.InstanceContext> jest wydawana, właściwości <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> kontrolują, kiedy obiekt usługi jest wydawany.  
  
### <a name="well-known-singleton-services"></a>Dobrze znane usługi pojedyncze  
 Jedna odmiana obiektów usługi pojedynczego wystąpienia jest czasami przydatna: można utworzyć obiekt usługi samodzielnie i utworzyć hosta usługi za pomocą tego obiektu. W tym celu należy również ustawić właściwość <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.InstanceContextMode.Single> lub wyjątek jest zgłaszany podczas otwierania hosta usługi.  
  
 Użyj konstruktora <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType>, aby utworzyć taką usługę. Jest to alternatywa dla implementacji niestandardowego <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType>, jeśli chcesz podać konkretne wystąpienie obiektu do użycia przez pojedynczą usługę. Można użyć tego przeciążenia, gdy typ implementacji usługi jest trudny do skonstruowania (na przykład, jeśli nie implementuje konstruktora publicznego bez parametrów).  
  
 Należy pamiętać, że gdy obiekt jest dostarczany do tego konstruktora, niektóre funkcje związane z zachowaniem wystąpienia Windows Communication Foundation (WCF) działają inaczej. Na przykład wywoływanie <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> nie ma wpływu na wystąpienie pojedynczego obiektu. Podobnie wszystkie inne mechanizmy zwalniania wystąpień są ignorowane. <xref:System.ServiceModel.ServiceHost> zawsze zachowuje się tak, jakby Właściwość <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> została ustawiona na <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> dla wszystkich operacji.  
  
### <a name="sharing-instancecontext-objects"></a>Udostępnianie obiektów InstanceContext  
 Można również kontrolować, które kanały sesji lub wywołania są skojarzone z tym obiektem <xref:System.ServiceModel.InstanceContext> przez wykonywanie tego skojarzenia samodzielnie.  
  
## <a name="concurrency"></a>Współbieżność  
 Współbieżność to kontrolka liczby wątków aktywnych w <xref:System.ServiceModel.InstanceContext> w dowolnym momencie. Jest to kontrolowane przy użyciu <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> z wyliczeniem <xref:System.ServiceModel.ConcurrencyMode>.  
  
 Dostępne są następujące trzy tryby współbieżności:  
  
- <xref:System.ServiceModel.ConcurrencyMode.Single>: każdy kontekst wystąpienia może mieć maksymalnie jeden komunikat przetwarzania wątku w danym momencie. Inne wątki, które chcą korzystać z tego samego kontekstu wystąpienia, muszą blokować do momentu opuszczenia kontekstu wystąpienia przez oryginalny wątek.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Multiple>: każde wystąpienie usługi może mieć wiele wątków przetwarzających komunikaty współbieżnie. Implementacja usługi musi być bezpieczna wątkowo, aby można było używać tego trybu współbieżności.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant>: każde wystąpienie usługi przetwarza jeden komunikat w danym momencie, ale akceptuje wywołania operacji ponownego wykonania. Usługa akceptuje te wywołania tylko wtedy, gdy jest wywoływany przez obiekt klienta WCF.  
  
> [!NOTE]
> Zrozumienie i Programowanie kodu, który bezpiecznie korzysta z więcej niż jednego wątku może być trudne do zapisania. Przed użyciem <xref:System.ServiceModel.ConcurrencyMode.Multiple> lub <xref:System.ServiceModel.ConcurrencyMode.Reentrant> wartości upewnij się, że usługa została prawidłowo zaprojektowana dla tych trybów. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>.  
  
 Użycie współbieżności jest związane z trybem wystąpienia. W <xref:System.ServiceModel.InstanceContextMode.PerCall> tworzenia wystąpienia współbieżność nie jest istotna, ponieważ każdy komunikat jest przetwarzany przez nowy <xref:System.ServiceModel.InstanceContext> i dlatego w <xref:System.ServiceModel.InstanceContext>nie jest aktywny więcej niż jeden wątek.  
  
 Poniższy przykład kodu demonstruje ustawienie właściwości <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> na <xref:System.ServiceModel.ConcurrencyMode.Multiple>.  
  
```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]   
public class CalculatorService : ICalculatorConcurrency   
{   
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Sesje współpracują z ustawieniami InstanceContext  
 Sesje i <xref:System.ServiceModel.InstanceContext> współdziałają w zależności od kombinacji wartości <xref:System.ServiceModel.SessionMode> Enumeration w kontrakcie i właściwości <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> w implementacji usługi, która kontroluje skojarzenie między kanałami i określonymi obiektami usługi.  
  
 W poniższej tabeli przedstawiono wynik kanału przychodzącego, obsługujący sesje lub nieobsługujący sesji z daną kombinacją wartości właściwości <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> i właściwości <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType>.  
  
|Wartość InstanceContextmode|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|PerCall|-Zachowanie przy użyciu kanału sesji: sesji i <xref:System.ServiceModel.InstanceContext> dla każdego wywołania.<br />-Zachowanie przy użyciu kanału bez sesji: Wystąpił wyjątek.|-Zachowanie przy użyciu kanału sesji: sesji i <xref:System.ServiceModel.InstanceContext> dla każdego wywołania.<br />-Zachowanie przy użyciu kanału bez sesji: <xref:System.ServiceModel.InstanceContext> dla każdego wywołania.|-Zachowanie przy użyciu kanału sesji: Wystąpił wyjątek.<br />-Zachowanie przy użyciu kanału bez sesji: <xref:System.ServiceModel.InstanceContext> dla każdego wywołania.|  
|PerSession|-Zachowanie przy użyciu kanału sesji: sesji i <xref:System.ServiceModel.InstanceContext> dla każdego kanału.<br />-Zachowanie przy użyciu kanału bez sesji: Wystąpił wyjątek.|-Zachowanie przy użyciu kanału sesji: sesji i <xref:System.ServiceModel.InstanceContext> dla każdego kanału.<br />-Zachowanie przy użyciu kanału bez sesji: <xref:System.ServiceModel.InstanceContext> dla każdego wywołania.|-Zachowanie przy użyciu kanału sesji: Wystąpił wyjątek.<br />-Zachowanie przy użyciu kanału bez sesji: <xref:System.ServiceModel.InstanceContext> dla każdego wywołania.|  
|Single|-Zachowanie przy użyciu kanału sesji: sesji i jednego <xref:System.ServiceModel.InstanceContext> dla wszystkich wywołań.<br />-Zachowanie przy użyciu kanału bez sesji: Wystąpił wyjątek.|-Zachowanie przy użyciu kanału sesji: sesji i <xref:System.ServiceModel.InstanceContext> dla utworzonej lub konkretnego dla użytkownika elementu.<br />-Zachowanie przy użyciu kanału bez sesji: <xref:System.ServiceModel.InstanceContext> dla obiektu utworzonego lub określonego przez użytkownika.|-Zachowanie przy użyciu kanału sesji: Wystąpił wyjątek.<br />-Zachowanie przy użyciu kanału bez sesji: <xref:System.ServiceModel.InstanceContext> dla każdego utworzonego elementu singleton lub określonego przez użytkownika.|  
  
## <a name="see-also"></a>Zobacz także

- [Korzystanie z sesji](../../../../docs/framework/wcf/using-sessions.md)
- [Instrukcje: tworzenie usługi wymagającej użycia sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
- [Instrukcje: tworzenie wystąpienia usługi kontroli](../../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
- [Współbieżność](../../../../docs/framework/wcf/samples/concurrency.md)
- [Tworzenie wystąpienia](../../../../docs/framework/wcf/samples/instancing.md)
- [Sesja](../../../../docs/framework/wcf/samples/session.md)
