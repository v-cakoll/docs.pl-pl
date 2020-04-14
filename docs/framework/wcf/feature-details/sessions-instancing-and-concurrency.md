---
title: Sesje, tworzenie wystąpień i współbieżność
ms.date: 03/30/2017
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
ms.openlocfilehash: 19dedddadad2f27acdeeaceb2c186a731fa79c32
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243118"
---
# <a name="sessions-instancing-and-concurrency"></a>Sesje, tworzenie wystąpień i współbieżność
*Sesja* jest korelacja wszystkich wiadomości wysyłanych między dwoma punktami końcowymi. *Instancing* odnosi się do kontrolowania okresu istnienia obiektów <xref:System.ServiceModel.InstanceContext> usługi zdefiniowanych przez użytkownika i ich powiązanych obiektów. *Współbieżność* jest terminem nadanym kontroli liczby wątków wykonywanych w <xref:System.ServiceModel.InstanceContext> tym samym czasie.  
  
 W tym temacie opisano te ustawienia, sposób ich używania i różne interakcje między nimi.  
  
## <a name="sessions"></a>Sesje  
 Gdy umowa serwisowa <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> ustawia <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>właściwość do , że umowa mówi, że wszystkie wywołania (czyli podstawowe wymiany komunikatów, które obsługują wywołania) musi być częścią tej samej konwersacji. Jeśli umowa określa, że zezwala na sesje, ale nie wymaga jednego, klienci mogą łączyć się i ustanawiać sesję, czy nie. Jeśli sesja kończy się i wiadomość jest wysyłana za ten sam kanał oparty na sesji wyjątek.  
  
 Sesje WCF mają następujące główne funkcje koncepcyjne:  
  
- Są one jawnie inicjowane i zakończone przez aplikację wywołującą.  
  
- Wiadomości dostarczane podczas sesji są przetwarzane w kolejności, w jakiej są odbierane.  
  
- Sesje skorelować grupę wiadomości do konwersacji. Znaczenie tej korelacji jest abstrakcją. Na przykład jeden kanał oparty na sesji może skorelować wiadomości na podstawie udostępnionego połączenia sieciowego, podczas gdy inny kanał oparty na sesji może skorelować wiadomości na podstawie udostępnionego tagu w treści wiadomości. Funkcje, które mogą pochodzić z sesji zależą od charakteru korelacji.  
  
- Nie ma ogólnego magazynu danych skojarzonego z sesją WCF.  
  
 Jeśli znasz <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> klasę w ASP.NET aplikacji i funkcji, które zapewnia, można zauważyć następujące różnice między tego rodzaju sesji i WCF sesji:  
  
- ASP.NET sesje są zawsze inicjowane przez serwer.  
  
- ASP.NET sesje są niejawnie nieuiarszane.  
  
- ASP.NET sesji zapewniają ogólny mechanizm przechowywania danych między żądaniami.  
  
 Aplikacje klienckie i aplikacje usług współdziałają z sesjami na różne sposoby. Aplikacje klienckie inicjują sesje, a następnie odbierają i przetwarzają wiadomości wysłane w ramach sesji. Aplikacje usługi można użyć sesji jako punkt rozszerzalności, aby dodać dodatkowe zachowanie. Odbywa się to przez pracę <xref:System.ServiceModel.InstanceContext> bezpośrednio z dostawcą kontekstu wystąpienia niestandardowego lub zaimplementowanie.  
  
## <a name="instancing"></a>Tworzenie wystąpienia  
 Zachowanie instancing (zestaw przy <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> użyciu właściwości) <xref:System.ServiceModel.InstanceContext> kontroluje sposób jest tworzony w odpowiedzi na wiadomości przychodzące. Domyślnie każdy <xref:System.ServiceModel.InstanceContext> jest skojarzony z jednym obiektem usługi zdefiniowanym przez <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> użytkownika, więc (w przypadku domyślnym) ustawienie właściwości kontroluje również instancing obiektów usługi zdefiniowanej przez użytkownika. Wyliczenie <xref:System.ServiceModel.InstanceContextMode> definiuje tryby instancing.  
  
 Dostępne są następujące tryby instancingu:  
  
- <xref:System.ServiceModel.InstanceContextMode.PerCall>: Dla <xref:System.ServiceModel.InstanceContext> każdego żądania klienta tworzony jest nowy (i w związku z tym obiekt usługi).  
  
- <xref:System.ServiceModel.InstanceContextMode.PerSession>: Nowy <xref:System.ServiceModel.InstanceContext> (i w związku z tym obiekt usługi) jest tworzony dla każdej nowej sesji klienta i utrzymywany przez cały okres istnienia tej sesji (wymaga to powiązania, które obsługuje sesje).  
  
- <xref:System.ServiceModel.InstanceContextMode.Single>: Pojedynczy <xref:System.ServiceModel.InstanceContext> (i dlatego obiekt usługi) obsługuje wszystkie żądania klienta przez cały okres istnienia aplikacji.  
  
 Poniższy przykład kodu <xref:System.ServiceModel.InstanceContextMode> pokazuje <xref:System.ServiceModel.InstanceContextMode.PerSession> wartość domyślną, jawnie ustawioną w klasie usługi.  
  
```csharp  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]
public class CalculatorService : ICalculatorInstance
{
    ...  
}  
```  
  
 I podczas <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> gdy właściwość <xref:System.ServiceModel.InstanceContext> kontroluje, <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> jak <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> często jest zwalniany, i właściwości kontroli, gdy obiekt usługi jest zwolniony.  
  
### <a name="well-known-singleton-services"></a>Dobrze znane usługi Singleton  
 Jedna odmiana obiektów usługi pojedynczego wystąpienia jest czasami przydatna: można utworzyć obiekt usługi samodzielnie i utworzyć hosta usługi przy użyciu tego obiektu. Aby to zrobić, należy <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> również <xref:System.ServiceModel.InstanceContextMode.Single> ustawić właściwość lub wyjątek jest zgłaszany po otwarciu hosta usługi.  
  
 Użyj <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29> konstruktora, aby utworzyć taką usługę. Stanowi alternatywę dla implementowania <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> niestandardowego, gdy chcesz podać wystąpienie określonego obiektu do użycia przez usługę singleton. Można użyć tego przeciążenia, gdy typ implementacji usługi jest trudne do skonstruowania (na przykład, jeśli nie implementuje bezwametrycznego konstruktora publicznego).  
  
 Należy zauważyć, że gdy obiekt jest dostarczany do tego konstruktora, niektóre funkcje związane z Windows Communication Foundation (WCF) zachowanie instancing działać inaczej. Na przykład <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> wywołanie nie ma wpływu, gdy jest podana wystąpienie obiektu pojedynczego. Podobnie każdy inny mechanizm zwalniania wystąpienia jest ignorowany. Zawsze <xref:System.ServiceModel.ServiceHost> zachowuje się tak, jakby <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> właściwość jest ustawiona dla wszystkich operacji.  
  
### <a name="sharing-instancecontext-objects"></a>Udostępnianie obiektów instancjowych  
 Można również kontrolować, który sesyjny kanał <xref:System.ServiceModel.InstanceContext> lub wywołanie jest skojarzone z który obiekt, wykonując to skojarzenie samodzielnie.  
  
## <a name="concurrency"></a>Współbieżność  
 Współbieżność jest kontrolą liczby wątków aktywnych <xref:System.ServiceModel.InstanceContext> w dowolnym momencie. Jest to kontrolowane <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> przy <xref:System.ServiceModel.ConcurrencyMode> użyciu z wyliczenia.  
  
 Dostępne są następujące trzy tryby współbieżności:  
  
- <xref:System.ServiceModel.ConcurrencyMode.Single>: Każdy kontekst wystąpienia może mieć maksymalnie jeden wątek przetwarzania wiadomości w kontekście wystąpienia w czasie. Inne wątki, które chcą użyć tego samego kontekstu wystąpienia musi zablokować, dopóki oryginalny wątek kończy kontekst wystąpienia.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Multiple>: Każde wystąpienie usługi może mieć wiele wątków przetwarzania wiadomości jednocześnie. Implementacja usługi musi być bezpieczna dla wątków, aby używać tego trybu współbieżności.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant>: Każde wystąpienie usługi przetwarza po jednej wiadomości naraz, ale akceptuje ponowne wniesienie połączeń operacyjnych. Usługa akceptuje tylko te wywołania, gdy jest wywoływanie za pośrednictwem obiektu klienta WCF.  
  
> [!NOTE]
> Zrozumienie i tworzenie kodu, który bezpiecznie używa więcej niż jednego wątku może być trudne do zapisania pomyślnie. Przed <xref:System.ServiceModel.ConcurrencyMode.Multiple> użyciem lub <xref:System.ServiceModel.ConcurrencyMode.Reentrant> wartości, upewnij się, że usługa jest prawidłowo zaprojektowany dla tych trybów. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>.  
  
 Użycie współbieżności jest związane z trybem instancing. W <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing współbieżność nie jest istotne, ponieważ każda wiadomość <xref:System.ServiceModel.InstanceContext> jest przetwarzana przez nowy i dlatego <xref:System.ServiceModel.InstanceContext>nigdy więcej niż jeden wątek jest aktywny w .  
  
 Poniższy przykład kodu pokazuje <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> ustawienie <xref:System.ServiceModel.ConcurrencyMode.Multiple>właściwości na .  
  
```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]
public class CalculatorService : ICalculatorConcurrency
{
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Sesje współdziałają z ustawieniami intertekstu wystąpienia  
 Sesje <xref:System.ServiceModel.InstanceContext> i interakcji w zależności od <xref:System.ServiceModel.SessionMode> kombinacji wartości wyliczenia <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> w umowie i właściwości na implementacji usługi, która kontroluje skojarzenie między kanałami i określonych obiektów usługi.  
  
 W poniższej tabeli przedstawiono wynik kanału przychodzącego obsługującego sesje lub nie obsługujące <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> sesji, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> biorąc pod uwagę kombinację wartości właściwości i właściwości usługi.  
  
|Wartość InstanceContextMode|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|Percall|- Zachowanie z kanałem sesji: Sesja i <xref:System.ServiceModel.InstanceContext> dla każdego połączenia.<br />- Zachowanie z kanału bez sesji: wyjątek jest generowany.|- Zachowanie z kanałem sesji: Sesja i <xref:System.ServiceModel.InstanceContext> dla każdego połączenia.<br />- Zachowanie z kanału <xref:System.ServiceModel.InstanceContext> bez sesji: Dla każdego połączenia.|- Zachowanie z kanału sesji: wyjątek jest generowany.<br />- Zachowanie z kanału <xref:System.ServiceModel.InstanceContext> bez sesji: Dla każdego połączenia.|  
|Persession|- Zachowanie z kanałem sesji: Sesja i <xref:System.ServiceModel.InstanceContext> dla każdego kanału.<br />- Zachowanie z kanału bez sesji: wyjątek jest generowany.|- Zachowanie z kanałem sesji: Sesja i <xref:System.ServiceModel.InstanceContext> dla każdego kanału.<br />- Zachowanie z kanału <xref:System.ServiceModel.InstanceContext> bez sesji: Dla każdego połączenia.|- Zachowanie z kanału sesji: wyjątek jest generowany.<br />- Zachowanie z kanału <xref:System.ServiceModel.InstanceContext> bez sesji: Dla każdego połączenia.|  
|Single|- Zachowanie z kanałem sesji: <xref:System.ServiceModel.InstanceContext> Sesja i jeden dla wszystkich połączeń.<br />- Zachowanie z kanału bez sesji: wyjątek jest generowany.|- Zachowanie z kanałem sesji: Sesja i <xref:System.ServiceModel.InstanceContext> dla utworzonego lub określonego przez użytkownika singleton.<br />- Zachowanie z kanału <xref:System.ServiceModel.InstanceContext> bez sesji: dla utworzonego lub określonego przez użytkownika singleton.|- Zachowanie z kanału sesji: wyjątek jest generowany.<br />- Zachowanie z kanału <xref:System.ServiceModel.InstanceContext> bez sesji: dla każdego utworzonego singleton lub dla użytkownika określonego singleton.|  
  
## <a name="see-also"></a>Zobacz też

- [Korzystanie z sesji](../../../../docs/framework/wcf/using-sessions.md)
- [Instrukcje: tworzenie usługi wymagającej użycia sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
- [Instrukcje: tworzenie wystąpienia usługi kontroli](../../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
- [Współbieżność](../../../../docs/framework/wcf/samples/concurrency.md)
- [Tworzenie wystąpienia](../../../../docs/framework/wcf/samples/instancing.md)
- [Sesja](../../../../docs/framework/wcf/samples/session.md)
