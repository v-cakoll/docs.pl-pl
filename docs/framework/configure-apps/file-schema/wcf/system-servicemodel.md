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
ms.openlocfilehash: 2125ce00b0e23f2e93ff251549f9c1276892b16b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399446"
---
# \<system.serviceModel>
<span data-ttu-id="43b50-102">Ta sekcja konfiguracji zawiera wszystkie elementy konfiguracji programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="43b50-102">This configuration section contains all the Windows Communication Foundation (WCF) ServiceModel configuration elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.serviceModel>**  
  
## <a name="syntax"></a><span data-ttu-id="43b50-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="43b50-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43b50-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="43b50-104">Attributes and Elements</span></span>  
 <span data-ttu-id="43b50-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="43b50-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43b50-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="43b50-106">Attributes</span></span>  
 <span data-ttu-id="43b50-107">Brak</span><span class="sxs-lookup"><span data-stu-id="43b50-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="43b50-108">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="43b50-108">Child Elements</span></span>  
  
|<span data-ttu-id="43b50-109">Element</span><span class="sxs-lookup"><span data-stu-id="43b50-109">Element</span></span>|<span data-ttu-id="43b50-110">Opis</span><span class="sxs-lookup"><span data-stu-id="43b50-110">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviors>](behaviors.md)|<span data-ttu-id="43b50-111">Ta sekcja definiuje dwie kolekcje podrzędne o nazwach `endpointBehaviors` i `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="43b50-111">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="43b50-112">Każda kolekcja definiuje elementy zachowań używane odpowiednio przez punkty końcowe i usługi.</span><span class="sxs-lookup"><span data-stu-id="43b50-112">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="43b50-113">Każdy element zachowanie jest określony przez jego unikatowy `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="43b50-113">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[\<bindings>](bindings.md)|<span data-ttu-id="43b50-114">Ta sekcja zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="43b50-114">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="43b50-115">Każdy wpis jest identyfikowany przez jego unikatowy `name` .</span><span class="sxs-lookup"><span data-stu-id="43b50-115">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="43b50-116">Usługi używają powiązań przez łączenie ich przy użyciu `name` .</span><span class="sxs-lookup"><span data-stu-id="43b50-116">Services use bindings by linking them using the `name`.</span></span>|  
|[\<client>](client.md)|<span data-ttu-id="43b50-117">Ta sekcja zawiera listę punktów końcowych używanych przez klienta do nawiązywania połączenia z usługą.</span><span class="sxs-lookup"><span data-stu-id="43b50-117">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[\<comContracts>](comcontracts.md)|<span data-ttu-id="43b50-118">Ta sekcja zawiera definicje umów COM włączonych dla usług WCF i współdziałania z modelem COM.</span><span class="sxs-lookup"><span data-stu-id="43b50-118">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[\<commonBehaviors>](commonbehaviors.md)|<span data-ttu-id="43b50-119">Tę sekcję można zdefiniować tylko w pliku Machine. config.</span><span class="sxs-lookup"><span data-stu-id="43b50-119">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="43b50-120">Definiuje dwie kolekcje podrzędne o nazwach `endpointBehaviors` i `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="43b50-120">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="43b50-121">Każda kolekcja definiuje elementy zachowań używane przez wszystkie punkty końcowe i usługi WCF odpowiednio na maszynie.</span><span class="sxs-lookup"><span data-stu-id="43b50-121">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="43b50-122">Jeśli zachowanie jest zdefiniowane w obu `<commonBehaviors>` `<behaviors>` sekcjach, zachowanie w \<behaviors> sekcji ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="43b50-122">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="43b50-123">Ta sekcja zawiera ustawienia funkcji diagnostyki WCF.</span><span class="sxs-lookup"><span data-stu-id="43b50-123">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="43b50-124">Użytkownik może włączyć/wyłączyć śledzenie, liczniki wydajności i dostawcę WMI, a także może dodawać niestandardowe filtry komunikatów.</span><span class="sxs-lookup"><span data-stu-id="43b50-124">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[\<extensions>](extensions-section.md)|<span data-ttu-id="43b50-125">Ta sekcja zawiera kolekcję rozszerzeń, które umożliwiają użytkownikowi tworzenie powiązań zdefiniowanych przez użytkownika, zachowań i innych aspektów rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="43b50-125">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[\<protocolMapping>](protocolmapping.md)|<span data-ttu-id="43b50-126">Ta sekcja definiuje zestaw domyślnego mapowania protokołów między schematami protokołu transportowego (np. http, net. TCP, net. pipe itp.) i powiązania WCF.</span><span class="sxs-lookup"><span data-stu-id="43b50-126">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[\<routing>](routing.md)|<span data-ttu-id="43b50-127">Ta sekcja definiuje zestaw filtrów routingu, które określają typ Windows Communication Foundation (WCF), który <xref:System.ServiceModel.Dispatcher.MessageFilter> ma być używany podczas oceniania wiadomości przychodzących, a także tabele routingu definiujące docelowe punkty końcowe do wysyłania komunikatów, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="43b50-127">This section defines a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="43b50-128">W tej sekcji zdefiniowano typ tworzenia wystąpień środowiska hostingu usługi dla określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="43b50-128">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="43b50-129">Jeśli ta sekcja jest pusta, używany jest typ domyślny.</span><span class="sxs-lookup"><span data-stu-id="43b50-129">If this section is empty, the default type is used.</span></span>|  
|[\<services>](services.md)|<span data-ttu-id="43b50-130">Sekcja zawiera kolekcję usług.</span><span class="sxs-lookup"><span data-stu-id="43b50-130">The section contains a collection of services.</span></span> <span data-ttu-id="43b50-131">Dla każdej usługi zdefiniowanej w zestawie ten element zawiera `service` element określający ustawienia dla usługi.</span><span class="sxs-lookup"><span data-stu-id="43b50-131">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="43b50-132">Ta sekcja definiuje zbiór standardowych punktów końcowych, które są wstępnie skonfigurowanymi punktami końcowymi wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="43b50-132">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="43b50-133">Standardowy punkt końcowy będzie miał co najmniej jeden atrybut Address, Binding i Contract ustawiony na wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="43b50-133">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="43b50-134">Na przykład w punkcie końcowym odnajdywania kontrakt jest ustalony.</span><span class="sxs-lookup"><span data-stu-id="43b50-134">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="43b50-135">Możesz również użyć standardowych punktów końcowych, aby zwiększyć punkt końcowy usługi z nowymi właściwościami podobnymi do definiowania powiązań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="43b50-135">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|
|[\<tracking>](tracking-of-wcf.md)|<span data-ttu-id="43b50-136">W tej sekcji zdefiniowano ustawienia śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="43b50-136">This section defines tracking settings for a workflow service.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="43b50-137">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="43b50-137">Parent Elements</span></span>  
  
|<span data-ttu-id="43b50-138">Element</span><span class="sxs-lookup"><span data-stu-id="43b50-138">Element</span></span>|<span data-ttu-id="43b50-139">Opis</span><span class="sxs-lookup"><span data-stu-id="43b50-139">Description</span></span>|  
|-------------|-----------------|  
|\<configuration>|<span data-ttu-id="43b50-140">Element główny dla wszystkich elementów konfiguracji w PLiku konfiguracji PLatformy .NET.</span><span class="sxs-lookup"><span data-stu-id="43b50-140">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43b50-141">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43b50-141">Remarks</span></span>  
 <span data-ttu-id="43b50-142">Funkcja WCF nie dodaje elementów do sekcji konfiguracji innych produktów.</span><span class="sxs-lookup"><span data-stu-id="43b50-142">WCF does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="43b50-143">Usługi WCF są zdefiniowane w `services` sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="43b50-143">WCF services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="43b50-144">Zestaw może zawierać dowolną liczbę usług.</span><span class="sxs-lookup"><span data-stu-id="43b50-144">An assembly can contain any number of services.</span></span> <span data-ttu-id="43b50-145">Każda usługa ma swoją własną `service` sekcję konfiguracyjną.</span><span class="sxs-lookup"><span data-stu-id="43b50-145">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="43b50-146">Sekcja i jej zawartość definiują kontrakt usługi, zachowanie i punkty końcowe określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="43b50-146">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="43b50-147">`name`Wymagany jest tylko atrybut usługi.</span><span class="sxs-lookup"><span data-stu-id="43b50-147">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="43b50-148">Domyślnie nazwa usługi opisuje źródłowy typ CLR używany do implementowania usługi. można jednak zmienić właściwość ConfigurationName w <xref:System.ServiceModel.ServiceContractAttribute> celu zastąpienia wymagania dotyczącego typu CLR.</span><span class="sxs-lookup"><span data-stu-id="43b50-148">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="43b50-149">`behaviorConfiguration`Atrybut jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="43b50-149">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="43b50-150">Identyfikuje zachowanie usługi używane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="43b50-150">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="43b50-151">Zachowanie określone przez ten atrybut musi łączyć się z zachowaniem usługi zdefiniowanym w zakresie tego samego pliku konfiguracji (tj. tym samym lub plikiem nadrzędnym).</span><span class="sxs-lookup"><span data-stu-id="43b50-151">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="43b50-152">Każda usługa ujawnia jeden lub więcej punktów końcowych zdefiniowanych w `endpoint` elemencie.</span><span class="sxs-lookup"><span data-stu-id="43b50-152">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="43b50-153">Każdy punkt końcowy ma własny adres i powiązanie.</span><span class="sxs-lookup"><span data-stu-id="43b50-153">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="43b50-154">Wszystkie powiązania używane w pliku konfiguracji muszą być zdefiniowane w zakresie pliku.</span><span class="sxs-lookup"><span data-stu-id="43b50-154">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="43b50-155">Powiązania są połączone z punktami końcowymi przez kombinację atrybutów `name` i `bindingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="43b50-155">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="43b50-156">`binding`Atrybut określa, w którym sekcji jest zdefiniowane powiązanie.</span><span class="sxs-lookup"><span data-stu-id="43b50-156">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="43b50-157">`bindingConfiguration`Atrybut definiuje skonfigurowane powiązanie w sekcji powiązania.</span><span class="sxs-lookup"><span data-stu-id="43b50-157">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="43b50-158">Sekcja powiązania może definiować kilka skonfigurowanych powiązań.</span><span class="sxs-lookup"><span data-stu-id="43b50-158">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43b50-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="43b50-159">Example</span></span>  
 <span data-ttu-id="43b50-160">Jest to przykład pliku konfiguracji WCF.</span><span class="sxs-lookup"><span data-stu-id="43b50-160">This is an example of a WCF configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43b50-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43b50-161">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
