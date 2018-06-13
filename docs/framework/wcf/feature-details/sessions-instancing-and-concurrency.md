---
title: Sesje, tworzenie wystąpień i współbieżność
ms.date: 03/30/2017
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
ms.openlocfilehash: a3f56a08c695b4d92529d2c1bec625e9e8c6b6ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33506577"
---
# <a name="sessions-instancing-and-concurrency"></a>Sesje, tworzenie wystąpień i współbieżność
A *sesji* jest korelacji wszystkich wiadomości wysłanych między dwoma punktami końcowymi. *Tworzenie wystąpienia* odwołuje się do kontrolowania okres istnienia obiektów zdefiniowanych przez użytkownika usług i ich powiązane <xref:System.ServiceModel.InstanceContext> obiektów. *Współbieżność* jest terminu podanego do formantu liczbę wątków działających w <xref:System.ServiceModel.InstanceContext> w tym samym czasie.  
  
 W tym temacie opisano te ustawienia, jak używać i różnych interakcje między nimi.  
  
## <a name="sessions"></a>Kategoria Sessions  
 Gdy kontrakt usługi Określa <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> właściwości <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>, że kontrakt jest informujący o tym, że wszystkie wywołania (to znaczy podstawowej wymiany komunikatów obsługujących wywołania) musi być częścią ta sama konwersacja. Jeśli kontrakt Określa czy umożliwia sesji, ale nie wymaga jednego, mogą łączyć się klienci, a albo ustanowić sesję, czy nie. Jeśli sesja zakończy się oraz wiadomości przesyłane z tego samego opartymi na sesji jest zgłaszany wyjątek kanału.  
  
 Sesje WCF oferują następujące funkcje koncepcyjnej główne:  
  
-   Jawnie są inicjowane i został przerwany przez wywołanie aplikacji.  
  
-   Komunikaty dostarczone podczas sesji są przetwarzane w kolejności, w którym są odbierane.  
  
-   Sesje skorelowania grupy wiadomości w konwersacji. Znaczenie tej korelacji jest klasą abstrakcyjną. Na przykład jeden kanał opartymi na sesji mogą mieć związek wiadomości opartych na połączenie sieciowe udostępnionych podczas innego opartymi na sesji kanału może skorelować wiadomości opartych na udostępnionych tagu w treści wiadomości. Funkcje, które mogą być uzyskane z sesji są zależne od charakteru korelacji.  
  
-   Brak ma magazynu ogólnych danych skojarzonych z sesją programu WCF.  
  
 Jeśli znasz <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> klasy w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji i funkcji umożliwia, można zauważyć następujące różnice między tego rodzaju sesji i sesje WCF:  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sesje są zawsze inicjowanych przez serwer.  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sesje są niejawnie nieuporządkowaną.  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sesje udostępniają mechanizm magazynu danych ogólnych żądań.  
  
 Aplikacje klienckie i aplikacje usług interakcji z sesji na różne sposoby. Aplikacje klienckie zainicjować sesji i następnie odbierania i przetwarzania wiadomości wysyłane w ramach sesji. Aplikacje usługi mogą używać sesji jako punkt rozszerzeń można dodać dodatkowe zachowanie. W tym celu praca bezpośrednio z <xref:System.ServiceModel.InstanceContext> lub implementowanie dostawcy kontekstu niestandardowego wystąpienia.  
  
## <a name="instancing"></a>Tworzenie wystąpienia  
 Zachowanie wystąpień (skonfigurowane za pomocą <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> właściwości) kontrolki jak <xref:System.ServiceModel.InstanceContext> jest tworzony w odpowiedzi na wiadomości przychodzących. Domyślnie każdy <xref:System.ServiceModel.InstanceContext> jest skojarzony z jednego obiektu usługi zdefiniowane przez użytkownika, tak (w przypadku domyślnego) ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwość również określa wystąpień obiektów zdefiniowanych przez użytkownika usługi. <xref:System.ServiceModel.InstanceContextMode> Wyliczenie definiuje tryb wystąpień.  
  
 Dostępne są następujące tryby wystąpień:  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerCall>: Nowy <xref:System.ServiceModel.InstanceContext> (i w związku z tym usługa obiektu) jest tworzony dla każdego żądania klienta.  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerSession>: Nowy <xref:System.ServiceModel.InstanceContext> (i w związku z tym usługa obiektu) jest tworzone dla każdej nowej sesji klienta i przechowywane przez czas ich istnienia sesji (wymaga powiązania, które obsługuje sesji).  
  
-   <xref:System.ServiceModel.InstanceContextMode.Single>: Jeden <xref:System.ServiceModel.InstanceContext> (i w związku z tym usługa obiektu) obsługuje wszystkie żądania klienta przez czas ich istnienia aplikacji.  
  
 Poniższy przykład kodu pokazuje domyślne <xref:System.ServiceModel.InstanceContextMode> wartość <xref:System.ServiceModel.InstanceContextMode.PerSession> jawnie ustawiania klasy usługi.  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]   
public class CalculatorService : ICalculatorInstance   
{   
    ...  
}  
```  
  
 I podczas <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> właściwość określa, jak często <xref:System.ServiceModel.InstanceContext> wydaniu <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> właściwości formantu, kiedy zwolniony jest obiekt usługi.  
  
### <a name="well-known-singleton-services"></a>Dobrze znanego pojedynczego wystąpienia usług  
 Czasami jest przydatne jedną odmianę obiektów usługi SIS: można utworzyć obiektu usługi samodzielnie i Utwórz hosta usługi przy użyciu tego obiektu. Aby to zrobić, należy także ustawić <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> właściwości <xref:System.ServiceModel.InstanceContextMode.Single> lub jest zgłaszany wyjątek, po otwarciu hosta usługi.  
  
 Użyj <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> konstruktora w celu utworzenia takiej usługi. Zapewnia alternatywę do wdrażania niestandardowego <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> po możesz podać wystąpienie określonego obiektu do użytku przez usługi singleton. Można użyć tego przeciążenia, gdy Twoje typ implementacji usługi jest trudne do skonstruowania (na przykład, jeśli nie implementuje domyślnego publicznego konstruktora bez parametrów).  
  
 Należy pamiętać, że jeśli obiekt został dostarczony do tego konstruktora, niektóre funkcje związane z do systemu Windows Communication Foundation (WCF) wystąpień zachowanie działają inaczej. Na przykład wywołanie elementu <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> nie obowiązuje, gdy została podana pojedyncze wystąpienie obiektu. Podobnie inny mechanizm wersji wystąpienia jest ignorowana. <xref:System.ServiceModel.ServiceHost> Zawsze zachowuje się tak, jakby <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> ma ustawioną wartość właściwości <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> dla wszystkich operacji.  
  
### <a name="sharing-instancecontext-objects"></a>Udostępnianie obiektów InstanceContext  
 Można również sterować które podczas zamykania kanału sesji lub połączenia jest skojarzony z którym <xref:System.ServiceModel.InstanceContext> obiektu przez siebie wykonanie tego skojarzenia.  
  
## <a name="concurrency"></a>Współbieżność  
 Współbieżność jest formant liczbę wątków, które są aktywne w <xref:System.ServiceModel.InstanceContext> w dowolnym momencie. To jest kontrolowany za pomocą <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> z <xref:System.ServiceModel.ConcurrencyMode> wyliczenia.  
  
 Dostępne są następujące trzy tryby współbieżności:  
  
-   <xref:System.ServiceModel.ConcurrencyMode.Single>: Każdy kontekst wystąpienia może zawierać maksymalnie jeden wątek przetwarzania komunikatów w kontekście wystąpienia naraz. Inne wątki chcą używać tego samego wystąpienia kontekstu zablokować aż do oryginalnego wątku opuszcza kontekstu wystąpienia.  
  
-   <xref:System.ServiceModel.ConcurrencyMode.Multiple>: Każde wystąpienie usługi może mieć wiele wątków jednocześnie przetwarzanie komunikatów. Implementacja usługi musi być wielowątkowość ten tryb współbieżności.  
  
-   <xref:System.ServiceModel.ConcurrencyMode.Reentrant>: Każde wystąpienie usługi przetwarza jeden komunikat w czasie, ale akceptuje wywołań wielobieżnej operacji. Usługa akceptuje tylko te wywołania, gdy wywołuje za pośrednictwem obiektu klienta WCF.  
  
> [!NOTE]
>  Opis i tworzenia kodu korzystającego z bezpiecznie więcej niż jeden wątek może być trudne do zapisania pomyślnie. Przed użyciem <xref:System.ServiceModel.ConcurrencyMode.Multiple> lub <xref:System.ServiceModel.ConcurrencyMode.Reentrant> wartości, upewnij się, że usługa prawidłowo jest przeznaczony dla tych trybów. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>.  
  
 Użycie współbieżności jest powiązany z trybu tworzenia. W <xref:System.ServiceModel.InstanceContextMode.PerCall> wystąpień, współbieżności nie jest ważna, ponieważ każdy komunikat jest przetwarzany przez nowy <xref:System.ServiceModel.InstanceContext> i w związku z tym jest aktywny w nie więcej niż jeden wątek <xref:System.ServiceModel.InstanceContext>.  
  
 Poniższy przykład kodu pokazuje ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> właściwości <xref:System.ServiceModel.ConcurrencyMode.Multiple>.  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]   
public class CalculatorService : ICalculatorConcurrency   
{   
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Sesje interakcję z ustawieniami InstanceContext  
 Sesje i <xref:System.ServiceModel.InstanceContext> interakcji kombinacja wartości w zależności od <xref:System.ServiceModel.SessionMode> wyliczenia w umowie i <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> właściwość implementacji usługi, która kontroluje skojarzenie między kanałów i określonych obiekty usługi.  
  
 W poniższej tabeli przedstawiono wynik kanał przychodzący Obsługa sesji albo nie obsługuje sesji podana usługa kombinacja wartości <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> właściwości i <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> właściwości.  
  
|Wartość InstanceContextMode|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|PerCall|-Zachowanie podczas zamykania kanału: sesji i <xref:System.ServiceModel.InstanceContext> dla każdego wywołania.<br />— Zachowanie z kanałem Bezsesyjne: wyjątek.|-Zachowanie podczas zamykania kanału: sesji i <xref:System.ServiceModel.InstanceContext> dla każdego wywołania.<br />— Zachowanie z kanałem Bezsesyjne: <xref:System.ServiceModel.InstanceContext> dla każdego wywołania.|-Zachowanie podczas zamykania kanału: wyjątek.<br />— Zachowanie z kanałem Bezsesyjne: <xref:System.ServiceModel.InstanceContext> dla każdego wywołania.|  
|PerSession|-Zachowanie podczas zamykania kanału: sesji i <xref:System.ServiceModel.InstanceContext> dla poszczególnych kanałów.<br />— Zachowanie z kanałem Bezsesyjne: wyjątek.|-Zachowanie podczas zamykania kanału: sesji i <xref:System.ServiceModel.InstanceContext> dla poszczególnych kanałów.<br />— Zachowanie z kanałem Bezsesyjne: <xref:System.ServiceModel.InstanceContext> dla każdego wywołania.|-Zachowanie podczas zamykania kanału: wyjątek.<br />— Zachowanie z kanałem Bezsesyjne: <xref:System.ServiceModel.InstanceContext> dla każdego wywołania.|  
|Single|-Zachowanie podczas zamykania kanału: sesji i jeden <xref:System.ServiceModel.InstanceContext> dla wszystkich wywołań.<br />— Zachowanie z kanałem Bezsesyjne: wyjątek.|-Zachowanie podczas zamykania kanału: sesji i <xref:System.ServiceModel.InstanceContext> dla pojedynczego wystąpienia utworzone lub określonych przez użytkownika.<br />— Zachowanie z kanałem Bezsesyjne: <xref:System.ServiceModel.InstanceContext> dla pojedynczego wystąpienia utworzone lub określonych przez użytkownika.|-Zachowanie podczas zamykania kanału: wyjątek.<br />— Zachowanie z kanałem Bezsesyjne: <xref:System.ServiceModel.InstanceContext> dla każdej utworzonej pojedyncze lub pojedyncze określone przez użytkownika.|  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z sesji](../../../../docs/framework/wcf/using-sessions.md)  
 [Instrukcje: tworzenie usługi wymagającej użycia sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)  
 [Instrukcje: tworzenie wystąpienia usługi kontroli](../../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)  
 [Współbieżność](../../../../docs/framework/wcf/samples/concurrency.md)  
 [Tworzenie wystąpienia](../../../../docs/framework/wcf/samples/instancing.md)  
 [Sesja](../../../../docs/framework/wcf/samples/session.md)
