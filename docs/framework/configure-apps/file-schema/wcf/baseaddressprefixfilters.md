---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 0673507b72690c3a5c7dcc35442c05e378dba43c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153038"
---
# <a name="baseaddressprefixfilters"></a><span data-ttu-id="a188d-101">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="a188d-101">\<baseAddressPrefixFilters></span></span>
<span data-ttu-id="a188d-102">Reprezentuje kolekcję elementów konfiguracji, które określają przechodzą przez filtry, które zapewniają mechanizm, aby wybrać odpowiednie powiązania internetowych usług informacyjnych (IIS) podczas hostowania aplikacji Windows Communication Foundation (WCF) w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="a188d-102">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="a188d-103">\<baseAddressPrefixFilters> nie rozpoznaje "localhost"; zamiast tego użyj w pełni kwalifikowanej nazwy maszyny.</span><span class="sxs-lookup"><span data-stu-id="a188d-103">\<baseAddressPrefixFilters> does not recognize "localhost"; use the fully qualified machine name instead.</span></span>  
  
<span data-ttu-id="a188d-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a188d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a188d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a188d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a188d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serwisHostingEnvironment>**](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="a188d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="a188d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddressPrefixFilters>**</span><span class="sxs-lookup"><span data-stu-id="a188d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddressPrefixFilters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a188d-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="a188d-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a188d-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a188d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a188d-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a188d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a188d-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a188d-111">Attributes</span></span>  
 <span data-ttu-id="a188d-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="a188d-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a188d-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a188d-113">Child Elements</span></span>  
  
|<span data-ttu-id="a188d-114">Element</span><span class="sxs-lookup"><span data-stu-id="a188d-114">Element</span></span>|<span data-ttu-id="a188d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a188d-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a188d-116">\<dodaj></span><span class="sxs-lookup"><span data-stu-id="a188d-116">\<add></span></span>](add-of-baseaddressprefixfilter.md)|<span data-ttu-id="a188d-117">Dodaje element konfiguracji, który określa filtr prefiksu dla adresów podstawowych używanych przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="a188d-117">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a188d-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a188d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a188d-119">Element</span><span class="sxs-lookup"><span data-stu-id="a188d-119">Element</span></span>|<span data-ttu-id="a188d-120">Opis</span><span class="sxs-lookup"><span data-stu-id="a188d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a188d-121">\<serwisHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="a188d-121">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="a188d-122">Definiuje typ wystąpienia środowiska hostingu usługi dla określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="a188d-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a188d-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a188d-123">Remarks</span></span>  
 <span data-ttu-id="a188d-124">Filtr prefiksu umożliwia dostawcom hostingu współużytkowania określenie identyfikatorów URI, które mają być używane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="a188d-124">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="a188d-125">Umożliwia współużytkowane hosty do obsługi wielu aplikacji z różnymi adresami podstawowymi dla tego samego schematu w tej samej lokacji.</span><span class="sxs-lookup"><span data-stu-id="a188d-125">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="a188d-126">Witryny sieci Web usług IIS są kontenerami dla aplikacji wirtualnych, które zawierają katalogi wirtualne.</span><span class="sxs-lookup"><span data-stu-id="a188d-126">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="a188d-127">Dostęp do aplikacji w lokacji można uzyskać za pośrednictwem co najmniej jednego powiązania usług IIS.</span><span class="sxs-lookup"><span data-stu-id="a188d-127">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="a188d-128">Powiązania usługi IIS zawierają dwie informacje: protokół wiązania i wiążące informacje.</span><span class="sxs-lookup"><span data-stu-id="a188d-128">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="a188d-129">Protokół powiązania (na przykład HTTP) definiuje schemat, za pośrednictwem którego następuje komunikacja, a informacje o powiązaniach (na przykład adres IP, port, hostheader) zawierają dane używane do uzyskiwania dostępu do witryny.</span><span class="sxs-lookup"><span data-stu-id="a188d-129">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="a188d-130">Usługi IIS obsługują określanie wielu powiązań IIS dla każdej lokacji, co powoduje wiele adresów podstawowych dla każdego schematu.</span><span class="sxs-lookup"><span data-stu-id="a188d-130">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="a188d-131">Ponieważ usługa WCF hostowana w witrynie umożliwia powiązanie tylko jednego adresu podstawowego dla każdego schematu, można użyć funkcji filtru prefiksów, aby wybrać wymagany adres podstawowy usługi hostowanego.</span><span class="sxs-lookup"><span data-stu-id="a188d-131">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="a188d-132">Przychodzące adresy podstawowe dostarczane przez usługi IIS są filtrowane na podstawie opcjonalnego filtru listy prefiksów.</span><span class="sxs-lookup"><span data-stu-id="a188d-132">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="a188d-133">Na przykład witryna może zawierać następujące adresy podstawowe:</span><span class="sxs-lookup"><span data-stu-id="a188d-133">For example, your site can contain the following base addresses:</span></span>
  
```
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="a188d-134">Za pomocą następującego pliku konfiguracyjnego można określić filtr prefiksu na poziomie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a188d-134">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="a188d-135">W tym `net.tcp://test1.fabrikam.com:8000` przykładzie i `http://test2.fabrikam.com:9000` są jedynymi adresami podstawowymi dla ich odpowiednich systemów, które mogą być przekazywane.</span><span class="sxs-lookup"><span data-stu-id="a188d-135">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="a188d-136">Domyślnie, gdy prefiks nie jest określony, wszystkie adresy są przekazywane przez.</span><span class="sxs-lookup"><span data-stu-id="a188d-136">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="a188d-137">Określenie prefiksu umożliwia tylko pasujące adres podstawowy dla tego schematu, które mają być przekazywane przez.</span><span class="sxs-lookup"><span data-stu-id="a188d-137">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a188d-138">Filtr nie obsługuje żadnych symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="a188d-138">The filter does not support any wildcards.</span></span> <span data-ttu-id="a188d-139">Ponadto adresy podstawowe dostarczone przez usługi IIS mogą mieć adresy powiązane `baseAddressPrefixFilters` z innymi systemami, które nie są obecne w wykazie.</span><span class="sxs-lookup"><span data-stu-id="a188d-139">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="a188d-140">Adresy te nie są odfiltrowywały.</span><span class="sxs-lookup"><span data-stu-id="a188d-140">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a188d-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a188d-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="a188d-142">Hosting</span><span class="sxs-lookup"><span data-stu-id="a188d-142">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
