---
title: <system.serviceModel>
description: Dowiedz się więcej na temat elementów konfiguracji ServiceModel programu WCF, które umożliwiają konfigurowanie aplikacji usług i klientów platformy WCF.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
ms.openlocfilehash: 567cbd2cc07ee82e795daa067b9034b2b8dc1974
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85243961"
---
# \<system.serviceModel>
<span data-ttu-id="ea759-103">Ta sekcja konfiguracji zawiera wszystkie elementy konfiguracji programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ea759-103">This configuration section contains all the Windows Communication Foundation (WCF) ServiceModel configuration elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.serviceModel>**  
  
## <a name="syntax"></a><span data-ttu-id="ea759-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea759-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea759-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ea759-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ea759-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ea759-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea759-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ea759-107">Attributes</span></span>  
 <span data-ttu-id="ea759-108">Brak</span><span class="sxs-lookup"><span data-stu-id="ea759-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ea759-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ea759-109">Child Elements</span></span>  
  
|<span data-ttu-id="ea759-110">Element</span><span class="sxs-lookup"><span data-stu-id="ea759-110">Element</span></span>|<span data-ttu-id="ea759-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ea759-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviors>](behaviors.md)|<span data-ttu-id="ea759-112">Ta sekcja definiuje dwie kolekcje podrzędne o nazwach `endpointBehaviors` i `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="ea759-112">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="ea759-113">Każda kolekcja definiuje elementy zachowań używane odpowiednio przez punkty końcowe i usługi.</span><span class="sxs-lookup"><span data-stu-id="ea759-113">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="ea759-114">Każdy element zachowanie jest określony przez jego unikatowy `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ea759-114">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[\<bindings>](bindings.md)|<span data-ttu-id="ea759-115">Ta sekcja zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="ea759-115">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="ea759-116">Każdy wpis jest identyfikowany przez jego unikatowy `name` .</span><span class="sxs-lookup"><span data-stu-id="ea759-116">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="ea759-117">Usługi używają powiązań przez łączenie ich przy użyciu `name` .</span><span class="sxs-lookup"><span data-stu-id="ea759-117">Services use bindings by linking them using the `name`.</span></span>|  
|[\<client>](client.md)|<span data-ttu-id="ea759-118">Ta sekcja zawiera listę punktów końcowych używanych przez klienta do nawiązywania połączenia z usługą.</span><span class="sxs-lookup"><span data-stu-id="ea759-118">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[\<comContracts>](comcontracts.md)|<span data-ttu-id="ea759-119">Ta sekcja zawiera definicje umów COM włączonych dla usług WCF i współdziałania z modelem COM.</span><span class="sxs-lookup"><span data-stu-id="ea759-119">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[\<commonBehaviors>](commonbehaviors.md)|<span data-ttu-id="ea759-120">Tę sekcję można zdefiniować tylko w pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="ea759-120">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="ea759-121">Definiuje dwie kolekcje podrzędne o nazwach `endpointBehaviors` i `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="ea759-121">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="ea759-122">Każda kolekcja definiuje elementy zachowań używane przez wszystkie punkty końcowe i usługi WCF odpowiednio na maszynie.</span><span class="sxs-lookup"><span data-stu-id="ea759-122">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="ea759-123">Jeśli zachowanie jest zdefiniowane w obu `<commonBehaviors>` `<behaviors>` sekcjach, zachowanie w \<behaviors> sekcji ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="ea759-123">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="ea759-124">Ta sekcja zawiera ustawienia funkcji diagnostyki WCF.</span><span class="sxs-lookup"><span data-stu-id="ea759-124">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="ea759-125">Użytkownik może włączyć/wyłączyć śledzenie, liczniki wydajności i dostawcę WMI, a także może dodawać niestandardowe filtry komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ea759-125">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[\<extensions>](extensions-section.md)|<span data-ttu-id="ea759-126">Ta sekcja zawiera kolekcję rozszerzeń, które umożliwiają użytkownikowi tworzenie powiązań zdefiniowanych przez użytkownika, zachowań i innych aspektów rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="ea759-126">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[\<protocolMapping>](protocolmapping.md)|<span data-ttu-id="ea759-127">Ta sekcja definiuje zestaw domyślnego mapowania protokołów między schematami protokołu transportowego (np. http, net. TCP, net. pipe itp.) i powiązania WCF.</span><span class="sxs-lookup"><span data-stu-id="ea759-127">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[\<routing>](routing.md)|<span data-ttu-id="ea759-128">Ta sekcja definiuje zestaw filtrów routingu, które określają typ Windows Communication Foundation (WCF), który <xref:System.ServiceModel.Dispatcher.MessageFilter> ma być używany podczas oceniania wiadomości przychodzących, a także tabele routingu definiujące docelowe punkty końcowe do wysyłania komunikatów, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="ea759-128">This section defines a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="ea759-129">W tej sekcji zdefiniowano typ tworzenia wystąpień środowiska hostingu usługi dla określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="ea759-129">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="ea759-130">Jeśli ta sekcja jest pusta, używany jest typ domyślny.</span><span class="sxs-lookup"><span data-stu-id="ea759-130">If this section is empty, the default type is used.</span></span>|  
|[\<services>](services.md)|<span data-ttu-id="ea759-131">Sekcja zawiera kolekcję usług.</span><span class="sxs-lookup"><span data-stu-id="ea759-131">The section contains a collection of services.</span></span> <span data-ttu-id="ea759-132">Dla każdej usługi zdefiniowanej w zestawie ten element zawiera `service` element określający ustawienia dla usługi.</span><span class="sxs-lookup"><span data-stu-id="ea759-132">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="ea759-133">Ta sekcja definiuje zbiór standardowych punktów końcowych, które są wstępnie skonfigurowanymi punktami końcowymi wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="ea759-133">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="ea759-134">Standardowy punkt końcowy będzie miał co najmniej jeden atrybut Address, Binding i Contract ustawiony na wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="ea759-134">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="ea759-135">Na przykład w punkcie końcowym odnajdywania kontrakt jest ustalony.</span><span class="sxs-lookup"><span data-stu-id="ea759-135">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="ea759-136">Możesz również użyć standardowych punktów końcowych, aby zwiększyć punkt końcowy usługi z nowymi właściwościami podobnymi do definiowania powiązań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="ea759-136">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|
|[\<tracking>](tracking-of-wcf.md)|<span data-ttu-id="ea759-137">W tej sekcji zdefiniowano ustawienia śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ea759-137">This section defines tracking settings for a workflow service.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ea759-138">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ea759-138">Parent Elements</span></span>  
  
|<span data-ttu-id="ea759-139">Element</span><span class="sxs-lookup"><span data-stu-id="ea759-139">Element</span></span>|<span data-ttu-id="ea759-140">Opis</span><span class="sxs-lookup"><span data-stu-id="ea759-140">Description</span></span>|  
|-------------|-----------------|  
|\<configuration>|<span data-ttu-id="ea759-141">Element główny dla wszystkich elementów konfiguracji w PLiku konfiguracji PLatformy .NET.</span><span class="sxs-lookup"><span data-stu-id="ea759-141">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea759-142">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ea759-142">Remarks</span></span>  
 <span data-ttu-id="ea759-143">Funkcja WCF nie dodaje elementów do sekcji konfiguracji innych produktów.</span><span class="sxs-lookup"><span data-stu-id="ea759-143">WCF does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="ea759-144">Usługi WCF są zdefiniowane w `services` sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ea759-144">WCF services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="ea759-145">Zestaw może zawierać dowolną liczbę usług.</span><span class="sxs-lookup"><span data-stu-id="ea759-145">An assembly can contain any number of services.</span></span> <span data-ttu-id="ea759-146">Każda usługa ma swoją własną `service` sekcję konfiguracyjną.</span><span class="sxs-lookup"><span data-stu-id="ea759-146">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="ea759-147">Sekcja i jej zawartość definiują kontrakt usługi, zachowanie i punkty końcowe określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="ea759-147">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="ea759-148">`name`Wymagany jest tylko atrybut usługi.</span><span class="sxs-lookup"><span data-stu-id="ea759-148">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="ea759-149">Domyślnie nazwa usługi opisuje źródłowy typ CLR używany do implementowania usługi. można jednak zmienić właściwość ConfigurationName w <xref:System.ServiceModel.ServiceContractAttribute> celu zastąpienia wymagania dotyczącego typu CLR.</span><span class="sxs-lookup"><span data-stu-id="ea759-149">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="ea759-150">`behaviorConfiguration`Atrybut jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ea759-150">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="ea759-151">Identyfikuje zachowanie usługi używane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="ea759-151">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="ea759-152">Zachowanie określone przez ten atrybut musi łączyć się z zachowaniem usługi zdefiniowanym w zakresie tego samego pliku konfiguracji (tj. tym samym lub plikiem nadrzędnym).</span><span class="sxs-lookup"><span data-stu-id="ea759-152">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="ea759-153">Każda usługa ujawnia jeden lub więcej punktów końcowych zdefiniowanych w `endpoint` elemencie.</span><span class="sxs-lookup"><span data-stu-id="ea759-153">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="ea759-154">Każdy punkt końcowy ma własny adres i powiązanie.</span><span class="sxs-lookup"><span data-stu-id="ea759-154">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="ea759-155">Wszystkie powiązania używane w pliku konfiguracji muszą być zdefiniowane w zakresie pliku.</span><span class="sxs-lookup"><span data-stu-id="ea759-155">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="ea759-156">Powiązania są połączone z punktami końcowymi przez kombinację atrybutów `name` i `bindingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="ea759-156">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="ea759-157">`binding`Atrybut określa, w którym sekcji jest zdefiniowane powiązanie.</span><span class="sxs-lookup"><span data-stu-id="ea759-157">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="ea759-158">`bindingConfiguration`Atrybut definiuje skonfigurowane powiązanie w sekcji powiązania.</span><span class="sxs-lookup"><span data-stu-id="ea759-158">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="ea759-159">Sekcja powiązania może definiować kilka skonfigurowanych powiązań.</span><span class="sxs-lookup"><span data-stu-id="ea759-159">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea759-160">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea759-160">Example</span></span>  
 <span data-ttu-id="ea759-161">Jest to przykład pliku konfiguracji WCF.</span><span class="sxs-lookup"><span data-stu-id="ea759-161">This is an example of a WCF configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ea759-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea759-162">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
