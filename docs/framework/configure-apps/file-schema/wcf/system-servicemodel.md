---
title: '&lt;system.serviceModel&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 563825a92dbdeb90cd17d107795525686b7b4080
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltsystemservicemodelgt"></a><span data-ttu-id="3e67e-102">&lt;system.serviceModel&gt;</span><span class="sxs-lookup"><span data-stu-id="3e67e-102">&lt;system.serviceModel&gt;</span></span>
<span data-ttu-id="3e67e-103">Ta sekcja konfiguracji zawiera wszystkie [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] elementy konfiguracyjne ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="3e67e-103">This configuration section contains all the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] ServiceModel configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e67e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e67e-104">Syntax</span></span>  
  
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
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e67e-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3e67e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3e67e-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3e67e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e67e-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3e67e-107">Attributes</span></span>  
 <span data-ttu-id="3e67e-108">Brak</span><span class="sxs-lookup"><span data-stu-id="3e67e-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3e67e-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3e67e-109">Child Elements</span></span>  
  
|<span data-ttu-id="3e67e-110">Element</span><span class="sxs-lookup"><span data-stu-id="3e67e-110">Element</span></span>|<span data-ttu-id="3e67e-111">Opis</span><span class="sxs-lookup"><span data-stu-id="3e67e-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e67e-112">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="3e67e-112">\<behaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)|<span data-ttu-id="3e67e-113">Ta sekcja definiuje dwie kolekcje elementów podrzędnych o nazwie `endpointBehaviors` i `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="3e67e-113">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="3e67e-114">Każda kolekcja definiuje elementy zachowanie odpowiednio używane przez punkty końcowe i usług.</span><span class="sxs-lookup"><span data-stu-id="3e67e-114">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="3e67e-115">Każdy element zachowanie jest określony przez jego unikatowy `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="3e67e-115">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[<span data-ttu-id="3e67e-116">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="3e67e-116">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="3e67e-117">Ta sekcja przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="3e67e-117">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="3e67e-118">Każdy wpis jest identyfikowany przez jego unikatowy `name`.</span><span class="sxs-lookup"><span data-stu-id="3e67e-118">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="3e67e-119">Usługi używają powiązania łącząc je za pomocą `name`.</span><span class="sxs-lookup"><span data-stu-id="3e67e-119">Services use bindings by linking them using the `name`.</span></span>|  
|[<span data-ttu-id="3e67e-120">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="3e67e-120">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="3e67e-121">Ta sekcja zawiera listę punktów końcowych, które klient używa do łączenia się z usługą.</span><span class="sxs-lookup"><span data-stu-id="3e67e-121">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[<span data-ttu-id="3e67e-122">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="3e67e-122">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|<span data-ttu-id="3e67e-123">Ta sekcja definiuje kontrakty COM włączone dla usługi WCF i COM interop.</span><span class="sxs-lookup"><span data-stu-id="3e67e-123">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[<span data-ttu-id="3e67e-124">\<commonBehaviors ></span><span class="sxs-lookup"><span data-stu-id="3e67e-124">\<commonBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|<span data-ttu-id="3e67e-125">W tej sekcji można zdefiniować tylko w pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="3e67e-125">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="3e67e-126">Definiuje dwie kolekcje elementów podrzędnych o nazwie `endpointBehaviors` i `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="3e67e-126">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="3e67e-127">Każda kolekcja definiuje używane przez wszystkie elementy zachowanie [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] punktów końcowych i usług na komputerze odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="3e67e-127">Each collection defines behavior elements consumed by all [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="3e67e-128">Jeśli to zachowanie jest zdefiniowany zarówno `<commonBehaviors>` i `<behaviors>` sekcje zachowanie w \<zachowania > sekcji podano preferencji.</span><span class="sxs-lookup"><span data-stu-id="3e67e-128">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[<span data-ttu-id="3e67e-129">\<Rozszerzenia ></span><span class="sxs-lookup"><span data-stu-id="3e67e-129">\<extensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|<span data-ttu-id="3e67e-130">Ta sekcja zawiera kolekcję rozszerzeń, które umożliwiają użytkownikowi utworzenie powiązań zdefiniowanych przez użytkownika, zachowania i inne aspekty rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="3e67e-130">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[<span data-ttu-id="3e67e-131">\<Diagnostyka ></span><span class="sxs-lookup"><span data-stu-id="3e67e-131">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="3e67e-132">Ta sekcja zawiera ustawienia dla funkcji diagnostyki usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="3e67e-132">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="3e67e-133">Użytkownik może Włączanie/wyłączanie śledzenia, liczniki wydajności i dostawcy WMI i dodać filtry niestandardowe komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3e67e-133">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[<span data-ttu-id="3e67e-134">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="3e67e-134">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="3e67e-135">Ta sekcja definiuje zestawu domyślnego mapowania protokołu pomiędzy schematami protokołu transportu (np. http, net.tcp, net.pipe, itp.) i powiązaniami WCF.</span><span class="sxs-lookup"><span data-stu-id="3e67e-135">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[<span data-ttu-id="3e67e-136">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="3e67e-136">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="3e67e-137">Ta sekcja definiuje zestaw filtrów routingu, które określają typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu tabele definiują docelowych punktów końcowych do wysyłania komunikatów do gdy kryteria filtru.</span><span class="sxs-lookup"><span data-stu-id="3e67e-137">This section defines a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[<span data-ttu-id="3e67e-138">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="3e67e-138">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="3e67e-139">Ta sekcja definiuje typ usługi, którą Środowisko hostingu środowiskowego dla danego transportu.</span><span class="sxs-lookup"><span data-stu-id="3e67e-139">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="3e67e-140">Jeśli w tej sekcji jest pusta, domyślny typ jest używany.</span><span class="sxs-lookup"><span data-stu-id="3e67e-140">If this section is empty, the default type is used.</span></span>|  
|[<span data-ttu-id="3e67e-141">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="3e67e-141">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="3e67e-142">Sekcja zawiera kolekcję usług.</span><span class="sxs-lookup"><span data-stu-id="3e67e-142">The section contains a collection of services.</span></span> <span data-ttu-id="3e67e-143">Dla każdej usługi zdefiniowane w zestawie, ten element zawiera `service` element Określanie ustawień usługi.</span><span class="sxs-lookup"><span data-stu-id="3e67e-143">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[<span data-ttu-id="3e67e-144">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="3e67e-144">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="3e67e-145">Ta sekcja definiuje kolekcji standardowych punktów końcowych, które są do ponownego użycia wstępnie skonfigurowanymi punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="3e67e-145">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="3e67e-146">Standardowy punkt końcowy będzie mieć jeden lub więcej z address, binding i atrybuty kontraktu ustawioną wartością stałą.</span><span class="sxs-lookup"><span data-stu-id="3e67e-146">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="3e67e-147">Na przykład w punkcie końcowym odnajdywania kontrakt jest stała.</span><span class="sxs-lookup"><span data-stu-id="3e67e-147">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="3e67e-148">Umożliwia także standardowych punktów końcowych do rozszerzenia punktu końcowego usługi z nowymi właściwościami podobne do definiowania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="3e67e-148">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3e67e-149">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3e67e-149">Parent Elements</span></span>  
  
|<span data-ttu-id="3e67e-150">Element</span><span class="sxs-lookup"><span data-stu-id="3e67e-150">Element</span></span>|<span data-ttu-id="3e67e-151">Opis</span><span class="sxs-lookup"><span data-stu-id="3e67e-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3e67e-152">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="3e67e-152">\<configuration></span></span>|<span data-ttu-id="3e67e-153">Element główny dla wszystkich elementów konfiguracji w PLiku konfiguracji PLatformy .NET.</span><span class="sxs-lookup"><span data-stu-id="3e67e-153">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e67e-154">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e67e-154">Remarks</span></span>  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="3e67e-155">nie dodać elementy do sekcji konfiguracji innych produktów.</span><span class="sxs-lookup"><span data-stu-id="3e67e-155"> does not add elements to the configuration sections of other products.</span></span>  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="3e67e-156">usługi są zdefiniowane w `services` sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3e67e-156"> services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="3e67e-157">Zestaw może zawierać dowolną liczbę usług.</span><span class="sxs-lookup"><span data-stu-id="3e67e-157">An assembly can contain any number of services.</span></span> <span data-ttu-id="3e67e-158">Każda usługa ma własną `service` sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3e67e-158">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="3e67e-159">Sekcji i jego zawartości definiowanie kontraktu usługi, zachowania i punkty końcowe określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="3e67e-159">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="3e67e-160">Tylko usługi `name` atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="3e67e-160">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="3e67e-161">Domyślnie nazwa usługi w tym artykule opisano podstawowy typ CLR używane do implementowania usługi; Jednak możesz zmienić właściwość ConfigurationName na <xref:System.ServiceModel.ServiceContractAttribute> Aby przesłonić wymaganie typu CLR.</span><span class="sxs-lookup"><span data-stu-id="3e67e-161">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="3e67e-162">`behaviorConfiguration` Atrybutu jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3e67e-162">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="3e67e-163">Identyfikuje zachowanie usługi używane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="3e67e-163">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="3e67e-164">Zachowanie określonego przez tego atrybutu musi połączyć zachowania usługi, zdefiniowanego w zakresie pliku konfiguracyjnym (tj. tego samego pliku lub pliku nadrzędnego).</span><span class="sxs-lookup"><span data-stu-id="3e67e-164">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="3e67e-165">Każda usługa przedstawia jedną lub więcej punktów końcowych zdefiniowanych w `endpoint` elementu.</span><span class="sxs-lookup"><span data-stu-id="3e67e-165">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="3e67e-166">Każdy punkt końcowy ma własny adres i powiązanie.</span><span class="sxs-lookup"><span data-stu-id="3e67e-166">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="3e67e-167">Wszystkie powiązania używane w pliku konfiguracji musi być zdefiniowana w zakresie pliku.</span><span class="sxs-lookup"><span data-stu-id="3e67e-167">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="3e67e-168">Powiązania są połączone z punktów końcowych za pomocą kombinacji atrybutów `name` i `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="3e67e-168">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="3e67e-169">`binding` Atrybut definiuje, w której sekcji zdefiniowano powiązania.</span><span class="sxs-lookup"><span data-stu-id="3e67e-169">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="3e67e-170">`bindingConfiguration` Atrybut definiuje, które skonfigurowanego powiązania w sekcji binding jest używany.</span><span class="sxs-lookup"><span data-stu-id="3e67e-170">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="3e67e-171">Powiązania sekcji można określić kilka skonfigurowanego powiązania.</span><span class="sxs-lookup"><span data-stu-id="3e67e-171">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e67e-172">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e67e-172">Example</span></span>  
 <span data-ttu-id="3e67e-173">To jest przykładowy plik konfiguracji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="3e67e-173">This is an example of a WCF configuration file.</span></span>  
  
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
        <diagnostics wmiProviderEnabled="false" performanceCountersEnabled="false" tracingEnabled="false">  
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
  
## <a name="see-also"></a><span data-ttu-id="3e67e-174">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e67e-174">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
