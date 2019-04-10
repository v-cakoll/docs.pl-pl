---
title: <system.serviceModel>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
ms.openlocfilehash: c176f7f470cc65bb135e5f92935102e09c7e8485
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209830"
---
# <a name="systemservicemodel"></a><span data-ttu-id="1d6b0-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1d6b0-102">\<system.serviceModel></span></span>
<span data-ttu-id="1d6b0-103">Ta sekcja konfiguracji zawiera wszystkie elementy konfiguracyjne ServiceModel Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1d6b0-103">This configuration section contains all the Windows Communication Foundation (WCF) ServiceModel configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d6b0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d6b0-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <behaviors>
  </behaviors>
  <bindings>
  </bindings>
  <client>
  </client>
  <comContracts>
  </comContracts>
  <commonBehaviors>
  </commonBehaviors>
  <diagnostics>
  </diagnostics>
  <extensions>
  </extensions>
  <protocolMapping>
  </protocolMapping>
  <routing>
  </routing>
  <serviceHostingEnvironment>
  </serviceHostingEnvironment>
  <services>
  </services>
  <standardEndpoints>
  </standardEndpoints>
  <tracking>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d6b0-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1d6b0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1d6b0-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d6b0-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1d6b0-107">Attributes</span></span>  
 <span data-ttu-id="1d6b0-108">Brak</span><span class="sxs-lookup"><span data-stu-id="1d6b0-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1d6b0-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1d6b0-109">Child Elements</span></span>  
  
|<span data-ttu-id="1d6b0-110">Element</span><span class="sxs-lookup"><span data-stu-id="1d6b0-110">Element</span></span>|<span data-ttu-id="1d6b0-111">Opis</span><span class="sxs-lookup"><span data-stu-id="1d6b0-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d6b0-112">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="1d6b0-112">\<behaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)|<span data-ttu-id="1d6b0-113">Ta sekcja definiuje dwie kolekcje elementów podrzędnych o nazwie `endpointBehaviors` i `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-113">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="1d6b0-114">Każdej kolekcji definiuje zachowanie elementy używane przez punkty końcowe i usługi, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-114">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="1d6b0-115">Każdy element zachowanie jest określony przez jego unikatowy `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-115">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[<span data-ttu-id="1d6b0-116">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="1d6b0-116">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="1d6b0-117">Ta sekcja przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-117">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="1d6b0-118">Każdy wpis jest określony przez jego unikatowy `name`.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-118">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="1d6b0-119">Usługi używają powiązania, łącząc je za pomocą `name`.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-119">Services use bindings by linking them using the `name`.</span></span>|  
|[<span data-ttu-id="1d6b0-120">\<client></span><span class="sxs-lookup"><span data-stu-id="1d6b0-120">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="1d6b0-121">Ta sekcja zawiera listę punktów końcowych, których klient używa do łączenia się z usługą.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-121">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[<span data-ttu-id="1d6b0-122">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="1d6b0-122">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|<span data-ttu-id="1d6b0-123">Ta sekcja definiuje kontrakty COM włączone dla usługi WCF i COM interop.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-123">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[<span data-ttu-id="1d6b0-124">\<commonBehaviors></span><span class="sxs-lookup"><span data-stu-id="1d6b0-124">\<commonBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|<span data-ttu-id="1d6b0-125">W tej sekcji można zdefiniować tylko w pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-125">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="1d6b0-126">Definiuje dwie kolekcje elementów podrzędnych o nazwie `endpointBehaviors` i `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-126">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="1d6b0-127">Każdej kolekcji definiuje zachowanie elementy używane przez wszystkie punkty końcowe WCF i usługi na maszynie, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-127">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="1d6b0-128">Jeśli to zachowanie jest zdefiniowany w obu `<commonBehaviors>` i `<behaviors>` sekcje zachowanie w \<zachowania > sekcji otrzymuje preferencji.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-128">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[<span data-ttu-id="1d6b0-129">\<Diagnostyka ></span><span class="sxs-lookup"><span data-stu-id="1d6b0-129">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="1d6b0-130">Ta sekcja zawiera ustawienia dla funkcji diagnostyki platformy WCF.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-130">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="1d6b0-131">Użytkownik mogą włączać i wyłączać śledzenia, liczniki wydajności i dostawcy WMI i można dodać niestandardowy komunikat filtrów.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-131">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[<span data-ttu-id="1d6b0-132">\<extensions></span><span class="sxs-lookup"><span data-stu-id="1d6b0-132">\<extensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|<span data-ttu-id="1d6b0-133">Ta sekcja zawiera Kolekcja rozszerzeń, które umożliwiają użytkownikowi utworzenie powiązań zdefiniowanych przez użytkownika, zachowania i inne aspekty rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-133">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[<span data-ttu-id="1d6b0-134">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="1d6b0-134">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="1d6b0-135">Ta sekcja definiuje zestaw domyślnego mapowania protokołu pomiędzy schematami protokołu transportu (np. http, net.tcp, net.pipe, itp.) i powiązaniami WCF.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-135">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[<span data-ttu-id="1d6b0-136">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="1d6b0-136">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="1d6b0-137">Ta sekcja definiuje zestaw filtrów routingu, które określają typ obiektu programu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu definiujące miejsce docelowe punktów końcowych, aby wysyłać komunikaty do kiedy tabele Filtr dopasowuje wartość.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-137">This section defines a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[<span data-ttu-id="1d6b0-138">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="1d6b0-138">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="1d6b0-139">Ta sekcja definiuje typ usługi, którą Środowisko hostingu środowiskowego dla danego transportu.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-139">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="1d6b0-140">Jeśli w tej sekcji jest pusta, używany jest domyślny typ.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-140">If this section is empty, the default type is used.</span></span>|  
|[<span data-ttu-id="1d6b0-141">\<services></span><span class="sxs-lookup"><span data-stu-id="1d6b0-141">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="1d6b0-142">Sekcja zawiera kolekcję usług.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-142">The section contains a collection of services.</span></span> <span data-ttu-id="1d6b0-143">Dla każdej usługi zdefiniowane w zestawie, ten element zawiera `service` element określający ustawienia usługi.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-143">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[<span data-ttu-id="1d6b0-144">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="1d6b0-144">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="1d6b0-145">Ta sekcja definiuje zbiór standardowych punktów końcowych, które są do ponownego użycia wstępnie skonfigurowanymi punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-145">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="1d6b0-146">Standardowy punkt końcowy będzie mieć jeden lub więcej adresów, powiązania i atrybuty kontraktu ustawiona na wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-146">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="1d6b0-147">Na przykład punkt końcowy odnajdywania kontrakt jest stała.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-147">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="1d6b0-148">Standardowe punkty końcowe umożliwia również rozszerzenie punkt końcowy usługi z nowymi właściwościami podobne do definiowania powiązań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-148">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|
|[<span data-ttu-id="1d6b0-149">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="1d6b0-149">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tracking-of-wcf.md)|<span data-ttu-id="1d6b0-150">Ta sekcja definiuje ustawienia śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-150">This section defines tracking settings for a workflow service.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1d6b0-151">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1d6b0-151">Parent Elements</span></span>  
  
|<span data-ttu-id="1d6b0-152">Element</span><span class="sxs-lookup"><span data-stu-id="1d6b0-152">Element</span></span>|<span data-ttu-id="1d6b0-153">Opis</span><span class="sxs-lookup"><span data-stu-id="1d6b0-153">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1d6b0-154">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="1d6b0-154">\<configuration></span></span>|<span data-ttu-id="1d6b0-155">Element główny dla wszystkich elementów konfiguracji w PLiku konfiguracji PLatformy .NET.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-155">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d6b0-156">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d6b0-156">Remarks</span></span>  
 <span data-ttu-id="1d6b0-157">Usługi WCF nie powoduje dodania elementów konfiguracji w sekcjach dotyczących innych produktów.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-157">WCF does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="1d6b0-158">Usługi WCF są zdefiniowane w `services` sekcję pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-158">WCF services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="1d6b0-159">Zestaw może zawierać dowolną liczbę usług.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-159">An assembly can contain any number of services.</span></span> <span data-ttu-id="1d6b0-160">Każda usługa ma swoje własne `service` sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-160">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="1d6b0-161">Sekcji i jego zawartości definiowanie kontraktu usługi, zachowanie i punktów końcowych określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-161">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="1d6b0-162">Tylko usługi `name` atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-162">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="1d6b0-163">Domyślnie, nazwa usługi w tym artykule opisano podstawowy typ środowiska CLR, używany do implementowania usługi; jednak Właściwość ConfigurationName może ulec zmianie po <xref:System.ServiceModel.ServiceContractAttribute> Aby przesłonić wymaganie typu CLR.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-163">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="1d6b0-164">`behaviorConfiguration` Atrybut jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-164">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="1d6b0-165">Identyfikuje zachowanie usługi, używanych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-165">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="1d6b0-166">Zachowanie określone przez atrybut ten należy połączyć zachowanie usługi zdefiniowane w zakresie tego samego pliku konfiguracji (tj. tego samego pliku lub pliku nadrzędnego).</span><span class="sxs-lookup"><span data-stu-id="1d6b0-166">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="1d6b0-167">Każda usługa udostępnia jedną lub więcej punktów końcowych zdefiniowanych w `endpoint` elementu.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-167">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="1d6b0-168">Każdy punkt końcowy ma swój własny adres i powiązanie.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-168">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="1d6b0-169">Wszystkie powiązania używane w pliku konfiguracyjnym musi być zdefiniowany w zakresie pliku.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-169">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="1d6b0-170">Powiązania są połączone z punktów końcowych za pomocą kombinacji atrybutów `name` i `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-170">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="1d6b0-171">`binding` Atrybut definiuje, w której sekcji zdefiniowano powiązania.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-171">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="1d6b0-172">`bindingConfiguration` Atrybut definiuje, które skonfigurowanego powiązania w ramach sekcji powiązania jest używany.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-172">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="1d6b0-173">Sekcja powiązania można zdefiniować kilka skonfigurowanego powiązania.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-173">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d6b0-174">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d6b0-174">Example</span></span>  
 <span data-ttu-id="1d6b0-175">To jest przykładowy plik konfiguracji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="1d6b0-175">This is an example of a WCF configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <!-- List of Behaviors -->
    </behaviors>
    <client>
      <!-- List of Endpoints -->
    </client>
    <diagnostics wmiProviderEnabled="false"
                 performanceCountersEnabled="false"
                 tracingEnabled="false">
    </diagnostics>
    <serviceHostingEnvironment>
      <!-- List of entries -->
    </serviceHostingEnvironment>
    <comContracts>
      <!-- List of COM+ Contracts -->
    </comContracts>
    <services>
      <!-- List of Services -->
    </services>
    <bindings>
      <!-- List of Bindings -->
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="1d6b0-176">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d6b0-176">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
