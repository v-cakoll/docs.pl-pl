---
title: '&lt;serviceHostingEnvironment&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a08df7c620065bb483d276e3ead2c179040f1c9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicehostingenvironmentgt"></a><span data-ttu-id="c7e26-102">&lt;serviceHostingEnvironment&gt;</span><span class="sxs-lookup"><span data-stu-id="c7e26-102">&lt;serviceHostingEnvironment&gt;</span></span>
<span data-ttu-id="c7e26-103">Ten element definiuje typ, który usługę hostingu środowiskowego dla danego transportu.</span><span class="sxs-lookup"><span data-stu-id="c7e26-103">This element defines the type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="c7e26-104">Jeśli ten element jest pusta, domyślny typ jest używany.</span><span class="sxs-lookup"><span data-stu-id="c7e26-104">If this element is empty, the default type is used.</span></span> <span data-ttu-id="c7e26-105">Ten element może być użyty tylko w aplikacji lub pliki konfiguracji na poziomie maszyny.</span><span class="sxs-lookup"><span data-stu-id="c7e26-105">This element can only be used at the application or machine level configuration files.</span></span>  
  
 <span data-ttu-id="c7e26-106">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c7e26-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="c7e26-107">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="c7e26-107">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7e26-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7e26-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean" 
                           minFreeMemoryPercentageToActivateService="Integer" 
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String" service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String" transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7e26-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c7e26-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c7e26-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c7e26-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7e26-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c7e26-111">Attributes</span></span>  
  
|<span data-ttu-id="c7e26-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c7e26-112">Attribute</span></span>|<span data-ttu-id="c7e26-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c7e26-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c7e26-114">aspNetCompatibilityEnabled</span><span class="sxs-lookup"><span data-stu-id="c7e26-114">aspNetCompatibilityEnabled</span></span>|<span data-ttu-id="c7e26-115">Wartość logiczna wskazująca, czy tryb zgodności ASP.NET został włączony dla bieżącej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7e26-115">A Boolean value indicating whether the ASP.NET compatibility mode has been turned on for the current application.</span></span> <span data-ttu-id="c7e26-116">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="c7e26-116">The default is `false`.</span></span><br /><br /> <span data-ttu-id="c7e26-117">Jeśli ten atrybut ma wartość `true`, żądania do [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] przepływu usług za pośrednictwem potoku HTTP programu ASP.NET i komunikacji za pośrednictwem protokołów innych niż HTTP jest zabronione.</span><span class="sxs-lookup"><span data-stu-id="c7e26-117">When this attribute is set to `true`, requests to [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services flow through the ASP.NET HTTP pipeline, and communication over non-HTTP protocols is prohibited.</span></span> <span data-ttu-id="c7e26-118">Aby uzyskać więcej informacji, zobacz [usługi WCF i platformy ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="c7e26-118">For more information, see [WCF Services and ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span>|  
|<span data-ttu-id="c7e26-119">Ustawienia minFreeMemoryPercentageToActivateService</span><span class="sxs-lookup"><span data-stu-id="c7e26-119">minFreeMemoryPercentageToActivateService</span></span>|<span data-ttu-id="c7e26-120">Liczba całkowita, która określa minimalną ilość wolnej pamięci, która powinna być dostępna w systemie, zanim [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] można aktywować usługi.</span><span class="sxs-lookup"><span data-stu-id="c7e26-120">An integer that specifies the minimum amount of free memory that should be available to the system, before a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service can be activated.</span></span> <span data-ttu-id="c7e26-121">**Uwaga:** określania tego atrybutu wraz z częściowa relacja zaufania w pliku web.config [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usługi spowoduje <xref:System.Security.SecurityException> po uruchomieniu usługi.</span><span class="sxs-lookup"><span data-stu-id="c7e26-121">**Caution:**  Specifying this attribute along with partial trust in the web.config file of a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service will result in a <xref:System.Security.SecurityException> when the service is run.</span></span>|  
|<span data-ttu-id="c7e26-122">multipleSiteBindingsEnabled</span><span class="sxs-lookup"><span data-stu-id="c7e26-122">multipleSiteBindingsEnabled</span></span>|<span data-ttu-id="c7e26-123">Wartość logiczna określająca, czy włączono wielokrotne powiązania usługi IIS dla każdej witryny.</span><span class="sxs-lookup"><span data-stu-id="c7e26-123">A Boolean value that specifies whether multiple IIS bindings per site is enabled.</span></span><br /><br /> <span data-ttu-id="c7e26-124">Usługi IIS składa się z witryn sieci web, które są kontenerami dla katalogów wirtualnych zawierających aplikacje wirtualne.</span><span class="sxs-lookup"><span data-stu-id="c7e26-124">IIS consists of web sites, which are containers for virtual applications containing virtual directories.</span></span> <span data-ttu-id="c7e26-125">Za pomocą co najmniej jednego powiązania usługi IIS można uzyskać dostępu do aplikacji w lokacji.</span><span class="sxs-lookup"><span data-stu-id="c7e26-125">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="c7e26-126">Powiązanie z usług IIS oferuje dwa rodzaje informacji: Protokół powiązania i informacje o wiązaniu.</span><span class="sxs-lookup"><span data-stu-id="c7e26-126">An IIS binding provides two pieces of information: a binding protocol and binding information.</span></span> <span data-ttu-id="c7e26-127">Protokół powiązania definiuje schemat, przez który dane są przesyłane, a informacje o wiązaniu są to informacje używane do uzyskania dostępu do witryny.</span><span class="sxs-lookup"><span data-stu-id="c7e26-127">Binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span> <span data-ttu-id="c7e26-128">Przykładem Protokół powiązania, które mogą być protokołu HTTP, a informacje o wiązaniu może zawierać adres IP portu nagłówek hosta, itp.</span><span class="sxs-lookup"><span data-stu-id="c7e26-128">An example of a binding protocol can be HTTP, whereas binding information can contain an IP address, Port, host header, etc.</span></span><br /><br /> <span data-ttu-id="c7e26-129">Usługi IIS obsługują określania wielokrotne powiązania usługi IIS dla każdej witryny, co prowadzi do wielu adresów bazowych dla każdego schematu.</span><span class="sxs-lookup"><span data-stu-id="c7e26-129">IIS supports specifying multiple IIS bindings per site, which results in multiple base addresses per scheme.</span></span> <span data-ttu-id="c7e26-130">Jednak [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usługi hostowanej przez witrynę umożliwia powiązanie z tylko jedną właściwość baseAddress dla każdego schematu.</span><span class="sxs-lookup"><span data-stu-id="c7e26-130">However, a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service hosted under a site allows binding to only one baseAddress per scheme.</span></span><br /><br /> <span data-ttu-id="c7e26-131">Aby włączyć wielokrotne powiązania usługi IIS dla każdej witryny dla [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usługi, ustaw ten atrybut `true`.</span><span class="sxs-lookup"><span data-stu-id="c7e26-131">To enable multiple IIS bindings per site for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service, set this attribute to `true`.</span></span> <span data-ttu-id="c7e26-132">Należy zauważyć, że wiele powiązania witryny jest obsługiwana tylko dla protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="c7e26-132">Notice that multiple site binding is supported only for the HTTP protocol.</span></span> <span data-ttu-id="c7e26-133">Adres punktów końcowych w pliku konfiguracji musi być pełny identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="c7e26-133">The address of endpoints in the configuration file needs to be a complete URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c7e26-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c7e26-134">Child Elements</span></span>  
  
|<span data-ttu-id="c7e26-135">Element</span><span class="sxs-lookup"><span data-stu-id="c7e26-135">Element</span></span>|<span data-ttu-id="c7e26-136">Opis</span><span class="sxs-lookup"><span data-stu-id="c7e26-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c7e26-137">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="c7e26-137">\<baseAddressPrefixFilters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|<span data-ttu-id="c7e26-138">Kolekcja elementów konfiguracji, które określają prefiks filtrów dla adres podstawowy używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="c7e26-138">A collection of configuration elements that specify prefix filters for the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="c7e26-139">\<serviceActivations ></span><span class="sxs-lookup"><span data-stu-id="c7e26-139">\<serviceActivations></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceactivations.md)|<span data-ttu-id="c7e26-140">Sekcja konfiguracyjna, który opisuje ustawienia aktywacji.</span><span class="sxs-lookup"><span data-stu-id="c7e26-140">A configuration section that describes activation settings.</span></span>|  
|[<span data-ttu-id="c7e26-141">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="c7e26-141">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="c7e26-142">Kolekcja elementów konfiguracji, które określa rodzaj danego transportu.</span><span class="sxs-lookup"><span data-stu-id="c7e26-142">A collection of configuration elements that identify the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c7e26-143">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c7e26-143">Parent Elements</span></span>  
  
|<span data-ttu-id="c7e26-144">Element</span><span class="sxs-lookup"><span data-stu-id="c7e26-144">Element</span></span>|<span data-ttu-id="c7e26-145">Opis</span><span class="sxs-lookup"><span data-stu-id="c7e26-145">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c7e26-146">ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c7e26-146">serviceModel</span></span>|<span data-ttu-id="c7e26-147">Element główny wszystkich elementów konfiguracji systemu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c7e26-147">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7e26-148">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c7e26-148">Remarks</span></span>  
 <span data-ttu-id="c7e26-149">Domyślnie uruchomienia obok siebie z programem ASP.NET w hostowanej domeny aplikacji (AppDomain) usług WCF.</span><span class="sxs-lookup"><span data-stu-id="c7e26-149">By default, WCF services run side-by-side with ASP.NET in hosted Application Domains (AppDomain).</span></span> <span data-ttu-id="c7e26-150">Mimo że WCF i platforma ASP.NET mogą współistnieć w tej samej domenie aplikacji, usługi WCF żądania nie są przetwarzane przez potoku HTTP platformy ASP.NET domyślnie.</span><span class="sxs-lookup"><span data-stu-id="c7e26-150">Even though WCF and ASP.NET can coexist in the same AppDomain, WCF requests are not processed by the ASP.NET HTTP Pipeline by default.</span></span> <span data-ttu-id="c7e26-151">W związku z tym kilku elementów aplikacji platformy ASP.NET nie są dostępne dla usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="c7e26-151">As a result, several elements of the ASP.NET application platform are not available to WCF services.</span></span> <span data-ttu-id="c7e26-152">Obejmują one</span><span class="sxs-lookup"><span data-stu-id="c7e26-152">These include</span></span>  
  
-   <span data-ttu-id="c7e26-153">Autoryzacji URL pliku ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c7e26-153">ASP.NET File/URL Authorization</span></span>  
  
-   <span data-ttu-id="c7e26-154">Personifikacja w programie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c7e26-154">ASP.NET Impersonation</span></span>  
  
-   <span data-ttu-id="c7e26-155">Plik cookie na podstawie stanu sesji</span><span class="sxs-lookup"><span data-stu-id="c7e26-155">Cookie-based Session State</span></span>  
  
-   <span data-ttu-id="c7e26-156">Właściwość HttpContext.Current</span><span class="sxs-lookup"><span data-stu-id="c7e26-156">HttpContext.Current</span></span>  
  
-   <span data-ttu-id="c7e26-157">Rozszerzalność potoku za pośrednictwem HttpModule niestandardowych</span><span class="sxs-lookup"><span data-stu-id="c7e26-157">Pipeline Extensibility via custom HttpModule</span></span>  
  
 <span data-ttu-id="c7e26-158">Jeśli usługi WCF muszą działać w kontekście programu ASP.NET i komunikować się tylko za pośrednictwem protokołu HTTP, można użyć tryb zgodności ASP.NET dla usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="c7e26-158">If your WCF services need to function in the ASP.NET context, and communicate only over HTTP, you can use WCF’s ASP.NET compatibility mode.</span></span> <span data-ttu-id="c7e26-159">Ten tryb jest włączony podczas `aspNetCompatibilityEnabled` atrybut ma ustawioną `true` na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7e26-159">This mode is turned on when the `aspNetCompatibilityEnabled` attribute is set to `true` at the application level.</span></span> <span data-ttu-id="c7e26-160">Implementacji usługi muszą mieć możliwość uruchamiania w trybie zgodności z użyciem <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="c7e26-160">Service implementations must declare their ability to run in compatibility mode using the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> class.</span></span> <span data-ttu-id="c7e26-161">Po włączeniu trybu zgodności</span><span class="sxs-lookup"><span data-stu-id="c7e26-161">When the compatibility mode is enabled,</span></span>  
  
-   <span data-ttu-id="c7e26-162">Autoryzacji URL pliku ASP.NET jest wymuszana przed WCF autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="c7e26-162">ASP.NET File/URL Authorization is enforced prior to WCF authorization.</span></span> <span data-ttu-id="c7e26-163">Decyzję dotyczącą autoryzacji jest oparta na poziomie transportu tożsamości żądania.</span><span class="sxs-lookup"><span data-stu-id="c7e26-163">An authorization decision is based on the transport-level identity of the request.</span></span> <span data-ttu-id="c7e26-164">Tożsamości na poziomie wiadomości są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="c7e26-164">Identities at the message level are ignored.</span></span>  
  
-   <span data-ttu-id="c7e26-165">Uruchom operacji usługi WCF do wykonania w kontekście personifikacji platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c7e26-165">WCF service operations start to execute in the ASP.NET impersonation context.</span></span> <span data-ttu-id="c7e26-166">Jeśli zarówno personifikacji aplikacji ASP.NET i WCF personifikacji są włączone dla określonej usługi, stosuje kontekstu personifikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="c7e26-166">If both ASP.NET impersonation and WCF impersonation are enabled for a specific service, the WCF impersonation context applies.</span></span>  
  
-   <span data-ttu-id="c7e26-167">Właściwość HttpContext.Current można używać z kodem usługi WCF i usługi będą mogli udostępnianie punktów końcowych protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="c7e26-167">HttpContext.Current can be used from WCF service code, and services are prevented from exposing non-HTTP endpoints.</span></span>  
  
-   <span data-ttu-id="c7e26-168">Usługi WCF żądania są przetwarzane przez potoku ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c7e26-168">WCF requests are processed by the ASP.NET pipeline.</span></span> <span data-ttu-id="c7e26-169">HttpModules, które zostały skonfigurowane do działania na przychodzące żądania może również przetwarzanie żądań WCF.</span><span class="sxs-lookup"><span data-stu-id="c7e26-169">HttpModules that have been configured to act on incoming requests can also process WCF requests.</span></span> <span data-ttu-id="c7e26-170">Obejmują one składniki platformy ASP.NET (np. <xref:System.Web.SessionState.SessionStateModule>), oraz moduły niestandardowe innych firm.</span><span class="sxs-lookup"><span data-stu-id="c7e26-170">These can include ASP.NET platform components (e.g., <xref:System.Web.SessionState.SessionStateModule>), as well as custom third party modules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7e26-171">Przykład</span><span class="sxs-lookup"><span data-stu-id="c7e26-171">Example</span></span>  
 <span data-ttu-id="c7e26-172">Poniższy przykład kodu pokazuje sposób włączania trybu zgodności z ASP.</span><span class="sxs-lookup"><span data-stu-id="c7e26-172">The following code sample shows how to enable ASP Compatibility Mode.</span></span>  
  
## <a name="code"></a><span data-ttu-id="c7e26-173">Kod</span><span class="sxs-lookup"><span data-stu-id="c7e26-173">Code</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7e26-174">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7e26-174">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="c7e26-175">Hosting</span><span class="sxs-lookup"><span data-stu-id="c7e26-175">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)  
 [<span data-ttu-id="c7e26-176">Usługi WCF i platforma ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c7e26-176">WCF Services and ASP.NET</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
