---
title: Sesje, tworzenie wystąpień i współbieżność
ms.date: 03/30/2017
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
ms.openlocfilehash: 52c9ed5d672ea05fec3333c9fece8b693143d6f3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586107"
---
# <a name="sessions-instancing-and-concurrency"></a>Sesje, tworzenie wystąpień i współbieżność
A *sesji* korelacja wszystkich komunikatów przesyłanych między dwoma punktami końcowymi. *Tworzenie wystąpienia* odwołuje się do kontrolowania okresu istnienia obiektów zdefiniowanych przez użytkownika usług i ich powiązane <xref:System.ServiceModel.InstanceContext> obiektów. *Współbieżność* termin do sterowania liczby wątków działających w <xref:System.ServiceModel.InstanceContext> w tym samym czasie.  
  
 W tym temacie opisano te ustawienia, jak ich używać, a różne interakcje między nimi.  
  
## <a name="sessions"></a>Kategoria Sessions  
 Gdy kontrakt usługi Określa <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> właściwości <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>, kontrakt ten jest informujący o tym, że wszystkie wywołania (czyli bazowego wymianę komunikatów, które obsługują wywołania) musi być częścią tej samej konwersacji. Jeśli kontrakt Określa, że w przypadku umożliwia sesji, ale nie wymaga jednej mają, klienci mogą łączyć się i albo ustanowienia sesji, czy nie. Jeśli sesja zakończy się, a jeśli tak, to a wiadomości przesyłane za pośrednictwem takie same oparte na sesji kanału wyjątek jest zgłaszany.  
  
 Sesje WCF oferują następujące funkcje koncepcyjny główne:  
  
- Jawnie są inicjowane i został przerwany przez aplikacji wywołującej.  
  
- Wiadomości dostarczone w trakcie sesji są przetwarzane w kolejności, w której zostały odebrane.  
  
- Sesje skorelowania grupę wiadomości w konwersacji. Znaczenie tej korelacji jest klasą abstrakcyjną. Na przykład jeden kanał oparte na sesji mogą mieć związek komunikaty na podstawie sieci udostępnionego połączenia podczas inną drogą oparte na sesji mogą mieć związek wiadomości według znaczników udostępnionych w treści komunikatu. Funkcje, które mogą być uzyskane z sesji zależą od rodzaju korelacji.  
  
- Brak nie magazynu ogólnych danych skojarzonych z sesją usługi WCF.  
  
 Jeśli znasz <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> klasy w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji i funkcji zawiera, można zauważyć następujące różnice między tego rodzaju sesji i sesje WCF:  
  
- [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sesje są zawsze inicjowanych przez serwer.  
  
- [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sesje są niejawnie nieuporządkowane.  
  
- [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sesje udostępniają mechanizm magazynu danych ogólnych dla żądań.  
  
 Aplikacje usługi i aplikacje klienckie wchodzić w interakcje z sesjami na różne sposoby. Aplikacje klienckie zainicjować sesji odbierać i przetwarzać komunikaty wysyłane w ramach sesji. Aplikacje usługi można użyć sesji jako punktu rozszerzalności, można dodać dodatkowe zachowanie. Jest to realizowane przez pracy bezpośrednio z <xref:System.ServiceModel.InstanceContext> lub implementacji dostawcy niestandardowego wystąpienia kontekstu.  
  
## <a name="instancing"></a>Tworzenie wystąpienia  
 Zachowanie wystąpień (ustawić za pomocą <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> właściwość) kontrolki sposób, w jaki <xref:System.ServiceModel.InstanceContext> jest tworzony w odpowiedzi na wiadomości przychodzące. Domyślnie każdy <xref:System.ServiceModel.InstanceContext> jest skojarzony z jednego obiektu usługi zdefiniowane przez użytkownika, tak (w przypadku domyślnej) ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość kontroluje, tworzenie wystąpień obiektów zdefiniowanych przez użytkownika usługi. <xref:System.ServiceModel.InstanceContextMode> Wyliczenie definiuje tryby wystąpień.  
  
 Dostępne są następujące tryby wystąpień:  
  
- <xref:System.ServiceModel.InstanceContextMode.PerCall>: Nowy <xref:System.ServiceModel.InstanceContext> (i w związku z tym usługa obiektu) jest tworzony dla każdego żądania klienta.  
  
- <xref:System.ServiceModel.InstanceContextMode.PerSession>: Nowy <xref:System.ServiceModel.InstanceContext> (i w związku z tym usługa obiektu) jest tworzone dla każdej nowej sesji klienta i utrzymywana ze względu na okres istnienia sesji (wymaga powiązanie, które obsługuje sesji).  
  
- <xref:System.ServiceModel.InstanceContextMode.Single>: Pojedynczy <xref:System.ServiceModel.InstanceContext> (i w związku z tym usługa obiektu) obsługuje wszystkie żądania klienta dla cyklu życia aplikacji.  
  
 Poniższy przykład kodu pokazuje domyślną <xref:System.ServiceModel.InstanceContextMode> wartość <xref:System.ServiceModel.InstanceContextMode.PerSession> jest jawnie ustawione na klasę usługi.  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]   
public class CalculatorService : ICalculatorInstance   
{   
    ...  
}  
```  
  
 I otrzymało <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> właściwość określa, jak często <xref:System.ServiceModel.InstanceContext> zwolnieniu <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> właściwości formantu, kiedy obiekt usługi jest zwolniony.  
  
### <a name="well-known-singleton-services"></a>Usługami Singleton dobrze znane  
 Czasami przydaje jedną odmianę na obiektach usługi SIS: można utworzyć obiektu usługi samodzielnie i Utwórz hosta usługi przy użyciu tego obiektu. Aby to zrobić, należy także ustawić <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> właściwości <xref:System.ServiceModel.InstanceContextMode.Single> lub wyjątek jest zgłaszany, gdy host usługi jest otwarty.  
  
 Użyj <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> Konstruktor do tworzenia takiej usługi. Jego stanowi alternatywę dla implementacji niestandardowego <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> po możesz podać wystąpienie określonego obiektu do użytku przez usługi singleton. Możesz użyć tego przeciążenia danego typu wdrożenia usługi jest trudne do konstruowania (na przykład, jeśli nie implementuje domyślnego konstruktora publicznego bez parametrów).  
  
 Należy pamiętać, że jeśli obiekt znajduje się do tego konstruktora, niektóre funkcje związane z do Windows Communication Foundation (WCF) wystąpień zachowanie działają inaczej. Na przykład, wywołanie <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> nie obowiązuje, gdy została podana pojedyncze wystąpienie obiektu. Podobnie inny mechanizm wersji wystąpienia jest ignorowany. <xref:System.ServiceModel.ServiceHost> Zawsze zachowuje się tak, jakby <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> właściwość jest ustawiona na <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> dla wszystkich operacji.  
  
### <a name="sharing-instancecontext-objects"></a>Udostępnianie obiektów typu InstanceContext  
 Można również sterować które kanału sesji lub wywołanie jest skojarzone z którym <xref:System.ServiceModel.InstanceContext> obiektu, wykonując tego skojarzenia, samodzielnie.  
  
## <a name="concurrency"></a>Współbieżność  
 Współbieżność jest formant liczba wątków aktywny w <xref:System.ServiceModel.InstanceContext> w dowolnym momencie. To jest kontrolowany za pomocą <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> z <xref:System.ServiceModel.ConcurrencyMode> wyliczenia.  
  
 Dostępne są następujące trzy tryby współbieżności:  
  
- <xref:System.ServiceModel.ConcurrencyMode.Single>: W każdym kontekście wystąpienie może mieć co najwyżej jeden wątek przetwarzanie komunikatów w kontekście wystąpienia w danym momencie. Inne wątki, które chcą korzystać z tym samym kontekście wystąpienia muszą blokować do momentu, oryginalnym wątek kończy działanie kontekstu wystąpienia.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Multiple>: Każde wystąpienie usługi może mieć wiele wątków jednocześnie przetwarzanie komunikatów. Implementacja usługi musi być wątków, aby użyć tego trybu współbieżności.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant>: Każde wystąpienie usługi przetwarza jeden komunikat w danym momencie, ale akceptuje wywołania wielobieżnej operacji. Usługa akceptuje tylko te wywołania, gdy wywołuje za pośrednictwem obiektu klienta programu WCF.  
  
> [!NOTE]
>  Opis i tworzenia kodu, która bezpiecznie używa więcej niż jeden wątek może być trudne do pisania pomyślnie. Przed rozpoczęciem korzystania z <xref:System.ServiceModel.ConcurrencyMode.Multiple> lub <xref:System.ServiceModel.ConcurrencyMode.Reentrant> wartości, upewnij się, że usługa prawidłowo jest przeznaczony dla tych trybów. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>.  
  
 Użycie współbieżności jest powiązana z trybu wystąpień. W <xref:System.ServiceModel.InstanceContextMode.PerCall> wystąpień, współbieżności nie jest ważna, ponieważ każdy komunikat jest przetwarzany przez nowy <xref:System.ServiceModel.InstanceContext> i w związku z tym, nigdy nie więcej niż jeden wątek jest aktywny w <xref:System.ServiceModel.InstanceContext>.  
  
 Poniższy przykład kodu pokazuje ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> właściwość <xref:System.ServiceModel.ConcurrencyMode.Multiple>.  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]   
public class CalculatorService : ICalculatorConcurrency   
{   
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Sesje wchodzić w interakcje przy użyciu typu InstanceContext ustawień  
 Sesje i <xref:System.ServiceModel.InstanceContext> wchodzić w interakcje w zależności od kombinacji wartości <xref:System.ServiceModel.SessionMode> wyliczenia w Umowie oraz <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> właściwość implementacji usługi Określa skojarzenie między kanałów i specyficznych dla obiekty usługi.  
  
 W poniższej tabeli przedstawiono wynik kanał przychodzący obsługi sesji albo nie obsługuje sesji, biorąc pod uwagę usługę kombinacja wartości <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> właściwości i <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> właściwości.  
  
|Wartość właściwość InstanceContextMode|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|PerCall|-Zachowanie za pomocą kanału sesji: Sesję i <xref:System.ServiceModel.InstanceContext> dla każdego wywołania.<br />-Zachowanie Bezsesyjne kanału: Jest zgłaszany wyjątek.|-Zachowanie za pomocą kanału sesji: Sesję i <xref:System.ServiceModel.InstanceContext> dla każdego wywołania.<br />-Zachowanie Bezsesyjne kanału: <xref:System.ServiceModel.InstanceContext> Dla każdego wywołania.|-Zachowanie za pomocą kanału sesji: Jest zgłaszany wyjątek.<br />-Zachowanie Bezsesyjne kanału: <xref:System.ServiceModel.InstanceContext> Dla każdego wywołania.|  
|PerSession|-Zachowanie za pomocą kanału sesji: Sesję i <xref:System.ServiceModel.InstanceContext> dla każdego kanału.<br />-Zachowanie Bezsesyjne kanału: Jest zgłaszany wyjątek.|-Zachowanie za pomocą kanału sesji: Sesję i <xref:System.ServiceModel.InstanceContext> dla każdego kanału.<br />-Zachowanie Bezsesyjne kanału: <xref:System.ServiceModel.InstanceContext> Dla każdego wywołania.|-Zachowanie za pomocą kanału sesji: Jest zgłaszany wyjątek.<br />-Zachowanie Bezsesyjne kanału: <xref:System.ServiceModel.InstanceContext> Dla każdego wywołania.|  
|Single|-Zachowanie za pomocą kanału sesji: Sesję i jeden <xref:System.ServiceModel.InstanceContext> dla wszystkich wywołań.<br />-Zachowanie Bezsesyjne kanału: Jest zgłaszany wyjątek.|-Zachowanie za pomocą kanału sesji: Sesję i <xref:System.ServiceModel.InstanceContext> dla pojedynczego wystąpienia utworzone lub określone przez użytkownika.<br />-Zachowanie Bezsesyjne kanału: <xref:System.ServiceModel.InstanceContext> Dla pojedynczego wystąpienia utworzone lub określone przez użytkownika.|-Zachowanie za pomocą kanału sesji: Jest zgłaszany wyjątek.<br />-Zachowanie Bezsesyjne kanału: <xref:System.ServiceModel.InstanceContext> Dla każdego utworzonego pojedyncze lub pojedyncze określonych przez użytkownika.|  
  
## <a name="see-also"></a>Zobacz także

- [Korzystanie z sesji](../../../../docs/framework/wcf/using-sessions.md)
- [Instrukcje: Tworzenie usługi wymagającej użycia sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
- [Instrukcje: Tworzenie wystąpienia usługi kontroli](../../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
- [Współbieżność](../../../../docs/framework/wcf/samples/concurrency.md)
- [Tworzenie wystąpienia](../../../../docs/framework/wcf/samples/instancing.md)
- [Sesja](../../../../docs/framework/wcf/samples/session.md)
