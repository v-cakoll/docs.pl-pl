---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 378db238d647be2248c0303f45aece42f7ea5b31
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227629"
---
# <a name="baseaddressprefixfilters"></a><span data-ttu-id="4dc37-101">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="4dc37-101">\<baseAddressPrefixFilters></span></span>
<span data-ttu-id="4dc37-102">Reprezentuje kolekcję konfiguracji, które elementy, które określają przechodzą przez filtry, które zapewniają mechanizm wyboru odpowiednich powiązań usług Internet Information Services (IIS) w przypadku hostowania aplikacji Windows Communication Foundation (WCF) w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="4dc37-102">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="4dc37-103">\<baseAddressPrefixFilters > nie rozpoznaje "localhost", zamiast tego użyj w pełni kwalifikowanej nazwy komputera.</span><span class="sxs-lookup"><span data-stu-id="4dc37-103">\<baseAddressPrefixFilters> does not recognize "localhost", use the fully qualified machine name instead.</span></span>  
  
 <span data-ttu-id="4dc37-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4dc37-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4dc37-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="4dc37-105">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dc37-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4dc37-106">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4dc37-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4dc37-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4dc37-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4dc37-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4dc37-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4dc37-109">Attributes</span></span>  
 <span data-ttu-id="4dc37-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="4dc37-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4dc37-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4dc37-111">Child Elements</span></span>  
  
|<span data-ttu-id="4dc37-112">Element</span><span class="sxs-lookup"><span data-stu-id="4dc37-112">Element</span></span>|<span data-ttu-id="4dc37-113">Opis</span><span class="sxs-lookup"><span data-stu-id="4dc37-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4dc37-114">\<add></span><span class="sxs-lookup"><span data-stu-id="4dc37-114">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddressprefixfilter.md)|<span data-ttu-id="4dc37-115">Dodaje element konfiguracji, który określa filtr prefiksu adres podstawowy, używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="4dc37-115">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4dc37-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4dc37-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4dc37-117">Element</span><span class="sxs-lookup"><span data-stu-id="4dc37-117">Element</span></span>|<span data-ttu-id="4dc37-118">Opis</span><span class="sxs-lookup"><span data-stu-id="4dc37-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4dc37-119">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="4dc37-119">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="4dc37-120">Definiuje typ, który usługę hostingu środowiskowego dla danego transportu.</span><span class="sxs-lookup"><span data-stu-id="4dc37-120">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4dc37-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4dc37-121">Remarks</span></span>  
 <span data-ttu-id="4dc37-122">Filtr prefiksu umożliwia udostępniony dostawcy hostingu określić, które identyfikatory URI, które mają być używane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="4dc37-122">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="4dc37-123">Dzięki temu hosty udostępnione do hostowania wielu aplikacji przy użyciu różnych adresami podstawowymi dla tego samego schematu w tej samej lokacji.</span><span class="sxs-lookup"><span data-stu-id="4dc37-123">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="4dc37-124">Witryn sieci Web IIS są kontenerami dla aplikacji wirtualnych, które zawierają katalogów wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="4dc37-124">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="4dc37-125">Aplikacja w lokacji jest możliwy za pośrednictwem jednego lub więcej powiązań usług IIS.</span><span class="sxs-lookup"><span data-stu-id="4dc37-125">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="4dc37-126">Powiązania usługi IIS zapewniają dwóch rodzajów informacji: Protokół powiązania i informacje o powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="4dc37-126">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="4dc37-127">Powiązanie protokołu (na przykład HTTP) definiuje schemat, przez który dane są przesyłane i informacje (na przykład adres IP, portu, nagłówka hosta) zawiera dane używane do uzyskiwania dostępu do witryny.</span><span class="sxs-lookup"><span data-stu-id="4dc37-127">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="4dc37-128">Program IIS obsługuje Określanie wielu powiązań usług IIS dla każdej lokacji, co skutkuje z wieloma adresami podstawowymi dla każdego schematu.</span><span class="sxs-lookup"><span data-stu-id="4dc37-128">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="4dc37-129">Ponieważ usługi WCF hostowanej przez witrynę pozwala na powiązanie tylko jeden adres podstawowy dla każdego schematu, można użyć funkcji filtrowania prefiksu i wybierz wymagany adres podstawowy usługi hostowanej.</span><span class="sxs-lookup"><span data-stu-id="4dc37-129">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="4dc37-130">Przychodzące adres podstawowy, dostarczone przez usługi IIS, są filtrowane w oparciu o filtr list opcjonalny prefiks.</span><span class="sxs-lookup"><span data-stu-id="4dc37-130">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="4dc37-131">Na przykład witryna może zawierać następujące adresy podstawowy.</span><span class="sxs-lookup"><span data-stu-id="4dc37-131">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="4dc37-132">Następujący plik konfiguracji służy do określania prefiksu filtr na poziomie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4dc37-132">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="4dc37-133">W tym przykładzie `net.tcp://test1.fabrikam.com:8000` i `http://test2.fabrikam.com:9000` są tylko podstawowy adres ich systemów, które mogą być przekazywane.</span><span class="sxs-lookup"><span data-stu-id="4dc37-133">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="4dc37-134">Domyślnie jeśli nie określono prefiksu, wszystkie adresy są przekazywane.</span><span class="sxs-lookup"><span data-stu-id="4dc37-134">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="4dc37-135">Umożliwia określenie prefiksu tylko pasujących adres podstawowy dla tego schematu, które zostaną przekazane za pośrednictwem.</span><span class="sxs-lookup"><span data-stu-id="4dc37-135">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4dc37-136">Filtr nie obsługuje żadnych symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="4dc37-136">The filter does not support any wildcards.</span></span> <span data-ttu-id="4dc37-137">Ponadto baseAddresses dostarczane przez usługi IIS wiążące adresy powiązany z innych systemów, które nie znajduje się w `baseAddressPrefixFilters` listy.</span><span class="sxs-lookup"><span data-stu-id="4dc37-137">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="4dc37-138">Te adresy nie są odfiltrowywane.</span><span class="sxs-lookup"><span data-stu-id="4dc37-138">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dc37-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4dc37-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="4dc37-140">Hosting</span><span class="sxs-lookup"><span data-stu-id="4dc37-140">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
