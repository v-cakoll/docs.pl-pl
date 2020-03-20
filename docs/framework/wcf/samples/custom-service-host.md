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
# <a name="custom-service-host"></a><span data-ttu-id="efcdc-102">Niestandardowy host usługi</span><span class="sxs-lookup"><span data-stu-id="efcdc-102">Custom Service Host</span></span>
<span data-ttu-id="efcdc-103">W tym przykładzie pokazano, jak <xref:System.ServiceModel.ServiceHost> używać niestandardowej pochodnej klasy, aby zmienić zachowanie w czasie wykonywania usługi.</span><span class="sxs-lookup"><span data-stu-id="efcdc-103">This sample demonstrates how to use a custom derivative of the <xref:System.ServiceModel.ServiceHost> class to alter the run-time behavior of a service.</span></span> <span data-ttu-id="efcdc-104">Takie podejście zapewnia wielokrotnego stosowania alternatywy do konfigurowania dużej liczby usług w typowy sposób.</span><span class="sxs-lookup"><span data-stu-id="efcdc-104">This approach provides a reusable alternative to configuring a large number of services in a common way.</span></span> <span data-ttu-id="efcdc-105">W przykładzie pokazano również, <xref:System.ServiceModel.Activation.ServiceHostFactory> jak używać klasy do używania niestandardowego servicehost w środowisku hostingu internetowych usług informacyjnych (IIS) lub usługi aktywacji procesów systemu Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="efcdc-105">The sample also demonstrates how to use the <xref:System.ServiceModel.Activation.ServiceHostFactory> class to use a custom ServiceHost in the Internet Information Services (IIS) or Windows Process Activation Service (WAS) hosting environment.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="efcdc-106">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="efcdc-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="efcdc-107">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="efcdc-107">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="efcdc-108">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="efcdc-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="efcdc-109">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="efcdc-109">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a><span data-ttu-id="efcdc-110">Informacje o scenariuszu</span><span class="sxs-lookup"><span data-stu-id="efcdc-110">About the scenario</span></span>
 <span data-ttu-id="efcdc-111">Aby zapobiec niezamierzonemu ujawnieniu potencjalnie poufnych metadanych usługi, domyślna konfiguracja usług Windows Communication Foundation (WCF) wyłącza publikowanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="efcdc-111">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="efcdc-112">To zachowanie jest domyślnie bezpieczne, ale oznacza również, że nie można użyć narzędzia importu metadanych (na przykład Svcutil.exe) do generowania kodu klienta wymaganego do wywołania usługi, chyba że zachowanie publikowania metadanych usługi jest jawnie włączone w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="efcdc-112">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
 <span data-ttu-id="efcdc-113">Włączanie publikowania metadanych dla dużej liczby usług obejmuje dodanie tych samych elementów konfiguracji do każdej usługi, co powoduje dużą ilość informacji o konfiguracji, która jest zasadniczo taka sama.</span><span class="sxs-lookup"><span data-stu-id="efcdc-113">Enabling metadata publishing for a large number of services involves adding the same configuration elements to each individual service, which results in a large amount of configuration information that is essentially the same.</span></span> <span data-ttu-id="efcdc-114">Jako alternatywę dla konfigurowania każdej usługi indywidualnie, istnieje możliwość zapisu kodu imperatywu, który umożliwia publikowanie metadanych raz, a następnie ponownie użyć tego kodu w kilku różnych usług.</span><span class="sxs-lookup"><span data-stu-id="efcdc-114">As an alternative to configuring each service individually, it is possible to write the imperative code that enables metadata publishing once and then reuse that code across several different services.</span></span> <span data-ttu-id="efcdc-115">Jest to realizowane przez utworzenie nowej klasy, <xref:System.ServiceModel.ServiceHost> która wywodzi się z `ApplyConfiguration`() metody () i zastępuje ją, aby bezwzględnie dodać zachowanie publikowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="efcdc-115">This is accomplished by creating a new class that derives from <xref:System.ServiceModel.ServiceHost> and overrides the `ApplyConfiguration`() method to imperatively add the metadata publishing behavior.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="efcdc-116">Dla jasności w tym przykładzie pokazano, jak utworzyć niezabezpieczony punkt końcowy publikowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="efcdc-116">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="efcdc-117">Takie punkty końcowe są potencjalnie dostępne dla anonimowych nieuwierzytetycznych konsumentów i należy zwrócić uwagę przed wdrożeniem takich punktów końcowych, aby upewnić się, że publiczne ujawnienie metadanych usługi jest właściwe.</span><span class="sxs-lookup"><span data-stu-id="efcdc-117">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span>  
  
## <a name="implementing-a-custom-servicehost"></a><span data-ttu-id="efcdc-118">Implementowanie niestandardowego hosta usługi</span><span class="sxs-lookup"><span data-stu-id="efcdc-118">Implementing a custom ServiceHost</span></span>
 <span data-ttu-id="efcdc-119">Klasa <xref:System.ServiceModel.ServiceHost> udostępnia kilka przydatnych metod wirtualnych, które dziedzicze mogą zastąpić, aby zmienić zachowanie w czasie wykonywania usługi.</span><span class="sxs-lookup"><span data-stu-id="efcdc-119">The <xref:System.ServiceModel.ServiceHost> class exposes several useful virtual methods that inheritors can override to alter the run-time behavior of a service.</span></span> <span data-ttu-id="efcdc-120">Na przykład `ApplyConfiguration`() metoda odczytuje informacje o konfiguracji usługi z <xref:System.ServiceModel.Description.ServiceDescription> magazynu konfiguracji i zmienia hosta odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="efcdc-120">For example, the `ApplyConfiguration`() method reads service configuration information from the configuration store and alters the host's <xref:System.ServiceModel.Description.ServiceDescription> accordingly.</span></span> <span data-ttu-id="efcdc-121">Domyślna implementacja odczytuje konfigurację z pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="efcdc-121">The default implementation reads configuration from the application’s configuration file.</span></span> <span data-ttu-id="efcdc-122">Implementacje niestandardowe `ApplyConfiguration`można zastąpić () <xref:System.ServiceModel.Description.ServiceDescription> do dalszej zmiany przy użyciu kodu imperatywnego lub nawet zastąpić domyślny magazyn konfiguracji całkowicie.</span><span class="sxs-lookup"><span data-stu-id="efcdc-122">Custom implementations can override `ApplyConfiguration`() to further alter the <xref:System.ServiceModel.Description.ServiceDescription> using imperative code or even replace the default configuration store entirely.</span></span> <span data-ttu-id="efcdc-123">Na przykład, aby odczytać konfigurację punktu końcowego usługi z bazy danych zamiast pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="efcdc-123">For example, to read a service’s endpoint configuration from a database instead of the application’s configuration file.</span></span>  
  
 <span data-ttu-id="efcdc-124">W tym przykładzie chcemy utworzyć niestandardowy ServiceHost, który dodaje ServiceMetadataBehavior (który umożliwia publikowanie metadanych), nawet jeśli to zachowanie nie jest jawnie dodawane w pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="efcdc-124">In this sample, we want to build a custom ServiceHost that adds the ServiceMetadataBehavior, (which enables metadata publishing), even if this behavior is not explicitly added in the service’s configuration file.</span></span> <span data-ttu-id="efcdc-125">Aby to osiągnąć, tworzymy nową klasę, która dziedziczy <xref:System.ServiceModel.ServiceHost> i zastępuje `ApplyConfiguration`().</span><span class="sxs-lookup"><span data-stu-id="efcdc-125">To accomplish this, we create a new class that inherits from <xref:System.ServiceModel.ServiceHost> and overrides `ApplyConfiguration`().</span></span>  
  
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
  
 <span data-ttu-id="efcdc-126">Ponieważ nie chcemy ignorować żadnej konfiguracji, która została podana w pliku konfiguracyjnym aplikacji, pierwszą rzeczą, którą wykonuje nasze zastąpienie `ApplyConfiguration`() jest wywołanie implementacji podstawowej.</span><span class="sxs-lookup"><span data-stu-id="efcdc-126">Because we do not want to ignore any configuration that has been provided in the application’s configuration file, the first thing our override of `ApplyConfiguration`() does is call the base implementation.</span></span> <span data-ttu-id="efcdc-127">Po zakończeniu tej metody, możemy bezwzględnie dodać <xref:System.ServiceModel.Description.ServiceMetadataBehavior> do opisu przy użyciu następującego kodu imperatywu.</span><span class="sxs-lookup"><span data-stu-id="efcdc-127">Once this method completes, we can imperatively add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> to the description using the following imperative code.</span></span>  
  
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
  
 <span data-ttu-id="efcdc-128">Ostatnią rzeczą, `ApplyConfiguration`którą musi wykonać nasze () zastąpienie, jest dodanie domyślnego punktu końcowego metadanych.</span><span class="sxs-lookup"><span data-stu-id="efcdc-128">The last thing our `ApplyConfiguration`() override must do is add the default metadata endpoint.</span></span> <span data-ttu-id="efcdc-129">Zgodnie z konwencją jeden punkt końcowy metadanych jest tworzony dla każdego identyfikatora URI w kolekcji BaseAddresses hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="efcdc-129">By convention, one metadata endpoint is created for each URI in the service host’s BaseAddresses collection.</span></span>  
  
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
  
## <a name="using-a-custom-servicehost-in-self-host"></a><span data-ttu-id="efcdc-130">Korzystanie z niestandardowego hosta usługi w hostach</span><span class="sxs-lookup"><span data-stu-id="efcdc-130">Using a custom ServiceHost in self-host</span></span>  
 <span data-ttu-id="efcdc-131">Teraz, gdy zakończyliśmy naszą niestandardową implementację ServiceHost, możemy użyć jej do dodania zachowania publikowania `SelfDescribingServiceHost`metadanych do dowolnej usługi, hostując tę usługę wewnątrz wystąpienia naszego .</span><span class="sxs-lookup"><span data-stu-id="efcdc-131">Now that we have completed our custom ServiceHost implementation, we can use it to add metadata publishing behavior to any service by hosting that service inside of an instance of our `SelfDescribingServiceHost`.</span></span> <span data-ttu-id="efcdc-132">Poniższy kod pokazuje, jak go używać w scenariuszu samodzielnego hosta.</span><span class="sxs-lookup"><span data-stu-id="efcdc-132">The following code shows how to use it in the self-host scenario.</span></span>  
  
```csharp
SelfDescribingServiceHost host =
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 <span data-ttu-id="efcdc-133">Nasz niestandardowy host nadal odczytuje konfigurację punktu końcowego usługi z pliku konfiguracyjnego aplikacji, tak jakby użyliśmy klasy domyślnej <xref:System.ServiceModel.ServiceHost> do hostowania usługi.</span><span class="sxs-lookup"><span data-stu-id="efcdc-133">Our custom host still reads the service’s endpoint configuration from the application’s configuration file, just as if we had used the default <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="efcdc-134">Jednak ponieważ dodaliśmy logikę, aby włączyć publikowanie metadanych wewnątrz naszego hosta niestandardowego, nie musimy już jawnie włączać zachowania publikowania metadanych w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="efcdc-134">However, because we added the logic to enable metadata publishing inside of our custom host, we no longer must explicitly enable the metadata publishing behavior in configuration.</span></span> <span data-ttu-id="efcdc-135">Takie podejście ma wyraźną zaletę podczas tworzenia aplikacji, która zawiera kilka usług i chcesz włączyć publikowanie metadanych na każdym z nich bez pisania tych samych elementów konfiguracji w kółko.</span><span class="sxs-lookup"><span data-stu-id="efcdc-135">This approach has a distinct advantage when you are building an application that contains several services and you want to enable metadata publishing on each of them without writing the same configuration elements over and over.</span></span>  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a><span data-ttu-id="efcdc-136">Korzystanie z niestandardowego hosta usługi w usługach IIS lub WAS</span><span class="sxs-lookup"><span data-stu-id="efcdc-136">Using a custom ServiceHost in IIS or WAS</span></span>  
 <span data-ttu-id="efcdc-137">Korzystanie z niestandardowego hosta usługi w scenariuszach hosta własnego jest proste, ponieważ jest to kod aplikacji, który jest ostatecznie odpowiedzialny za tworzenie i otwieranie wystąpienia hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="efcdc-137">Using a custom service host in self-host scenarios is straightforward, because it is your application code that is ultimately responsible for creating and opening the service host instance.</span></span> <span data-ttu-id="efcdc-138">Jednak w środowisku hostingowym usług IIS lub WAS infrastruktura WCF dynamicznie występuje z tworzeniem wystąpienia hosta usługi w odpowiedzi na przychodzące wiadomości.</span><span class="sxs-lookup"><span data-stu-id="efcdc-138">In the IIS or WAS hosting environment, however, the WCF infrastructure is dynamically instantiating your service’s host in response to incoming messages.</span></span> <span data-ttu-id="efcdc-139">Hosty usługi niestandardowej mogą być również używane w tym środowisku hostingowym, ale wymagają dodatkowego kodu w postaci ServiceHostFactory.</span><span class="sxs-lookup"><span data-stu-id="efcdc-139">Custom service hosts can also be used in this hosting environment, but they require some additional code in the form of a ServiceHostFactory.</span></span> <span data-ttu-id="efcdc-140">Poniższy kod przedstawia <xref:System.ServiceModel.Activation.ServiceHostFactory> pochodną tego zwraca `SelfDescribingServiceHost`wystąpienia naszych niestandardowych .</span><span class="sxs-lookup"><span data-stu-id="efcdc-140">The following code shows a derivative of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns instances of our custom `SelfDescribingServiceHost`.</span></span>  
  
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
  
 <span data-ttu-id="efcdc-141">Jak widać, implementowanie niestandardowego ServiceHostFactory jest bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="efcdc-141">As you can see, implementing a custom ServiceHostFactory is very straightforward.</span></span> <span data-ttu-id="efcdc-142">Wszystkie niestandardowe logiki znajduje się wewnątrz ServiceHost implementacji; fabryka zwraca wystąpienie klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="efcdc-142">All of the custom logic resides inside of the ServiceHost implementation; the factory returns an instance of the derived class.</span></span>  
  
 <span data-ttu-id="efcdc-143">Aby użyć niestandardowej fabryki z implementacją usługi, musimy dodać dodatkowe metadane do pliku .svc usługi.</span><span class="sxs-lookup"><span data-stu-id="efcdc-143">To use a custom factory with a service implementation, we must add some additional metadata to the service’s .svc file.</span></span>  
  
```xml
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"
               language=c# Debug="true" %>
```
  
 <span data-ttu-id="efcdc-144">W tym miejscu `Factory` dodaliśmy dodatkowy `@ServiceHost` atrybut do dyrektywy i przekazali nazwę typu CLR naszej fabryki niestandardowej jako wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="efcdc-144">Here we have added an additional `Factory` attribute to the `@ServiceHost` directive, and passed the CLR type name of our custom factory as the attribute’s value.</span></span> <span data-ttu-id="efcdc-145">Gdy usługi IIS lub WAS odbiera komunikat dla tej usługi, WCF hosting infrastruktury najpierw tworzy wystąpienie ServiceHostFactory, a następnie utworzyć wystąpienie samego hosta usługi przez wywołanie `ServiceHostFactory.CreateServiceHost()`.</span><span class="sxs-lookup"><span data-stu-id="efcdc-145">When IIS or WAS receives a message for this service, the WCF hosting infrastructure first creates an instance of the ServiceHostFactory and then instantiate the service host itself by calling `ServiceHostFactory.CreateServiceHost()`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="efcdc-146">Uruchamianie przykładowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="efcdc-146">Running the sample</span></span>  
 <span data-ttu-id="efcdc-147">Mimo że ten przykład zapewnia w pełni funkcjonalną implementację klienta i usługi, punktem próbki jest zilustrowanie sposobu zmiany zachowania w czasie wykonywania usługi za pomocą hosta niestandardowego., wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="efcdc-147">Although this sample does provide a fully-functional client and service implementation, the point of the sample is to illustrate how to alter a service’s run-time behavior by means of a custom host., do the following steps:</span></span>  
  
### <a name="observe-the-effect-of-the-custom-host"></a><span data-ttu-id="efcdc-148">Obserwuj efekt hosta niestandardowego</span><span class="sxs-lookup"><span data-stu-id="efcdc-148">Observe the effect of the custom host</span></span>
  
1. <span data-ttu-id="efcdc-149">Otwórz plik Web.config usługi i należy zauważyć, że nie ma konfiguracji jawnie włączającej metadane usługi.</span><span class="sxs-lookup"><span data-stu-id="efcdc-149">Open the service's Web.config file and observe that there is no configuration explicitly enabling metadata for the service.</span></span>  
  
2. <span data-ttu-id="efcdc-150">Otwórz plik .svc usługi i obserwować, że jego @ServiceHost dyrektywa zawiera Factory atrybut, który określa nazwę niestandardowego ServiceHostFactory.</span><span class="sxs-lookup"><span data-stu-id="efcdc-150">Open the service's .svc file and observe that its @ServiceHost directive contains a Factory attribute that specifies the name of a custom ServiceHostFactory.</span></span>  
  
### <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="efcdc-151">Konfigurowanie, tworzenie i uruchamianie próbki</span><span class="sxs-lookup"><span data-stu-id="efcdc-151">Set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="efcdc-152">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="efcdc-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="efcdc-153">Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="efcdc-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="efcdc-154">Po utworzeniu rozwiązania uruchom plik Setup.bat, aby skonfigurować aplikację ServiceModelSamples w usługach IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="efcdc-154">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="efcdc-155">Katalog ServiceModelSamples powinien teraz być wyświetlany jako aplikacja usług IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="efcdc-155">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="efcdc-156">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="efcdc-156">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

5. <span data-ttu-id="efcdc-157">Aby usunąć aplikację IIS 7.0, uruchom *plik Cleanup.bat*.</span><span class="sxs-lookup"><span data-stu-id="efcdc-157">To remove the IIS 7.0 application, run *Cleanup.bat*.</span></span>

## <a name="see-also"></a><span data-ttu-id="efcdc-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="efcdc-158">See also</span></span>

- [<span data-ttu-id="efcdc-159">Instrukcje: hostowanie usługi WCF w programie IIS</span><span class="sxs-lookup"><span data-stu-id="efcdc-159">How to: Host a WCF Service in IIS</span></span>](../feature-details/how-to-host-a-wcf-service-in-iis.md)
