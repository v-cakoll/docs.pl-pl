---
title: '&lt;baseAddressPrefixFilters&gt;'
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 21a926d07aa818ce4ff5c2b85a04167fdd531047
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667248"
---
# <a name="ltbaseaddressprefixfiltersgt"></a><span data-ttu-id="526fc-102">&lt;baseAddressPrefixFilters&gt;</span><span class="sxs-lookup"><span data-stu-id="526fc-102">&lt;baseAddressPrefixFilters&gt;</span></span>
<span data-ttu-id="526fc-103">Reprezentuje kolekcję konfiguracji, które elementy, które określają przechodzą przez filtry, które zapewniają mechanizm wyboru odpowiednich powiązań usług Internet Information Services (IIS) w przypadku hostowania aplikacji Windows Communication Foundation (WCF) w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="526fc-103">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="526fc-104">\<baseAddressPrefixFilters > nie rozpoznaje "localhost", zamiast tego użyj w pełni kwalifikowanej nazwy komputera.</span><span class="sxs-lookup"><span data-stu-id="526fc-104">\<baseAddressPrefixFilters> does not recognize "localhost", use the fully qualified machine name instead.</span></span>  
  
 <span data-ttu-id="526fc-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="526fc-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="526fc-106">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="526fc-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="526fc-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="526fc-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="526fc-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="526fc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="526fc-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="526fc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="526fc-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="526fc-110">Attributes</span></span>  
 <span data-ttu-id="526fc-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="526fc-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="526fc-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="526fc-112">Child Elements</span></span>  
  
|<span data-ttu-id="526fc-113">Element</span><span class="sxs-lookup"><span data-stu-id="526fc-113">Element</span></span>|<span data-ttu-id="526fc-114">Opis</span><span class="sxs-lookup"><span data-stu-id="526fc-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="526fc-115">\<add></span><span class="sxs-lookup"><span data-stu-id="526fc-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddressprefixfilter.md)|<span data-ttu-id="526fc-116">Dodaje element konfiguracji, który określa filtr prefiksu adres podstawowy, używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="526fc-116">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="526fc-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="526fc-117">Parent Elements</span></span>  
  
|<span data-ttu-id="526fc-118">Element</span><span class="sxs-lookup"><span data-stu-id="526fc-118">Element</span></span>|<span data-ttu-id="526fc-119">Opis</span><span class="sxs-lookup"><span data-stu-id="526fc-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="526fc-120">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="526fc-120">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="526fc-121">Definiuje typ, który usługę hostingu środowiskowego dla danego transportu.</span><span class="sxs-lookup"><span data-stu-id="526fc-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="526fc-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="526fc-122">Remarks</span></span>  
 <span data-ttu-id="526fc-123">Filtr prefiksu umożliwia udostępniony dostawcy hostingu określić, które identyfikatory URI, które mają być używane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="526fc-123">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="526fc-124">Dzięki temu hosty udostępnione do hostowania wielu aplikacji przy użyciu różnych adresami podstawowymi dla tego samego schematu w tej samej lokacji.</span><span class="sxs-lookup"><span data-stu-id="526fc-124">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="526fc-125">Witryn sieci Web IIS są kontenerami dla aplikacji wirtualnych, które zawierają katalogów wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="526fc-125">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="526fc-126">Aplikacja w lokacji jest możliwy za pośrednictwem jednego lub więcej powiązań usług IIS.</span><span class="sxs-lookup"><span data-stu-id="526fc-126">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="526fc-127">Powiązania usługi IIS zapewniają dwóch rodzajów informacji: Protokół powiązania i informacje o powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="526fc-127">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="526fc-128">Powiązanie protokołu (na przykład HTTP) definiuje schemat, przez który dane są przesyłane i informacje (na przykład adres IP, portu, nagłówka hosta) zawiera dane używane do uzyskiwania dostępu do witryny.</span><span class="sxs-lookup"><span data-stu-id="526fc-128">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="526fc-129">Program IIS obsługuje Określanie wielu powiązań usług IIS dla każdej lokacji, co skutkuje z wieloma adresami podstawowymi dla każdego schematu.</span><span class="sxs-lookup"><span data-stu-id="526fc-129">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="526fc-130">Ponieważ usługi WCF hostowanej przez witrynę pozwala na powiązanie tylko jeden adres podstawowy dla każdego schematu, można użyć funkcji filtrowania prefiksu i wybierz wymagany adres podstawowy usługi hostowanej.</span><span class="sxs-lookup"><span data-stu-id="526fc-130">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="526fc-131">Przychodzące adres podstawowy, dostarczone przez usługi IIS, są filtrowane w oparciu o filtr list opcjonalny prefiks.</span><span class="sxs-lookup"><span data-stu-id="526fc-131">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="526fc-132">Na przykład witryna może zawierać następujące adresy podstawowy.</span><span class="sxs-lookup"><span data-stu-id="526fc-132">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="526fc-133">Następujący plik konfiguracji służy do określania prefiksu filtr na poziomie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="526fc-133">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="526fc-134">W tym przykładzie `net.tcp://test1.fabrikam.com:8000` i `http://test2.fabrikam.com:9000` są tylko podstawowy adres ich systemów, które mogą być przekazywane.</span><span class="sxs-lookup"><span data-stu-id="526fc-134">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="526fc-135">Domyślnie jeśli nie określono prefiksu, wszystkie adresy są przekazywane.</span><span class="sxs-lookup"><span data-stu-id="526fc-135">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="526fc-136">Umożliwia określenie prefiksu tylko pasujących adres podstawowy dla tego schematu, które zostaną przekazane za pośrednictwem.</span><span class="sxs-lookup"><span data-stu-id="526fc-136">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="526fc-137">Filtr nie obsługuje żadnych symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="526fc-137">The filter does not support any wildcards.</span></span> <span data-ttu-id="526fc-138">Ponadto baseAddresses dostarczane przez usługi IIS wiążące adresy powiązany z innych systemów, które nie znajduje się w `baseAddressPrefixFilters` listy.</span><span class="sxs-lookup"><span data-stu-id="526fc-138">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="526fc-139">Te adresy nie są odfiltrowywane.</span><span class="sxs-lookup"><span data-stu-id="526fc-139">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="526fc-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="526fc-140">See also</span></span>
- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="526fc-141">Hosting</span><span class="sxs-lookup"><span data-stu-id="526fc-141">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
