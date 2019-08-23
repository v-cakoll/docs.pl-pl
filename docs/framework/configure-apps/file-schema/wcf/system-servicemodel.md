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
ms.openlocfilehash: 4fa6916437bb569029efe270ba8296703d89c539
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938917"
---
# <a name="systemservicemodel"></a><span data-ttu-id="2c0f3-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2c0f3-102">\<system.serviceModel></span></span>
<span data-ttu-id="2c0f3-103">Ta sekcja konfiguracji zawiera wszystkie elementy konfiguracji programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2c0f3-103">This configuration section contains all the Windows Communication Foundation (WCF) ServiceModel configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c0f3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c0f3-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c0f3-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2c0f3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2c0f3-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c0f3-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2c0f3-107">Attributes</span></span>  
 <span data-ttu-id="2c0f3-108">Brak</span><span class="sxs-lookup"><span data-stu-id="2c0f3-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2c0f3-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2c0f3-109">Child Elements</span></span>  
  
|<span data-ttu-id="2c0f3-110">Element</span><span class="sxs-lookup"><span data-stu-id="2c0f3-110">Element</span></span>|<span data-ttu-id="2c0f3-111">Opis</span><span class="sxs-lookup"><span data-stu-id="2c0f3-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c0f3-112">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="2c0f3-112">\<behaviors></span></span>](behaviors.md)|<span data-ttu-id="2c0f3-113">Ta sekcja definiuje dwie kolekcje podrzędne o `endpointBehaviors` nazwach i `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-113">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="2c0f3-114">Każda kolekcja definiuje elementy zachowań używane odpowiednio przez punkty końcowe i usługi.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-114">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="2c0f3-115">Każdy element zachowanie jest określony przez jego unikatowy `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-115">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[<span data-ttu-id="2c0f3-116">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="2c0f3-116">\<bindings></span></span>](bindings.md)|<span data-ttu-id="2c0f3-117">Ta sekcja zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-117">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="2c0f3-118">Każdy wpis jest identyfikowany przez jego `name`unikatowy.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-118">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="2c0f3-119">Usługi używają powiązań przez łączenie ich przy użyciu `name`.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-119">Services use bindings by linking them using the `name`.</span></span>|  
|[<span data-ttu-id="2c0f3-120">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="2c0f3-120">\<client></span></span>](client.md)|<span data-ttu-id="2c0f3-121">Ta sekcja zawiera listę punktów końcowych używanych przez klienta do nawiązywania połączenia z usługą.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-121">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[<span data-ttu-id="2c0f3-122">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="2c0f3-122">\<comContracts></span></span>](comcontracts.md)|<span data-ttu-id="2c0f3-123">Ta sekcja zawiera definicje umów COM włączonych dla usług WCF i współdziałania z modelem COM.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-123">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[<span data-ttu-id="2c0f3-124">\<commonBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2c0f3-124">\<commonBehaviors></span></span>](commonbehaviors.md)|<span data-ttu-id="2c0f3-125">Tę sekcję można zdefiniować tylko w pliku Machine. config.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-125">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="2c0f3-126">Definiuje dwie kolekcje podrzędne o `endpointBehaviors` nazwach `serviceBehaviors`i.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-126">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="2c0f3-127">Każda kolekcja definiuje elementy zachowań używane przez wszystkie punkty końcowe i usługi WCF odpowiednio na maszynie.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-127">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="2c0f3-128">Jeśli zachowanie jest zdefiniowane w obu `<commonBehaviors>` `<behaviors>` sekcjach \<, zachowanie w sekcji zachowań > ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-128">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[<span data-ttu-id="2c0f3-129">\<> diagnostyki</span><span class="sxs-lookup"><span data-stu-id="2c0f3-129">\<diagnostics></span></span>](diagnostics.md)|<span data-ttu-id="2c0f3-130">Ta sekcja zawiera ustawienia funkcji diagnostyki WCF.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-130">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="2c0f3-131">Użytkownik może włączyć/wyłączyć śledzenie, liczniki wydajności i dostawcę WMI, a także może dodawać niestandardowe filtry komunikatów.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-131">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[<span data-ttu-id="2c0f3-132">\<> rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="2c0f3-132">\<extensions></span></span>](extensions-section.md)|<span data-ttu-id="2c0f3-133">Ta sekcja zawiera kolekcję rozszerzeń, które umożliwiają użytkownikowi tworzenie powiązań zdefiniowanych przez użytkownika, zachowań i innych aspektów rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-133">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[<span data-ttu-id="2c0f3-134">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="2c0f3-134">\<protocolMapping></span></span>](protocolmapping.md)|<span data-ttu-id="2c0f3-135">Ta sekcja definiuje zestaw domyślnego mapowania protokołów między schematami protokołu transportowego (np. http, net. TCP, net. pipe itp.) i powiązania WCF.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-135">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[<span data-ttu-id="2c0f3-136">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="2c0f3-136">\<routing></span></span>](routing.md)|<span data-ttu-id="2c0f3-137">Ta sekcja definiuje zestaw filtrów routingu, które określają typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , który ma być używany podczas oceniania wiadomości przychodzących, a także tabele routingu definiujące docelowe punkty końcowe do wysyłania komunikatów, gdy filtruje dopasowania.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-137">This section defines a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[<span data-ttu-id="2c0f3-138">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="2c0f3-138">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="2c0f3-139">W tej sekcji zdefiniowano typ tworzenia wystąpień środowiska hostingu usługi dla określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-139">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="2c0f3-140">Jeśli ta sekcja jest pusta, używany jest typ domyślny.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-140">If this section is empty, the default type is used.</span></span>|  
|[<span data-ttu-id="2c0f3-141">\<> usług</span><span class="sxs-lookup"><span data-stu-id="2c0f3-141">\<services></span></span>](services.md)|<span data-ttu-id="2c0f3-142">Sekcja zawiera kolekcję usług.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-142">The section contains a collection of services.</span></span> <span data-ttu-id="2c0f3-143">Dla każdej usługi zdefiniowanej w zestawie ten element zawiera `service` element określający ustawienia dla usługi.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-143">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[<span data-ttu-id="2c0f3-144">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="2c0f3-144">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="2c0f3-145">Ta sekcja definiuje zbiór standardowych punktów końcowych, które są wstępnie skonfigurowanymi punktami końcowymi wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-145">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="2c0f3-146">Standardowy punkt końcowy będzie miał co najmniej jeden atrybut Address, Binding i Contract ustawiony na wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-146">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="2c0f3-147">Na przykład w punkcie końcowym odnajdywania kontrakt jest ustalony.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-147">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="2c0f3-148">Możesz również użyć standardowych punktów końcowych, aby zwiększyć punkt końcowy usługi z nowymi właściwościami podobnymi do definiowania powiązań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-148">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|
|[<span data-ttu-id="2c0f3-149">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="2c0f3-149">\<tracking></span></span>](tracking-of-wcf.md)|<span data-ttu-id="2c0f3-150">W tej sekcji zdefiniowano ustawienia śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-150">This section defines tracking settings for a workflow service.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2c0f3-151">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2c0f3-151">Parent Elements</span></span>  
  
|<span data-ttu-id="2c0f3-152">Element</span><span class="sxs-lookup"><span data-stu-id="2c0f3-152">Element</span></span>|<span data-ttu-id="2c0f3-153">Opis</span><span class="sxs-lookup"><span data-stu-id="2c0f3-153">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2c0f3-154">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2c0f3-154">\<configuration></span></span>|<span data-ttu-id="2c0f3-155">Element główny dla wszystkich elementów konfiguracji w PLiku konfiguracji PLatformy .NET.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-155">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c0f3-156">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2c0f3-156">Remarks</span></span>  
 <span data-ttu-id="2c0f3-157">Funkcja WCF nie dodaje elementów do sekcji konfiguracji innych produktów.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-157">WCF does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="2c0f3-158">Usługi WCF są zdefiniowane w `services` sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-158">WCF services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="2c0f3-159">Zestaw może zawierać dowolną liczbę usług.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-159">An assembly can contain any number of services.</span></span> <span data-ttu-id="2c0f3-160">Każda usługa ma swoją własną `service` sekcję konfiguracyjną.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-160">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="2c0f3-161">Sekcja i jej zawartość definiują kontrakt usługi, zachowanie i punkty końcowe określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-161">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="2c0f3-162">Wymagany jest tylko `name` atrybut usługi.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-162">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="2c0f3-163">Domyślnie nazwa usługi opisuje źródłowy typ CLR używany do implementowania usługi. można jednak zmienić właściwość ConfigurationName w <xref:System.ServiceModel.ServiceContractAttribute> celu zastąpienia wymagania dotyczącego typu CLR.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-163">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="2c0f3-164">`behaviorConfiguration` Atrybut jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-164">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="2c0f3-165">Identyfikuje zachowanie usługi używane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-165">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="2c0f3-166">Zachowanie określone przez ten atrybut musi łączyć się z zachowaniem usługi zdefiniowanym w zakresie tego samego pliku konfiguracji (tj. tym samym lub plikiem nadrzędnym).</span><span class="sxs-lookup"><span data-stu-id="2c0f3-166">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="2c0f3-167">Każda usługa ujawnia jeden lub więcej punktów końcowych zdefiniowanych `endpoint` w elemencie.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-167">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="2c0f3-168">Każdy punkt końcowy ma własny adres i powiązanie.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-168">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="2c0f3-169">Wszystkie powiązania używane w pliku konfiguracji muszą być zdefiniowane w zakresie pliku.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-169">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="2c0f3-170">Powiązania są połączone z punktami końcowymi przez kombinację `name` atrybutów `bindingConfiguration`i.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-170">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="2c0f3-171">`binding` Atrybut określa, w którym sekcji jest zdefiniowane powiązanie.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-171">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="2c0f3-172">`bindingConfiguration` Atrybut definiuje skonfigurowane powiązanie w sekcji powiązania.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-172">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="2c0f3-173">Sekcja powiązania może definiować kilka skonfigurowanych powiązań.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-173">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c0f3-174">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c0f3-174">Example</span></span>  
 <span data-ttu-id="2c0f3-175">Jest to przykład pliku konfiguracji WCF.</span><span class="sxs-lookup"><span data-stu-id="2c0f3-175">This is an example of a WCF configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2c0f3-176">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c0f3-176">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
