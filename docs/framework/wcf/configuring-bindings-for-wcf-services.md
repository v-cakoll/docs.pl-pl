---
title: "Konfigurowanie powiązań dla usług WCF (Windows Communication Foundation)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 92fc3886f81ee401cbd3de2fb6ef251e4c340394
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a><span data-ttu-id="f24eb-102">Konfigurowanie powiązań dla usług WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="f24eb-102">Configuring Bindings for Windows Communication Foundation Services</span></span>
<span data-ttu-id="f24eb-103">Podczas tworzenia aplikacji, ma często mają być odroczone decyzje administratora po wdrożeniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f24eb-103">When creating an application, you often want to defer decisions to the administrator after the deployment of the application.</span></span> <span data-ttu-id="f24eb-104">Na przykład często istnieje żaden sposób uzyskać z wyprzedzeniem, co adres usługi lub identyfikator URI (Uniform Resource), będzie.</span><span class="sxs-lookup"><span data-stu-id="f24eb-104">For example, there is often no way of knowing in advance what a service address, or Uniform Resource Identifier (URI), will be.</span></span> <span data-ttu-id="f24eb-105">Zamiast kodować adres, zaleca się pozwalają administratorowi zrobić po utworzeniu usługi.</span><span class="sxs-lookup"><span data-stu-id="f24eb-105">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="f24eb-106">Tego rodzaju elastyczności odbywa się za pośrednictwem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f24eb-106">This flexibility is accomplished through configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f24eb-107">Użyj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z `/config` Przełącz na szybkie tworzenie plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f24eb-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config` switch to quickly create configuration files.</span></span>  
  
## <a name="major-sections"></a><span data-ttu-id="f24eb-108">Sekcje główne</span><span class="sxs-lookup"><span data-stu-id="f24eb-108">Major Sections</span></span>  
 <span data-ttu-id="f24eb-109">[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Konfiguracja systemu obejmuje następujące trzy sekcje główne (`serviceModel`, `bindings`, i `services`):</span><span class="sxs-lookup"><span data-stu-id="f24eb-109">The [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] configuration scheme includes the following three major sections (`serviceModel`, `bindings`, and `services`):</span></span>  
  
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
  
### <a name="servicemodel-elements"></a><span data-ttu-id="f24eb-110">Elementy modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f24eb-110">ServiceModel Elements</span></span>  
 <span data-ttu-id="f24eb-111">Korzystając z sekcji ograniczone przez `system.ServiceModel` element, aby skonfigurować typ usługi z jednego lub więcej punktów końcowych, a także ustawienia usługi.</span><span class="sxs-lookup"><span data-stu-id="f24eb-111">You can use the section bounded by the `system.ServiceModel` element to configure a service type with one or more endpoints, as well as settings for a service.</span></span> <span data-ttu-id="f24eb-112">Następnie można skonfigurować za pomocą adresu, kontrakt i powiązanie każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f24eb-112">Each endpoint can then be configured with an address, a contract, and a binding.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="f24eb-113">punktów końcowych, zobacz [Przegląd tworzenia punktów końcowych](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f24eb-113"> endpoints, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="f24eb-114">Jeśli nie określono żadnych punktów końcowych, środowisko uruchomieniowe dodaje domyślne punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="f24eb-114">If no endpoints are specified, the runtime adds default endpoints.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="f24eb-115">domyślne punkty końcowe, powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f24eb-115"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="f24eb-116">Powiązanie określa transportów (potoki protokołu HTTP, TCP, kolejkowania) i protokołów (zabezpieczeń, niezawodności, przepływy transakcji) i składa się z elementów, z których każdy określa aspektów jak punkt końcowy komunikuje się z świecie wiązania.</span><span class="sxs-lookup"><span data-stu-id="f24eb-116">A binding specifies transports (HTTP, TCP, pipes, Message Queuing) and protocols (Security, Reliability, Transaction flows) and consists of binding elements, each of which specifies an aspect of how an endpoint communicates with the world.</span></span>  
  
 <span data-ttu-id="f24eb-117">Na przykład określenie [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) wskazuje element do obsługi protokołu HTTP jako transportu dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f24eb-117">For example, specifying the [\<basicHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element indicates to use HTTP as the transport for an endpoint.</span></span> <span data-ttu-id="f24eb-118">Ten element jest używany do przesyłania się punkt końcowy w czasie wykonywania, gdy jest otwarty przy użyciu tego punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="f24eb-118">This is used to wire up the endpoint at run time when the service using this endpoint is opened.</span></span>  
  
 <span data-ttu-id="f24eb-119">Istnieją dwa rodzaje powiązań: wstępnie zdefiniowanych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="f24eb-119">There are two kinds of bindings: predefined and custom.</span></span> <span data-ttu-id="f24eb-120">Wstępnie zdefiniowanych powiązań kombinację przydatne elementy, które są używane w typowych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="f24eb-120">Predefined bindings contain useful combinations of elements that are used in common scenarios.</span></span> <span data-ttu-id="f24eb-121">Dla listy wstępnie zdefiniowanych powiązań typy, które [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] udostępnia, zobacz [powiązania System-Provided](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="f24eb-121">For a list of predefined binding types that [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] provides, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="f24eb-122">Jeśli żadna kolekcja wstępnie zdefiniowanych powiązania ma poprawne kombinacja funkcji, które wymaga aplikacji usługi, można utworzyć powiązania niestandardowe, aby spełnić wymagania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f24eb-122">If no predefined binding collection has the correct combination of features that a service application needs, you can construct custom bindings to meet the application's requirements.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="f24eb-123">powiązania niestandardowe, zobacz [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="f24eb-123"> custom bindings, see [\<customBinding>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
 <span data-ttu-id="f24eb-124">Cztery następujące przykłady przedstawiają najbardziej typowe konfiguracje powiązania, używany do konfigurowania [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="f24eb-124">The following four examples illustrate the most common binding configurations used for setting up a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span>  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a><span data-ttu-id="f24eb-125">Określający typ powiązania punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="f24eb-125">Specifying an Endpoint to Use a Binding Type</span></span>  
 <span data-ttu-id="f24eb-126">Pierwszym przykładzie przedstawiono sposób określić punkt końcowy skonfigurowany adres, kontrakt i powiązania.</span><span class="sxs-lookup"><span data-stu-id="f24eb-126">The first example illustrates how to specify an endpoint configured with an address, a contract, and a binding.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!—- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />  
  </endpoint>  
</service>  
```  
  
 <span data-ttu-id="f24eb-127">W tym przykładzie `name` atrybut wskazuje typ usługi, których konfiguracja jest ustawiona na.</span><span class="sxs-lookup"><span data-stu-id="f24eb-127">In this example, the `name` attribute indicates which service type the configuration is for.</span></span> <span data-ttu-id="f24eb-128">Po utworzeniu usługi kodu za pomocą `HelloWorld` kontraktu, został zainicjowany z wszystkich punktów końcowych zdefiniowanych w przykładowej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f24eb-128">When you create a service in your code with the `HelloWorld` contract, it is initialized with all of the endpoints defined in the example configuration.</span></span> <span data-ttu-id="f24eb-129">Jeśli zestaw implementuje tylko jeden kontrakt usługi, `name` atrybut może zostać pominięty, ponieważ usługa korzysta z typu dostępne tylko.</span><span class="sxs-lookup"><span data-stu-id="f24eb-129">If the assembly implements only one service contract, the `name` attribute can be omitted because the service uses the only available type.</span></span> <span data-ttu-id="f24eb-130">Atrybut przyjmuje ciąg, który musi być w formacie`Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span><span class="sxs-lookup"><span data-stu-id="f24eb-130">The attribute takes a string, which must be in the format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>  
  
 <span data-ttu-id="f24eb-131">`address` Atrybut określa identyfikator URI, który innych punktów końcowych używają do komunikowania się z usługą.</span><span class="sxs-lookup"><span data-stu-id="f24eb-131">The `address` attribute specifies the URI that other endpoints use to communicate to the service.</span></span> <span data-ttu-id="f24eb-132">Identyfikator URI może być ścieżką bezwzględną ani względną.</span><span class="sxs-lookup"><span data-stu-id="f24eb-132">The URI can be either an absolute or relative path.</span></span> <span data-ttu-id="f24eb-133">Jeśli zostanie podany adres względny, hosta powinien podać adres podstawowy, który jest odpowiedni dla używany w powiązaniu schemat transportu.</span><span class="sxs-lookup"><span data-stu-id="f24eb-133">If a relative address is provided, the host is expected to provide a base address that is appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="f24eb-134">Jeśli nie skonfigurowano adres podstawowy adres zakłada się, że adres dla tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f24eb-134">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span>  
  
 <span data-ttu-id="f24eb-135">`contract` Atrybut określa kontrakt jest ujawniany przez ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="f24eb-135">The `contract` attribute specifies the contract this endpoint is exposing.</span></span> <span data-ttu-id="f24eb-136">Typ implementacji usługi musi implementować typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="f24eb-136">The service implementation type must implement the contract type.</span></span> <span data-ttu-id="f24eb-137">Jeśli implementacji usługi implementuje typu jeden kontrakt, tej właściwości można pominąć.</span><span class="sxs-lookup"><span data-stu-id="f24eb-137">If a service implementation implements a single contract type, then this property can be omitted.</span></span>  
  
 <span data-ttu-id="f24eb-138">`binding` Atrybut wybiera powiązania wstępnie zdefiniowanych lub niestandardowych w celu użycia dla tego określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f24eb-138">The `binding` attribute selects a predefined or custom binding to use for this specific endpoint.</span></span> <span data-ttu-id="f24eb-139">Domyślny wybór powiązania, który jest korzysta z punktu końcowego, który nie wybierze jawnie powiązanie `BasicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="f24eb-139">An endpoint that does not explicitly select a binding uses the default binding selection, which is `BasicHttpBinding`.</span></span>  
  
#### <a name="modifying-a-predefined-binding"></a><span data-ttu-id="f24eb-140">Modyfikowanie wstępnie zdefiniowanych powiązań</span><span class="sxs-lookup"><span data-stu-id="f24eb-140">Modifying a Predefined Binding</span></span>  
 <span data-ttu-id="f24eb-141">W poniższym przykładzie są modyfikowane wstępnie zdefiniowanych powiązań.</span><span class="sxs-lookup"><span data-stu-id="f24eb-141">In the following example, a predefined binding is modified.</span></span> <span data-ttu-id="f24eb-142">Następnie można go skonfigurować dowolnego punktu końcowego w usłudze.</span><span class="sxs-lookup"><span data-stu-id="f24eb-142">It can then be used to configure any endpoint in the service.</span></span> <span data-ttu-id="f24eb-143">Powiązanie jest modyfikowany przez ustawienie <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> wartość na 1 sekundę.</span><span class="sxs-lookup"><span data-stu-id="f24eb-143">The binding is modified by setting the <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> value to 1 second.</span></span> <span data-ttu-id="f24eb-144">Należy pamiętać, że właściwość zwraca <xref:System.TimeSpan> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f24eb-144">Note that the property returns a <xref:System.TimeSpan> object.</span></span>  
  
 <span data-ttu-id="f24eb-145">Który zmienić powiązania znajduje się w sekcji powiązania.</span><span class="sxs-lookup"><span data-stu-id="f24eb-145">That altered binding is found in the bindings section.</span></span> <span data-ttu-id="f24eb-146">To zmienić powiązania można teraz używać podczas tworzenia dowolnego punktu końcowego ustawiając `binding` atrybutu w `endpoint` elementu.</span><span class="sxs-lookup"><span data-stu-id="f24eb-146">This altered binding can now be used when creating any endpoint by setting the `binding` attribute in the `endpoint` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f24eb-147">Jeśli można podać nazwę określonego powiązanie, `bindingConfiguration` określony w usłudze punktu końcowego musi być zgodna z nim.</span><span class="sxs-lookup"><span data-stu-id="f24eb-147">If you give a particular name to the binding, the `bindingConfiguration` specified in the service endpoint must match with it.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />  
  </endpoint>  
</service>  
<bindings>  
    <basicHttpBinding   
        receiveTimeout="00:00:01"  
    />  
</bindings>  
```  
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a><span data-ttu-id="f24eb-148">Konfigurowanie zachowania do zastosowania do usługi</span><span class="sxs-lookup"><span data-stu-id="f24eb-148">Configuring a Behavior to Apply to a Service</span></span>  
 <span data-ttu-id="f24eb-149">W poniższym przykładzie określone zachowanie jest skonfigurowany dla typu usługi.</span><span class="sxs-lookup"><span data-stu-id="f24eb-149">In the following example, a specific behavior is configured for the service type.</span></span> <span data-ttu-id="f24eb-150">`ServiceMetadataBehavior` Element służy do włączenia [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) wysłać zapytania do usługi i Generowanie dokumentów sieci Web Services Description Language (WSDL) z metadanych.</span><span class="sxs-lookup"><span data-stu-id="f24eb-150">The `ServiceMetadataBehavior` element is used to enable the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to query the service and generate Web Services Description Language (WSDL) documents from the metadata.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f24eb-151">Jeśli nadaj nazwę określonego zachowania, `behaviorConfiguration` określony w usłudze lub punkt końcowy musi odpowiadać sekcji.</span><span class="sxs-lookup"><span data-stu-id="f24eb-151">If you give a particular name to the behavior, the `behaviorConfiguration` specified in the service or endpoint section must match it.</span></span>  
  
```xml  
<behaviors>  
    <behavior>  
        <ServiceMetadata httpGetEnabled="true" />   
    </behavior>  
</behaviors>  
<services>  
    <service   
       name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
       <endpoint   
          address="http://computer:8080/Hello"  
          contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
          binding="basicHttpBinding" />  
       </endpoint>  
    </service>  
</services>  
```  
  
 <span data-ttu-id="f24eb-152">Poprzedniego umożliwia konfiguracji, kiedy klient wywołania w celu uzyskania metadanych "HelloWorld" wpisana usługi.</span><span class="sxs-lookup"><span data-stu-id="f24eb-152">The preceding configuration enables a client to call and get the metadata of the "HelloWorld" typed service.</span></span>  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a><span data-ttu-id="f24eb-153">Określanie usługi przy użyciu dwa punkty końcowe przy użyciu wartości inne powiązanie</span><span class="sxs-lookup"><span data-stu-id="f24eb-153">Specifying a Service with Two Endpoints Using Different Binding Values</span></span>  
 <span data-ttu-id="f24eb-154">W tym przykładzie ostatniego dwa punkty końcowe są skonfigurowane do `HelloWorld` typ usługi.</span><span class="sxs-lookup"><span data-stu-id="f24eb-154">In this last example, two endpoints are configured for the `HelloWorld` service type.</span></span> <span data-ttu-id="f24eb-155">Każdy punkt końcowy korzysta z innej dostosowane `bindingConfiguration` atrybut ten sam typ powiązania (każdego modyfikuje `basicHttpBinding`).</span><span class="sxs-lookup"><span data-stu-id="f24eb-155">Each endpoint uses a different customized  `bindingConfiguration` attribute of the same binding type (each modifies the `basicHttpBinding`).</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
    <endpoint  
        address="http://computer:8080/Hello1"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="shortTimeout"  
    </endpoint>  
    <endpoint  
        address="http://computer:8080/Hello2"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="Secure"  
     </endpoint>  
</service>  
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
  
 <span data-ttu-id="f24eb-156">Możesz uzyskać takie samo zachowanie używa konfiguracji domyślnej, dodając `protocolMapping` sekcji i konfigurowania powiązań, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f24eb-156">You can get the same behavior using the default configuration by adding a `protocolMapping` section and configuring the bindings as demonstrated in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f24eb-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f24eb-157">See Also</span></span>  
 [<span data-ttu-id="f24eb-158">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="f24eb-158">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="f24eb-159">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="f24eb-159">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)  
 [<span data-ttu-id="f24eb-160">Przegląd tworzenia punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="f24eb-160">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [<span data-ttu-id="f24eb-161">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="f24eb-161">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
