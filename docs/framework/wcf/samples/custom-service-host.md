---
title: Niestandardowy host usługi
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: 2aed557d1d045c08aed206660aa7b4b75ffe0e2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145075"
---
# <a name="custom-service-host"></a>Niestandardowy host usługi
W tym przykładzie pokazano, jak <xref:System.ServiceModel.ServiceHost> używać niestandardowej pochodnej klasy, aby zmienić zachowanie w czasie wykonywania usługi. Takie podejście zapewnia wielokrotnego stosowania alternatywy do konfigurowania dużej liczby usług w typowy sposób. W przykładzie pokazano również, <xref:System.ServiceModel.Activation.ServiceHostFactory> jak używać klasy do używania niestandardowego servicehost w środowisku hostingu internetowych usług informacyjnych (IIS) lub usługi aktywacji procesów systemu Windows (WAS).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a>Informacje o scenariuszu
 Aby zapobiec niezamierzonemu ujawnieniu potencjalnie poufnych metadanych usługi, domyślna konfiguracja usług Windows Communication Foundation (WCF) wyłącza publikowanie metadanych. To zachowanie jest domyślnie bezpieczne, ale oznacza również, że nie można użyć narzędzia importu metadanych (na przykład Svcutil.exe) do generowania kodu klienta wymaganego do wywołania usługi, chyba że zachowanie publikowania metadanych usługi jest jawnie włączone w konfiguracji.  
  
 Włączanie publikowania metadanych dla dużej liczby usług obejmuje dodanie tych samych elementów konfiguracji do każdej usługi, co powoduje dużą ilość informacji o konfiguracji, która jest zasadniczo taka sama. Jako alternatywę dla konfigurowania każdej usługi indywidualnie, istnieje możliwość zapisu kodu imperatywu, który umożliwia publikowanie metadanych raz, a następnie ponownie użyć tego kodu w kilku różnych usług. Jest to realizowane przez utworzenie nowej klasy, <xref:System.ServiceModel.ServiceHost> która wywodzi się z `ApplyConfiguration`() metody () i zastępuje ją, aby bezwzględnie dodać zachowanie publikowania metadanych.  
  
> [!IMPORTANT]
> Dla jasności w tym przykładzie pokazano, jak utworzyć niezabezpieczony punkt końcowy publikowania metadanych. Takie punkty końcowe są potencjalnie dostępne dla anonimowych nieuwierzytetycznych konsumentów i należy zwrócić uwagę przed wdrożeniem takich punktów końcowych, aby upewnić się, że publiczne ujawnienie metadanych usługi jest właściwe.  
  
## <a name="implementing-a-custom-servicehost"></a>Implementowanie niestandardowego hosta usługi
 Klasa <xref:System.ServiceModel.ServiceHost> udostępnia kilka przydatnych metod wirtualnych, które dziedzicze mogą zastąpić, aby zmienić zachowanie w czasie wykonywania usługi. Na przykład `ApplyConfiguration`() metoda odczytuje informacje o konfiguracji usługi z <xref:System.ServiceModel.Description.ServiceDescription> magazynu konfiguracji i zmienia hosta odpowiednio. Domyślna implementacja odczytuje konfigurację z pliku konfiguracyjnego aplikacji. Implementacje niestandardowe `ApplyConfiguration`można zastąpić () <xref:System.ServiceModel.Description.ServiceDescription> do dalszej zmiany przy użyciu kodu imperatywnego lub nawet zastąpić domyślny magazyn konfiguracji całkowicie. Na przykład, aby odczytać konfigurację punktu końcowego usługi z bazy danych zamiast pliku konfiguracyjnego aplikacji.  
  
 W tym przykładzie chcemy utworzyć niestandardowy ServiceHost, który dodaje ServiceMetadataBehavior (który umożliwia publikowanie metadanych), nawet jeśli to zachowanie nie jest jawnie dodawane w pliku konfiguracji usługi. Aby to osiągnąć, tworzymy nową klasę, która dziedziczy <xref:System.ServiceModel.ServiceHost> i zastępuje `ApplyConfiguration`().  
  
```csharp
class SelfDescribingServiceHost : ServiceHost  
{  
    public SelfDescribingServiceHost(Type serviceType, params Uri[] baseAddresses)  
        : base(serviceType, baseAddresses) { }  
  
    //Overriding ApplyConfiguration() allows us to
    //alter the ServiceDescription prior to opening  
    //the service host.
    protected override void ApplyConfiguration()  
    {  
        //First, we call base.ApplyConfiguration()  
        //to read any configuration that was provided for  
        //the service we're hosting. After this call,  
        //this.Description describes the service  
        //as it was configured.  
        base.ApplyConfiguration();
  
        //(rest of implementation elided for clarity)  
    }  
}  
```  
  
 Ponieważ nie chcemy ignorować żadnej konfiguracji, która została podana w pliku konfiguracyjnym aplikacji, pierwszą rzeczą, którą wykonuje nasze zastąpienie `ApplyConfiguration`() jest wywołanie implementacji podstawowej. Po zakończeniu tej metody, możemy bezwzględnie dodać <xref:System.ServiceModel.Description.ServiceMetadataBehavior> do opisu przy użyciu następującego kodu imperatywu.  
  
```csharp
ServiceMetadataBehavior mexBehavior = this.Description.Behaviors.Find<ServiceMetadataBehavior>();  
if (mexBehavior == null)  
{  
    mexBehavior = new ServiceMetadataBehavior();  
    this.Description.Behaviors.Add(mexBehavior);  
}  
else  
{  
    //Metadata behavior has already been configured,
    //so we do not have any work to do.  
    return;  
}  
```  
  
 Ostatnią rzeczą, `ApplyConfiguration`którą musi wykonać nasze () zastąpienie, jest dodanie domyślnego punktu końcowego metadanych. Zgodnie z konwencją jeden punkt końcowy metadanych jest tworzony dla każdego identyfikatora URI w kolekcji BaseAddresses hosta usługi.  
  
```csharp
//Add a metadata endpoint at each base address  
//using the "/mex" addressing convention  
foreach (Uri baseAddress in this.BaseAddresses)  
{  
    if (baseAddress.Scheme == Uri.UriSchemeHttp)  
    {  
        mexBehavior.HttpGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeHttps)  
    {  
        mexBehavior.HttpsGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpsBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetPipe)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexNamedPipeBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetTcp)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexTcpBinding(),  
                                "mex");  
    }  
}  
```  
  
## <a name="using-a-custom-servicehost-in-self-host"></a>Korzystanie z niestandardowego hosta usługi w hostach  
 Teraz, gdy zakończyliśmy naszą niestandardową implementację ServiceHost, możemy użyć jej do dodania zachowania publikowania `SelfDescribingServiceHost`metadanych do dowolnej usługi, hostując tę usługę wewnątrz wystąpienia naszego . Poniższy kod pokazuje, jak go używać w scenariuszu samodzielnego hosta.  
  
```csharp
SelfDescribingServiceHost host =
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 Nasz niestandardowy host nadal odczytuje konfigurację punktu końcowego usługi z pliku konfiguracyjnego aplikacji, tak jakby użyliśmy klasy domyślnej <xref:System.ServiceModel.ServiceHost> do hostowania usługi. Jednak ponieważ dodaliśmy logikę, aby włączyć publikowanie metadanych wewnątrz naszego hosta niestandardowego, nie musimy już jawnie włączać zachowania publikowania metadanych w konfiguracji. Takie podejście ma wyraźną zaletę podczas tworzenia aplikacji, która zawiera kilka usług i chcesz włączyć publikowanie metadanych na każdym z nich bez pisania tych samych elementów konfiguracji w kółko.  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a>Korzystanie z niestandardowego hosta usługi w usługach IIS lub WAS  
 Korzystanie z niestandardowego hosta usługi w scenariuszach hosta własnego jest proste, ponieważ jest to kod aplikacji, który jest ostatecznie odpowiedzialny za tworzenie i otwieranie wystąpienia hosta usługi. Jednak w środowisku hostingowym usług IIS lub WAS infrastruktura WCF dynamicznie występuje z tworzeniem wystąpienia hosta usługi w odpowiedzi na przychodzące wiadomości. Hosty usługi niestandardowej mogą być również używane w tym środowisku hostingowym, ale wymagają dodatkowego kodu w postaci ServiceHostFactory. Poniższy kod przedstawia <xref:System.ServiceModel.Activation.ServiceHostFactory> pochodną tego zwraca `SelfDescribingServiceHost`wystąpienia naszych niestandardowych .  
  
```csharp
public class SelfDescribingServiceHostFactory : ServiceHostFactory  
{  
    protected override ServiceHost CreateServiceHost(Type serviceType,
     Uri[] baseAddresses)  
    {  
        //All the custom factory does is return a new instance  
        //of our custom host class. The bulk of the custom logic should  
        //live in the custom host (as opposed to the factory)
        //for maximum  
        //reuse value outside of the IIS/WAS hosting environment.  
        return new SelfDescribingServiceHost(serviceType,
                                             baseAddresses);  
    }  
}  
```  
  
 Jak widać, implementowanie niestandardowego ServiceHostFactory jest bardzo proste. Wszystkie niestandardowe logiki znajduje się wewnątrz ServiceHost implementacji; fabryka zwraca wystąpienie klasy pochodnej.  
  
 Aby użyć niestandardowej fabryki z implementacją usługi, musimy dodać dodatkowe metadane do pliku .svc usługi.  
  
```xml
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"
               language=c# Debug="true" %>
```
  
 W tym miejscu `Factory` dodaliśmy dodatkowy `@ServiceHost` atrybut do dyrektywy i przekazali nazwę typu CLR naszej fabryki niestandardowej jako wartość atrybutu. Gdy usługi IIS lub WAS odbiera komunikat dla tej usługi, WCF hosting infrastruktury najpierw tworzy wystąpienie ServiceHostFactory, a następnie utworzyć wystąpienie samego hosta usługi przez wywołanie `ServiceHostFactory.CreateServiceHost()`.  
  
## <a name="running-the-sample"></a>Uruchamianie przykładowej aplikacji  
 Mimo że ten przykład zapewnia w pełni funkcjonalną implementację klienta i usługi, punktem próbki jest zilustrowanie sposobu zmiany zachowania w czasie wykonywania usługi za pomocą hosta niestandardowego., wykonaj następujące kroki:  
  
### <a name="observe-the-effect-of-the-custom-host"></a>Obserwuj efekt hosta niestandardowego
  
1. Otwórz plik Web.config usługi i należy zauważyć, że nie ma konfiguracji jawnie włączającej metadane usługi.  
  
2. Otwórz plik .svc usługi i obserwować, że jego @ServiceHost dyrektywa zawiera Factory atrybut, który określa nazwę niestandardowego ServiceHostFactory.  
  
### <a name="set-up-build-and-run-the-sample"></a>Konfigurowanie, tworzenie i uruchamianie próbki
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](building-the-samples.md).

3. Po utworzeniu rozwiązania uruchom plik Setup.bat, aby skonfigurować aplikację ServiceModelSamples w usługach IIS 7.0. Katalog ServiceModelSamples powinien teraz być wyświetlany jako aplikacja usług IIS 7.0.

4. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](running-the-samples.md).

5. Aby usunąć aplikację IIS 7.0, uruchom *plik Cleanup.bat*.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: hostowanie usługi WCF w programie IIS](../feature-details/how-to-host-a-wcf-service-in-iis.md)
