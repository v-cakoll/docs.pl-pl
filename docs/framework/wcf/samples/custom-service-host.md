---
title: Niestandardowy host usługi
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: c02ceb114a5346ea2a851f711f1ab9b50373cb75
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="custom-service-host"></a><span data-ttu-id="d4e3f-102">Niestandardowy host usługi</span><span class="sxs-lookup"><span data-stu-id="d4e3f-102">Custom Service Host</span></span>
<span data-ttu-id="d4e3f-103">W tym przykładzie przedstawiono sposób użycia niestandardowego pochodną <xref:System.ServiceModel.ServiceHost> klasy do zmiany zachowania usługi w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-103">This sample demonstrates how to use a custom derivative of the <xref:System.ServiceModel.ServiceHost> class to alter the run-time behavior of a service.</span></span> <span data-ttu-id="d4e3f-104">Metoda ta umożliwia wielokrotnego użytku sposobem konfigurowania wielu usług w typowy sposób.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-104">This approach provides a reusable alternative to configuring a large number of services in a common way.</span></span> <span data-ttu-id="d4e3f-105">Próbka przedstawiono również sposób użycia <xref:System.ServiceModel.Activation.ServiceHostFactory> klasy do użycia niestandardowego elementu ServiceHost w środowisku macierzystym Internet Information Services (IIS) lub usługi aktywacji procesów systemu Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="d4e3f-105">The sample also demonstrates how to use the <xref:System.ServiceModel.Activation.ServiceHostFactory> class to use a custom ServiceHost in the Internet Information Services (IIS) or Windows Process Activation Service (WAS) hosting environment.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d4e3f-106">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d4e3f-107">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="d4e3f-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d4e3f-108">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d4e3f-109">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a><span data-ttu-id="d4e3f-110">Scenariusz — informacje</span><span class="sxs-lookup"><span data-stu-id="d4e3f-110">About the Scenario</span></span>  
 <span data-ttu-id="d4e3f-111">Aby zapobiec przypadkowe ujawnienie metadanych usługi potencjalnie poufnych, konfigurację domyślną dla usług Windows Communication Foundation (WCF) wyłącza Publikowanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-111">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="d4e3f-112">To zachowanie jest domyślnie bezpieczne, ale również zaimportować narzędzia (na przykład Svcutil.exe) oznacza, że metadane nie można użyć do generowania kodu klienta wymaganych do wywołania tej usługi, chyba że jawnie włączone jest zachowanie podczas publikowania metadanych usługi w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-112">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
 <span data-ttu-id="d4e3f-113">Włączanie publikowania metadanych dla dużej liczby usług obejmuje dodawanie te same elementy konfiguracji do każdej pojedynczej usługi, co powoduje duże ilości informacji o konfiguracji, który jest zasadniczo taki sam.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-113">Enabling metadata publishing for a large number of services involves adding the same configuration elements to each individual service, which results in a large amount of configuration information that is essentially the same.</span></span> <span data-ttu-id="d4e3f-114">Jako alternatywę do konfigurowania poszczególnych usług indywidualnie jest można napisać kod imperatywnych, który umożliwia raz publikowania metadanych i następnie ponowne użycie tego kodu na kilka różnych usług.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-114">As an alternative to configuring each service individually, it is possible to write the imperative code that enables metadata publishing once and then reuse that code across several different services.</span></span> <span data-ttu-id="d4e3f-115">Jest to osiągane przez utworzenie nowej klasy, która jest pochodną <xref:System.ServiceModel.ServiceHost> i zastępuje `ApplyConfiguration`— metoda (), aby dodać imperatively zachowanie publikowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-115">This is accomplished by creating a new class that derives from <xref:System.ServiceModel.ServiceHost> and overrides the `ApplyConfiguration`() method to imperatively add the metadata publishing behavior.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d4e3f-116">Dla jasności ten przykład przedstawia sposób tworzenia punkt końcowy publikowania metadanych niezabezpieczona.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-116">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="d4e3f-117">Takie punkty końcowe są potencjalnie dostępne dla anonimowych użytkowników nieuwierzytelnionych i należy uważać przed wdrożeniem takich punktów końcowych w celu zapewnienia publicznie ujawniająca metadanych usługi odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-117">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span>  
  
## <a name="implementing-a-custom-servicehost"></a><span data-ttu-id="d4e3f-118">Implementowanie niestandardowego elementu ServiceHost</span><span class="sxs-lookup"><span data-stu-id="d4e3f-118">Implementing a Custom ServiceHost</span></span>  
 <span data-ttu-id="d4e3f-119"><xref:System.ServiceModel.ServiceHost> Klasy udostępnia kilka metod wirtualnych przydatne dziedziczenia można zastąpić do zmiany zachowania czasu wykonywania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-119">The <xref:System.ServiceModel.ServiceHost> class exposes several useful virtual methods that inheritors can override to alter the run-time behavior of a service.</span></span> <span data-ttu-id="d4e3f-120">Na przykład `ApplyConfiguration`() metoda odczytuje informacje konfiguracyjne usługi z magazynu konfiguracji i zmienia hosta <xref:System.ServiceModel.Description.ServiceDescription> odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-120">For example, the `ApplyConfiguration`() method reads service configuration information from the configuration store and alters the host's <xref:System.ServiceModel.Description.ServiceDescription> accordingly.</span></span> <span data-ttu-id="d4e3f-121">Domyślna implementacja odczytuje konfiguracji z pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-121">The default implementation reads configuration from the application’s configuration file.</span></span> <span data-ttu-id="d4e3f-122">Można zastąpić implementacji niestandardowych `ApplyConfiguration`() do dalszej alter <xref:System.ServiceModel.Description.ServiceDescription> przy użyciu kodu imperatywnych lub nawet całkowicie zastąpić magazynu konfiguracji domyślnej.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-122">Custom implementations can override `ApplyConfiguration`() to further alter the <xref:System.ServiceModel.Description.ServiceDescription> using imperative code or even replace the default configuration store entirely.</span></span> <span data-ttu-id="d4e3f-123">Na przykład, aby odczytać konfiguracji punktu końcowego usługi z bazy danych zamiast pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-123">For example, to read a service’s endpoint configuration from a database instead of the application’s configuration file.</span></span>  
  
 <span data-ttu-id="d4e3f-124">W tym przykładzie chcemy utworzyć niestandardowe ServiceHost, który dodaje ServiceMetadataBehavior, (który umożliwia publikowanie metadanych), nawet jeśli jest to zachowanie nie jest jawnie dodać w pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-124">In this sample, we want to build a custom ServiceHost that adds the ServiceMetadataBehavior, (which enables metadata publishing), even if this behavior is not explicitly added in the service’s configuration file.</span></span> <span data-ttu-id="d4e3f-125">Aby to zrobić, utworzymy nową klasę, która dziedziczy <xref:System.ServiceModel.ServiceHost> i zastępuje `ApplyConfiguration`().</span><span class="sxs-lookup"><span data-stu-id="d4e3f-125">To accomplish this, we create a new class that inherits from <xref:System.ServiceModel.ServiceHost> and overrides `ApplyConfiguration`().</span></span>  
  
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
  
 <span data-ttu-id="d4e3f-126">Ponieważ nie chcemy Ignoruj żadnej konfiguracji, które podano w pliku konfiguracji aplikacji, najpierw naszych zastępowania `ApplyConfiguration`() jest to wywołanie implementacji podstawowej.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-126">Because we do not want to ignore any configuration that has been provided in the application’s configuration file, the first thing our override of `ApplyConfiguration`() does is call the base implementation.</span></span> <span data-ttu-id="d4e3f-127">Po zakończeniu tej metody, można dodać imperatively <xref:System.ServiceModel.Description.ServiceMetadataBehavior> w opisie przy użyciu następującego kodu nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-127">Once this method completes, we can imperatively add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> to the description using the following imperative code.</span></span>  
  
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
  
 <span data-ttu-id="d4e3f-128">Ostatnim etapem naszych `ApplyConfiguration`wykonaj zastąpienia () jest dodawany domyślny punkt końcowy metadanych.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-128">The last thing our `ApplyConfiguration`() override must do is add the default metadata endpoint.</span></span> <span data-ttu-id="d4e3f-129">Konwencja jeden punkt końcowy metadanych jest tworzony dla każdego identyfikatora URI w kolekcji BaseAddresses hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-129">By convention, one metadata endpoint is created for each URI in the service host’s BaseAddresses collection.</span></span>  
  
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
  
## <a name="using-a-custom-servicehost-in-self-host"></a><span data-ttu-id="d4e3f-130">Używanie niestandardowych ServiceHost w host samodzielny</span><span class="sxs-lookup"><span data-stu-id="d4e3f-130">Using a custom ServiceHost in self-host</span></span>  
 <span data-ttu-id="d4e3f-131">Teraz, kiedy możemy zakończone naszych implementacja niestandardowa ServiceHost, wykorzystamy je dodać zachowanie podczas publikowania metadanych do dowolnej usługi, udostępniając usługi wewnątrz wystąpienia naszych `SelfDescribingServiceHost`.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-131">Now that we have completed our custom ServiceHost implementation, we can use it to add metadata publishing behavior to any service by hosting that service inside of an instance of our `SelfDescribingServiceHost`.</span></span> <span data-ttu-id="d4e3f-132">Poniższy kod przedstawia sposób użycia go w scenariuszu host samodzielny.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-132">The following code shows how to use it in the self-host scenario.</span></span>  
  
```  
SelfDescribingServiceHost host =   
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 <span data-ttu-id="d4e3f-133">Nasze hosta niestandardowego nadal odczytuje konfiguracji punktu końcowego usługi z pliku konfiguracji aplikacji, tak jakby było użyliśmy domyślne <xref:System.ServiceModel.ServiceHost> klasy do obsługi usługi.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-133">Our custom host still reads the service’s endpoint configuration from the application’s configuration file, just as if we had used the default <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="d4e3f-134">Jednak ponieważ dodaliśmy logiki można włączyć publikowania wewnątrz naszego hosta niestandardowego metadanych, firma Microsoft nie jest już jawnie włączyć zachowanie publikowania w konfiguracji metadanych.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-134">However, because we added the logic to enable metadata publishing inside of our custom host, we no longer must explicitly enable the metadata publishing behavior in configuration.</span></span> <span data-ttu-id="d4e3f-135">Takie podejście charakteryzuje się różne korzyści podczas tworzenia aplikacji, która zawiera kilka usług i chcesz włączyć publikowanie metadanych na każdym z nich, bez konieczności samodzielnego pisania te same elementy konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-135">This approach has a distinct advantage when you are building an application that contains several services and you want to enable metadata publishing on each of them without writing the same configuration elements over and over.</span></span>  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a><span data-ttu-id="d4e3f-136">Przy użyciu niestandardowych ServiceHost w usługach IIS lub WAS</span><span class="sxs-lookup"><span data-stu-id="d4e3f-136">Using a Custom ServiceHost in IIS or WAS</span></span>  
 <span data-ttu-id="d4e3f-137">W scenariuszach hosta samodzielnego przy użyciu hosta niestandardowego usługi jest proste, ponieważ jest kod aplikacji ostatecznie odpowiedzialną za tworzenie i otwieranie wystąpienie hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-137">Using a custom service host in self-host scenarios is straightforward, because it is your application code that is ultimately responsible for creating and opening the service host instance.</span></span> <span data-ttu-id="d4e3f-138">W usługach IIS lub WAS Środowisko hostingu jednak infrastruktura WCF jest dynamicznie tworzenia wystąpienia usługi hosta w odpowiedzi na wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-138">In the IIS or WAS hosting environment, however, the WCF infrastructure is dynamically instantiating your service’s host in response to incoming messages.</span></span> <span data-ttu-id="d4e3f-139">Hosty usługi niestandardowej można także w tym środowisku hostingu, ale wymagają dodatkowy kod w formularzu elementu ServiceHostFactory.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-139">Custom service hosts can also be used in this hosting environment, but they require some additional code in the form of a ServiceHostFactory.</span></span> <span data-ttu-id="d4e3f-140">Poniższy kod przedstawia pochodną <xref:System.ServiceModel.Activation.ServiceHostFactory> zwracająca wystąpienia klasy Nasze niestandardowe `SelfDescribingServiceHost`.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-140">The following code shows a derivative of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns instances of our custom `SelfDescribingServiceHost`.</span></span>  
  
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
  
 <span data-ttu-id="d4e3f-141">Jak widać, Implementowanie niestandardowego elementu ServiceHostFactory jest bardzo prosta.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-141">As you can see, implementing a custom ServiceHostFactory is very straightforward.</span></span> <span data-ttu-id="d4e3f-142">Wszystkie niestandardowej logiki znajduje się wewnątrz implementacji ServiceHost; Fabryka Zwraca wystąpienie klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-142">All of the custom logic resides inside of the ServiceHost implementation; the factory returns an instance of the derived class.</span></span>  
  
 <span data-ttu-id="d4e3f-143">Aby użyć niestandardowej fabryki z implementacją usługi, możemy dodać niektóre dodatkowe metadane w pliku svc usługi.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-143">To use a custom factory with a service implementation, we must add some additional metadata to the service’s .svc file.</span></span>  
  
```  
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"  
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"  
               language=c# Debug="true" %>  
```  
  
 <span data-ttu-id="d4e3f-144">W tym miejscu dodano dodatkowe `Factory` atrybutu `@ServiceHost` dyrektywy i przekazany CLR wpisz nazwę fabryki niestandardowych jako wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-144">Here we have added an additional `Factory` attribute to the `@ServiceHost` directive, and passed the CLR type name of our custom factory as the attribute’s value.</span></span> <span data-ttu-id="d4e3f-145">Gdy usługi IIS lub WAS odbiera komunikat dla tej usługi, infrastruktura WCF hostingu najpierw tworzy wystąpienie elementu ServiceHostFactory i następnie utworzyć przez wywołanie metody wystąpienia sam host usługi `ServiceHostFactory.CreateServiceHost()`.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-145">When IIS or WAS receives a message for this service, the WCF hosting infrastructure first creates an instance of the ServiceHostFactory and then instantiate the service host itself by calling `ServiceHostFactory.CreateServiceHost()`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="d4e3f-146">Uruchomiona próbki</span><span class="sxs-lookup"><span data-stu-id="d4e3f-146">Running the Sample</span></span>  
 <span data-ttu-id="d4e3f-147">Mimo że w tym przykładzie zapewnienia pełnej funkcjonalności klienta i wdrożenia usługi, punkt próbki jest pokazano, jak zmienić zachowanie środowiska wykonawczego usługi przy użyciu hosta niestandardowego., wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="d4e3f-147">Although this sample does provide a fully-functional client and service implementation, the point of the sample is to illustrate how to alter a service’s run-time behavior by means of a custom host., do the following steps:</span></span>  
  
#### <a name="to-observe-the-effect-of-the-custom-host"></a><span data-ttu-id="d4e3f-148">Aby sprawdzić efekt hosta niestandardowego</span><span class="sxs-lookup"><span data-stu-id="d4e3f-148">To observe the effect of the custom host</span></span>  
  
1.  <span data-ttu-id="d4e3f-149">Otwórz plik Web.config usługi i sprawdź, czy nie istnieje konfiguracja jawnie włączenie metadanych dla usługi.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-149">Open the service’s Web.config file and observe that there is no configuration explicitly enabling metadata for the service.</span></span>  
  
2.  <span data-ttu-id="d4e3f-150">Otwórz plik .svc usługi i że jego @ServiceHost dyrektywa zawiera atrybut Factory, który określa nazwę niestandardowego elementu ServiceHostFactory.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-150">Open the service’s .svc file and observe that its @ServiceHost directive contains a Factory attribute that specifies the name of a custom ServiceHostFactory.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d4e3f-151">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="d4e3f-151">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d4e3f-152">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d4e3f-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d4e3f-153">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d4e3f-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d4e3f-154">Po utworzeniu rozwiązania należy uruchomić pliku Setup.bat, aby skonfigurować aplikację ServiceModelSamples w [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d4e3f-154">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="d4e3f-155">Katalog ServiceModelSamples powinien zostać wyświetlony jako [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-155">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4.  <span data-ttu-id="d4e3f-156">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d4e3f-156">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="d4e3f-157">Aby usunąć [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikacji, uruchom Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="d4e3f-157">To remove the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] application, run Cleanup.bat.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4e3f-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4e3f-158">See Also</span></span>  
 [<span data-ttu-id="d4e3f-159">Instrukcje: hostowanie usługi WCF w programie IIS</span><span class="sxs-lookup"><span data-stu-id="d4e3f-159">How to: Host a WCF Service in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
