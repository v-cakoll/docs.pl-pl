---
title: Niestandardowy host usługi
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: 86dd8c5cebfb8ea6f9a2b95f7698362eb34c1a7c
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716799"
---
# <a name="custom-service-host"></a>Niestandardowy host usługi
Ten przykład pokazuje, jak używać niestandardowych pochodnych klasy <xref:System.ServiceModel.ServiceHost>, aby zmienić zachowanie usługi w czasie wykonywania. Takie podejście umożliwia użycie alternatywnej alternatywy do konfigurowania dużej liczby usług w typowy sposób. W przykładzie pokazano również, jak użyć klasy <xref:System.ServiceModel.Activation.ServiceHostFactory>, aby użyć niestandardowego ServiceHost w Internet Information Services (IIS) lub w usłudze aktywacji procesów systemu Windows (WAS).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a>Informacje o tym scenariuszu  
 Aby zapobiec przypadkowemu ujawnieniu potencjalnie poufnych metadanych usługi, konfiguracja domyślna dla usług Windows Communication Foundation (WCF) wyłącza Publikowanie metadanych. To zachowanie jest domyślnie bezpieczne, ale oznacza to, że nie można użyć narzędzia do importowania metadanych (takiego jak Svcutil. exe) w celu wygenerowania kodu klienta wymaganego do wywołania usługi, chyba że zachowanie publikowania metadanych usługi jest jawnie włączone w konfiguracji.  
  
 Włączenie publikowania metadanych dla dużej liczby usług obejmuje dodanie tych samych elementów konfiguracji do poszczególnych usług, co skutkuje znaczną ilością informacji o konfiguracji, które są zasadniczo takie same. Alternatywnie, aby skonfigurować poszczególne usługi indywidualnie, można napisać bezwzględny kod, który umożliwia Publikowanie metadanych jednokrotnie, a następnie ponownie wykorzystać ten kod dla kilku różnych usług. Jest to realizowane przez utworzenie nowej klasy, która pochodzi od <xref:System.ServiceModel.ServiceHost> i przesłania metodę `ApplyConfiguration`(), aby bezwzględnie dodać zachowanie publikowania metadanych.  
  
> [!IMPORTANT]
> Dla jasności ten przykład pokazuje, jak utworzyć niezabezpieczony punkt końcowy publikowania metadanych. Takie punkty końcowe są potencjalnie dostępne dla anonimowych użytkowników nieuwierzytelnionych i należy zachować ostrożność przed wdrożeniem takich punktów końcowych, aby upewnić się, że można publicznie odzamknąć metadane usługi.  
  
## <a name="implementing-a-custom-servicehost"></a>Implementowanie niestandardowego ServiceHost  
 Klasa <xref:System.ServiceModel.ServiceHost> uwidacznia kilka przydatnych metod wirtualnych, które dziedziczą mogą przesłonić, aby zmienić zachowanie usługi w czasie wykonywania. Na przykład Metoda `ApplyConfiguration`() odczytuje informacje o konfiguracji usługi z magazynu konfiguracji i odpowiednio zmienia <xref:System.ServiceModel.Description.ServiceDescription> hosta. Domyślna implementacja odczytuje konfigurację z pliku konfiguracyjnego aplikacji. Implementacje niestandardowe mogą przesłonić `ApplyConfiguration`(), aby jeszcze bardziej zmienić <xref:System.ServiceModel.Description.ServiceDescription> przy użyciu kodu bezwzględnego, a nawet całkowicie zastąpić domyślny magazyn konfiguracji. Na przykład, aby odczytać konfigurację punktu końcowego usługi z bazy danych zamiast pliku konfiguracji aplikacji.  
  
 W tym przykładzie chcemy utworzyć niestandardowy ServiceHost, który dodaje ServiceMetadataBehavior (co umożliwia Publikowanie metadanych), nawet jeśli to zachowanie nie zostanie jawnie dodane w pliku konfiguracji usługi. Aby to osiągnąć, tworzymy nową klasę, która dziedziczy po <xref:System.ServiceModel.ServiceHost> i przesłania `ApplyConfiguration`().  
  
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
  
 Ponieważ nie chcemy ignorować żadnej konfiguracji, która została dostarczona w pliku konfiguracyjnym aplikacji, pierwsze zastępowanie `ApplyConfiguration`() jest wywołaniem podstawowej implementacji. Po zakończeniu tej metody możemy bezwzględnie dodać <xref:System.ServiceModel.Description.ServiceMetadataBehavior> do opisu przy użyciu następującego kodu.  
  
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
  
 Ostatnim zastępowaniem naszych `ApplyConfiguration`() musi być dodanie domyślnego punktu końcowego metadanych. Zgodnie z Konwencją jeden punkt końcowy metadanych jest tworzony dla każdego identyfikatora URI w kolekcji BaseAddresses hosta usługi.  
  
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
  
## <a name="using-a-custom-servicehost-in-self-host"></a>Używanie niestandardowego ServiceHost na własnym hoście  
 Po ukończeniu naszej niestandardowej implementacji ServiceHost można użyć jej do dodania zachowania publikowania metadanych do dowolnej usługi, udostępniając ją w ramach wystąpienia naszego `SelfDescribingServiceHost`. Poniższy kod przedstawia sposób korzystania z niego w scenariuszu z własnym hostem.  
  
```csharp
SelfDescribingServiceHost host =   
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 Nasz Host niestandardowy nadal odczytuje konfigurację punktu końcowego usługi z pliku konfiguracyjnego aplikacji, podobnie jak w przypadku użycia domyślnej klasy <xref:System.ServiceModel.ServiceHost> do hostowania usługi. Jednak ze względu na to, że dodaliśmy logikę umożliwiającą opublikowanie metadanych w ramach naszego hosta niestandardowego, nie należy jawnie włączać zachowania publikowania metadanych w konfiguracji. Takie podejście ma różne zalety podczas kompilowania aplikacji, która zawiera kilka usług i chcesz włączyć Publikowanie metadanych na każdym z nich bez konieczności pisania tych samych elementów konfiguracji w porównaniu do i więcej.  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a>Używanie niestandardowego ServiceHost w usługach IIS lub  
 Używanie niestandardowego hosta usługi w scenariuszach z własnym hostem jest proste, ponieważ jest to kod aplikacji, który jest ostatecznie odpowiedzialny za tworzenie i otwieranie wystąpienia hosta usługi. Jednak w usługach IIS lub w środowisku macierzystym Infrastruktura WCF tworzy dynamicznie wystąpienie hosta usługi w odpowiedzi na komunikaty przychodzące. Niestandardowe hosty usługi mogą być również używane w tym środowisku hostingu, ale wymagają one dodatkowego kodu w formie obiektu ServiceHostFactory. Poniższy kod przedstawia pochodną <xref:System.ServiceModel.Activation.ServiceHostFactory>, która zwraca wystąpienia naszego niestandardowego `SelfDescribingServiceHost`.  
  
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
  
 Jak widać, implementacja niestandardowego obiektu ServiceHostFactory jest bardzo prosta. Cała logika niestandardowa znajduje się wewnątrz implementacji ServiceHost; Fabryka zwraca wystąpienie klasy pochodnej.  
  
 Aby użyć fabryki niestandardowej z implementacją usługi, należy dodać dodatkowe metadane do pliku SVC usługi.  
  
```  
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"  
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"  
               language=c# Debug="true" %>  
```  
  
 W tym miejscu dodaliśmy do dyrektywy `@ServiceHost` dodatkowy atrybut `Factory` i przeszedł nazwę typu CLR fabryki niestandardowej jako wartość atrybutu. Gdy usługi IIS lub otrzymali komunikat dla tej usługi, infrastruktura hostingu WCF najpierw tworzy wystąpienie obiektu ServiceHostFactory, a następnie uruchamia samego hosta usługi przez wywołanie `ServiceHostFactory.CreateServiceHost()`.  
  
## <a name="running-the-sample"></a>Uruchamianie przykładu  
 Mimo że ten przykład zapewnia w pełni funkcjonalną implementację klienta i usługi, punkt przykładu ilustruje sposób zmiany zachowania w czasie wykonywania usługi za pomocą niestandardowego hosta. wykonaj następujące czynności:  
  
#### <a name="to-observe-the-effect-of-the-custom-host"></a>Aby obserwować efekt niestandardowego hosta  
  
1. Otwórz plik Web. config usługi i sprawdź, czy nie ma konfiguracji jawnie włączającej metadane dla usługi.  
  
2. Otwórz plik SVC usługi i sprawdź, czy jego dyrektywa @ServiceHost zawiera atrybut fabryki, który określa nazwę niestandardowego obiektu ServiceHostFactory.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Po skompilowaniu rozwiązania Uruchom polecenie Setup. bat, aby skonfigurować aplikację ServiceModelSamples w usługach IIS 7,0. Katalog ServiceModelSamples powinien teraz pojawić się jako aplikacja usług IIS 7,0.  
  
4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5. Aby usunąć aplikację IIS 7,0, uruchom polecenie Oczyść. bat.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: hostowanie usługi WCF w programie IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
