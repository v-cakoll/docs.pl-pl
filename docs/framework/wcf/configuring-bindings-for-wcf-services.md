---
title: Konfigurowanie wiązań dla usług WCF (Windows Communication Foundation)
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: 92f9457dd0c118c9a7c578a7088f66cdea1e5ad0
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320665"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a><span data-ttu-id="e6819-102">Konfigurowanie wiązań dla usług WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="e6819-102">Configuring Bindings for Windows Communication Foundation Services</span></span>
<span data-ttu-id="e6819-103">Podczas tworzenia aplikacji często chcesz odroczyć decyzje administratora po wdrożeniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e6819-103">When creating an application, you often want to defer decisions to the administrator after the deployment of the application.</span></span> <span data-ttu-id="e6819-104">Na przykład często nie ma możliwości znajomości informacji o adresie usługi lub Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="e6819-104">For example, there is often no way of knowing in advance what a service address, or Uniform Resource Identifier (URI), will be.</span></span> <span data-ttu-id="e6819-105">Zamiast kodowania adresu, preferowane jest umożliwienie administratorowi wykonania tej czynności po utworzeniu usługi.</span><span class="sxs-lookup"><span data-stu-id="e6819-105">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="e6819-106">Ta elastyczność jest realizowana przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e6819-106">This flexibility is accomplished through configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e6819-107">Użyj [Narzędzia do przesyłania metadanych ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) z przełącznikiem `/config`, aby szybko utworzyć pliki konfiguracyjne.</span><span class="sxs-lookup"><span data-stu-id="e6819-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config` switch to quickly create configuration files.</span></span>  
  
## <a name="major-sections"></a><span data-ttu-id="e6819-108">Sekcje główne</span><span class="sxs-lookup"><span data-stu-id="e6819-108">Major Sections</span></span>  
 <span data-ttu-id="e6819-109">Schemat konfiguracji Windows Communication Foundation (WCF) zawiera następujące trzy główne sekcje (`serviceModel`, `bindings` i `services`):</span><span class="sxs-lookup"><span data-stu-id="e6819-109">The Windows Communication Foundation (WCF) configuration scheme includes the following three major sections (`serviceModel`, `bindings`, and `services`):</span></span>  
  
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
  
### <a name="servicemodel-elements"></a><span data-ttu-id="e6819-110">Elementy ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e6819-110">ServiceModel Elements</span></span>  
 <span data-ttu-id="e6819-111">Możesz użyć sekcji podzielonej przez element `system.ServiceModel`, aby skonfigurować typ usługi z co najmniej jednym punktem końcowym, a także ustawieniami usługi.</span><span class="sxs-lookup"><span data-stu-id="e6819-111">You can use the section bounded by the `system.ServiceModel` element to configure a service type with one or more endpoints, as well as settings for a service.</span></span> <span data-ttu-id="e6819-112">Każdy punkt końcowy można następnie skonfigurować przy użyciu adresu, kontraktu i powiązania.</span><span class="sxs-lookup"><span data-stu-id="e6819-112">Each endpoint can then be configured with an address, a contract, and a binding.</span></span> <span data-ttu-id="e6819-113">Aby uzyskać więcej informacji na temat punktów końcowych, zobacz [Omówienie tworzenia punktów końcowych](endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e6819-113">For more information about endpoints, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="e6819-114">Jeśli nie określono żadnych punktów końcowych, środowisko uruchomieniowe dodaje domyślne punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="e6819-114">If no endpoints are specified, the runtime adds default endpoints.</span></span> <span data-ttu-id="e6819-115">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e6819-115">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="e6819-116">Powiązanie określa transporty (HTTP, TCP, potoki, kolejkowanie komunikatów) i protokoły (zabezpieczenia, niezawodność, przepływy transakcji) i składa się z elementów powiązania, z których każdy określa aspekt komunikacji punktu końcowego z światem.</span><span class="sxs-lookup"><span data-stu-id="e6819-116">A binding specifies transports (HTTP, TCP, pipes, Message Queuing) and protocols (Security, Reliability, Transaction flows) and consists of binding elements, each of which specifies an aspect of how an endpoint communicates with the world.</span></span>  
  
 <span data-ttu-id="e6819-117">Na przykład określenie elementu [\<basicHttpBinding >](../configure-apps/file-schema/wcf/basichttpbinding.md) wskazuje na użycie protokołu HTTP jako transportu dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e6819-117">For example, specifying the [\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) element indicates to use HTTP as the transport for an endpoint.</span></span> <span data-ttu-id="e6819-118">Jest on używany do naprowadzenia łączności punktu końcowego w czasie wykonywania, gdy zostanie otwarta usługa korzystająca z tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e6819-118">This is used to wire up the endpoint at run time when the service using this endpoint is opened.</span></span>  
  
 <span data-ttu-id="e6819-119">Istnieją dwa rodzaje powiązań: wstępnie zdefiniowane i niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="e6819-119">There are two kinds of bindings: predefined and custom.</span></span> <span data-ttu-id="e6819-120">Wstępnie zdefiniowane powiązania zawierają przydatne kombinacje elementów, które są używane w typowych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="e6819-120">Predefined bindings contain useful combinations of elements that are used in common scenarios.</span></span> <span data-ttu-id="e6819-121">Aby zapoznać się z listą wstępnie zdefiniowanych typów powiązań udostępnianych przez funkcję WCF, zobacz [powiązania dostarczone przez system](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="e6819-121">For a list of predefined binding types that WCF provides, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="e6819-122">Jeśli żadna wstępnie zdefiniowana kolekcja powiązań nie ma poprawnej kombinacji funkcji wymaganych przez aplikację usługi, można skonstruować niestandardowe powiązania w celu spełnienia wymagań aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e6819-122">If no predefined binding collection has the correct combination of features that a service application needs, you can construct custom bindings to meet the application's requirements.</span></span> <span data-ttu-id="e6819-123">Aby uzyskać więcej informacji na temat powiązań niestandardowych, zobacz [\<customBinding >](../configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="e6819-123">For more information about custom bindings, see [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
 <span data-ttu-id="e6819-124">Poniższe cztery przykłady ilustrują najczęstsze konfiguracje powiązań używane do konfigurowania usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="e6819-124">The following four examples illustrate the most common binding configurations used for setting up a WCF service.</span></span>  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a><span data-ttu-id="e6819-125">Określanie punktu końcowego w celu użycia typu powiązania</span><span class="sxs-lookup"><span data-stu-id="e6819-125">Specifying an Endpoint to Use a Binding Type</span></span>  
 <span data-ttu-id="e6819-126">Pierwszy przykład ilustruje sposób określania punktu końcowego skonfigurowanego za pomocą adresu, kontraktu i powiązania.</span><span class="sxs-lookup"><span data-stu-id="e6819-126">The first example illustrates how to specify an endpoint configured with an address, a contract, and a binding.</span></span>  
  
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
  
 <span data-ttu-id="e6819-127">W tym przykładzie atrybut `name` wskazuje typ usługi, dla której jest konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="e6819-127">In this example, the `name` attribute indicates which service type the configuration is for.</span></span> <span data-ttu-id="e6819-128">Podczas tworzenia usługi w kodzie przy użyciu kontraktu `HelloWorld` zostanie on zainicjowany ze wszystkimi punktami końcowymi zdefiniowanymi w przykładowej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e6819-128">When you create a service in your code with the `HelloWorld` contract, it is initialized with all of the endpoints defined in the example configuration.</span></span> <span data-ttu-id="e6819-129">Jeśli zestaw implementuje tylko jeden kontrakt usługi, atrybut `name` może zostać pominięty, ponieważ usługa używa jedynego dostępnego typu.</span><span class="sxs-lookup"><span data-stu-id="e6819-129">If the assembly implements only one service contract, the `name` attribute can be omitted because the service uses the only available type.</span></span> <span data-ttu-id="e6819-130">Atrybut przyjmuje ciąg, który musi mieć format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span><span class="sxs-lookup"><span data-stu-id="e6819-130">The attribute takes a string, which must be in the format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>  
  
 <span data-ttu-id="e6819-131">Atrybut `address` Określa identyfikator URI używany przez inne punkty końcowe do komunikowania się z usługą.</span><span class="sxs-lookup"><span data-stu-id="e6819-131">The `address` attribute specifies the URI that other endpoints use to communicate to the service.</span></span> <span data-ttu-id="e6819-132">Identyfikator URI może być ścieżką bezwzględną lub względną.</span><span class="sxs-lookup"><span data-stu-id="e6819-132">The URI can be either an absolute or relative path.</span></span> <span data-ttu-id="e6819-133">Jeśli zostanie podany adres względny, host powinien podać adres podstawowy, który jest odpowiedni dla schematu transportu używanego w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="e6819-133">If a relative address is provided, the host is expected to provide a base address that is appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="e6819-134">Jeśli adres nie jest skonfigurowany, zakłada się, że adres podstawowy jest adresem dla tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e6819-134">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span>  
  
 <span data-ttu-id="e6819-135">Atrybut `contract` określa kontrakt ujawniany przez ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="e6819-135">The `contract` attribute specifies the contract this endpoint is exposing.</span></span> <span data-ttu-id="e6819-136">Typ implementacji usługi musi implementować typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e6819-136">The service implementation type must implement the contract type.</span></span> <span data-ttu-id="e6819-137">Jeśli implementacja usługi implementuje pojedynczy typ kontraktu, ta właściwość może zostać pominięta.</span><span class="sxs-lookup"><span data-stu-id="e6819-137">If a service implementation implements a single contract type, then this property can be omitted.</span></span>  
  
 <span data-ttu-id="e6819-138">Atrybut `binding` wybiera wstępnie zdefiniowane lub niestandardowe powiązanie do użycia dla tego określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e6819-138">The `binding` attribute selects a predefined or custom binding to use for this specific endpoint.</span></span> <span data-ttu-id="e6819-139">Punkt końcowy, który nie wybiera jawnie powiązania używa domyślnego wyboru powiązania, który jest `BasicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="e6819-139">An endpoint that does not explicitly select a binding uses the default binding selection, which is `BasicHttpBinding`.</span></span>  
  
#### <a name="modifying-a-predefined-binding"></a><span data-ttu-id="e6819-140">Modyfikowanie wstępnie zdefiniowanego powiązania</span><span class="sxs-lookup"><span data-stu-id="e6819-140">Modifying a Predefined Binding</span></span>  
 <span data-ttu-id="e6819-141">W poniższym przykładzie modyfikowane jest wstępnie zdefiniowane powiązanie.</span><span class="sxs-lookup"><span data-stu-id="e6819-141">In the following example, a predefined binding is modified.</span></span> <span data-ttu-id="e6819-142">Można go następnie użyć do skonfigurowania dowolnego punktu końcowego w usłudze.</span><span class="sxs-lookup"><span data-stu-id="e6819-142">It can then be used to configure any endpoint in the service.</span></span> <span data-ttu-id="e6819-143">Powiązanie jest modyfikowane przez ustawienie wartości <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> na 1 sekundę.</span><span class="sxs-lookup"><span data-stu-id="e6819-143">The binding is modified by setting the <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> value to 1 second.</span></span> <span data-ttu-id="e6819-144">Należy zauważyć, że właściwość zwraca obiekt <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="e6819-144">Note that the property returns a <xref:System.TimeSpan> object.</span></span>  
  
 <span data-ttu-id="e6819-145">To zmienione powiązanie można znaleźć w sekcji powiązań.</span><span class="sxs-lookup"><span data-stu-id="e6819-145">That altered binding is found in the bindings section.</span></span> <span data-ttu-id="e6819-146">To zmienione powiązanie może być teraz używane podczas tworzenia dowolnego punktu końcowego przez ustawienie atrybutu `binding` w elemencie `endpoint`.</span><span class="sxs-lookup"><span data-stu-id="e6819-146">This altered binding can now be used when creating any endpoint by setting the `binding` attribute in the `endpoint` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e6819-147">W przypadku nadania określonej nazwy powiązaniem wartość `bindingConfiguration` określona w punkcie końcowym usługi musi być zgodna z tym elementem.</span><span class="sxs-lookup"><span data-stu-id="e6819-147">If you give a particular name to the binding, the `bindingConfiguration` specified in the service endpoint must match with it.</span></span>  
  
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
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a><span data-ttu-id="e6819-148">Konfigurowanie zachowania do zastosowania do usługi</span><span class="sxs-lookup"><span data-stu-id="e6819-148">Configuring a Behavior to Apply to a Service</span></span>  
 <span data-ttu-id="e6819-149">W poniższym przykładzie określone zachowanie jest skonfigurowane dla typu usługi.</span><span class="sxs-lookup"><span data-stu-id="e6819-149">In the following example, a specific behavior is configured for the service type.</span></span> <span data-ttu-id="e6819-150">Element `ServiceMetadataBehavior` służy do włączenia narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) w celu wysyłania zapytań do usługi i generowania dokumentów Web Services Description Language (WSDL) z metadanych.</span><span class="sxs-lookup"><span data-stu-id="e6819-150">The `ServiceMetadataBehavior` element is used to enable the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to query the service and generate Web Services Description Language (WSDL) documents from the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e6819-151">W przypadku nadania określonej nazwy zachowaniem wartość `behaviorConfiguration` określona w sekcji Service lub Endpoint musi być zgodna.</span><span class="sxs-lookup"><span data-stu-id="e6819-151">If you give a particular name to the behavior, the `behaviorConfiguration` specified in the service or endpoint section must match it.</span></span>  
  
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
  
 <span data-ttu-id="e6819-152">Poprzednia konfiguracja pozwala klientowi na wywołanie i Pobieranie metadanych usługi typu "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="e6819-152">The preceding configuration enables a client to call and get the metadata of the "HelloWorld" typed service.</span></span>  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a><span data-ttu-id="e6819-153">Określanie usługi z dwoma punktami końcowymi przy użyciu różnych wartości powiązania</span><span class="sxs-lookup"><span data-stu-id="e6819-153">Specifying a Service with Two Endpoints Using Different Binding Values</span></span>  
 <span data-ttu-id="e6819-154">W tym ostatnim przykładzie dla typu usługi `HelloWorld` skonfigurowano dwa punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="e6819-154">In this last example, two endpoints are configured for the `HelloWorld` service type.</span></span> <span data-ttu-id="e6819-155">Każdy punkt końcowy używa innego niestandardowego atrybutu `bindingConfiguration` tego samego typu powiązania (każda modyfikuje `basicHttpBinding`).</span><span class="sxs-lookup"><span data-stu-id="e6819-155">Each endpoint uses a different customized  `bindingConfiguration` attribute of the same binding type (each modifies the `basicHttpBinding`).</span></span>  
  
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
  
 <span data-ttu-id="e6819-156">Możesz uzyskać takie samo zachowanie przy użyciu konfiguracji domyślnej, dodając sekcję `protocolMapping` i konfigurując powiązania, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e6819-156">You can get the same behavior using the default configuration by adding a `protocolMapping` section and configuring the bindings as demonstrated in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e6819-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6819-157">See also</span></span>

- [<span data-ttu-id="e6819-158">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="e6819-158">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="e6819-159">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="e6819-159">System-Provided Bindings</span></span>](system-provided-bindings.md)
- [<span data-ttu-id="e6819-160">Przegląd tworzenia punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="e6819-160">Endpoint Creation Overview</span></span>](endpoint-creation-overview.md)
- [<span data-ttu-id="e6819-161">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="e6819-161">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
