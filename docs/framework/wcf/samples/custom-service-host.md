---
title: Niestandardowy host usługi
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: 271233015739024428a7a29815f66278c9d7aa04
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789926"
---
# <a name="custom-service-host"></a><span data-ttu-id="439a2-102">Niestandardowy host usługi</span><span class="sxs-lookup"><span data-stu-id="439a2-102">Custom Service Host</span></span>
<span data-ttu-id="439a2-103">Ten przykład pokazuje, jak używać niestandardowych pochodnych klasy <xref:System.ServiceModel.ServiceHost>, aby zmienić zachowanie usługi w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="439a2-103">This sample demonstrates how to use a custom derivative of the <xref:System.ServiceModel.ServiceHost> class to alter the run-time behavior of a service.</span></span> <span data-ttu-id="439a2-104">Takie podejście umożliwia użycie alternatywnej alternatywy do konfigurowania dużej liczby usług w typowy sposób.</span><span class="sxs-lookup"><span data-stu-id="439a2-104">This approach provides a reusable alternative to configuring a large number of services in a common way.</span></span> <span data-ttu-id="439a2-105">W przykładzie pokazano również, jak użyć klasy <xref:System.ServiceModel.Activation.ServiceHostFactory>, aby użyć niestandardowego ServiceHost w Internet Information Services (IIS) lub w usłudze aktywacji procesów systemu Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="439a2-105">The sample also demonstrates how to use the <xref:System.ServiceModel.Activation.ServiceHostFactory> class to use a custom ServiceHost in the Internet Information Services (IIS) or Windows Process Activation Service (WAS) hosting environment.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="439a2-106">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="439a2-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="439a2-107">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="439a2-107">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="439a2-108">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="439a2-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="439a2-109">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="439a2-109">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a><span data-ttu-id="439a2-110">Informacje o tym scenariuszu</span><span class="sxs-lookup"><span data-stu-id="439a2-110">About the scenario</span></span>
 <span data-ttu-id="439a2-111">Aby zapobiec przypadkowemu ujawnieniu potencjalnie poufnych metadanych usługi, konfiguracja domyślna dla usług Windows Communication Foundation (WCF) wyłącza Publikowanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="439a2-111">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="439a2-112">To zachowanie jest domyślnie bezpieczne, ale oznacza to, że nie można użyć narzędzia do importowania metadanych (takiego jak Svcutil. exe) w celu wygenerowania kodu klienta wymaganego do wywołania usługi, chyba że zachowanie publikowania metadanych usługi jest jawnie włączone w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="439a2-112">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
 <span data-ttu-id="439a2-113">Włączenie publikowania metadanych dla dużej liczby usług obejmuje dodanie tych samych elementów konfiguracji do poszczególnych usług, co skutkuje znaczną ilością informacji o konfiguracji, które są zasadniczo takie same.</span><span class="sxs-lookup"><span data-stu-id="439a2-113">Enabling metadata publishing for a large number of services involves adding the same configuration elements to each individual service, which results in a large amount of configuration information that is essentially the same.</span></span> <span data-ttu-id="439a2-114">Alternatywnie, aby skonfigurować poszczególne usługi indywidualnie, można napisać bezwzględny kod, który umożliwia Publikowanie metadanych jednokrotnie, a następnie ponownie wykorzystać ten kod dla kilku różnych usług.</span><span class="sxs-lookup"><span data-stu-id="439a2-114">As an alternative to configuring each service individually, it is possible to write the imperative code that enables metadata publishing once and then reuse that code across several different services.</span></span> <span data-ttu-id="439a2-115">Jest to realizowane przez utworzenie nowej klasy, która pochodzi od <xref:System.ServiceModel.ServiceHost> i przesłania metodę `ApplyConfiguration`(), aby bezwzględnie dodać zachowanie publikowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="439a2-115">This is accomplished by creating a new class that derives from <xref:System.ServiceModel.ServiceHost> and overrides the `ApplyConfiguration`() method to imperatively add the metadata publishing behavior.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="439a2-116">Dla jasności ten przykład pokazuje, jak utworzyć niezabezpieczony punkt końcowy publikowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="439a2-116">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="439a2-117">Takie punkty końcowe są potencjalnie dostępne dla anonimowych użytkowników nieuwierzytelnionych i należy zachować ostrożność przed wdrożeniem takich punktów końcowych, aby upewnić się, że można publicznie odzamknąć metadane usługi.</span><span class="sxs-lookup"><span data-stu-id="439a2-117">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span>  
  
## <a name="implementing-a-custom-servicehost"></a><span data-ttu-id="439a2-118">Implementowanie niestandardowego ServiceHost</span><span class="sxs-lookup"><span data-stu-id="439a2-118">Implementing a custom ServiceHost</span></span>
 <span data-ttu-id="439a2-119">Klasa <xref:System.ServiceModel.ServiceHost> uwidacznia kilka przydatnych metod wirtualnych, które dziedziczą mogą przesłonić, aby zmienić zachowanie usługi w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="439a2-119">The <xref:System.ServiceModel.ServiceHost> class exposes several useful virtual methods that inheritors can override to alter the run-time behavior of a service.</span></span> <span data-ttu-id="439a2-120">Na przykład Metoda `ApplyConfiguration`() odczytuje informacje o konfiguracji usługi z magazynu konfiguracji i odpowiednio zmienia <xref:System.ServiceModel.Description.ServiceDescription> hosta.</span><span class="sxs-lookup"><span data-stu-id="439a2-120">For example, the `ApplyConfiguration`() method reads service configuration information from the configuration store and alters the host's <xref:System.ServiceModel.Description.ServiceDescription> accordingly.</span></span> <span data-ttu-id="439a2-121">Domyślna implementacja odczytuje konfigurację z pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="439a2-121">The default implementation reads configuration from the application’s configuration file.</span></span> <span data-ttu-id="439a2-122">Implementacje niestandardowe mogą przesłonić `ApplyConfiguration`(), aby jeszcze bardziej zmienić <xref:System.ServiceModel.Description.ServiceDescription> przy użyciu kodu bezwzględnego, a nawet całkowicie zastąpić domyślny magazyn konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="439a2-122">Custom implementations can override `ApplyConfiguration`() to further alter the <xref:System.ServiceModel.Description.ServiceDescription> using imperative code or even replace the default configuration store entirely.</span></span> <span data-ttu-id="439a2-123">Na przykład, aby odczytać konfigurację punktu końcowego usługi z bazy danych zamiast pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="439a2-123">For example, to read a service’s endpoint configuration from a database instead of the application’s configuration file.</span></span>  
  
 <span data-ttu-id="439a2-124">W tym przykładzie chcemy utworzyć niestandardowy ServiceHost, który dodaje ServiceMetadataBehavior (co umożliwia Publikowanie metadanych), nawet jeśli to zachowanie nie zostanie jawnie dodane w pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="439a2-124">In this sample, we want to build a custom ServiceHost that adds the ServiceMetadataBehavior, (which enables metadata publishing), even if this behavior is not explicitly added in the service’s configuration file.</span></span> <span data-ttu-id="439a2-125">Aby to osiągnąć, tworzymy nową klasę, która dziedziczy po <xref:System.ServiceModel.ServiceHost> i przesłania `ApplyConfiguration`().</span><span class="sxs-lookup"><span data-stu-id="439a2-125">To accomplish this, we create a new class that inherits from <xref:System.ServiceModel.ServiceHost> and overrides `ApplyConfiguration`().</span></span>  
  
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
  
 <span data-ttu-id="439a2-126">Ponieważ nie chcemy ignorować żadnej konfiguracji, która została dostarczona w pliku konfiguracyjnym aplikacji, pierwsze zastępowanie `ApplyConfiguration`() jest wywołaniem podstawowej implementacji.</span><span class="sxs-lookup"><span data-stu-id="439a2-126">Because we do not want to ignore any configuration that has been provided in the application’s configuration file, the first thing our override of `ApplyConfiguration`() does is call the base implementation.</span></span> <span data-ttu-id="439a2-127">Po zakończeniu tej metody możemy bezwzględnie dodać <xref:System.ServiceModel.Description.ServiceMetadataBehavior> do opisu przy użyciu następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="439a2-127">Once this method completes, we can imperatively add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> to the description using the following imperative code.</span></span>  
  
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
  
 <span data-ttu-id="439a2-128">Ostatnim zastępowaniem naszych `ApplyConfiguration`() musi być dodanie domyślnego punktu końcowego metadanych.</span><span class="sxs-lookup"><span data-stu-id="439a2-128">The last thing our `ApplyConfiguration`() override must do is add the default metadata endpoint.</span></span> <span data-ttu-id="439a2-129">Zgodnie z Konwencją jeden punkt końcowy metadanych jest tworzony dla każdego identyfikatora URI w kolekcji BaseAddresses hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="439a2-129">By convention, one metadata endpoint is created for each URI in the service host’s BaseAddresses collection.</span></span>  
  
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
  
## <a name="using-a-custom-servicehost-in-self-host"></a><span data-ttu-id="439a2-130">Używanie niestandardowego ServiceHost na własnym hoście</span><span class="sxs-lookup"><span data-stu-id="439a2-130">Using a custom ServiceHost in self-host</span></span>  
 <span data-ttu-id="439a2-131">Po ukończeniu naszej niestandardowej implementacji ServiceHost można użyć jej do dodania zachowania publikowania metadanych do dowolnej usługi, udostępniając ją w ramach wystąpienia naszego `SelfDescribingServiceHost`.</span><span class="sxs-lookup"><span data-stu-id="439a2-131">Now that we have completed our custom ServiceHost implementation, we can use it to add metadata publishing behavior to any service by hosting that service inside of an instance of our `SelfDescribingServiceHost`.</span></span> <span data-ttu-id="439a2-132">Poniższy kod przedstawia sposób korzystania z niego w scenariuszu z własnym hostem.</span><span class="sxs-lookup"><span data-stu-id="439a2-132">The following code shows how to use it in the self-host scenario.</span></span>  
  
```csharp
SelfDescribingServiceHost host =   
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 <span data-ttu-id="439a2-133">Nasz Host niestandardowy nadal odczytuje konfigurację punktu końcowego usługi z pliku konfiguracyjnego aplikacji, podobnie jak w przypadku użycia domyślnej klasy <xref:System.ServiceModel.ServiceHost> do hostowania usługi.</span><span class="sxs-lookup"><span data-stu-id="439a2-133">Our custom host still reads the service’s endpoint configuration from the application’s configuration file, just as if we had used the default <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="439a2-134">Jednak ze względu na to, że dodaliśmy logikę umożliwiającą opublikowanie metadanych w ramach naszego hosta niestandardowego, nie należy jawnie włączać zachowania publikowania metadanych w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="439a2-134">However, because we added the logic to enable metadata publishing inside of our custom host, we no longer must explicitly enable the metadata publishing behavior in configuration.</span></span> <span data-ttu-id="439a2-135">Takie podejście ma różne zalety podczas kompilowania aplikacji, która zawiera kilka usług i chcesz włączyć Publikowanie metadanych na każdym z nich bez konieczności pisania tych samych elementów konfiguracji w porównaniu do i więcej.</span><span class="sxs-lookup"><span data-stu-id="439a2-135">This approach has a distinct advantage when you are building an application that contains several services and you want to enable metadata publishing on each of them without writing the same configuration elements over and over.</span></span>  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a><span data-ttu-id="439a2-136">Używanie niestandardowego ServiceHost w usługach IIS lub</span><span class="sxs-lookup"><span data-stu-id="439a2-136">Using a custom ServiceHost in IIS or WAS</span></span>  
 <span data-ttu-id="439a2-137">Używanie niestandardowego hosta usługi w scenariuszach z własnym hostem jest proste, ponieważ jest to kod aplikacji, który jest ostatecznie odpowiedzialny za tworzenie i otwieranie wystąpienia hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="439a2-137">Using a custom service host in self-host scenarios is straightforward, because it is your application code that is ultimately responsible for creating and opening the service host instance.</span></span> <span data-ttu-id="439a2-138">Jednak w usługach IIS lub w środowisku macierzystym Infrastruktura WCF tworzy dynamicznie wystąpienie hosta usługi w odpowiedzi na komunikaty przychodzące.</span><span class="sxs-lookup"><span data-stu-id="439a2-138">In the IIS or WAS hosting environment, however, the WCF infrastructure is dynamically instantiating your service’s host in response to incoming messages.</span></span> <span data-ttu-id="439a2-139">Niestandardowe hosty usługi mogą być również używane w tym środowisku hostingu, ale wymagają one dodatkowego kodu w formie obiektu ServiceHostFactory.</span><span class="sxs-lookup"><span data-stu-id="439a2-139">Custom service hosts can also be used in this hosting environment, but they require some additional code in the form of a ServiceHostFactory.</span></span> <span data-ttu-id="439a2-140">Poniższy kod przedstawia pochodną <xref:System.ServiceModel.Activation.ServiceHostFactory>, która zwraca wystąpienia naszego niestandardowego `SelfDescribingServiceHost`.</span><span class="sxs-lookup"><span data-stu-id="439a2-140">The following code shows a derivative of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns instances of our custom `SelfDescribingServiceHost`.</span></span>  
  
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
  
 <span data-ttu-id="439a2-141">Jak widać, implementacja niestandardowego obiektu ServiceHostFactory jest bardzo prosta.</span><span class="sxs-lookup"><span data-stu-id="439a2-141">As you can see, implementing a custom ServiceHostFactory is very straightforward.</span></span> <span data-ttu-id="439a2-142">Cała logika niestandardowa znajduje się wewnątrz implementacji ServiceHost; Fabryka zwraca wystąpienie klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="439a2-142">All of the custom logic resides inside of the ServiceHost implementation; the factory returns an instance of the derived class.</span></span>  
  
 <span data-ttu-id="439a2-143">Aby użyć fabryki niestandardowej z implementacją usługi, należy dodać dodatkowe metadane do pliku SVC usługi.</span><span class="sxs-lookup"><span data-stu-id="439a2-143">To use a custom factory with a service implementation, we must add some additional metadata to the service’s .svc file.</span></span>  
  
```xml
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"
               language=c# Debug="true" %>
```
  
 <span data-ttu-id="439a2-144">W tym miejscu dodaliśmy do dyrektywy `@ServiceHost` dodatkowy atrybut `Factory` i przeszedł nazwę typu CLR fabryki niestandardowej jako wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="439a2-144">Here we have added an additional `Factory` attribute to the `@ServiceHost` directive, and passed the CLR type name of our custom factory as the attribute’s value.</span></span> <span data-ttu-id="439a2-145">Gdy usługi IIS lub otrzymali komunikat dla tej usługi, infrastruktura hostingu WCF najpierw tworzy wystąpienie obiektu ServiceHostFactory, a następnie uruchamia samego hosta usługi przez wywołanie `ServiceHostFactory.CreateServiceHost()`.</span><span class="sxs-lookup"><span data-stu-id="439a2-145">When IIS or WAS receives a message for this service, the WCF hosting infrastructure first creates an instance of the ServiceHostFactory and then instantiate the service host itself by calling `ServiceHostFactory.CreateServiceHost()`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="439a2-146">Uruchamianie przykładu</span><span class="sxs-lookup"><span data-stu-id="439a2-146">Running the sample</span></span>  
 <span data-ttu-id="439a2-147">Mimo że ten przykład zapewnia w pełni funkcjonalną implementację klienta i usługi, punkt przykładu ilustruje sposób zmiany zachowania w czasie wykonywania usługi za pomocą niestandardowego hosta. wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="439a2-147">Although this sample does provide a fully-functional client and service implementation, the point of the sample is to illustrate how to alter a service’s run-time behavior by means of a custom host., do the following steps:</span></span>  
  
### <a name="observe-the-effect-of-the-custom-host"></a><span data-ttu-id="439a2-148">Obserwuj efekt hosta niestandardowego</span><span class="sxs-lookup"><span data-stu-id="439a2-148">Observe the effect of the custom host</span></span>
  
1. <span data-ttu-id="439a2-149">Otwórz plik Web. config usługi i sprawdź, czy nie ma konfiguracji jawnie włączającej metadane dla usługi.</span><span class="sxs-lookup"><span data-stu-id="439a2-149">Open the service's Web.config file and observe that there is no configuration explicitly enabling metadata for the service.</span></span>  
  
2. <span data-ttu-id="439a2-150">Otwórz plik SVC usługi i sprawdź, czy jego dyrektywa @ServiceHost zawiera atrybut fabryki, który określa nazwę niestandardowego obiektu ServiceHostFactory.</span><span class="sxs-lookup"><span data-stu-id="439a2-150">Open the service's .svc file and observe that its @ServiceHost directive contains a Factory attribute that specifies the name of a custom ServiceHostFactory.</span></span>  
  
### <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="439a2-151">Konfigurowanie, kompilowanie i uruchamianie przykładu</span><span class="sxs-lookup"><span data-stu-id="439a2-151">Set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="439a2-152">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="439a2-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="439a2-153">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="439a2-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="439a2-154">Po skompilowaniu rozwiązania Uruchom polecenie Setup. bat, aby skonfigurować aplikację ServiceModelSamples w usługach IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="439a2-154">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="439a2-155">Katalog ServiceModelSamples powinien teraz pojawić się jako aplikacja usług IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="439a2-155">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="439a2-156">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="439a2-156">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

5. <span data-ttu-id="439a2-157">Aby usunąć aplikację IIS 7,0, uruchom polecenie *Oczyść. bat*.</span><span class="sxs-lookup"><span data-stu-id="439a2-157">To remove the IIS 7.0 application, run *Cleanup.bat*.</span></span>

## <a name="see-also"></a><span data-ttu-id="439a2-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="439a2-158">See also</span></span>

- [<span data-ttu-id="439a2-159">Instrukcje: hostowanie usługi WCF w programie IIS</span><span class="sxs-lookup"><span data-stu-id="439a2-159">How to: Host a WCF Service in IIS</span></span>](../feature-details/how-to-host-a-wcf-service-in-iis.md)
