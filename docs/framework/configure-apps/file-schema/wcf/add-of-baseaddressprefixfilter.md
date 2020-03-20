---
title: <add> dla <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: 8fdae02b558708a9b3f4535123752dce12dd5cf5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153143"
---
# <a name="add-of-baseaddressprefixfilter"></a><span data-ttu-id="7586e-102">\<dodaj> baseAddressPrefixFilter \<></span><span class="sxs-lookup"><span data-stu-id="7586e-102">\<add> of \<baseAddressPrefixFilter></span></span>
<span data-ttu-id="7586e-103">Reprezentuje element konfiguracji, który określa filtr przekazywania, który zapewnia mechanizm, aby wybrać odpowiednie powiązania internetowych usług informacyjnych (IIS) podczas hostowania aplikacji Windows Communication Foundation (WCF) w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="7586e-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
<span data-ttu-id="7586e-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7586e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7586e-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7586e-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7586e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serwisHostingEnvironment>**](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="7586e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="7586e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddressPrefixFilters>**](baseaddressprefixfilters.md)</span><span class="sxs-lookup"><span data-stu-id="7586e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddressPrefixFilters>**](baseaddressprefixfilters.md)</span></span>\
<span data-ttu-id="7586e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dodaj>**</span><span class="sxs-lookup"><span data-stu-id="7586e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7586e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="7586e-109">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7586e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7586e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7586e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7586e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7586e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7586e-112">Attributes</span></span>  
  
|<span data-ttu-id="7586e-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7586e-113">Attribute</span></span>|<span data-ttu-id="7586e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7586e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7586e-115">Prefiks</span><span class="sxs-lookup"><span data-stu-id="7586e-115">prefix</span></span>|<span data-ttu-id="7586e-116">Identyfikator URI, który jest używany do dopasowania części adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="7586e-116">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7586e-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7586e-117">Child Elements</span></span>  
 <span data-ttu-id="7586e-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="7586e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7586e-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7586e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7586e-120">Element</span><span class="sxs-lookup"><span data-stu-id="7586e-120">Element</span></span>|<span data-ttu-id="7586e-121">Opis</span><span class="sxs-lookup"><span data-stu-id="7586e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7586e-122">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="7586e-122">\<baseAddressPrefixFilters></span></span>](baseaddressprefixfilters.md)|<span data-ttu-id="7586e-123">Kolekcja elementów konfiguracji, które określają filtry przekazywania, które zapewniają mechanizm, aby wybrać odpowiednie powiązania usług IIS podczas hostowania aplikacji Programu Windows Communication Foundation (WCF) w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="7586e-123">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7586e-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7586e-124">Remarks</span></span>  
 <span data-ttu-id="7586e-125">Filtr prefiksu umożliwia dostawcom hostingu współużytkowania określenie identyfikatorów URI, które mają być używane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="7586e-125">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="7586e-126">Umożliwia współużytkowane hosty do obsługi wielu aplikacji z różnymi adresami podstawowymi dla tego samego schematu w tej samej lokacji.</span><span class="sxs-lookup"><span data-stu-id="7586e-126">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="7586e-127">Witryny sieci Web usług IIS są kontenerami dla aplikacji wirtualnych, które zawierają katalogi wirtualne.</span><span class="sxs-lookup"><span data-stu-id="7586e-127">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="7586e-128">Dostęp do aplikacji w lokacji można uzyskać za pośrednictwem jednego lub więcej powiązań usług IIS.</span><span class="sxs-lookup"><span data-stu-id="7586e-128">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="7586e-129">Powiązania usługi IIS zawierają dwie informacje: protokół wiązania i wiążące informacje.</span><span class="sxs-lookup"><span data-stu-id="7586e-129">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="7586e-130">Protokół powiązania (na przykład HTTP) definiuje schemat, za pośrednictwem którego następuje komunikacja, a informacje o powiązaniach (na przykład adres IP, port, hostheader) zawierają dane używane do uzyskiwania dostępu do witryny.</span><span class="sxs-lookup"><span data-stu-id="7586e-130">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="7586e-131">Usługi IIS obsługują określanie wielu powiązań IIS dla każdej lokacji, co powoduje wiele adresów podstawowych dla każdego schematu.</span><span class="sxs-lookup"><span data-stu-id="7586e-131">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="7586e-132">Ponieważ usługa WCF hostowana w witrynie umożliwia powiązanie tylko jednego adresu podstawowego dla każdego schematu, można użyć funkcji filtru prefiksów, aby wybrać wymagany adres podstawowy usługi hostowanego.</span><span class="sxs-lookup"><span data-stu-id="7586e-132">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="7586e-133">Przychodzące adresy podstawowe dostarczane przez usługi IIS są filtrowane na podstawie opcjonalnego filtru listy prefiksów.</span><span class="sxs-lookup"><span data-stu-id="7586e-133">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="7586e-134">Na przykład witryna może zawierać następujące adresy podstawowe:</span><span class="sxs-lookup"><span data-stu-id="7586e-134">For example, your site can contain the following base addresses:</span></span>
  
```
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="7586e-135">Za pomocą następującego pliku konfiguracyjnego można określić filtr prefiksu na poziomie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7586e-135">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
```xml  
<system.serviceModel>
  <serviceHostingEnvironment>
    <baseAddressPrefixFilters>
      <add prefix="net.tcp://test1.fabrikam.com:8000" />
      <add prefix="http://test2.fabrikam.com:9000" />
    </baseAddressPrefixFilters>
  </serviceHostingEnvironment>
</system.serviceModel>
```  
  
 <span data-ttu-id="7586e-136">W tym `net.tcp://test1.fabrikam.com:8000` przykładzie są `http://test2.fabrikam.com:9000` jedynymi adresami podstawowymi dla ich odpowiednich systemów, które mogą być przekazywane.</span><span class="sxs-lookup"><span data-stu-id="7586e-136">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="7586e-137">Domyślnie, gdy prefiks nie jest określony, wszystkie adresy są przekazywane przez.</span><span class="sxs-lookup"><span data-stu-id="7586e-137">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="7586e-138">Określenie prefiksu umożliwia tylko pasujące adres podstawowy dla tego schematu, które mają być przekazywane przez.</span><span class="sxs-lookup"><span data-stu-id="7586e-138">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7586e-139">Filtr nie obsługuje żadnych symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="7586e-139">The filter does not support any wildcards.</span></span> <span data-ttu-id="7586e-140">Ponadto adresy podstawowe dostarczone przez usługi IIS mogą mieć adresy powiązane `baseAddressPrefixFilters` z innymi systemami, które nie są obecne w wykazie.</span><span class="sxs-lookup"><span data-stu-id="7586e-140">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="7586e-141">Adresy te nie są odfiltrowywały.</span><span class="sxs-lookup"><span data-stu-id="7586e-141">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7586e-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7586e-142">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="7586e-143">Hosting</span><span class="sxs-lookup"><span data-stu-id="7586e-143">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
