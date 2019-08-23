---
title: <serviceHostingEnvironment>
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: b81c9f3c4260f415f057cd74b6f113d88f635978
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936292"
---
# <a name="servicehostingenvironment"></a><span data-ttu-id="bf4d5-101">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="bf4d5-101">\<serviceHostingEnvironment></span></span>
<span data-ttu-id="bf4d5-102">Ten element definiuje typ tworzenia wystąpień środowiska hostingu usługi dla określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-102">This element defines the type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="bf4d5-103">Jeśli ten element jest pusty, używany jest typ domyślny.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-103">If this element is empty, the default type is used.</span></span> <span data-ttu-id="bf4d5-104">Tego elementu można używać tylko w plikach konfiguracji na poziomie aplikacji lub komputera.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-104">This element can only be used at the application or machine level configuration files.</span></span>  
  
 <span data-ttu-id="bf4d5-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bf4d5-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="bf4d5-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="bf4d5-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf4d5-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf4d5-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean"
                           minFreeMemoryPercentageToActivateService="Integer"
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf4d5-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bf4d5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bf4d5-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf4d5-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bf4d5-110">Attributes</span></span>  
  
|<span data-ttu-id="bf4d5-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bf4d5-111">Attribute</span></span>|<span data-ttu-id="bf4d5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="bf4d5-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bf4d5-113">aspNetCompatibilityEnabled</span><span class="sxs-lookup"><span data-stu-id="bf4d5-113">aspNetCompatibilityEnabled</span></span>|<span data-ttu-id="bf4d5-114">Wartość logiczna wskazująca, czy tryb zgodności ASP.NET został włączony dla bieżącej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-114">A Boolean value indicating whether the ASP.NET compatibility mode has been turned on for the current application.</span></span> <span data-ttu-id="bf4d5-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="bf4d5-116">Gdy ten atrybut jest ustawiony na `true`, żądania do Windows Communication Foundation (WCF) usługi przepływu za pośrednictwem potoku HTTP ASP.NET, a komunikacja za pośrednictwem protokołów innych niż HTTP jest zabronione.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-116">When this attribute is set to `true`, requests to Windows Communication Foundation (WCF) services flow through the ASP.NET HTTP pipeline, and communication over non-HTTP protocols is prohibited.</span></span> <span data-ttu-id="bf4d5-117">Aby uzyskać więcej informacji, zobacz [usługi WCF i ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="bf4d5-117">For more information, see [WCF Services and ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span></span>|  
|<span data-ttu-id="bf4d5-118">minFreeMemoryPercentageToActivateService</span><span class="sxs-lookup"><span data-stu-id="bf4d5-118">minFreeMemoryPercentageToActivateService</span></span>|<span data-ttu-id="bf4d5-119">Liczba całkowita określająca minimalną ilość wolnej pamięci, która powinna być dostępna dla systemu, zanim będzie można aktywować usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-119">An integer that specifies the minimum amount of free memory that should be available to the system, before a WCF service can be activated.</span></span> <span data-ttu-id="bf4d5-120">**Ostrzeżenie**  Określenie tego atrybutu wraz z częściowym zaufaniem w pliku Web. config usługi WCF spowoduje, że <xref:System.Security.SecurityException> usługa zostanie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-120">**Caution:**  Specifying this attribute along with partial trust in the web.config file of a WCF service will result in a <xref:System.Security.SecurityException> when the service is run.</span></span>|  
|<span data-ttu-id="bf4d5-121">multipleSiteBindingsEnabled</span><span class="sxs-lookup"><span data-stu-id="bf4d5-121">multipleSiteBindingsEnabled</span></span>|<span data-ttu-id="bf4d5-122">Wartość logiczna określająca, czy włączono wiele powiązań usług IIS dla każdej witryny.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-122">A Boolean value that specifies whether multiple IIS bindings per site is enabled.</span></span><br /><br /> <span data-ttu-id="bf4d5-123">Usługi IIS składają się z witryn sieci Web, które są kontenerami dla aplikacji wirtualnych zawierających katalogi wirtualne.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-123">IIS consists of web sites, which are containers for virtual applications containing virtual directories.</span></span> <span data-ttu-id="bf4d5-124">Dostęp do aplikacji w lokacji można uzyskać za pomocą jednego lub kilku powiązań usług IIS.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-124">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="bf4d5-125">Powiązanie usług IIS zawiera dwie informacje: powiązania dotyczące protokołu i powiązania.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-125">An IIS binding provides two pieces of information: a binding protocol and binding information.</span></span> <span data-ttu-id="bf4d5-126">Protokół powiązania definiuje schemat, w którym odbywa się komunikacja, a informacje o powiązaniu są informacjami używanymi do uzyskiwania dostępu do witryny.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-126">Binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span> <span data-ttu-id="bf4d5-127">Przykładem protokołu powiązania może być HTTP, natomiast informacje o powiązaniu mogą zawierać adres IP, port, nagłówek hosta itp.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-127">An example of a binding protocol can be HTTP, whereas binding information can contain an IP address, Port, host header, etc.</span></span><br /><br /> <span data-ttu-id="bf4d5-128">Usługi IIS obsługują Określanie wielu powiązań usług IIS dla każdej witryny, co daje w wyniku wiele adresów bazowych na schemat.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-128">IIS supports specifying multiple IIS bindings per site, which results in multiple base addresses per scheme.</span></span> <span data-ttu-id="bf4d5-129">Jednak usługa Windows Communication Foundation (WCF) hostowana w ramach lokacji umożliwia powiązanie z tylko jedną baseAddress na schemat.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-129">However, a Windows Communication Foundation (WCF) service hosted under a site allows binding to only one baseAddress per scheme.</span></span><br /><br /> <span data-ttu-id="bf4d5-130">Aby włączyć wiele powiązań usług IIS dla każdej witryny dla usługi Windows Communication Foundation (WCF), ustaw ten atrybut `true`na.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-130">To enable multiple IIS bindings per site for a Windows Communication Foundation (WCF) service, set this attribute to `true`.</span></span> <span data-ttu-id="bf4d5-131">Zauważ, że wiele powiązań witryny jest obsługiwana tylko dla protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-131">Notice that multiple site binding is supported only for the HTTP protocol.</span></span> <span data-ttu-id="bf4d5-132">Adres punktów końcowych w pliku konfiguracji musi być kompletnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-132">The address of endpoints in the configuration file needs to be a complete URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf4d5-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bf4d5-133">Child Elements</span></span>  
  
|<span data-ttu-id="bf4d5-134">Element</span><span class="sxs-lookup"><span data-stu-id="bf4d5-134">Element</span></span>|<span data-ttu-id="bf4d5-135">Opis</span><span class="sxs-lookup"><span data-stu-id="bf4d5-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf4d5-136">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="bf4d5-136">\<baseAddressPrefixFilters></span></span>](baseaddressprefixfilters.md)|<span data-ttu-id="bf4d5-137">Kolekcja elementów konfiguracji, które określają filtry prefiksu dla adresów bazowych używanych przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-137">A collection of configuration elements that specify prefix filters for the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="bf4d5-138">\<> ServiceActivations</span><span class="sxs-lookup"><span data-stu-id="bf4d5-138">\<serviceActivations></span></span>](serviceactivations.md)|<span data-ttu-id="bf4d5-139">Sekcja konfiguracji opisująca ustawienia aktywacji.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-139">A configuration section that describes activation settings.</span></span>|  
|[<span data-ttu-id="bf4d5-140">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="bf4d5-140">\<transportConfigurationTypes></span></span>](transportconfigurationtypes.md)|<span data-ttu-id="bf4d5-141">Kolekcja elementów konfiguracji, które identyfikują typ określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-141">A collection of configuration elements that identify the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf4d5-142">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bf4d5-142">Parent Elements</span></span>  
  
|<span data-ttu-id="bf4d5-143">Element</span><span class="sxs-lookup"><span data-stu-id="bf4d5-143">Element</span></span>|<span data-ttu-id="bf4d5-144">Opis</span><span class="sxs-lookup"><span data-stu-id="bf4d5-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bf4d5-145">Modelu</span><span class="sxs-lookup"><span data-stu-id="bf4d5-145">serviceModel</span></span>|<span data-ttu-id="bf4d5-146">Element główny wszystkich elementów konfiguracji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="bf4d5-146">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf4d5-147">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf4d5-147">Remarks</span></span>  
 <span data-ttu-id="bf4d5-148">Domyślnie usługi WCF działają równolegle z ASP.NET w domenach hostowanych aplikacji (AppDomain).</span><span class="sxs-lookup"><span data-stu-id="bf4d5-148">By default, WCF services run side-by-side with ASP.NET in hosted Application Domains (AppDomain).</span></span> <span data-ttu-id="bf4d5-149">Mimo że WCF i ASP.NET mogą współistnieć w tej samej domenie aplikacji, domyślnie żądania WCF nie są przetwarzane przez potok HTTP ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-149">Even though WCF and ASP.NET can coexist in the same AppDomain, WCF requests are not processed by the ASP.NET HTTP Pipeline by default.</span></span> <span data-ttu-id="bf4d5-150">W związku z tym niektóre elementy platformy aplikacji ASP.NET nie są dostępne dla usług WCF.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-150">As a result, several elements of the ASP.NET application platform are not available to WCF services.</span></span> <span data-ttu-id="bf4d5-151">Obejmują one</span><span class="sxs-lookup"><span data-stu-id="bf4d5-151">These include</span></span>  
  
- <span data-ttu-id="bf4d5-152">ASP.NET autoryzacja plików/adresów URL</span><span class="sxs-lookup"><span data-stu-id="bf4d5-152">ASP.NET File/URL Authorization</span></span>  
  
- <span data-ttu-id="bf4d5-153">Personifikacja ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bf4d5-153">ASP.NET Impersonation</span></span>  
  
- <span data-ttu-id="bf4d5-154">Stan sesji na podstawie pliku cookie</span><span class="sxs-lookup"><span data-stu-id="bf4d5-154">Cookie-based Session State</span></span>  
  
- <span data-ttu-id="bf4d5-155">HttpContext. Current</span><span class="sxs-lookup"><span data-stu-id="bf4d5-155">HttpContext.Current</span></span>  
  
- <span data-ttu-id="bf4d5-156">Rozszerzalność potoku za pomocą niestandardowego modułu HttpModule</span><span class="sxs-lookup"><span data-stu-id="bf4d5-156">Pipeline Extensibility via custom HttpModule</span></span>  
  
 <span data-ttu-id="bf4d5-157">Jeśli usługi WCF muszą działać w kontekście ASP.NET i komunikować się tylko za pośrednictwem protokołu HTTP, można użyć trybu zgodności ASP.NET programu WCF.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-157">If your WCF services need to function in the ASP.NET context, and communicate only over HTTP, you can use WCF’s ASP.NET compatibility mode.</span></span> <span data-ttu-id="bf4d5-158">Ten tryb jest włączony, `aspNetCompatibilityEnabled` gdy atrybut jest ustawiony na `true` na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-158">This mode is turned on when the `aspNetCompatibilityEnabled` attribute is set to `true` at the application level.</span></span> <span data-ttu-id="bf4d5-159">Implementacje usług muszą deklarować możliwość uruchamiania w trybie zgodności przy użyciu <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-159">Service implementations must declare their ability to run in compatibility mode using the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> class.</span></span> <span data-ttu-id="bf4d5-160">Gdy tryb zgodności jest włączony,</span><span class="sxs-lookup"><span data-stu-id="bf4d5-160">When the compatibility mode is enabled,</span></span>  
  
- <span data-ttu-id="bf4d5-161">ASP.NET autoryzacja plików/adresów URL jest wymuszana przed autoryzacją WCF.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-161">ASP.NET File/URL Authorization is enforced prior to WCF authorization.</span></span> <span data-ttu-id="bf4d5-162">Decyzja o autoryzacji jest oparta na tożsamości na poziomie transportu żądania.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-162">An authorization decision is based on the transport-level identity of the request.</span></span> <span data-ttu-id="bf4d5-163">Tożsamości na poziomie komunikatu są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-163">Identities at the message level are ignored.</span></span>  
  
- <span data-ttu-id="bf4d5-164">Operacje usługi WCF zaczynają działać w kontekście personifikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-164">WCF service operations start to execute in the ASP.NET impersonation context.</span></span> <span data-ttu-id="bf4d5-165">W przypadku włączenia zarówno personifikacji ASP.NET, jak i personifikacji WCF dla określonej usługi stosuje się kontekst personifikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-165">If both ASP.NET impersonation and WCF impersonation are enabled for a specific service, the WCF impersonation context applies.</span></span>  
  
- <span data-ttu-id="bf4d5-166">Element HttpContext. Current może być używany z kodu usługi WCF, a usługi nie mogą uwidaczniać punktów końcowych innych niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-166">HttpContext.Current can be used from WCF service code, and services are prevented from exposing non-HTTP endpoints.</span></span>  
  
- <span data-ttu-id="bf4d5-167">Żądania WCF są przetwarzane przez potok ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-167">WCF requests are processed by the ASP.NET pipeline.</span></span> <span data-ttu-id="bf4d5-168">Elementy HttpModules, które zostały skonfigurowane do działania na żądania przychodzące mogą również przetwarzać żądania WCF.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-168">HttpModules that have been configured to act on incoming requests can also process WCF requests.</span></span> <span data-ttu-id="bf4d5-169">Mogą one obejmować składniki platformy ASP.NET (np. <xref:System.Web.SessionState.SessionStateModule>), a także niestandardowe moduły innych firm.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-169">These can include ASP.NET platform components (e.g., <xref:System.Web.SessionState.SessionStateModule>), as well as custom third party modules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf4d5-170">Przykład</span><span class="sxs-lookup"><span data-stu-id="bf4d5-170">Example</span></span>  
 <span data-ttu-id="bf4d5-171">Poniższy przykład kodu pokazuje, jak włączyć tryb zgodności ASP.</span><span class="sxs-lookup"><span data-stu-id="bf4d5-171">The following code sample shows how to enable ASP Compatibility Mode.</span></span>  
  
## <a name="code"></a><span data-ttu-id="bf4d5-172">Kod</span><span class="sxs-lookup"><span data-stu-id="bf4d5-172">Code</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a><span data-ttu-id="bf4d5-173">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf4d5-173">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="bf4d5-174">Hosting</span><span class="sxs-lookup"><span data-stu-id="bf4d5-174">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
- [<span data-ttu-id="bf4d5-175">Usługi WCF i platforma ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bf4d5-175">WCF Services and ASP.NET</span></span>](../../../wcf/feature-details/wcf-services-and-aspnet.md)
