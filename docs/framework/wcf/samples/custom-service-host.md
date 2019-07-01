---
title: Niestandardowy host usługi
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: 9c2a1fc1b398a3a9efcd0c824ca041a790448dd3
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487643"
---
# <a name="custom-service-host"></a>Niestandardowy host usługi
W tym przykładzie przedstawiono sposób użycia niestandardowego utworów zależnych od <xref:System.ServiceModel.ServiceHost> klasy do zmiany zachowania usługi w czasie wykonywania. Metoda ta umożliwia wielokrotnego użytku alternatywa konfigurowanie dużej liczby usług w typowy sposób. W przykładzie pokazano również sposób użycia <xref:System.ServiceModel.Activation.ServiceHostFactory> klasy, aby użyć niestandardowego elementu ServiceHost w środowisku hostingu usług Internet Information Services (IIS) lub Windows Process Activation Service (WAS).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a>Scenariusz — informacje  
 Aby zapobiegać niezamierzonym ujawnieniem metadanych usługi potencjalnie poufnych, konfigurację domyślną dla usług Windows Communication Foundation (WCF) powoduje wyłączenie publikowania metadanych. To zachowanie jest domyślnie bezpieczny, ale również zaimportować narzędzia (takie jak Svcutil.exe) oznacza, że metadane nie można użyć do wygenerowania kodu klienta wymaganych do wywołania tej usługi, chyba że jawnie włączone jest zachowanie publikowania metadanych usługi w konfiguracji.  
  
 Włączanie Publikowanie metadanych dla dużej liczby usług obejmuje dodanie tych samych elementów konfiguracji dla wszystkich poszczególnych usług, co skutkuje dużą ilość informacji o konfiguracji, który jest zasadniczo taki sam. Alternatywnie na oddzielne Konfigurowanie każdej usługi jest możliwe do pisania kodu imperatywnego, który umożliwia publikowanie raz metadanych i następnie ponowne użycie tego kodu na kilka różnych usług. Jest to osiągane przez utworzenie nowej klasy, która pochodzi od klasy <xref:System.ServiceModel.ServiceHost> i zastępuje `ApplyConfiguration`metodę (), aby dodać obowiązkowo zachowanie publikowania metadanych.  
  
> [!IMPORTANT]
>  Dla jasności ten przykład przedstawia sposób tworzenia punkt końcowy publikowania metadanych niezabezpieczona. Takie punkty końcowe są potencjalnie dostępne dla anonimowe, nieuwierzytelnione konsumentów i należy uważać, przed wdrożeniem tych punktów końcowych w celu zapewnienia publicznie ujawniająca metadanych usługi odpowiednie.  
  
## <a name="implementing-a-custom-servicehost"></a>Implementowanie niestandardowego elementu ServiceHost  
 <xref:System.ServiceModel.ServiceHost> Klasa udostępnia kilka metod wirtualnych przydatne przesłaniające przez obiektów dziedziczących do zmiany zachowania w czasie wykonywania usługi. Na przykład `ApplyConfiguration`— metoda () odczytuje informacje konfiguracyjne usługi z magazynu konfiguracji i zmienia hosta <xref:System.ServiceModel.Description.ServiceDescription> odpowiednio. Domyślna implementacja odczytuje konfiguracji z pliku konfiguracji aplikacji. Niestandardowe implementacje można zastąpić `ApplyConfiguration`() do dalszej zmiany <xref:System.ServiceModel.Description.ServiceDescription> przy użyciu kodu imperatywnego lub nawet zastąpienia domyślnego magazynu konfiguracji w całości. Na przykład, można odczytać konfiguracji punktu końcowego usługi z bazy danych zamiast pliku konfiguracji aplikacji.  
  
 W tym przykładzie chcemy utworzyć niestandardowego elementu ServiceHost, który dodaje ServiceMetadataBehavior, (który umożliwia publikowanie metadanych), nawet jeśli to zachowanie nie została jawnie dodana w pliku konfiguracji usługi. Aby to osiągnąć, możemy utworzyć nowej klasy, która dziedziczy <xref:System.ServiceModel.ServiceHost> i zastępuje `ApplyConfiguration`().  
  
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
  
 Ponieważ nie chcemy Ignoruj żadnej konfiguracji, który został dostarczony w pliku konfiguracji aplikacji, przede wszystkim naszym zastępowania metody `ApplyConfiguration`() jest to wywołanie implementację podstawową. Po ukończeniu tej metody można obowiązkowo dodamy <xref:System.ServiceModel.Description.ServiceMetadataBehavior> opisu, używając następującego kodu imperatywnego.  
  
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
  
 Ostatnią czynnością, jaką naszych `ApplyConfiguration`konieczne zastąpienie () jest dodać domyślny punkt końcowy metadanych. Zgodnie z Konwencją jeden punkt końcowy metadanych jest tworzony dla każdego identyfikatora URI w kolekcji BaseAddresses hosta usługi.  
  
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
  
## <a name="using-a-custom-servicehost-in-self-host"></a>Za pomocą niestandardowego elementu ServiceHost w samodzielnego hostowania  
 Teraz, gdy ukończyliśmy naszej niestandardowych implementacji elementu ServiceHost wykorzystamy je dodać zachowanie publikowania metadanych do dowolnej usługi, udostępniając usługi wewnątrz wystąpienia naszej `SelfDescribingServiceHost`. Poniższy kod przedstawia sposób używania go w tym scenariuszu samodzielnego hostowania.  
  
```  
SelfDescribingServiceHost host =   
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 Nasze niestandardowego hosta nadal odczytuje konfiguracji punktu końcowego usługi z pliku konfiguracji aplikacji, tak, jakby było użyte domyślne <xref:System.ServiceModel.ServiceHost> klasy do obsługi usługi. Jednak ponieważ dodaliśmy logiki, aby włączyć publikowanie w naszym niestandardowego hosta metadanych, firma Microsoft nie jest już jawnie włączyć metadanych zachowanie publikowania w konfiguracji. Takie podejście ma różne korzyści, gdy tworzysz aplikację, która zawiera kilka usług i chcesz włączyć publikowanie metadanych na każdym z nich, bez konieczności pisania te same elementy konfiguracji wielokrotnie.  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a>Za pomocą niestandardowego elementu ServiceHost w usługach IIS i WAS  
 Niestandardowy host usługi w scenariuszach hosta samodzielnego jest prosta, ponieważ jest on kodzie aplikacji, która jest ponoszą ostateczną odpowiedzialność za tworzenie i otwieranie instancja hosta usługi. W usługach IIS lub WAS Środowisko hostingu jednak infrastruktura WCF jest dynamicznie Tworzenie wystąpienia usługi hosta w odpowiedzi na wiadomości przychodzące. Hosty niestandardowych usług można również w tym środowisku hostingu, ale wymagają one dodatkowy kod w postaci elementu ServiceHostFactory. Poniższy kod przedstawia zależnych od <xref:System.ServiceModel.Activation.ServiceHostFactory> zwracająca wystąpienia klasy Nasze niestandardowe `SelfDescribingServiceHost`.  
  
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
  
 Jak widać, Implementowanie niestandardowego elementu ServiceHostFactory jest bardzo proste. Wszystkie niestandardowej logiki znajduje się wewnątrz elementu ServiceHost wdrożenia; Fabryka Zwraca wystąpienie klasy pochodnej.  
  
 Niestandardowych ustawień fabrycznych za pomocą implementacji usługi, możemy dodać pewnymi dodatkowymi metadanymi plikowi .svc usługi.  
  
```  
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"  
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"  
               language=c# Debug="true" %>  
```  
  
 W tym miejscu dodaliśmy dodatkowe `Factory` atrybutu `@ServiceHost` dyrektywy i przekazanych środowiska CLR, wpisz nazwę fabryki niestandardowe jako wartość atrybutu. Gdy usługi IIS i WAS otrzymuje komunikat dotyczący tej usługi, infrastruktury hostingu WCF najpierw tworzy wystąpienie elementu ServiceHostFactory i, tworzy sam host usługi przez wywołanie metody `ServiceHostFactory.CreateServiceHost()`.  
  
## <a name="running-the-sample"></a>Działa aplikacja przykładowa  
 Chociaż w tym przykładzie zapewniają klienta w pełni funkcjonalne i implementacji usługi, poniższego przykładu jest pokazują, jak zmienić zachowanie usługi w czasie wykonywania za pomocą niestandardowego hosta., wykonaj następujące czynności:  
  
#### <a name="to-observe-the-effect-of-the-custom-host"></a>Aby obserwować wpływ niestandardowego hosta  
  
1. Otwórz plik Web.config usługi i sprawdź, czy brak konfiguracji jawnie Włączanie metadanych dla usługi.  
  
2. Otwórz plik .svc usługi i Zauważ, że jego @ServiceHost dyrektywa zawiera atrybut fabryki, który określa nazwę niestandardowego elementu ServiceHostFactory.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Po rozwiązaniu została skompilowana, uruchom Setup.bat jest, aby skonfigurować aplikację ServiceModelSamples w usługach IIS 7.0. Katalog ServiceModelSamples teraz powinna zostać wyświetlona jako aplikację IIS 7.0.  
  
4. Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5. Aby usunąć aplikację usług IIS 7.0, uruchom Cleanup.bat.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Hostowanie usługi WCF w programie IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
