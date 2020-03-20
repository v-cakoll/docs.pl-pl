---
title: Konfigurowanie usług WCF w kodzie
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 4ff49b4e17ae179426cc033a955ecf2c71f2a3e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174813"
---
# <a name="configuring-wcf-services-in-code"></a><span data-ttu-id="c0844-102">Konfigurowanie usług WCF w kodzie</span><span class="sxs-lookup"><span data-stu-id="c0844-102">Configuring WCF Services in Code</span></span>
<span data-ttu-id="c0844-103">Windows Communication Foundation (WCF) umożliwia deweloperom konfigurowanie usług przy użyciu plików konfiguracyjnych lub kodu.</span><span class="sxs-lookup"><span data-stu-id="c0844-103">Windows Communication Foundation (WCF) allows developers to configure services using configuration files or code.</span></span>  <span data-ttu-id="c0844-104">Pliki konfiguracyjne są przydatne, gdy usługa musi być skonfigurowana po wdrożeniu.</span><span class="sxs-lookup"><span data-stu-id="c0844-104">Configuration files are useful when a service needs to be configured after being deployed.</span></span> <span data-ttu-id="c0844-105">Podczas korzystania z plików konfiguracyjnych specjalista IT musi tylko zaktualizować plik konfiguracyjny, nie jest wymagana ponowna kompilacja.</span><span class="sxs-lookup"><span data-stu-id="c0844-105">When using configuration files, an IT professional only needs to update the configuration file, no recompilation is required.</span></span> <span data-ttu-id="c0844-106">Pliki konfiguracyjne mogą być jednak złożone i trudne do utrzymania.</span><span class="sxs-lookup"><span data-stu-id="c0844-106">Configuration files, however, can be complex and difficult to maintain.</span></span> <span data-ttu-id="c0844-107">Nie ma obsługi debugowania plików konfiguracyjnych i elementy konfiguracji są odwoływane przez nazwy, które sprawia, że tworzenie plików konfiguracyjnych podatne na błędy i trudne.</span><span class="sxs-lookup"><span data-stu-id="c0844-107">There is no support for debugging configuration files and configuration elements are referenced by names which makes authoring configuration files error-prone and difficult.</span></span> <span data-ttu-id="c0844-108">WCF umożliwia również konfigurowanie usług w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c0844-108">WCF also allows you to configure services in code.</span></span> <span data-ttu-id="c0844-109">We wcześniejszych wersjach WCF (4.0 i wcześniejszych) konfigurowanie usług w kodzie <xref:System.ServiceModel.ServiceHost> było łatwe w scenariuszach hostowanych samodzielnie, klasa umożliwia skonfigurowanie punktów końcowych i zachowań przed wywołaniem ServiceHost.Open.</span><span class="sxs-lookup"><span data-stu-id="c0844-109">In earlier versions of WCF (4.0 and earlier) configuring services in code was easy in self-hosted scenarios, the <xref:System.ServiceModel.ServiceHost> class allowed you to configure endpoints and behaviors prior to calling ServiceHost.Open.</span></span> <span data-ttu-id="c0844-110">W scenariuszach hostowanych w sieci Web nie masz <xref:System.ServiceModel.ServiceHost> jednak bezpośredniego dostępu do klasy.</span><span class="sxs-lookup"><span data-stu-id="c0844-110">In web hosted scenarios, however, you don’t have direct access to the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="c0844-111">Aby skonfigurować usługę hosta sieci Web, `System.ServiceModel.ServiceHostFactory` konieczne było <xref:System.ServiceModel.Activation.ServiceHostFactory> utworzenie utworzonej i wykonanej dowolnej potrzebnej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c0844-111">To configure a web hosted service you were required to create a `System.ServiceModel.ServiceHostFactory` that created the <xref:System.ServiceModel.Activation.ServiceHostFactory> and performed any needed configuration.</span></span> <span data-ttu-id="c0844-112">Począwszy od platformy .NET 4.5, WCF zapewnia łatwiejszy sposób konfigurowania zarówno hostowanych samodzielnie, jak i hostowanych usług internetowych w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c0844-112">Starting with .NET 4.5, WCF provides an easier way to configure both self-hosted and web hosted services in code.</span></span>  
  
## <a name="the-configure-method"></a><span data-ttu-id="c0844-113">Metoda Konfiguruj</span><span class="sxs-lookup"><span data-stu-id="c0844-113">The Configure method</span></span>  
 <span data-ttu-id="c0844-114">Wystarczy zdefiniować publiczną `Configure` metodę statyczną wywołaną z następującym podpisem w klasie implementacji usługi:</span><span class="sxs-lookup"><span data-stu-id="c0844-114">Simply define a public static method called `Configure` with the following signature in your service implementation class:</span></span>  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 <span data-ttu-id="c0844-115">Configure Metoda przyjmuje <xref:System.ServiceModel.ServiceConfiguration> wystąpienie, które umożliwia deweloperowi dodawać punkty końcowe i zachowania.</span><span class="sxs-lookup"><span data-stu-id="c0844-115">The Configure method takes a <xref:System.ServiceModel.ServiceConfiguration> instance that enables the developer to add endpoints and behaviors.</span></span> <span data-ttu-id="c0844-116">Ta metoda jest wywoływana przez WCF przed otwarciem hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="c0844-116">This method is called by WCF before the service host is opened.</span></span> <span data-ttu-id="c0844-117">Po zdefiniowaniu wszystkie ustawienia konfiguracji usługi określone w pliku app.config lub web.config zostaną zignorowane.</span><span class="sxs-lookup"><span data-stu-id="c0844-117">When defined, any service configuration settings specified in an app.config or web.config file will be ignored.</span></span>  
  
 <span data-ttu-id="c0844-118">Poniższy fragment kodu ilustruje sposób `Configure` definiowania metody i dodawania punktu końcowego usługi, zachowania punktu końcowego i zachowań usługi:</span><span class="sxs-lookup"><span data-stu-id="c0844-118">The following code snippet illustrates how to define the `Configure` method and add a service endpoint, an endpoint behavior and service behaviors:</span></span>  
  
```csharp  
public class Service1 : IService1  
    {  
        public static void Configure(ServiceConfiguration config)  
        {  
            ServiceEndpoint se = new ServiceEndpoint(new ContractDescription("IService1"), new BasicHttpBinding(), new EndpointAddress("basic"));  
            se.Behaviors.Add(new MyEndpointBehavior());  
            config.AddServiceEndpoint(se);  
  
            config.Description.Behaviors.Add(new ServiceMetadataBehavior { HttpGetEnabled = true });  
            config.Description.Behaviors.Add(new ServiceDebugBehavior { IncludeExceptionDetailInFaults = true });  
        }  
  
        public string GetData(int value)  
        {  
            return $"You entered: {value}";
        }  
  
        public CompositeType GetDataUsingDataContract(CompositeType composite)  
        {  
            if (composite == null)  
            {  
                throw new ArgumentNullException("composite");  
            }  
            if (composite.BoolValue)  
            {  
                composite.StringValue += "Suffix";  
            }  
            return composite;  
        }  
    }  
```  
  
 <span data-ttu-id="c0844-119">Aby włączyć protokół, taki jak https dla usługi, można jawnie dodać punkt końcowy, który używa protokołu, lub automatycznie dodać punkty końcowe, wywołując ServiceConfiguration.EnableProtocol(Binding), który dodaje punkt końcowy dla każdego adresu podstawowego zgodne z protokołem i każdą zdefiniowaną umową serwisową.</span><span class="sxs-lookup"><span data-stu-id="c0844-119">To enable a protocol such as https for a service, you can either explicitly add an endpoint that uses the protocol or you can automatically add endpoints by calling ServiceConfiguration.EnableProtocol(Binding) which adds an endpoint for each base address compatible with the protocol and each service contract defined.</span></span> <span data-ttu-id="c0844-120">Poniższy kod ilustruje sposób korzystania z ServiceConfiguration.EnableProtocol metody:</span><span class="sxs-lookup"><span data-stu-id="c0844-120">The following code illustrates how to use the ServiceConfiguration.EnableProtocol method:</span></span>  
  
```csharp  
public class Service1 : IService1
{
    public string GetData(int value);
    public static void Configure(ServiceConfiguration config)
    {
        // Enable "Add Service Reference" support
       config.Description.Behaviors.Add( new ServiceMetadataBehavior { HttpGetEnabled = true });
       // set up support for http, https, net.tcp, net.pipe
       config.EnableProtocol(new BasicHttpBinding());
       config.EnableProtocol(new BasicHttpsBinding());
       config.EnableProtocol(new NetTcpBinding());
       config.EnableProtocol(new NetNamedPipeBinding());
       // add an extra BasicHttpBinding endpoint at http:///basic
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");
    }
}
```  
  
 <span data-ttu-id="c0844-121">Ustawienia w sekcji <`protocolMappings`> są używane tylko wtedy, gdy żadne punkty końcowe aplikacji nie są dodawane do <xref:System.ServiceModel.ServiceConfiguration> programowo. Opcjonalnie można załadować konfigurację usługi z domyślnego pliku konfiguracji aplikacji, wywołując, <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> a następnie zmienić ustawienia.</span><span class="sxs-lookup"><span data-stu-id="c0844-121">The settings in the <`protocolMappings`> section are only used if no application endpoints are added to the <xref:System.ServiceModel.ServiceConfiguration> programmatically.You can optionally load the service configuration from the default application configuration file by calling <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> and then change the settings.</span></span> <span data-ttu-id="c0844-122">Klasa <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> umożliwia również ładowanie konfiguracji ze scentralizowanej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c0844-122">The <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> class also allows you to load configuration from a centralized configuration.</span></span> <span data-ttu-id="c0844-123">Poniższy kod ilustruje sposób zaimplementowania tego:</span><span class="sxs-lookup"><span data-stu-id="c0844-123">The following code illustrates how to implement this:</span></span>  
  
```csharp
public class Service1 : IService1
{
    public void DoWork();
    public static void Configure(ServiceConfiguration config)
    {
          config.LoadFromConfiguration(ConfigurationManager.OpenMappedExeConfiguration(new ExeConfigurationFileMap { ExeConfigFilename = @"c:\sharedConfig\MyConfig.config" }, ConfigurationUserLevel.None));
    }
}  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="c0844-124">Pamiętaj, <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> że w <`host`>> tagu `system.serviceModel` <`service`> ignor <uje ustawienia>.</span><span class="sxs-lookup"><span data-stu-id="c0844-124">Note that <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignores <`host`> settings within the <`service`> tag of <`system.serviceModel`>.</span></span> <span data-ttu-id="c0844-125">Koncepcyjnie <`host`> dotyczy konfiguracji hosta, a nie konfiguracji usługi i jest ładowana przed wykonaniem metody Configure.</span><span class="sxs-lookup"><span data-stu-id="c0844-125">Conceptually, <`host`> is about host configuration, not service configuration, and it gets loaded before the Configure method executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0844-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0844-126">See also</span></span>

- [<span data-ttu-id="c0844-127">Konfigurowanie usług za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c0844-127">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)
- [<span data-ttu-id="c0844-128">Konfigurowanie zachowań klienta</span><span class="sxs-lookup"><span data-stu-id="c0844-128">Configuring Client Behaviors</span></span>](configuring-client-behaviors.md)
- [<span data-ttu-id="c0844-129">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="c0844-129">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="c0844-130">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="c0844-130">Configuration</span></span>](./samples/configuration-sample.md)
- [<span data-ttu-id="c0844-131">Aktywacja oparta na konfiguracji w usługach IIS i WAS</span><span class="sxs-lookup"><span data-stu-id="c0844-131">Configuration-Based Activation in IIS and WAS</span></span>](./feature-details/configuration-based-activation-in-iis-and-was.md)
- [<span data-ttu-id="c0844-132">Konfiguracja i obsługa metadanych</span><span class="sxs-lookup"><span data-stu-id="c0844-132">Configuration and Metadata Support</span></span>](./extending/configuration-and-metadata-support.md)
- [<span data-ttu-id="c0844-133">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="c0844-133">Configuration</span></span>](./diagnostics/exceptions-reference/configuration.md)
- [<span data-ttu-id="c0844-134">Instrukcje: określanie powiązania usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c0844-134">How to: Specify a Service Binding in Configuration</span></span>](how-to-specify-a-service-binding-in-configuration.md)
- [<span data-ttu-id="c0844-135">Instrukcje: tworzenie punktu końcowego usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c0844-135">How to: Create a Service Endpoint in Configuration</span></span>](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [<span data-ttu-id="c0844-136">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c0844-136">How to: Publish Metadata for a Service Using a Configuration File</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="c0844-137">Instrukcje: określanie powiązań klienta w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c0844-137">How to: Specify a Client Binding in Configuration</span></span>](how-to-specify-a-client-binding-in-configuration.md)
