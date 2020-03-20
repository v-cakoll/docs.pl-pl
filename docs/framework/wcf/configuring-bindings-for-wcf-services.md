---
title: Konfigurowanie wiązań dla usług WCF (Windows Communication Foundation)
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: e7ee1a8ce358c77e46db39af67bd9dc20114fb3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174826"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a><span data-ttu-id="179f3-102">Konfigurowanie wiązań dla usług WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="179f3-102">Configuring Bindings for Windows Communication Foundation Services</span></span>
<span data-ttu-id="179f3-103">Podczas tworzenia aplikacji często chcesz odroczyć decyzje do administratora po wdrożeniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="179f3-103">When creating an application, you often want to defer decisions to the administrator after the deployment of the application.</span></span> <span data-ttu-id="179f3-104">Na przykład często nie ma możliwości poznania z wyprzedzeniem, jaki będzie adres usługi lub jednolity identyfikator zasobu (URI).</span><span class="sxs-lookup"><span data-stu-id="179f3-104">For example, there is often no way of knowing in advance what a service address, or Uniform Resource Identifier (URI), will be.</span></span> <span data-ttu-id="179f3-105">Zamiast twardego kodowania adresu, zaleca się, aby zezwolić administratorowi to zrobić po utworzeniu usługi.</span><span class="sxs-lookup"><span data-stu-id="179f3-105">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="179f3-106">Ta elastyczność jest osiągana poprzez konfigurację.</span><span class="sxs-lookup"><span data-stu-id="179f3-106">This flexibility is accomplished through configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="179f3-107">Użyj [narzędzia Narzędzia do metadanych ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) z przełącznikiem, `/config` aby szybko utworzyć pliki konfiguracyjne.</span><span class="sxs-lookup"><span data-stu-id="179f3-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config` switch to quickly create configuration files.</span></span>  
  
## <a name="major-sections"></a><span data-ttu-id="179f3-108">Sekcje główne</span><span class="sxs-lookup"><span data-stu-id="179f3-108">Major Sections</span></span>  
 <span data-ttu-id="179f3-109">Schemat konfiguracji Windows Communication Foundation (WCF) obejmuje następujące`serviceModel` `bindings`trzy `services`główne sekcje ( , , , i):</span><span class="sxs-lookup"><span data-stu-id="179f3-109">The Windows Communication Foundation (WCF) configuration scheme includes the following three major sections (`serviceModel`, `bindings`, and `services`):</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <bindings>  
        </bindings>  
        <services>  
        </services>  
        <behaviors>  
        </behaviors>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="servicemodel-elements"></a><span data-ttu-id="179f3-110">Elementy ServiceModel</span><span class="sxs-lookup"><span data-stu-id="179f3-110">ServiceModel Elements</span></span>  
 <span data-ttu-id="179f3-111">Można użyć sekcji ograniczonej `system.ServiceModel` przez element, aby skonfigurować typ usługi z co najmniej jednym punktem końcowym, a także ustawienia dla usługi.</span><span class="sxs-lookup"><span data-stu-id="179f3-111">You can use the section bounded by the `system.ServiceModel` element to configure a service type with one or more endpoints, as well as settings for a service.</span></span> <span data-ttu-id="179f3-112">Każdy punkt końcowy można następnie skonfigurować z adresem, umową i powiązaniem.</span><span class="sxs-lookup"><span data-stu-id="179f3-112">Each endpoint can then be configured with an address, a contract, and a binding.</span></span> <span data-ttu-id="179f3-113">Aby uzyskać więcej informacji na temat punktów końcowych, zobacz [Omówienie tworzenia punktów końcowych](endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="179f3-113">For more information about endpoints, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="179f3-114">Jeśli nie określono żadnych punktów końcowych, środowisko wykonawcze dodaje domyślne punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="179f3-114">If no endpoints are specified, the runtime adds default endpoints.</span></span> <span data-ttu-id="179f3-115">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](simplified-configuration.md) i [uproszczona konfiguracja usług WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="179f3-115">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="179f3-116">Powiązanie określa transporty (HTTP, TCP, potoki, Usługi kolejkowania wiadomości) i protokoły (Zabezpieczenia, Niezawodność, Przepływy transakcji) i składa się z elementów wiązania, z których każdy określa aspekt komunikacji punktu końcowego ze światem.</span><span class="sxs-lookup"><span data-stu-id="179f3-116">A binding specifies transports (HTTP, TCP, pipes, Message Queuing) and protocols (Security, Reliability, Transaction flows) and consists of binding elements, each of which specifies an aspect of how an endpoint communicates with the world.</span></span>  
  
 <span data-ttu-id="179f3-117">Na przykład określenie [ \<podstawowego elementu>httpbinding](../configure-apps/file-schema/wcf/basichttpbinding.md) wskazuje, aby używać protokołu HTTP jako transportu dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="179f3-117">For example, specifying the [\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) element indicates to use HTTP as the transport for an endpoint.</span></span> <span data-ttu-id="179f3-118">Służy do przewodów punktu końcowego w czasie wykonywania, gdy usługa przy użyciu tego punktu końcowego jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="179f3-118">This is used to wire up the endpoint at run time when the service using this endpoint is opened.</span></span>  
  
 <span data-ttu-id="179f3-119">Istnieją dwa rodzaje powiązań: wstępnie zdefiniowane i niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="179f3-119">There are two kinds of bindings: predefined and custom.</span></span> <span data-ttu-id="179f3-120">Wstępnie zdefiniowane powiązania zawierają przydatne kombinacje elementów, które są używane w typowych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="179f3-120">Predefined bindings contain useful combinations of elements that are used in common scenarios.</span></span> <span data-ttu-id="179f3-121">Aby uzyskać listę wstępnie zdefiniowanych typów powiązań, które zapewnia WCF, zobacz [Powiązania dostarczone przez system](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="179f3-121">For a list of predefined binding types that WCF provides, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="179f3-122">Jeśli żadna wstępnie zdefiniowana kolekcja powiązań ma poprawną kombinację funkcji, których potrzebuje aplikacja usługi, można utworzyć niestandardowe powiązania, aby spełnić wymagania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="179f3-122">If no predefined binding collection has the correct combination of features that a service application needs, you can construct custom bindings to meet the application's requirements.</span></span> <span data-ttu-id="179f3-123">Aby uzyskać więcej informacji na temat powiązań niestandardowych, zobacz [ \<customBinding>](../configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="179f3-123">For more information about custom bindings, see [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
 <span data-ttu-id="179f3-124">Poniższe cztery przykłady ilustrują najbardziej typowe konfiguracje powiązania używane do konfigurowania usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="179f3-124">The following four examples illustrate the most common binding configurations used for setting up a WCF service.</span></span>  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a><span data-ttu-id="179f3-125">Określanie punktu końcowego do użycia typu powiązania</span><span class="sxs-lookup"><span data-stu-id="179f3-125">Specifying an Endpoint to Use a Binding Type</span></span>  
 <span data-ttu-id="179f3-126">Pierwszy przykład ilustruje sposób określania punktu końcowego skonfigurowanego z adresem, umową i powiązaniem.</span><span class="sxs-lookup"><span data-stu-id="179f3-126">The first example illustrates how to specify an endpoint configured with an address, a contract, and a binding.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!-- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
```  
  
 <span data-ttu-id="179f3-127">W tym przykładzie `name` atrybut wskazuje, jaki typ usługi jest dla konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="179f3-127">In this example, the `name` attribute indicates which service type the configuration is for.</span></span> <span data-ttu-id="179f3-128">Podczas tworzenia usługi w kodzie `HelloWorld` z umową, jest inicjowany ze wszystkimi punktami końcowymi zdefiniowanymi w przykładowej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="179f3-128">When you create a service in your code with the `HelloWorld` contract, it is initialized with all of the endpoints defined in the example configuration.</span></span> <span data-ttu-id="179f3-129">Jeśli zestaw implementuje tylko jeden `name` kontrakt serwisowy, atrybut można pominąć, ponieważ usługa używa tylko dostępny typ.</span><span class="sxs-lookup"><span data-stu-id="179f3-129">If the assembly implements only one service contract, the `name` attribute can be omitted because the service uses the only available type.</span></span> <span data-ttu-id="179f3-130">Atrybut przyjmuje ciąg, który musi być w formacie`Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span><span class="sxs-lookup"><span data-stu-id="179f3-130">The attribute takes a string, which must be in the format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>  
  
 <span data-ttu-id="179f3-131">Atrybut `address` określa identyfikator URI, który inne punkty końcowe używają do komunikowania się z usługą.</span><span class="sxs-lookup"><span data-stu-id="179f3-131">The `address` attribute specifies the URI that other endpoints use to communicate to the service.</span></span> <span data-ttu-id="179f3-132">Identyfikator URI może być ścieżką bezwzględną lub względną.</span><span class="sxs-lookup"><span data-stu-id="179f3-132">The URI can be either an absolute or relative path.</span></span> <span data-ttu-id="179f3-133">Jeśli podany jest adres względny, oczekuje się, że host poda adres podstawowy, który jest odpowiedni dla schematu transportu używanego w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="179f3-133">If a relative address is provided, the host is expected to provide a base address that is appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="179f3-134">Jeśli adres nie jest skonfigurowany, przyjmuje się, że adres podstawowy jest adresem dla tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="179f3-134">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span>  
  
 <span data-ttu-id="179f3-135">Atrybut `contract` określa kontrakt, który ujawnia ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="179f3-135">The `contract` attribute specifies the contract this endpoint is exposing.</span></span> <span data-ttu-id="179f3-136">Typ implementacji usługi musi implementować typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="179f3-136">The service implementation type must implement the contract type.</span></span> <span data-ttu-id="179f3-137">Jeśli implementacja usługi implementuje jeden typ kontraktu, można pominąć tę właściwość.</span><span class="sxs-lookup"><span data-stu-id="179f3-137">If a service implementation implements a single contract type, then this property can be omitted.</span></span>  
  
 <span data-ttu-id="179f3-138">Atrybut `binding` wybiera wstępnie zdefiniowane lub niestandardowe powiązanie do użycia dla tego określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="179f3-138">The `binding` attribute selects a predefined or custom binding to use for this specific endpoint.</span></span> <span data-ttu-id="179f3-139">Punkt końcowy, który jawnie nie wybiera powiązania, używa domyślnego zaznaczenia powiązania, którym jest `BasicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="179f3-139">An endpoint that does not explicitly select a binding uses the default binding selection, which is `BasicHttpBinding`.</span></span>  
  
#### <a name="modifying-a-predefined-binding"></a><span data-ttu-id="179f3-140">Modyfikowanie wstępnie zdefiniowanego powiązania</span><span class="sxs-lookup"><span data-stu-id="179f3-140">Modifying a Predefined Binding</span></span>  
 <span data-ttu-id="179f3-141">W poniższym przykładzie wstępnie zdefiniowane powiązanie jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="179f3-141">In the following example, a predefined binding is modified.</span></span> <span data-ttu-id="179f3-142">Następnie można użyć do skonfigurowania dowolnego punktu końcowego w usłudze.</span><span class="sxs-lookup"><span data-stu-id="179f3-142">It can then be used to configure any endpoint in the service.</span></span> <span data-ttu-id="179f3-143">Powiązanie jest modyfikowany <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> przez ustawienie wartości na 1 sekundę.</span><span class="sxs-lookup"><span data-stu-id="179f3-143">The binding is modified by setting the <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> value to 1 second.</span></span> <span data-ttu-id="179f3-144">Należy zauważyć, że <xref:System.TimeSpan> właściwość zwraca obiekt.</span><span class="sxs-lookup"><span data-stu-id="179f3-144">Note that the property returns a <xref:System.TimeSpan> object.</span></span>  
  
 <span data-ttu-id="179f3-145">To zmienione powiązanie znajduje się w sekcji powiązania.</span><span class="sxs-lookup"><span data-stu-id="179f3-145">That altered binding is found in the bindings section.</span></span> <span data-ttu-id="179f3-146">To zmienione powiązanie może być teraz używane podczas `binding` tworzenia dowolnego `endpoint` punktu końcowego przez ustawienie atrybutu w elemencie.</span><span class="sxs-lookup"><span data-stu-id="179f3-146">This altered binding can now be used when creating any endpoint by setting the `binding` attribute in the `endpoint` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="179f3-147">Jeśli nadasz określoną nazwę do `bindingConfiguration` powiązania, określony w punkcie końcowym usługi musi być zgodny z nim.</span><span class="sxs-lookup"><span data-stu-id="179f3-147">If you give a particular name to the binding, the `bindingConfiguration` specified in the service endpoint must match with it.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <endpoint
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
<bindings>  
    <basicHttpBinding
        receiveTimeout="00:00:01"  
    />  
</bindings>  
```  
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a><span data-ttu-id="179f3-148">Konfigurowanie zachowania do zastosowania do usługi</span><span class="sxs-lookup"><span data-stu-id="179f3-148">Configuring a Behavior to Apply to a Service</span></span>  
 <span data-ttu-id="179f3-149">W poniższym przykładzie określone zachowanie jest skonfigurowane dla typu usługi.</span><span class="sxs-lookup"><span data-stu-id="179f3-149">In the following example, a specific behavior is configured for the service type.</span></span> <span data-ttu-id="179f3-150">Element `ServiceMetadataBehavior` ten jest używany do włączania [Narzędzia narzędzia Do metadanych ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) w celu wykonywania zapytań do usługi i generowania dokumentów języka WSDL (Web Services Description Language) z metadanych.</span><span class="sxs-lookup"><span data-stu-id="179f3-150">The `ServiceMetadataBehavior` element is used to enable the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to query the service and generate Web Services Description Language (WSDL) documents from the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="179f3-151">Jeśli nadasz określoną nazwę do `behaviorConfiguration` zachowania, określone w sekcji usługi lub punktu końcowego musi być zgodna z nim.</span><span class="sxs-lookup"><span data-stu-id="179f3-151">If you give a particular name to the behavior, the `behaviorConfiguration` specified in the service or endpoint section must match it.</span></span>  
  
```xml  
<behaviors>  
    <behavior>  
        <ServiceMetadata httpGetEnabled="true" />
    </behavior>  
</behaviors>  
<services>  
    <service
       name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">
       <endpoint
          address="http://computer:8080/Hello"  
          contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
          binding="basicHttpBinding" />
    </service>  
</services>  
```  
  
 <span data-ttu-id="179f3-152">Poprzednia konfiguracja umożliwia klientowi wywołanie i uzyskanie metadanych usługi wpisanej przez "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="179f3-152">The preceding configuration enables a client to call and get the metadata of the "HelloWorld" typed service.</span></span>  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a><span data-ttu-id="179f3-153">Określanie usługi z dwoma punktami końcowymi przy użyciu różnych wartości wiązania</span><span class="sxs-lookup"><span data-stu-id="179f3-153">Specifying a Service with Two Endpoints Using Different Binding Values</span></span>  
 <span data-ttu-id="179f3-154">W tym ostatnim przykładzie dwa punkty końcowe są skonfigurowane dla typu `HelloWorld` usługi.</span><span class="sxs-lookup"><span data-stu-id="179f3-154">In this last example, two endpoints are configured for the `HelloWorld` service type.</span></span> <span data-ttu-id="179f3-155">Każdy punkt końcowy używa innego `bindingConfiguration` atrybutu dostosowanego tego samego typu `basicHttpBinding`powiązania (każdy modyfikuje ).</span><span class="sxs-lookup"><span data-stu-id="179f3-155">Each endpoint uses a different customized  `bindingConfiguration` attribute of the same binding type (each modifies the `basicHttpBinding`).</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
    <endpoint  
        address="http://computer:8080/Hello1"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="shortTimeout" />
    <endpoint  
        address="http://computer:8080/Hello2"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="Secure" />
</service>  
<bindings>  
    <basicHttpBinding
        name="shortTimeout"  
        timeout="00:00:00:01"
     />  
     <basicHttpBinding
        name="Secure">  
        <Security mode="Transport" />  
     </basicHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="179f3-156">Takie samo zachowanie można uzyskać przy użyciu `protocolMapping` konfiguracji domyślnej, dodając sekcję i konfigurując powiązania, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="179f3-156">You can get the same behavior using the default configuration by adding a `protocolMapping` section and configuring the bindings as demonstrated in the following example.</span></span>  
  
```xml  
<protocolMapping>  
    <add scheme="http" binding="basicHttpBinding" bindingConfiguration="shortTimeout" />  
    <add scheme="https" binding="basicHttpBinding" bindingConfiguration="Secure" />  
</protocolMapping>  
<bindings>  
    <basicHttpBinding
        name="shortTimeout"  
        timeout="00:00:00:01"
     />  
     <basicHttpBinding
        name="Secure" />  
        <Security mode="Transport" />  
</bindings>  
```  
  
## <a name="see-also"></a><span data-ttu-id="179f3-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="179f3-157">See also</span></span>

- [<span data-ttu-id="179f3-158">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="179f3-158">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="179f3-159">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="179f3-159">System-Provided Bindings</span></span>](system-provided-bindings.md)
- [<span data-ttu-id="179f3-160">Przegląd tworzenia punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="179f3-160">Endpoint Creation Overview</span></span>](endpoint-creation-overview.md)
- [<span data-ttu-id="179f3-161">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="179f3-161">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
