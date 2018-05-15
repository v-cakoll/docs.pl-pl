---
title: Uproszczona konfiguracja
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 9f35a5f4fa4ae6be63bd75a24f58b56dd236ee9c
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="simplified-configuration"></a><span data-ttu-id="eeb97-102">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="eeb97-102">Simplified Configuration</span></span>
<span data-ttu-id="eeb97-103">Konfigurowanie usług Windows Communication Foundation (WCF) może być złożonym zadaniem.</span><span class="sxs-lookup"><span data-stu-id="eeb97-103">Configuring Windows Communication Foundation (WCF) services can be a complex task.</span></span> <span data-ttu-id="eeb97-104">Istnieje wiele różnych opcji, a nie zawsze jest łatwa do ustalenia, jakie ustawienia są wymagane.</span><span class="sxs-lookup"><span data-stu-id="eeb97-104">There are many different options and it is not always easy to determine what settings are required.</span></span> <span data-ttu-id="eeb97-105">Podczas konfiguracji plików zwiększyć elastyczność usług WCF, są one również źródła dla wielu trudne do znalezienia problemów.</span><span class="sxs-lookup"><span data-stu-id="eeb97-105">While configuration files increase the flexibility of WCF services, they also are the source for many hard to find problems.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="eeb97-106"> te problemy zostały rozwiązane oraz przedstawiono sposób, aby zmniejszyć rozmiar i złożoność konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="eeb97-106"> addresses these problems and provides a way to reduce the size and complexity of service configuration.</span></span>  
  
## <a name="simplified-configuration"></a><span data-ttu-id="eeb97-107">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="eeb97-107">Simplified Configuration</span></span>  
 <span data-ttu-id="eeb97-108">W plikach konfiguracji usługi WCF <`system.serviceModel`> zawiera sekcji <`service`> element dla każdej usługi hostowanej.</span><span class="sxs-lookup"><span data-stu-id="eeb97-108">In WCF service configuration files, the <`system.serviceModel`> section contains a <`service`> element for each service hosted.</span></span> <span data-ttu-id="eeb97-109"><`service`> Kolekcja zawiera element <`endpoint`> elementy, które określ punkty końcowe udostępniane dla każdej usługi i opcjonalnie zestaw zachowań usługi.</span><span class="sxs-lookup"><span data-stu-id="eeb97-109">The <`service`> element contains a collection of <`endpoint`> elements that specify the endpoints exposed for each service and optionally a set of service behaviors.</span></span> <span data-ttu-id="eeb97-110"><`endpoint`> Elementy Podaj adres, powiązanie, i kontraktu udostępniane przez punkt końcowy i opcjonalnie powiązania konfiguracji i zachowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="eeb97-110">The <`endpoint`> elements specify the address, binding, and contract exposed by the endpoint, and optionally binding configuration and endpoint behaviors.</span></span> <span data-ttu-id="eeb97-111"><`system.serviceModel`> Sekcja zawiera również <`behaviors`> element, który pozwala na określenie zachowania usługi lub punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="eeb97-111">The <`system.serviceModel`> section also contains a <`behaviors`> element that allows you to specify service or endpoint behaviors.</span></span> <span data-ttu-id="eeb97-112">W poniższym przykładzie przedstawiono <`system.serviceModel`> pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="eeb97-112">The following example shows the <`system.serviceModel`> section of a configuration file.</span></span>  
  
```  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true">  
        <serviceDebug includeExceptionDetailInFaults="false">  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <bindings>  
   <basicHttpBinding>  
      <binding name=MyBindingConfig"  
               maxBufferSize="100"  
               maxReceiveBufferSize="100" />  
   </basicHttpBinding>  
   </bindings>   <services>  
    <service behaviorConfiguration="MyServiceBehavior"  
             name="MyService">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                contract="ICalculator"  
                bindingConfiguration="MyBindingConfig" />  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange"/>  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="eeb97-113"> Umożliwia konfigurowanie usługi WCF łatwiejsze usuwając konieczność <`service`> elementu.</span><span class="sxs-lookup"><span data-stu-id="eeb97-113"> makes configuring a WCF service easier by removing the requirement for the <`service`> element.</span></span> <span data-ttu-id="eeb97-114">Jeśli nie dodasz <`service`> sekcji lub dodać żadnych punktów końcowych w <`service`> sekcji, a usługą nie programowo definiuje żadnych punktów końcowych, a następnie zestaw domyślnych punktów końcowych są automatycznie dodawane do usługi, po jednej dla każdego adres podstawowy usługi i dla każdej umowy zaimplementowana przez usługę.</span><span class="sxs-lookup"><span data-stu-id="eeb97-114">If you do not add a <`service`>  section or add any endpoints in a <`service`> section and your service does not programmatically define any endpoints, then a set of default endpoints are automatically added to your service, one for each service base address and for each contract implemented by your service.</span></span> <span data-ttu-id="eeb97-115">W każdym z tych punktów końcowych odpowiada adres podstawowy adres punktu końcowego, powiązania jest określany przez adres podstawowy schemat i kontrakt jest implementowany przez usługę.</span><span class="sxs-lookup"><span data-stu-id="eeb97-115">In each of these endpoints, the endpoint address corresponds to the base address, the binding is determined by the base address scheme and the contract is the one implemented by your service.</span></span> <span data-ttu-id="eeb97-116">Nie trzeba określać żadnych punktów końcowych lub zachowania usługi lub zmiany ustawienia powiązania, nie trzeba określić cały plik konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="eeb97-116">If you do not need to specify any endpoints or service behaviors or make any binding setting changes, you do not need to specify a service configuration file at all.</span></span> <span data-ttu-id="eeb97-117">Jeśli zaimplementowano dwa kontrakty i hosta umożliwia transportu HTTP i TCP hosta usługi tworzy cztery domyślne punkty końcowe, jeden dla każdej umowy każdego transportu.</span><span class="sxs-lookup"><span data-stu-id="eeb97-117">If a service implements two contracts and the host enables both HTTP and TCP transports the service host creates four default endpoints, one for each contract using each transport.</span></span> <span data-ttu-id="eeb97-118">Aby utworzyć domyślne punkty końcowe usługi hosta musi znać jakie powiązania do użycia.</span><span class="sxs-lookup"><span data-stu-id="eeb97-118">To create default endpoints the service host must know what bindings to use.</span></span> <span data-ttu-id="eeb97-119">Te ustawienia są określone w <`protocolMappings`> sekcji w <`system.serviceModel`> sekcji.</span><span class="sxs-lookup"><span data-stu-id="eeb97-119">These settings are specified in a <`protocolMappings`> section within the <`system.serviceModel`> section.</span></span> <span data-ttu-id="eeb97-120"><`protocolMappings`> Sekcja zawiera listę zamapowane na typy powiązanie schematami protokołu transportu.</span><span class="sxs-lookup"><span data-stu-id="eeb97-120">The <`protocolMappings`> section contains a list of transport protocol schemes mapped to binding types.</span></span> <span data-ttu-id="eeb97-121">Host usługi używa adres podstawowy przekazywania w celu określenia powiązania, które do użycia.</span><span class="sxs-lookup"><span data-stu-id="eeb97-121">The service host uses the base addresses passed to it to determine which binding to use.</span></span> <span data-ttu-id="eeb97-122">W poniższym przykładzie użyto <`protocolMappings`> elementu.</span><span class="sxs-lookup"><span data-stu-id="eeb97-122">The following example uses the <`protocolMappings`> element.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="eeb97-123">Zmiana domyślnego elementów konfiguracji, takich jak powiązania lub zachowania, może mieć wpływ na usługi zdefiniowane w niższych poziomach hierarchii konfiguracji, ponieważ może korzystać z tych powiązań domyślne i zachowania.</span><span class="sxs-lookup"><span data-stu-id="eeb97-123">Changing default configuration elements, such as bindings or behaviors, might affect services defined in lower levels of the configuration hierarchy, since they might be using these default bindings and behaviors.</span></span> <span data-ttu-id="eeb97-124">W związku z tym, kto zmiany domyślnego powiązania i zachowania musi należy pamiętać, że te zmiany mogą mieć wpływ na inne usługi w hierarchii.</span><span class="sxs-lookup"><span data-stu-id="eeb97-124">Thus, whoever changes default bindings and behaviors needs to be aware that these changes might affect other services in the hierarchy.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eeb97-125">Usługi hostowanej przez usługi Internet Information Services (IIS) lub usługi aktywacji procesów systemu Windows (WAS) Użyj katalogu wirtualnego jako ich adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="eeb97-125">Services hosted under Internet Information Services (IIS) or Windows Process Activation Service (WAS) use the virtual directory as their base address.</span></span>  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 <span data-ttu-id="eeb97-126">W poprzednim przykładzie, punkt końcowy z adres podstawowy, który rozpoczyna się od schematu "http" używa <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="eeb97-126">In the previous example, an endpoint with a base address that starts with the "http" scheme uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="eeb97-127">Punkt końcowy z adres podstawowy, który rozpoczyna się od schematu "net.tcp" używa <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="eeb97-127">An endpoint with a base address that starts with the "net.tcp" scheme uses the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="eeb97-128">Można zastąpić ustawienia w lokalnym pliku App.config lub Web.config.</span><span class="sxs-lookup"><span data-stu-id="eeb97-128">You can override settings in a local App.config or Web.config file.</span></span>  
  
 <span data-ttu-id="eeb97-129">Każdy element <`protocolMappings`> sekcji, należy określić schemat i powiązania.</span><span class="sxs-lookup"><span data-stu-id="eeb97-129">Each element within the <`protocolMappings`> section must specify a scheme and a binding.</span></span> <span data-ttu-id="eeb97-130">Opcjonalnie można określić `bindingConfiguration` atrybut, który określa konfigurację powiązania w <`bindings`> pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="eeb97-130">Optionally it can specify a `bindingConfiguration` attribute that specifies a binding configuration within the <`bindings`> section of the configuration file.</span></span> <span data-ttu-id="eeb97-131">Jeśli nie `bindingConfiguration` jest określony, używana jest Konfiguracja wiązań anonimowych typu odpowiednie powiązania.</span><span class="sxs-lookup"><span data-stu-id="eeb97-131">If no `bindingConfiguration` is specified, the anonymous binding configuration of the appropriate binding type is used.</span></span>  
  
 <span data-ttu-id="eeb97-132">Zachowania usług są skonfigurowane dla domyślnych punktów końcowych przy użyciu anonimowego <`behavior`> sekcje w <`serviceBehaviors`> sekcji.</span><span class="sxs-lookup"><span data-stu-id="eeb97-132">Service behaviors are configured for the default endpoints by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span> <span data-ttu-id="eeb97-133">Wszelkie nienazwane <`behavior`> elementów w obrębie <`serviceBehaviors`> są używane do konfigurowania zachowań usługi.</span><span class="sxs-lookup"><span data-stu-id="eeb97-133">Any unnamed <`behavior`> elements within <`serviceBehaviors`> are used to configure service behaviors.</span></span> <span data-ttu-id="eeb97-134">Na przykład następujący plik konfiguracji umożliwia publikowanie metadanych usługi dla wszystkich usług w ramach hosta.</span><span class="sxs-lookup"><span data-stu-id="eeb97-134">For example, the following configuration file enables service metadata publishing for all services within the host.</span></span>  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <!-- No <service> tag is necessary. Default endpoints are added to the service -->  
    <!-- The service behavior with name="" is picked up by the service -->  
 </system.serviceModel>  
```  
  
 <span data-ttu-id="eeb97-135">Zachowania punktu końcowego są konfigurowane przy użyciu anonimowego <`behavior`> sekcje w <`serviceBehaviors`> sekcji.</span><span class="sxs-lookup"><span data-stu-id="eeb97-135">Endpoint behaviors are configured by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span>  
  
 <span data-ttu-id="eeb97-136">Poniższy przykład jest odpowiednikiem jeden na początku tego tematu, który korzysta z modelu uproszczona konfiguracja pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="eeb97-136">The following example is a configuration file equivalent to the one at the beginning of this topic that uses the simplified configuration model.</span></span>  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <bindings>  
       <basicHttpBinding>  
          <binding maxBufferSize="100"  
                   maxReceiveBufferSize="100" />  
       </basicHttpBinding>  
    </bindings>    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->  
    <!-- The service behavior with name="" will be picked up by the service -->  
    <protocolMapping>  
      <add scheme="http"     binding="basicHttpBinding" / </protocolMapping>  
  </system.serviceModel>  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="eeb97-137">Ta funkcja odnosi się tylko do konfiguracji usługi WCF nie konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="eeb97-137">This feature relates only to WCF service configuration, not client configuration.</span></span> <span data-ttu-id="eeb97-138">Większość razy Konfiguracja klienta WCF będą generowane przez narzędzia, takiego jak svcutil.exe lub dodanie odwołania do usługi z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eeb97-138">Most times, WCF client configuration will be generated by a tool such as svcutil.exe or adding a service reference from Visual Studio.</span></span> <span data-ttu-id="eeb97-139">W przypadku ręcznego konfigurowania klienta programu WCF należy dodać \<klienta > elementu konfiguracji i określ żadnych punktów końcowych, które chcesz wywołać.</span><span class="sxs-lookup"><span data-stu-id="eeb97-139">If you are manually configuring a WCF client you will need to add a \<client> element to the configuration and specify any endpoints you wish to call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeb97-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eeb97-140">See Also</span></span>  
 [<span data-ttu-id="eeb97-141">Konfigurowanie usług za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="eeb97-141">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [<span data-ttu-id="eeb97-142">Konfigurowanie powiązań dla usług</span><span class="sxs-lookup"><span data-stu-id="eeb97-142">Configuring Bindings for Services</span></span>](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 [<span data-ttu-id="eeb97-143">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="eeb97-143">Configuring System-Provided Bindings</span></span>](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="eeb97-144">Konfigurowanie usług</span><span class="sxs-lookup"><span data-stu-id="eeb97-144">Configuring Services</span></span>](../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="eeb97-145">Konfigurowanie systemu Windows Communication Foundation aplikacji</span><span class="sxs-lookup"><span data-stu-id="eeb97-145">Configuring Windows Communication Foundation Applications</span></span>](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [<span data-ttu-id="eeb97-146">Konfigurowanie usług WCF w kodzie</span><span class="sxs-lookup"><span data-stu-id="eeb97-146">Configuring WCF Services in Code</span></span>](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)
