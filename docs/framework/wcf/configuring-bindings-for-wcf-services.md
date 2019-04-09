---
title: Konfigurowanie wiązań dla usług WCF (Windows Communication Foundation)
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: 009011100af86e315aa41beb822b1448e2f21b25
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150452"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a><span data-ttu-id="323d9-102">Konfigurowanie wiązań dla usług WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="323d9-102">Configuring Bindings for Windows Communication Foundation Services</span></span>
<span data-ttu-id="323d9-103">Podczas tworzenia aplikacji, często zachodzi potrzeba Odrocz decyzji dla administratora po wdrożeniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="323d9-103">When creating an application, you often want to defer decisions to the administrator after the deployment of the application.</span></span> <span data-ttu-id="323d9-104">Na przykład często nie ma możliwości informacji z wyprzedzeniem o tym, jaki jest adres usługi lub identyfikator (URI), będzie.</span><span class="sxs-lookup"><span data-stu-id="323d9-104">For example, there is often no way of knowing in advance what a service address, or Uniform Resource Identifier (URI), will be.</span></span> <span data-ttu-id="323d9-105">Zamiast kodować adresu, jest bardziej pożądane, aby umożliwić administratorowi to zrobić po utworzeniu usługi.</span><span class="sxs-lookup"><span data-stu-id="323d9-105">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="323d9-106">Ta elastyczność odbywa się za pośrednictwem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="323d9-106">This flexibility is accomplished through configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="323d9-107">Użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z `/config` Przełącz na szybkie tworzenie plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="323d9-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config` switch to quickly create configuration files.</span></span>  
  
## <a name="major-sections"></a><span data-ttu-id="323d9-108">Główne sekcje</span><span class="sxs-lookup"><span data-stu-id="323d9-108">Major Sections</span></span>  
 <span data-ttu-id="323d9-109">Schemat konfiguracji usług Windows Communication Foundation (WCF) obejmuje następujące trzy główne sekcje (`serviceModel`, `bindings`, i `services`):</span><span class="sxs-lookup"><span data-stu-id="323d9-109">The Windows Communication Foundation (WCF) configuration scheme includes the following three major sections (`serviceModel`, `bindings`, and `services`):</span></span>  
  
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
  
### <a name="servicemodel-elements"></a><span data-ttu-id="323d9-110">Elementy modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="323d9-110">ServiceModel Elements</span></span>  
 <span data-ttu-id="323d9-111">Można użyć sekcji poprowadzoną `system.ServiceModel` element, aby skonfigurować typ usługi z jedną lub więcej punktów końcowych, a także ustawienia usługi.</span><span class="sxs-lookup"><span data-stu-id="323d9-111">You can use the section bounded by the `system.ServiceModel` element to configure a service type with one or more endpoints, as well as settings for a service.</span></span> <span data-ttu-id="323d9-112">Każdy punkt końcowy, można skonfigurować za pomocą adresu, kontrakt i powiązania.</span><span class="sxs-lookup"><span data-stu-id="323d9-112">Each endpoint can then be configured with an address, a contract, and a binding.</span></span> <span data-ttu-id="323d9-113">Aby uzyskać więcej informacji na temat punktów końcowych, zobacz [Przegląd tworzenia punktów końcowych](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="323d9-113">For more information about endpoints, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="323d9-114">Jeśli nie określono żadnych punktów końcowych, środowiska uruchomieniowego dodaje domyślne punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="323d9-114">If no endpoints are specified, the runtime adds default endpoints.</span></span> <span data-ttu-id="323d9-115">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązania i zachowań, zobacz [uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="323d9-115">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="323d9-116">Powiązanie określa transportów (potoki protokołu TCP protokołu HTTP usługi kolejkowania komunikatów) i protokołów (bezpieczeństwo, niezawodność, przepływy transakcji) i składa się z elementów, z których każdy określa aspektów jak punkt końcowy komunikuje się ze światem wiązania.</span><span class="sxs-lookup"><span data-stu-id="323d9-116">A binding specifies transports (HTTP, TCP, pipes, Message Queuing) and protocols (Security, Reliability, Transaction flows) and consists of binding elements, each of which specifies an aspect of how an endpoint communicates with the world.</span></span>  
  
 <span data-ttu-id="323d9-117">Na przykład określenie [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) wskazuje element, aby korzystać z protokołu HTTP jako transportu dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="323d9-117">For example, specifying the [\<basicHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element indicates to use HTTP as the transport for an endpoint.</span></span> <span data-ttu-id="323d9-118">Służy to do przewodowy punkt końcowy w czasie wykonywania, po otwarciu usługi przy użyciu tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="323d9-118">This is used to wire up the endpoint at run time when the service using this endpoint is opened.</span></span>  
  
 <span data-ttu-id="323d9-119">Istnieją dwa rodzaje powiązań: wstępnie zdefiniowanych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="323d9-119">There are two kinds of bindings: predefined and custom.</span></span> <span data-ttu-id="323d9-120">Wstępnie zdefiniowanych powiązań kombinację przydatne elementy, które są używane w typowych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="323d9-120">Predefined bindings contain useful combinations of elements that are used in common scenarios.</span></span> <span data-ttu-id="323d9-121">Aby uzyskać listę typów wstępnie zdefiniowanych powiązań, które oferuje usługi WCF, zobacz [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="323d9-121">For a list of predefined binding types that WCF provides, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="323d9-122">Jeśli nie kolekcji wstępnie zdefiniowanych powiązań ma poprawną kombinacją funkcje, których potrzebuje aplikacja usługi, można utworzyć powiązań niestandardowych w celu spełnienia wymagań aplikacji.</span><span class="sxs-lookup"><span data-stu-id="323d9-122">If no predefined binding collection has the correct combination of features that a service application needs, you can construct custom bindings to meet the application's requirements.</span></span> <span data-ttu-id="323d9-123">Aby uzyskać więcej informacji na temat powiązania niestandardowej zobacz [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="323d9-123">For more information about custom bindings, see [\<customBinding>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
 <span data-ttu-id="323d9-124">Cztery następujące przykłady przedstawiają najbardziej typowe konfiguracje powiązania, używany do konfigurowania usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="323d9-124">The following four examples illustrate the most common binding configurations used for setting up a WCF service.</span></span>  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a><span data-ttu-id="323d9-125">Określanie punktu końcowego do użycia typ powiązania</span><span class="sxs-lookup"><span data-stu-id="323d9-125">Specifying an Endpoint to Use a Binding Type</span></span>  
 <span data-ttu-id="323d9-126">Pierwszy przykład przedstawia sposób określić punkty końcowe skonfigurowane za pomocą adresu, kontrakt i powiązania.</span><span class="sxs-lookup"><span data-stu-id="323d9-126">The first example illustrates how to specify an endpoint configured with an address, a contract, and a binding.</span></span>  
  
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
  
 <span data-ttu-id="323d9-127">W tym przykładzie `name` atrybut wskazuje typ usługi, których konfiguracja jest ustawiona na.</span><span class="sxs-lookup"><span data-stu-id="323d9-127">In this example, the `name` attribute indicates which service type the configuration is for.</span></span> <span data-ttu-id="323d9-128">Podczas tworzenia usługi w kodzie za pomocą `HelloWorld` kontrakt jest inicjowany za pomocą wszystkich punktów końcowych zdefiniowanych w przykładowej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="323d9-128">When you create a service in your code with the `HelloWorld` contract, it is initialized with all of the endpoints defined in the example configuration.</span></span> <span data-ttu-id="323d9-129">Jeśli zestaw implementuje tylko jedną umowę serwisową, `name` atrybut można pominąć, ponieważ usługa korzysta jedynie dostępnych typów.</span><span class="sxs-lookup"><span data-stu-id="323d9-129">If the assembly implements only one service contract, the `name` attribute can be omitted because the service uses the only available type.</span></span> <span data-ttu-id="323d9-130">Atrybut przyjmuje ciąg, który musi być w formacie</span><span class="sxs-lookup"><span data-stu-id="323d9-130">The attribute takes a string, which must be in the format</span></span> `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`  
  
 <span data-ttu-id="323d9-131">`address` Atrybut określa identyfikator URI, który inne punkty końcowe używają do komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="323d9-131">The `address` attribute specifies the URI that other endpoints use to communicate to the service.</span></span> <span data-ttu-id="323d9-132">Identyfikator URI może być ścieżką bezwzględną lub względną.</span><span class="sxs-lookup"><span data-stu-id="323d9-132">The URI can be either an absolute or relative path.</span></span> <span data-ttu-id="323d9-133">Jeśli nie podano adresu względnego, host powinien zapewniać adres podstawowy, który jest odpowiedni dla używany w wiązaniu schemat transportu.</span><span class="sxs-lookup"><span data-stu-id="323d9-133">If a relative address is provided, the host is expected to provide a base address that is appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="323d9-134">Jeśli adres nie jest skonfigurowany, adres bazowy zakłada się, że adres dla tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="323d9-134">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span>  
  
 <span data-ttu-id="323d9-135">`contract` Atrybut określa kontrakt jest ujawniany przez ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="323d9-135">The `contract` attribute specifies the contract this endpoint is exposing.</span></span> <span data-ttu-id="323d9-136">Typ implementacji usługi musi implementować typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="323d9-136">The service implementation type must implement the contract type.</span></span> <span data-ttu-id="323d9-137">Jeśli implementacji usługi implementuje typ kontraktu pojedynczego, tej właściwości można pominąć.</span><span class="sxs-lookup"><span data-stu-id="323d9-137">If a service implementation implements a single contract type, then this property can be omitted.</span></span>  
  
 <span data-ttu-id="323d9-138">`binding` Atrybut wybiera powiązania wstępnie zdefiniowaną lub niestandardową w celu użycia dla tego określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="323d9-138">The `binding` attribute selects a predefined or custom binding to use for this specific endpoint.</span></span> <span data-ttu-id="323d9-139">Punkt końcowy, który nie wybierze jawnie powiązanie używa domyślny wybór powiązania, który jest `BasicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="323d9-139">An endpoint that does not explicitly select a binding uses the default binding selection, which is `BasicHttpBinding`.</span></span>  
  
#### <a name="modifying-a-predefined-binding"></a><span data-ttu-id="323d9-140">Modyfikowanie wstępnie zdefiniowanych powiązań</span><span class="sxs-lookup"><span data-stu-id="323d9-140">Modifying a Predefined Binding</span></span>  
 <span data-ttu-id="323d9-141">W poniższym przykładzie są modyfikowane wstępnie zdefiniowanych powiązań.</span><span class="sxs-lookup"><span data-stu-id="323d9-141">In the following example, a predefined binding is modified.</span></span> <span data-ttu-id="323d9-142">Następnie można go skonfigurować z dowolnego punktu końcowego w usłudze.</span><span class="sxs-lookup"><span data-stu-id="323d9-142">It can then be used to configure any endpoint in the service.</span></span> <span data-ttu-id="323d9-143">Powiązanie jest modyfikowany przez ustawienie <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> wartość na 1 sekundę.</span><span class="sxs-lookup"><span data-stu-id="323d9-143">The binding is modified by setting the <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> value to 1 second.</span></span> <span data-ttu-id="323d9-144">Należy zauważyć, że właściwość ta zwraca <xref:System.TimeSpan> obiektu.</span><span class="sxs-lookup"><span data-stu-id="323d9-144">Note that the property returns a <xref:System.TimeSpan> object.</span></span>  
  
 <span data-ttu-id="323d9-145">Który zmienić powiązania znajduje się w sekcji wiązania.</span><span class="sxs-lookup"><span data-stu-id="323d9-145">That altered binding is found in the bindings section.</span></span> <span data-ttu-id="323d9-146">To zmienić powiązania można teraz używać podczas tworzenia dowolnego punktu końcowego, ustawiając `binding` atrybutu w `endpoint` elementu.</span><span class="sxs-lookup"><span data-stu-id="323d9-146">This altered binding can now be used when creating any endpoint by setting the `binding` attribute in the `endpoint` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="323d9-147">Nadaj nazwę określonego do powiązania, `bindingConfiguration` określone w usłudze punktu końcowego musi być zgodna z nim.</span><span class="sxs-lookup"><span data-stu-id="323d9-147">If you give a particular name to the binding, the `bindingConfiguration` specified in the service endpoint must match with it.</span></span>  
  
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
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a><span data-ttu-id="323d9-148">Konfigurowanie zachowania do zastosowania do usług</span><span class="sxs-lookup"><span data-stu-id="323d9-148">Configuring a Behavior to Apply to a Service</span></span>  
 <span data-ttu-id="323d9-149">W poniższym przykładzie określone zachowanie jest skonfigurowany dla typu usługi.</span><span class="sxs-lookup"><span data-stu-id="323d9-149">In the following example, a specific behavior is configured for the service type.</span></span> <span data-ttu-id="323d9-150">`ServiceMetadataBehavior` Element służy do włączania [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) zapytań do usługi i Generowanie dokumentów sieci Web Services Description Language (WSDL) z metadanych.</span><span class="sxs-lookup"><span data-stu-id="323d9-150">The `ServiceMetadataBehavior` element is used to enable the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to query the service and generate Web Services Description Language (WSDL) documents from the metadata.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="323d9-151">Nadaj nazwę określonego z zachowaniem `behaviorConfiguration` określone w usłudze lub punkt końcowy sekcji musi zapewnić zgodność.</span><span class="sxs-lookup"><span data-stu-id="323d9-151">If you give a particular name to the behavior, the `behaviorConfiguration` specified in the service or endpoint section must match it.</span></span>  
  
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
  
 <span data-ttu-id="323d9-152">Poprzedni umożliwia konfigurację klienta w celu wywołania i Pobierz metadane nazwę "HelloWorld" wpisane usługi.</span><span class="sxs-lookup"><span data-stu-id="323d9-152">The preceding configuration enables a client to call and get the metadata of the "HelloWorld" typed service.</span></span>  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a><span data-ttu-id="323d9-153">Określanie usługi przy użyciu dwóch punktów końcowych przy użyciu wartości inne powiązanie</span><span class="sxs-lookup"><span data-stu-id="323d9-153">Specifying a Service with Two Endpoints Using Different Binding Values</span></span>  
 <span data-ttu-id="323d9-154">W tym przykładzie ostatnie dwa punkty końcowe są konfigurowane dla `HelloWorld` typ usługi.</span><span class="sxs-lookup"><span data-stu-id="323d9-154">In this last example, two endpoints are configured for the `HelloWorld` service type.</span></span> <span data-ttu-id="323d9-155">Każdy punkt końcowy korzysta z różnych dostosowane `bindingConfiguration` atrybutu typu powiązania (każda modyfikuje `basicHttpBinding`).</span><span class="sxs-lookup"><span data-stu-id="323d9-155">Each endpoint uses a different customized  `bindingConfiguration` attribute of the same binding type (each modifies the `basicHttpBinding`).</span></span>  
  
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
  
 <span data-ttu-id="323d9-156">Możesz uzyskać takie samo zachowanie za pomocą konfiguracji domyślnej, dodając `protocolMapping` sekcji i konfigurowanie powiązania, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="323d9-156">You can get the same behavior using the default configuration by adding a `protocolMapping` section and configuring the bindings as demonstrated in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="323d9-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="323d9-157">See also</span></span>

- [<span data-ttu-id="323d9-158">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="323d9-158">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="323d9-159">Wiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="323d9-159">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)
- [<span data-ttu-id="323d9-160">Przegląd tworzenia punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="323d9-160">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)
- [<span data-ttu-id="323d9-161">Konfigurowanie usług i klientów za pomocą wiązań</span><span class="sxs-lookup"><span data-stu-id="323d9-161">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
