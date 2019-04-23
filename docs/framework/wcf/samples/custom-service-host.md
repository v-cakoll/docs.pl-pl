---
title: Niestandardowy host usługi
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: d2eebd502fa02d01ac86cf88f336b72829a6116f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340935"
---
# <a name="custom-service-host"></a><span data-ttu-id="52295-102">Niestandardowy host usługi</span><span class="sxs-lookup"><span data-stu-id="52295-102">Custom Service Host</span></span>
<span data-ttu-id="52295-103">W tym przykładzie przedstawiono sposób użycia niestandardowego utworów zależnych od <xref:System.ServiceModel.ServiceHost> klasy do zmiany zachowania usługi w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="52295-103">This sample demonstrates how to use a custom derivative of the <xref:System.ServiceModel.ServiceHost> class to alter the run-time behavior of a service.</span></span> <span data-ttu-id="52295-104">Metoda ta umożliwia wielokrotnego użytku alternatywa konfigurowanie dużej liczby usług w typowy sposób.</span><span class="sxs-lookup"><span data-stu-id="52295-104">This approach provides a reusable alternative to configuring a large number of services in a common way.</span></span> <span data-ttu-id="52295-105">W przykładzie pokazano również sposób użycia <xref:System.ServiceModel.Activation.ServiceHostFactory> klasy, aby użyć niestandardowego elementu ServiceHost w środowisku hostingu usług Internet Information Services (IIS) lub Windows Process Activation Service (WAS).</span><span class="sxs-lookup"><span data-stu-id="52295-105">The sample also demonstrates how to use the <xref:System.ServiceModel.Activation.ServiceHostFactory> class to use a custom ServiceHost in the Internet Information Services (IIS) or Windows Process Activation Service (WAS) hosting environment.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="52295-106">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="52295-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="52295-107">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="52295-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="52295-108">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="52295-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="52295-109">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="52295-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a><span data-ttu-id="52295-110">Scenariusz — informacje</span><span class="sxs-lookup"><span data-stu-id="52295-110">About the Scenario</span></span>  
 <span data-ttu-id="52295-111">Aby zapobiegać niezamierzonym ujawnieniem metadanych usługi potencjalnie poufnych, konfigurację domyślną dla usług Windows Communication Foundation (WCF) powoduje wyłączenie publikowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="52295-111">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="52295-112">To zachowanie jest domyślnie bezpieczny, ale również zaimportować narzędzia (takie jak Svcutil.exe) oznacza, że metadane nie można użyć do wygenerowania kodu klienta wymaganych do wywołania tej usługi, chyba że jawnie włączone jest zachowanie publikowania metadanych usługi w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="52295-112">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
 <span data-ttu-id="52295-113">Włączanie Publikowanie metadanych dla dużej liczby usług obejmuje dodanie tych samych elementów konfiguracji dla wszystkich poszczególnych usług, co skutkuje dużą ilość informacji o konfiguracji, który jest zasadniczo taki sam.</span><span class="sxs-lookup"><span data-stu-id="52295-113">Enabling metadata publishing for a large number of services involves adding the same configuration elements to each individual service, which results in a large amount of configuration information that is essentially the same.</span></span> <span data-ttu-id="52295-114">Alternatywnie na oddzielne Konfigurowanie każdej usługi jest możliwe do pisania kodu imperatywnego, który umożliwia publikowanie raz metadanych i następnie ponowne użycie tego kodu na kilka różnych usług.</span><span class="sxs-lookup"><span data-stu-id="52295-114">As an alternative to configuring each service individually, it is possible to write the imperative code that enables metadata publishing once and then reuse that code across several different services.</span></span> <span data-ttu-id="52295-115">Jest to osiągane przez utworzenie nowej klasy, która pochodzi od klasy <xref:System.ServiceModel.ServiceHost> i zastępuje `ApplyConfiguration`metodę (), aby dodać obowiązkowo zachowanie publikowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="52295-115">This is accomplished by creating a new class that derives from <xref:System.ServiceModel.ServiceHost> and overrides the `ApplyConfiguration`() method to imperatively add the metadata publishing behavior.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="52295-116">Dla jasności ten przykład przedstawia sposób tworzenia punkt końcowy publikowania metadanych niezabezpieczona.</span><span class="sxs-lookup"><span data-stu-id="52295-116">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="52295-117">Takie punkty końcowe są potencjalnie dostępne dla anonimowe, nieuwierzytelnione konsumentów i należy uważać, przed wdrożeniem tych punktów końcowych w celu zapewnienia publicznie ujawniająca metadanych usługi odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="52295-117">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span>  
  
## <a name="implementing-a-custom-servicehost"></a><span data-ttu-id="52295-118">Implementowanie niestandardowego elementu ServiceHost</span><span class="sxs-lookup"><span data-stu-id="52295-118">Implementing a Custom ServiceHost</span></span>  
 <span data-ttu-id="52295-119"><xref:System.ServiceModel.ServiceHost> Klasa udostępnia kilka metod wirtualnych przydatne przesłaniające przez obiektów dziedziczących do zmiany zachowania w czasie wykonywania usługi.</span><span class="sxs-lookup"><span data-stu-id="52295-119">The <xref:System.ServiceModel.ServiceHost> class exposes several useful virtual methods that inheritors can override to alter the run-time behavior of a service.</span></span> <span data-ttu-id="52295-120">Na przykład `ApplyConfiguration`— metoda () odczytuje informacje konfiguracyjne usługi z magazynu konfiguracji i zmienia hosta <xref:System.ServiceModel.Description.ServiceDescription> odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="52295-120">For example, the `ApplyConfiguration`() method reads service configuration information from the configuration store and alters the host's <xref:System.ServiceModel.Description.ServiceDescription> accordingly.</span></span> <span data-ttu-id="52295-121">Domyślna implementacja odczytuje konfiguracji z pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="52295-121">The default implementation reads configuration from the application’s configuration file.</span></span> <span data-ttu-id="52295-122">Niestandardowe implementacje można zastąpić `ApplyConfiguration`() do dalszej zmiany <xref:System.ServiceModel.Description.ServiceDescription> przy użyciu kodu imperatywnego lub nawet zastąpienia domyślnego magazynu konfiguracji w całości.</span><span class="sxs-lookup"><span data-stu-id="52295-122">Custom implementations can override `ApplyConfiguration`() to further alter the <xref:System.ServiceModel.Description.ServiceDescription> using imperative code or even replace the default configuration store entirely.</span></span> <span data-ttu-id="52295-123">Na przykład, można odczytać konfiguracji punktu końcowego usługi z bazy danych zamiast pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="52295-123">For example, to read a service’s endpoint configuration from a database instead of the application’s configuration file.</span></span>  
  
 <span data-ttu-id="52295-124">W tym przykładzie chcemy utworzyć niestandardowego elementu ServiceHost, który dodaje ServiceMetadataBehavior, (który umożliwia publikowanie metadanych), nawet jeśli to zachowanie nie została jawnie dodana w pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="52295-124">In this sample, we want to build a custom ServiceHost that adds the ServiceMetadataBehavior, (which enables metadata publishing), even if this behavior is not explicitly added in the service’s configuration file.</span></span> <span data-ttu-id="52295-125">Aby to osiągnąć, możemy utworzyć nowej klasy, która dziedziczy <xref:System.ServiceModel.ServiceHost> i zastępuje `ApplyConfiguration`().</span><span class="sxs-lookup"><span data-stu-id="52295-125">To accomplish this, we create a new class that inherits from <xref:System.ServiceModel.ServiceHost> and overrides `ApplyConfiguration`().</span></span>  
  
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
  
 <span data-ttu-id="52295-126">Ponieważ nie chcemy Ignoruj żadnej konfiguracji, który został dostarczony w pliku konfiguracji aplikacji, przede wszystkim naszym zastępowania metody `ApplyConfiguration`() jest to wywołanie implementację podstawową.</span><span class="sxs-lookup"><span data-stu-id="52295-126">Because we do not want to ignore any configuration that has been provided in the application’s configuration file, the first thing our override of `ApplyConfiguration`() does is call the base implementation.</span></span> <span data-ttu-id="52295-127">Po ukończeniu tej metody można obowiązkowo dodamy <xref:System.ServiceModel.Description.ServiceMetadataBehavior> opisu, używając następującego kodu imperatywnego.</span><span class="sxs-lookup"><span data-stu-id="52295-127">Once this method completes, we can imperatively add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> to the description using the following imperative code.</span></span>  
  
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
  
 <span data-ttu-id="52295-128">Ostatnią czynnością, jaką naszych `ApplyConfiguration`konieczne zastąpienie () jest dodać domyślny punkt końcowy metadanych.</span><span class="sxs-lookup"><span data-stu-id="52295-128">The last thing our `ApplyConfiguration`() override must do is add the default metadata endpoint.</span></span> <span data-ttu-id="52295-129">Zgodnie z Konwencją jeden punkt końcowy metadanych jest tworzony dla każdego identyfikatora URI w kolekcji BaseAddresses hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="52295-129">By convention, one metadata endpoint is created for each URI in the service host’s BaseAddresses collection.</span></span>  
  
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
  
## <a name="using-a-custom-servicehost-in-self-host"></a><span data-ttu-id="52295-130">Za pomocą niestandardowego elementu ServiceHost w samodzielnego hostowania</span><span class="sxs-lookup"><span data-stu-id="52295-130">Using a custom ServiceHost in self-host</span></span>  
 <span data-ttu-id="52295-131">Teraz, gdy ukończyliśmy naszej niestandardowych implementacji elementu ServiceHost wykorzystamy je dodać zachowanie publikowania metadanych do dowolnej usługi, udostępniając usługi wewnątrz wystąpienia naszej `SelfDescribingServiceHost`.</span><span class="sxs-lookup"><span data-stu-id="52295-131">Now that we have completed our custom ServiceHost implementation, we can use it to add metadata publishing behavior to any service by hosting that service inside of an instance of our `SelfDescribingServiceHost`.</span></span> <span data-ttu-id="52295-132">Poniższy kod przedstawia sposób używania go w tym scenariuszu samodzielnego hostowania.</span><span class="sxs-lookup"><span data-stu-id="52295-132">The following code shows how to use it in the self-host scenario.</span></span>  
  
```  
SelfDescribingServiceHost host =   
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 <span data-ttu-id="52295-133">Nasze niestandardowego hosta nadal odczytuje konfiguracji punktu końcowego usługi z pliku konfiguracji aplikacji, tak, jakby było użyte domyślne <xref:System.ServiceModel.ServiceHost> klasy do obsługi usługi.</span><span class="sxs-lookup"><span data-stu-id="52295-133">Our custom host still reads the service’s endpoint configuration from the application’s configuration file, just as if we had used the default <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="52295-134">Jednak ponieważ dodaliśmy logiki, aby włączyć publikowanie w naszym niestandardowego hosta metadanych, firma Microsoft nie jest już jawnie włączyć metadanych zachowanie publikowania w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="52295-134">However, because we added the logic to enable metadata publishing inside of our custom host, we no longer must explicitly enable the metadata publishing behavior in configuration.</span></span> <span data-ttu-id="52295-135">Takie podejście ma różne korzyści, gdy tworzysz aplikację, która zawiera kilka usług i chcesz włączyć publikowanie metadanych na każdym z nich, bez konieczności pisania te same elementy konfiguracji wielokrotnie.</span><span class="sxs-lookup"><span data-stu-id="52295-135">This approach has a distinct advantage when you are building an application that contains several services and you want to enable metadata publishing on each of them without writing the same configuration elements over and over.</span></span>  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a><span data-ttu-id="52295-136">Za pomocą niestandardowego elementu ServiceHost w usługach IIS i WAS</span><span class="sxs-lookup"><span data-stu-id="52295-136">Using a Custom ServiceHost in IIS or WAS</span></span>  
 <span data-ttu-id="52295-137">Niestandardowy host usługi w scenariuszach hosta samodzielnego jest prosta, ponieważ jest on kodzie aplikacji, która jest ponoszą ostateczną odpowiedzialność za tworzenie i otwieranie instancja hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="52295-137">Using a custom service host in self-host scenarios is straightforward, because it is your application code that is ultimately responsible for creating and opening the service host instance.</span></span> <span data-ttu-id="52295-138">W usługach IIS lub WAS Środowisko hostingu jednak infrastruktura WCF jest dynamicznie Tworzenie wystąpienia usługi hosta w odpowiedzi na wiadomości przychodzące.</span><span class="sxs-lookup"><span data-stu-id="52295-138">In the IIS or WAS hosting environment, however, the WCF infrastructure is dynamically instantiating your service’s host in response to incoming messages.</span></span> <span data-ttu-id="52295-139">Hosty niestandardowych usług można również w tym środowisku hostingu, ale wymagają one dodatkowy kod w postaci elementu ServiceHostFactory.</span><span class="sxs-lookup"><span data-stu-id="52295-139">Custom service hosts can also be used in this hosting environment, but they require some additional code in the form of a ServiceHostFactory.</span></span> <span data-ttu-id="52295-140">Poniższy kod przedstawia zależnych od <xref:System.ServiceModel.Activation.ServiceHostFactory> zwracająca wystąpienia klasy Nasze niestandardowe `SelfDescribingServiceHost`.</span><span class="sxs-lookup"><span data-stu-id="52295-140">The following code shows a derivative of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns instances of our custom `SelfDescribingServiceHost`.</span></span>  
  
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
  
 <span data-ttu-id="52295-141">Jak widać, Implementowanie niestandardowego elementu ServiceHostFactory jest bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="52295-141">As you can see, implementing a custom ServiceHostFactory is very straightforward.</span></span> <span data-ttu-id="52295-142">Wszystkie niestandardowej logiki znajduje się wewnątrz elementu ServiceHost wdrożenia; Fabryka Zwraca wystąpienie klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="52295-142">All of the custom logic resides inside of the ServiceHost implementation; the factory returns an instance of the derived class.</span></span>  
  
 <span data-ttu-id="52295-143">Niestandardowych ustawień fabrycznych za pomocą implementacji usługi, możemy dodać pewnymi dodatkowymi metadanymi plikowi .svc usługi.</span><span class="sxs-lookup"><span data-stu-id="52295-143">To use a custom factory with a service implementation, we must add some additional metadata to the service’s .svc file.</span></span>  
  
```  
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"  
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"  
               language=c# Debug="true" %>  
```  
  
 <span data-ttu-id="52295-144">W tym miejscu dodaliśmy dodatkowe `Factory` atrybutu `@ServiceHost` dyrektywy i przekazanych środowiska CLR, wpisz nazwę fabryki niestandardowe jako wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="52295-144">Here we have added an additional `Factory` attribute to the `@ServiceHost` directive, and passed the CLR type name of our custom factory as the attribute’s value.</span></span> <span data-ttu-id="52295-145">Gdy usługi IIS i WAS otrzymuje komunikat dotyczący tej usługi, infrastruktury hostingu WCF najpierw tworzy wystąpienie elementu ServiceHostFactory i, tworzy sam host usługi przez wywołanie metody `ServiceHostFactory.CreateServiceHost()`.</span><span class="sxs-lookup"><span data-stu-id="52295-145">When IIS or WAS receives a message for this service, the WCF hosting infrastructure first creates an instance of the ServiceHostFactory and then instantiate the service host itself by calling `ServiceHostFactory.CreateServiceHost()`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="52295-146">Działa aplikacja przykładowa</span><span class="sxs-lookup"><span data-stu-id="52295-146">Running the Sample</span></span>  
 <span data-ttu-id="52295-147">Chociaż w tym przykładzie zapewniają klienta w pełni funkcjonalne i implementacji usługi, poniższego przykładu jest pokazują, jak zmienić zachowanie usługi w czasie wykonywania za pomocą niestandardowego hosta., wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="52295-147">Although this sample does provide a fully-functional client and service implementation, the point of the sample is to illustrate how to alter a service’s run-time behavior by means of a custom host., do the following steps:</span></span>  
  
#### <a name="to-observe-the-effect-of-the-custom-host"></a><span data-ttu-id="52295-148">Aby obserwować wpływ niestandardowego hosta</span><span class="sxs-lookup"><span data-stu-id="52295-148">To observe the effect of the custom host</span></span>  
  
1. <span data-ttu-id="52295-149">Otwórz plik Web.config usługi i sprawdź, czy brak konfiguracji jawnie Włączanie metadanych dla usługi.</span><span class="sxs-lookup"><span data-stu-id="52295-149">Open the service’s Web.config file and observe that there is no configuration explicitly enabling metadata for the service.</span></span>  
  
2. <span data-ttu-id="52295-150">Otwórz plik .svc usługi i Zauważ, że jego @ServiceHost dyrektywa zawiera atrybut fabryki, który określa nazwę niestandardowego elementu ServiceHostFactory.</span><span class="sxs-lookup"><span data-stu-id="52295-150">Open the service’s .svc file and observe that its @ServiceHost directive contains a Factory attribute that specifies the name of a custom ServiceHostFactory.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="52295-151">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="52295-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="52295-152">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="52295-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="52295-153">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="52295-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="52295-154">Po rozwiązaniu został utworzony, uruchom Setup.bat jest, aby skonfigurować aplikację ServiceModelSamples w [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="52295-154">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="52295-155">Katalog ServiceModelSamples teraz powinny się wyświetlać jako [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="52295-155">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4. <span data-ttu-id="52295-156">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="52295-156">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="52295-157">Aby usunąć [!INCLUDE[iisver](../../../../includes/iisver-md.md)] aplikację, uruchom Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="52295-157">To remove the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] application, run Cleanup.bat.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52295-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52295-158">See also</span></span>

- [<span data-ttu-id="52295-159">Instrukcje: Hostowanie usługi WCF w programie IIS</span><span class="sxs-lookup"><span data-stu-id="52295-159">How to: Host a WCF Service in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
