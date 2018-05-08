---
title: Niestandardowy host usługi
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: c081858d57d9575a616c7c057047b0593a177f3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="custom-service-host"></a>Niestandardowy host usługi
W tym przykładzie przedstawiono sposób użycia niestandardowego pochodną <xref:System.ServiceModel.ServiceHost> klasy do zmiany zachowania usługi w czasie wykonywania. Metoda ta umożliwia wielokrotnego użytku sposobem konfigurowania wielu usług w typowy sposób. Próbka przedstawiono również sposób użycia <xref:System.ServiceModel.Activation.ServiceHostFactory> klasy do użycia niestandardowego elementu ServiceHost w środowisku macierzystym Internet Information Services (IIS) lub usługi aktywacji procesów systemu Windows (WAS).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a>Scenariusz — informacje  
 Aby zapobiec przypadkowe ujawnienie metadanych usługi potencjalnie poufnych, konfigurację domyślną dla usług Windows Communication Foundation (WCF) wyłącza Publikowanie metadanych. To zachowanie jest domyślnie bezpieczne, ale również zaimportować narzędzia (na przykład Svcutil.exe) oznacza, że metadane nie można użyć do generowania kodu klienta wymaganych do wywołania tej usługi, chyba że jawnie włączone jest zachowanie podczas publikowania metadanych usługi w konfiguracji.  
  
 Włączanie publikowania metadanych dla dużej liczby usług obejmuje dodawanie te same elementy konfiguracji do każdej pojedynczej usługi, co powoduje duże ilości informacji o konfiguracji, który jest zasadniczo taki sam. Jako alternatywę do konfigurowania poszczególnych usług indywidualnie jest można napisać kod imperatywnych, który umożliwia raz publikowania metadanych i następnie ponowne użycie tego kodu na kilka różnych usług. Jest to osiągane przez utworzenie nowej klasy, która jest pochodną <xref:System.ServiceModel.ServiceHost> i zastępuje `ApplyConfiguration`— metoda (), aby dodać imperatively zachowanie publikowania metadanych.  
  
> [!IMPORTANT]
>  Dla jasności ten przykład przedstawia sposób tworzenia punkt końcowy publikowania metadanych niezabezpieczona. Takie punkty końcowe są potencjalnie dostępne dla anonimowych użytkowników nieuwierzytelnionych i należy uważać przed wdrożeniem takich punktów końcowych w celu zapewnienia publicznie ujawniająca metadanych usługi odpowiednie.  
  
## <a name="implementing-a-custom-servicehost"></a>Implementowanie niestandardowego elementu ServiceHost  
 <xref:System.ServiceModel.ServiceHost> Klasy udostępnia kilka metod wirtualnych przydatne dziedziczenia można zastąpić do zmiany zachowania czasu wykonywania dla usługi. Na przykład `ApplyConfiguration`() metoda odczytuje informacje konfiguracyjne usługi z magazynu konfiguracji i zmienia hosta <xref:System.ServiceModel.Description.ServiceDescription> odpowiednio. Domyślna implementacja odczytuje konfiguracji z pliku konfiguracji aplikacji. Można zastąpić implementacji niestandardowych `ApplyConfiguration`() do dalszej alter <xref:System.ServiceModel.Description.ServiceDescription> przy użyciu kodu imperatywnych lub nawet całkowicie zastąpić magazynu konfiguracji domyślnej. Na przykład, aby odczytać konfiguracji punktu końcowego usługi z bazy danych zamiast pliku konfiguracji aplikacji.  
  
 W tym przykładzie chcemy utworzyć niestandardowe ServiceHost, który dodaje ServiceMetadataBehavior, (który umożliwia publikowanie metadanych), nawet jeśli jest to zachowanie nie jest jawnie dodać w pliku konfiguracji usługi. Aby to zrobić, utworzymy nową klasę, która dziedziczy <xref:System.ServiceModel.ServiceHost> i zastępuje `ApplyConfiguration`().  
  
```  
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
  
 Ponieważ nie chcemy Ignoruj żadnej konfiguracji, które podano w pliku konfiguracji aplikacji, najpierw naszych zastępowania `ApplyConfiguration`() jest to wywołanie implementacji podstawowej. Po zakończeniu tej metody, można dodać imperatively <xref:System.ServiceModel.Description.ServiceMetadataBehavior> w opisie przy użyciu następującego kodu nadrzędnych.  
  
```  
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
  
 Ostatnim etapem naszych `ApplyConfiguration`wykonaj zastąpienia () jest dodawany domyślny punkt końcowy metadanych. Konwencja jeden punkt końcowy metadanych jest tworzony dla każdego identyfikatora URI w kolekcji BaseAddresses hosta usługi.  
  
```  
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
  
## <a name="using-a-custom-servicehost-in-self-host"></a>Używanie niestandardowych ServiceHost w host samodzielny  
 Teraz, kiedy możemy zakończone naszych implementacja niestandardowa ServiceHost, wykorzystamy je dodać zachowanie podczas publikowania metadanych do dowolnej usługi, udostępniając usługi wewnątrz wystąpienia naszych `SelfDescribingServiceHost`. Poniższy kod przedstawia sposób użycia go w scenariuszu host samodzielny.  
  
```  
SelfDescribingServiceHost host =   
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 Nasze hosta niestandardowego nadal odczytuje konfiguracji punktu końcowego usługi z pliku konfiguracji aplikacji, tak jakby było użyliśmy domyślne <xref:System.ServiceModel.ServiceHost> klasy do obsługi usługi. Jednak ponieważ dodaliśmy logiki można włączyć publikowania wewnątrz naszego hosta niestandardowego metadanych, firma Microsoft nie jest już jawnie włączyć zachowanie publikowania w konfiguracji metadanych. Takie podejście charakteryzuje się różne korzyści podczas tworzenia aplikacji, która zawiera kilka usług i chcesz włączyć publikowanie metadanych na każdym z nich, bez konieczności samodzielnego pisania te same elementy konfiguracji.  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a>Przy użyciu niestandardowych ServiceHost w usługach IIS lub WAS  
 W scenariuszach hosta samodzielnego przy użyciu hosta niestandardowego usługi jest proste, ponieważ jest kod aplikacji ostatecznie odpowiedzialną za tworzenie i otwieranie wystąpienie hosta usługi. W usługach IIS lub WAS hosting środowiska, jednak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury dynamicznie tworzenia wystąpienia usługi hosta w odpowiedzi na wiadomości przychodzących. Hosty usługi niestandardowej można także w tym środowisku hostingu, ale wymagają dodatkowy kod w formularzu elementu ServiceHostFactory. Poniższy kod przedstawia pochodną <xref:System.ServiceModel.Activation.ServiceHostFactory> zwracająca wystąpienia klasy Nasze niestandardowe `SelfDescribingServiceHost`.  
  
```  
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
  
 Jak widać, Implementowanie niestandardowego elementu ServiceHostFactory jest bardzo prosta. Wszystkie niestandardowej logiki znajduje się wewnątrz implementacji ServiceHost; Fabryka Zwraca wystąpienie klasy pochodnej.  
  
 Aby użyć niestandardowej fabryki z implementacją usługi, możemy dodać niektóre dodatkowe metadane w pliku svc usługi.  
  
```  
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"  
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"  
               language=c# Debug="true" %>  
```  
  
 W tym miejscu dodano dodatkowe `Factory` atrybutu `@ServiceHost` dyrektywy i przekazany CLR wpisz nazwę fabryki niestandardowych jako wartość atrybutu. Gdy usługi IIS lub WAS odbiera komunikat dla tej usługi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hosting infrastruktury najpierw tworzy wystąpienie elementu ServiceHostFactory, a następnie utworzyć przez wywołanie metody wystąpienia sam host usługi `ServiceHostFactory.CreateServiceHost()`.  
  
## <a name="running-the-sample"></a>Uruchomiona próbki  
 Mimo że w tym przykładzie zapewnienia pełnej funkcjonalności klienta i wdrożenia usługi, punkt próbki jest pokazano, jak zmienić zachowanie środowiska wykonawczego usługi przy użyciu hosta niestandardowego., wykonaj następujące czynności:  
  
#### <a name="to-observe-the-effect-of-the-custom-host"></a>Aby sprawdzić efekt hosta niestandardowego  
  
1.  Otwórz plik Web.config usługi i sprawdź, czy nie istnieje konfiguracja jawnie włączenie metadanych dla usługi.  
  
2.  Otwórz plik .svc usługi i że jego @ServiceHost dyrektywa zawiera atrybut Factory, który określa nazwę niestandardowego elementu ServiceHostFactory.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Po utworzeniu rozwiązania należy uruchomić pliku Setup.bat, aby skonfigurować aplikację ServiceModelSamples w [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. Katalog ServiceModelSamples powinien zostać wyświetlony jako [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikacji.  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Aby usunąć [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikacji, uruchom Cleanup.bat.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: hostowanie usługi WCF w programie IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
