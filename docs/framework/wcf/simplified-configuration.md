---
title: Uproszczona konfiguracja
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 4e316290c045b75896c61e36c1646440c18678e2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249633"
---
# <a name="simplified-configuration"></a><span data-ttu-id="a833d-102">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="a833d-102">Simplified Configuration</span></span>
<span data-ttu-id="a833d-103">Konfigurowanie usług Windows Communication Foundation (WCF) może być złożonym zadaniem.</span><span class="sxs-lookup"><span data-stu-id="a833d-103">Configuring Windows Communication Foundation (WCF) services can be a complex task.</span></span> <span data-ttu-id="a833d-104">Istnieje wiele różnych opcji i nie zawsze jest łatwo określić, jakie ustawienia są wymagane.</span><span class="sxs-lookup"><span data-stu-id="a833d-104">There are many different options and it is not always easy to determine what settings are required.</span></span> <span data-ttu-id="a833d-105">Podczas gdy pliki konfiguracyjne zwiększają elastyczność usług WCF, są one również źródłem wielu trudnych do znalezienia problemów.</span><span class="sxs-lookup"><span data-stu-id="a833d-105">While configuration files increase the flexibility of WCF services, they also are the source for many hard to find problems.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="a833d-106">rozwiązuje te problemy i zapewnia sposób zmniejszenia rozmiaru i złożoności konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="a833d-106">addresses these problems and provides a way to reduce the size and complexity of service configuration.</span></span>  
  
## <a name="simplified-configuration"></a><span data-ttu-id="a833d-107">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="a833d-107">Simplified Configuration</span></span>  
 <span data-ttu-id="a833d-108">W plikach konfiguracyjnych usługi WCF sekcja <`system.serviceModel`> zawiera <`service`> element dla każdej hostowanej usługi.</span><span class="sxs-lookup"><span data-stu-id="a833d-108">In WCF service configuration files, the <`system.serviceModel`> section contains a <`service`> element for each service hosted.</span></span> <span data-ttu-id="a833d-109"><`service`> element zawiera kolekcję <`endpoint`> elementów, które określają punkty końcowe udostępniane dla każdej usługi i opcjonalnie zestaw zachowań usługi.</span><span class="sxs-lookup"><span data-stu-id="a833d-109">The <`service`> element contains a collection of <`endpoint`> elements that specify the endpoints exposed for each service and optionally a set of service behaviors.</span></span> <span data-ttu-id="a833d-110">Elementy <`endpoint`> określają adres, powiązanie i kontrakt udostępniane przez punkt końcowy oraz opcjonalnie powiązanie zachowań konfiguracji i punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a833d-110">The <`endpoint`> elements specify the address, binding, and contract exposed by the endpoint, and optionally binding configuration and endpoint behaviors.</span></span> <span data-ttu-id="a833d-111">Sekcja `system.serviceModel` <> zawiera również element `behaviors`> <, który umożliwia określenie zachowań usługi lub punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a833d-111">The <`system.serviceModel`> section also contains a <`behaviors`> element that allows you to specify service or endpoint behaviors.</span></span> <span data-ttu-id="a833d-112">W poniższym przykładzie przedstawiono sekcję `system.serviceModel`> <pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="a833d-112">The following example shows the <`system.serviceModel`> section of a configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true" />  
        <serviceDebug includeExceptionDetailInFaults="false" />  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="a833d-113">ułatwia konfigurowanie usługi WCF przez usunięcie wymagań dotyczących elementu `service` <>.</span><span class="sxs-lookup"><span data-stu-id="a833d-113">makes configuring a WCF service easier by removing the requirement for the <`service`> element.</span></span> <span data-ttu-id="a833d-114">Jeśli nie dodasz <`service` sekcji> lub nie dodasz żadnych punktów końcowych `service` w sekcji <>, a usługa nie definiuje programowo żadnych punktów końcowych, zestaw domyślnych punktów końcowych zostanie automatycznie dodany do usługi, po jednym dla każdego adresu podstawowego usługi i dla każdej umowy zaimplementowanej przez usługę.</span><span class="sxs-lookup"><span data-stu-id="a833d-114">If you do not add a <`service`>  section or add any endpoints in a <`service`> section and your service does not programmatically define any endpoints, then a set of default endpoints are automatically added to your service, one for each service base address and for each contract implemented by your service.</span></span> <span data-ttu-id="a833d-115">W każdym z tych punktów końcowych adres punktu końcowego odpowiada adres podstawowy, powiązanie jest określana przez schemat adresów podstawowych i umowy jest zaimplementowane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="a833d-115">In each of these endpoints, the endpoint address corresponds to the base address, the binding is determined by the base address scheme and the contract is the one implemented by your service.</span></span> <span data-ttu-id="a833d-116">Jeśli nie trzeba określić żadnych punktów końcowych lub zachowań usługi lub wprowadzić żadnych zmian ustawień powiązania, nie trzeba w ogóle określić plik konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="a833d-116">If you do not need to specify any endpoints or service behaviors or make any binding setting changes, you do not need to specify a service configuration file at all.</span></span> <span data-ttu-id="a833d-117">Jeśli usługa implementuje dwa kontrakty i hosta włącza transporty HTTP i TCP hosta usługi tworzy cztery domyślne punkty końcowe, po jednym dla każdego kontraktu przy użyciu każdego transportu.</span><span class="sxs-lookup"><span data-stu-id="a833d-117">If a service implements two contracts and the host enables both HTTP and TCP transports the service host creates four default endpoints, one for each contract using each transport.</span></span> <span data-ttu-id="a833d-118">Aby utworzyć domyślne punkty końcowe hosta usługi musi wiedzieć, jakie powiązania do użycia.</span><span class="sxs-lookup"><span data-stu-id="a833d-118">To create default endpoints the service host must know what bindings to use.</span></span> <span data-ttu-id="a833d-119">Te ustawienia są określone w `protocolMappings` sekcji> <w sekcji `system.serviceModel` <>.</span><span class="sxs-lookup"><span data-stu-id="a833d-119">These settings are specified in a <`protocolMappings`> section within the <`system.serviceModel`> section.</span></span> <span data-ttu-id="a833d-120">Sekcja <`protocolMappings`> zawiera listę schematów protokołu transportu mapowanych na typy powiązań.</span><span class="sxs-lookup"><span data-stu-id="a833d-120">The <`protocolMappings`> section contains a list of transport protocol schemes mapped to binding types.</span></span> <span data-ttu-id="a833d-121">Host usługi używa adresów podstawowych przekazanych do niego, aby określić, które powiązanie do użycia.</span><span class="sxs-lookup"><span data-stu-id="a833d-121">The service host uses the base addresses passed to it to determine which binding to use.</span></span> <span data-ttu-id="a833d-122">W poniższym przykładzie użyto <`protocolMappings`> elementu.</span><span class="sxs-lookup"><span data-stu-id="a833d-122">The following example uses the <`protocolMappings`> element.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="a833d-123">Zmiana domyślnych elementów konfiguracji, takich jak powiązania lub zachowania, może mieć wpływ na usługi zdefiniowane na niższych poziomach hierarchii konfiguracji, ponieważ mogą one używać tych domyślnych powiązań i zachowań.</span><span class="sxs-lookup"><span data-stu-id="a833d-123">Changing default configuration elements, such as bindings or behaviors, might affect services defined in lower levels of the configuration hierarchy, since they might be using these default bindings and behaviors.</span></span> <span data-ttu-id="a833d-124">W związku z tym kto zmienia domyślne powiązania i zachowania musi mieć świadomość, że te zmiany mogą mieć wpływ na inne usługi w hierarchii.</span><span class="sxs-lookup"><span data-stu-id="a833d-124">Thus, whoever changes default bindings and behaviors needs to be aware that these changes might affect other services in the hierarchy.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a833d-125">Usługi hostowane w ramach internetowych usług informacyjnych (IIS) lub usługi aktywacji procesów systemu Windows (WAS) używają katalogu wirtualnego jako adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="a833d-125">Services hosted under Internet Information Services (IIS) or Windows Process Activation Service (WAS) use the virtual directory as their base address.</span></span>  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 <span data-ttu-id="a833d-126">W poprzednim przykładzie punkt końcowy z adresem podstawowym, który rozpoczyna się <xref:System.ServiceModel.BasicHttpBinding>od schematu "http", używa programu .</span><span class="sxs-lookup"><span data-stu-id="a833d-126">In the previous example, an endpoint with a base address that starts with the "http" scheme uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="a833d-127">Punkt końcowy z adresem podstawowym rozpoczynającym się od schematu "net.tcp" używa schematu <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="a833d-127">An endpoint with a base address that starts with the "net.tcp" scheme uses the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="a833d-128">Ustawienia można zastąpić w lokalnym pliku App.config lub Web.config.</span><span class="sxs-lookup"><span data-stu-id="a833d-128">You can override settings in a local App.config or Web.config file.</span></span>  
  
 <span data-ttu-id="a833d-129">Każdy element w sekcji `protocolMappings` <> musi określać schemat i powiązanie.</span><span class="sxs-lookup"><span data-stu-id="a833d-129">Each element within the <`protocolMappings`> section must specify a scheme and a binding.</span></span> <span data-ttu-id="a833d-130">Opcjonalnie można określić `bindingConfiguration` atrybut, który określa konfigurację powiązania `bindings` w <> sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a833d-130">Optionally it can specify a `bindingConfiguration` attribute that specifies a binding configuration within the <`bindings`> section of the configuration file.</span></span> <span data-ttu-id="a833d-131">Jeśli `bindingConfiguration` nie jest określony, używana jest konfiguracja powiązania anonimowego odpowiedniego typu powiązania.</span><span class="sxs-lookup"><span data-stu-id="a833d-131">If no `bindingConfiguration` is specified, the anonymous binding configuration of the appropriate binding type is used.</span></span>  
  
 <span data-ttu-id="a833d-132">Zachowania usługi są konfigurowane dla domyślnych punktów końcowych `behavior` przy użyciu anonimowych <sekcji `serviceBehaviors`> w <> sekcjach.</span><span class="sxs-lookup"><span data-stu-id="a833d-132">Service behaviors are configured for the default endpoints by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span> <span data-ttu-id="a833d-133">Wszystkie nienazwane <`behavior`> elementy w <`serviceBehaviors`> są używane do konfigurowania zachowań usługi.</span><span class="sxs-lookup"><span data-stu-id="a833d-133">Any unnamed <`behavior`> elements within <`serviceBehaviors`> are used to configure service behaviors.</span></span> <span data-ttu-id="a833d-134">Na przykład następujący plik konfiguracji umożliwia publikowanie metadanych usługi dla wszystkich usług w hoście.</span><span class="sxs-lookup"><span data-stu-id="a833d-134">For example, the following configuration file enables service metadata publishing for all services within the host.</span></span>  
  
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
  
 <span data-ttu-id="a833d-135">Zachowania punktów końcowych są konfigurowane przy `behavior` użyciu anonimowych <> sekcje `serviceBehaviors` w <> sekcjach.</span><span class="sxs-lookup"><span data-stu-id="a833d-135">Endpoint behaviors are configured by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span>  
  
 <span data-ttu-id="a833d-136">Poniższy przykład jest plikiem konfiguracji równoważnym z plikiem na początku tego tematu, który używa uproszczonego modelu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a833d-136">The following example is a configuration file equivalent to the one at the beginning of this topic that uses the simplified configuration model.</span></span>  
  
```xml  
<system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="true" />
          <serviceDebug includeExceptionDetailInFaults="false" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <bindings>
       <basicHttpBinding>
          <binding maxBufferSize="100"
                   maxReceiveBufferSize="100" />
       </basicHttpBinding>
    </bindings>
    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->
    <!-- The service behavior with name="" will be picked up by the service -->
    <protocolMapping>
      <add scheme="http" binding="basicHttpBinding" />
  </protocolMapping>
  </system.serviceModel>
```  
  
> [!IMPORTANT]
> <span data-ttu-id="a833d-137">Ta funkcja dotyczy tylko konfiguracji usługi WCF, a nie konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="a833d-137">This feature relates only to WCF service configuration, not client configuration.</span></span> <span data-ttu-id="a833d-138">W większości razy konfiguracja klienta WCF zostanie wygenerowana przez narzędzie, takie jak svcutil.exe lub dodanie odwołania do usługi z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a833d-138">Most times, WCF client configuration will be generated by a tool such as svcutil.exe or adding a service reference from Visual Studio.</span></span> <span data-ttu-id="a833d-139">Jeśli ręcznie konfigurujesz klienta WCF, musisz dodać \<element> klienta do konfiguracji i określić wszystkie punkty końcowe, które chcesz wywołać.</span><span class="sxs-lookup"><span data-stu-id="a833d-139">If you are manually configuring a WCF client you will need to add a \<client> element to the configuration and specify any endpoints you wish to call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a833d-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a833d-140">See also</span></span>

- [<span data-ttu-id="a833d-141">Konfigurowanie usług za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a833d-141">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)
- [<span data-ttu-id="a833d-142">Konfigurowanie powiązań dla usług</span><span class="sxs-lookup"><span data-stu-id="a833d-142">Configuring Bindings for Services</span></span>](configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="a833d-143">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="a833d-143">Configuring System-Provided Bindings</span></span>](./feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a833d-144">Konfigurowanie usług</span><span class="sxs-lookup"><span data-stu-id="a833d-144">Configuring Services</span></span>](configuring-services.md)
- [<span data-ttu-id="a833d-145">Konfigurowanie usług WCF</span><span class="sxs-lookup"><span data-stu-id="a833d-145">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="a833d-146">Konfigurowanie usług WCF w kodzie</span><span class="sxs-lookup"><span data-stu-id="a833d-146">Configuring WCF Services in Code</span></span>](configuring-wcf-services-in-code.md)
