---
title: <serviceHostingEnvironment>
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: 165dbed1b78d00f8d4dd3e482b9fee8a23db60da
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399613"
---
# \<serviceHostingEnvironment>
<span data-ttu-id="f71e6-101">Ten element definiuje typ tworzenia wystąpień środowiska hostingu usługi dla określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="f71e6-101">This element defines the type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="f71e6-102">Jeśli ten element jest pusty, używany jest typ domyślny.</span><span class="sxs-lookup"><span data-stu-id="f71e6-102">If this element is empty, the default type is used.</span></span> <span data-ttu-id="f71e6-103">Tego elementu można używać tylko w plikach konfiguracji na poziomie aplikacji lub komputera.</span><span class="sxs-lookup"><span data-stu-id="f71e6-103">This element can only be used at the application or machine level configuration files.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceHostingEnvironment>**  
  
## <a name="syntax"></a><span data-ttu-id="f71e6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f71e6-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f71e6-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f71e6-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f71e6-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f71e6-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f71e6-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f71e6-107">Attributes</span></span>  
  
|<span data-ttu-id="f71e6-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f71e6-108">Attribute</span></span>|<span data-ttu-id="f71e6-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f71e6-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f71e6-110">aspNetCompatibilityEnabled</span><span class="sxs-lookup"><span data-stu-id="f71e6-110">aspNetCompatibilityEnabled</span></span>|<span data-ttu-id="f71e6-111">Wartość logiczna wskazująca, czy tryb zgodności ASP.NET został włączony dla bieżącej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f71e6-111">A Boolean value indicating whether the ASP.NET compatibility mode has been turned on for the current application.</span></span> <span data-ttu-id="f71e6-112">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="f71e6-112">The default is `false`.</span></span><br /><br /> <span data-ttu-id="f71e6-113">Gdy ten atrybut jest ustawiony na `true` , żądania do Windows Communication Foundation (WCF) usługi przepływu za pośrednictwem potoku HTTP ASP.NET, a komunikacja za pośrednictwem protokołów innych niż HTTP jest zabronione.</span><span class="sxs-lookup"><span data-stu-id="f71e6-113">When this attribute is set to `true`, requests to Windows Communication Foundation (WCF) services flow through the ASP.NET HTTP pipeline, and communication over non-HTTP protocols is prohibited.</span></span> <span data-ttu-id="f71e6-114">Aby uzyskać więcej informacji, zobacz [usługi WCF i ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="f71e6-114">For more information, see [WCF Services and ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span></span>|  
|<span data-ttu-id="f71e6-115">minFreeMemoryPercentageToActivateService</span><span class="sxs-lookup"><span data-stu-id="f71e6-115">minFreeMemoryPercentageToActivateService</span></span>|<span data-ttu-id="f71e6-116">Liczba całkowita określająca minimalną ilość wolnej pamięci, która powinna być dostępna dla systemu, zanim będzie można aktywować usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="f71e6-116">An integer that specifies the minimum amount of free memory that should be available to the system, before a WCF service can be activated.</span></span> <span data-ttu-id="f71e6-117">**Przestroga:**  Określenie tego atrybutu wraz z częściowym zaufaniem w pliku Web. config usługi WCF spowoduje, że usługa zostanie <xref:System.Security.SecurityException> uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="f71e6-117">**Caution:**  Specifying this attribute along with partial trust in the web.config file of a WCF service will result in a <xref:System.Security.SecurityException> when the service is run.</span></span>|  
|<span data-ttu-id="f71e6-118">multipleSiteBindingsEnabled</span><span class="sxs-lookup"><span data-stu-id="f71e6-118">multipleSiteBindingsEnabled</span></span>|<span data-ttu-id="f71e6-119">Wartość logiczna określająca, czy włączono wiele powiązań usług IIS dla każdej witryny.</span><span class="sxs-lookup"><span data-stu-id="f71e6-119">A Boolean value that specifies whether multiple IIS bindings per site is enabled.</span></span><br /><br /> <span data-ttu-id="f71e6-120">Usługi IIS składają się z witryn sieci Web, które są kontenerami dla aplikacji wirtualnych zawierających katalogi wirtualne.</span><span class="sxs-lookup"><span data-stu-id="f71e6-120">IIS consists of web sites, which are containers for virtual applications containing virtual directories.</span></span> <span data-ttu-id="f71e6-121">Dostęp do aplikacji w lokacji można uzyskać za pomocą jednego lub kilku powiązań usług IIS.</span><span class="sxs-lookup"><span data-stu-id="f71e6-121">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="f71e6-122">Powiązanie usług IIS zawiera dwie informacje: powiązania dotyczące protokołu i powiązania.</span><span class="sxs-lookup"><span data-stu-id="f71e6-122">An IIS binding provides two pieces of information: a binding protocol and binding information.</span></span> <span data-ttu-id="f71e6-123">Protokół powiązania definiuje schemat, w którym odbywa się komunikacja, a informacje o powiązaniu są informacjami używanymi do uzyskiwania dostępu do witryny.</span><span class="sxs-lookup"><span data-stu-id="f71e6-123">Binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span> <span data-ttu-id="f71e6-124">Przykładem protokołu powiązania może być HTTP, natomiast informacje o powiązaniu mogą zawierać adres IP, port, nagłówek hosta itp.</span><span class="sxs-lookup"><span data-stu-id="f71e6-124">An example of a binding protocol can be HTTP, whereas binding information can contain an IP address, Port, host header, etc.</span></span><br /><br /> <span data-ttu-id="f71e6-125">Usługi IIS obsługują Określanie wielu powiązań usług IIS dla każdej witryny, co daje w wyniku wiele adresów bazowych na schemat.</span><span class="sxs-lookup"><span data-stu-id="f71e6-125">IIS supports specifying multiple IIS bindings per site, which results in multiple base addresses per scheme.</span></span> <span data-ttu-id="f71e6-126">Jednak usługa Windows Communication Foundation (WCF) hostowana w ramach lokacji umożliwia powiązanie z tylko jedną baseAddress na schemat.</span><span class="sxs-lookup"><span data-stu-id="f71e6-126">However, a Windows Communication Foundation (WCF) service hosted under a site allows binding to only one baseAddress per scheme.</span></span><br /><br /> <span data-ttu-id="f71e6-127">Aby włączyć wiele powiązań usług IIS dla każdej witryny dla usługi Windows Communication Foundation (WCF), ustaw ten atrybut na `true` .</span><span class="sxs-lookup"><span data-stu-id="f71e6-127">To enable multiple IIS bindings per site for a Windows Communication Foundation (WCF) service, set this attribute to `true`.</span></span> <span data-ttu-id="f71e6-128">Zauważ, że wiele powiązań witryny jest obsługiwana tylko dla protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f71e6-128">Notice that multiple site binding is supported only for the HTTP protocol.</span></span> <span data-ttu-id="f71e6-129">Adres punktów końcowych w pliku konfiguracji musi być kompletnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="f71e6-129">The address of endpoints in the configuration file needs to be a complete URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f71e6-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f71e6-130">Child Elements</span></span>  
  
|<span data-ttu-id="f71e6-131">Element</span><span class="sxs-lookup"><span data-stu-id="f71e6-131">Element</span></span>|<span data-ttu-id="f71e6-132">Opis</span><span class="sxs-lookup"><span data-stu-id="f71e6-132">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](baseaddressprefixfilters.md)|<span data-ttu-id="f71e6-133">Kolekcja elementów konfiguracji, które określają filtry prefiksu dla adresów bazowych używanych przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="f71e6-133">A collection of configuration elements that specify prefix filters for the base addresses used by the service host.</span></span>|  
|[\<serviceActivations>](serviceactivations.md)|<span data-ttu-id="f71e6-134">Sekcja konfiguracji opisująca ustawienia aktywacji.</span><span class="sxs-lookup"><span data-stu-id="f71e6-134">A configuration section that describes activation settings.</span></span>|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|<span data-ttu-id="f71e6-135">Kolekcja elementów konfiguracji, które identyfikują typ określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="f71e6-135">A collection of configuration elements that identify the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f71e6-136">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f71e6-136">Parent Elements</span></span>  
  
|<span data-ttu-id="f71e6-137">Element</span><span class="sxs-lookup"><span data-stu-id="f71e6-137">Element</span></span>|<span data-ttu-id="f71e6-138">Opis</span><span class="sxs-lookup"><span data-stu-id="f71e6-138">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f71e6-139">Modelu</span><span class="sxs-lookup"><span data-stu-id="f71e6-139">serviceModel</span></span>|<span data-ttu-id="f71e6-140">Element główny wszystkich elementów konfiguracji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f71e6-140">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f71e6-141">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f71e6-141">Remarks</span></span>  
 <span data-ttu-id="f71e6-142">Domyślnie usługi WCF działają równolegle z ASP.NET w domenach hostowanych aplikacji (AppDomain).</span><span class="sxs-lookup"><span data-stu-id="f71e6-142">By default, WCF services run side-by-side with ASP.NET in hosted Application Domains (AppDomain).</span></span> <span data-ttu-id="f71e6-143">Mimo że WCF i ASP.NET mogą współistnieć w tej samej domenie aplikacji, domyślnie żądania WCF nie są przetwarzane przez potok HTTP ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f71e6-143">Even though WCF and ASP.NET can coexist in the same AppDomain, WCF requests are not processed by the ASP.NET HTTP Pipeline by default.</span></span> <span data-ttu-id="f71e6-144">W związku z tym niektóre elementy platformy aplikacji ASP.NET nie są dostępne dla usług WCF.</span><span class="sxs-lookup"><span data-stu-id="f71e6-144">As a result, several elements of the ASP.NET application platform are not available to WCF services.</span></span> <span data-ttu-id="f71e6-145">Obejmują one</span><span class="sxs-lookup"><span data-stu-id="f71e6-145">These include</span></span>  
  
- <span data-ttu-id="f71e6-146">ASP.NET autoryzacja plików/adresów URL</span><span class="sxs-lookup"><span data-stu-id="f71e6-146">ASP.NET File/URL Authorization</span></span>  
  
- <span data-ttu-id="f71e6-147">Personifikacja w programie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f71e6-147">ASP.NET Impersonation</span></span>  
  
- <span data-ttu-id="f71e6-148">Stan sesji na podstawie pliku cookie</span><span class="sxs-lookup"><span data-stu-id="f71e6-148">Cookie-based Session State</span></span>  
  
- <span data-ttu-id="f71e6-149">HttpContext. Current</span><span class="sxs-lookup"><span data-stu-id="f71e6-149">HttpContext.Current</span></span>  
  
- <span data-ttu-id="f71e6-150">Rozszerzalność potoku za pomocą niestandardowego modułu HttpModule</span><span class="sxs-lookup"><span data-stu-id="f71e6-150">Pipeline Extensibility via custom HttpModule</span></span>  
  
 <span data-ttu-id="f71e6-151">Jeśli usługi WCF muszą działać w kontekście ASP.NET i komunikować się tylko za pośrednictwem protokołu HTTP, można użyć trybu zgodności ASP.NET programu WCF.</span><span class="sxs-lookup"><span data-stu-id="f71e6-151">If your WCF services need to function in the ASP.NET context, and communicate only over HTTP, you can use WCF’s ASP.NET compatibility mode.</span></span> <span data-ttu-id="f71e6-152">Ten tryb jest włączony, gdy `aspNetCompatibilityEnabled` atrybut jest ustawiony na `true` na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f71e6-152">This mode is turned on when the `aspNetCompatibilityEnabled` attribute is set to `true` at the application level.</span></span> <span data-ttu-id="f71e6-153">Implementacje usług muszą deklarować możliwość uruchamiania w trybie zgodności przy użyciu <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="f71e6-153">Service implementations must declare their ability to run in compatibility mode using the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> class.</span></span> <span data-ttu-id="f71e6-154">Gdy tryb zgodności jest włączony,</span><span class="sxs-lookup"><span data-stu-id="f71e6-154">When the compatibility mode is enabled,</span></span>  
  
- <span data-ttu-id="f71e6-155">ASP.NET autoryzacja plików/adresów URL jest wymuszana przed autoryzacją WCF.</span><span class="sxs-lookup"><span data-stu-id="f71e6-155">ASP.NET File/URL Authorization is enforced prior to WCF authorization.</span></span> <span data-ttu-id="f71e6-156">Decyzja o autoryzacji jest oparta na tożsamości na poziomie transportu żądania.</span><span class="sxs-lookup"><span data-stu-id="f71e6-156">An authorization decision is based on the transport-level identity of the request.</span></span> <span data-ttu-id="f71e6-157">Tożsamości na poziomie komunikatu są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f71e6-157">Identities at the message level are ignored.</span></span>  
  
- <span data-ttu-id="f71e6-158">Operacje usługi WCF zaczynają działać w kontekście personifikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f71e6-158">WCF service operations start to execute in the ASP.NET impersonation context.</span></span> <span data-ttu-id="f71e6-159">W przypadku włączenia zarówno personifikacji ASP.NET, jak i personifikacji WCF dla określonej usługi stosuje się kontekst personifikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="f71e6-159">If both ASP.NET impersonation and WCF impersonation are enabled for a specific service, the WCF impersonation context applies.</span></span>  
  
- <span data-ttu-id="f71e6-160">Element HttpContext. Current może być używany z kodu usługi WCF, a usługi nie mogą uwidaczniać punktów końcowych innych niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="f71e6-160">HttpContext.Current can be used from WCF service code, and services are prevented from exposing non-HTTP endpoints.</span></span>  
  
- <span data-ttu-id="f71e6-161">Żądania WCF są przetwarzane przez potok ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f71e6-161">WCF requests are processed by the ASP.NET pipeline.</span></span> <span data-ttu-id="f71e6-162">Elementy HttpModules, które zostały skonfigurowane do działania na żądania przychodzące mogą również przetwarzać żądania WCF.</span><span class="sxs-lookup"><span data-stu-id="f71e6-162">HttpModules that have been configured to act on incoming requests can also process WCF requests.</span></span> <span data-ttu-id="f71e6-163">Mogą one obejmować składniki platformy ASP.NET (np. <xref:System.Web.SessionState.SessionStateModule> ), a także niestandardowe moduły innych firm.</span><span class="sxs-lookup"><span data-stu-id="f71e6-163">These can include ASP.NET platform components (e.g., <xref:System.Web.SessionState.SessionStateModule>), as well as custom third party modules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f71e6-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="f71e6-164">Example</span></span>  
 <span data-ttu-id="f71e6-165">Poniższy przykład kodu pokazuje, jak włączyć tryb zgodności ASP.</span><span class="sxs-lookup"><span data-stu-id="f71e6-165">The following code sample shows how to enable ASP Compatibility Mode.</span></span>  
  
## <a name="code"></a><span data-ttu-id="f71e6-166">Kod</span><span class="sxs-lookup"><span data-stu-id="f71e6-166">Code</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a><span data-ttu-id="f71e6-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f71e6-167">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="f71e6-168">Hosting</span><span class="sxs-lookup"><span data-stu-id="f71e6-168">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
- [<span data-ttu-id="f71e6-169">Usługi WCF i platforma ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f71e6-169">WCF Services and ASP.NET</span></span>](../../../wcf/feature-details/wcf-services-and-aspnet.md)
