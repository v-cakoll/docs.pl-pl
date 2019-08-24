---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 55ffcfb5c0c84d68033d082cbe451696bd3c9dc2
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988354"
---
# <a name="baseaddressprefixfilters"></a><span data-ttu-id="80239-101">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="80239-101">\<baseAddressPrefixFilters></span></span>
<span data-ttu-id="80239-102">Reprezentuje kolekcję elementów konfiguracji, które określają filtry przekazywania, które zapewniają mechanizm wybierania odpowiednich powiązań Internet Information Services (IIS) podczas hostowania aplikacji Windows Communication Foundation (WCF) w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="80239-102">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="80239-103">\<baseAddressPrefixFilters > nie rozpoznaje "localhost", zamiast tego użyj w pełni kwalifikowanej nazwy komputera.</span><span class="sxs-lookup"><span data-stu-id="80239-103">\<baseAddressPrefixFilters> does not recognize "localhost", use the fully qualified machine name instead.</span></span>  
  
 <span data-ttu-id="80239-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="80239-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="80239-105">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="80239-105">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80239-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="80239-106">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80239-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="80239-107">Attributes and Elements</span></span>  
 <span data-ttu-id="80239-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="80239-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80239-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="80239-109">Attributes</span></span>  
 <span data-ttu-id="80239-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="80239-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="80239-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="80239-111">Child Elements</span></span>  
  
|<span data-ttu-id="80239-112">Element</span><span class="sxs-lookup"><span data-stu-id="80239-112">Element</span></span>|<span data-ttu-id="80239-113">Opis</span><span class="sxs-lookup"><span data-stu-id="80239-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80239-114">\<add></span><span class="sxs-lookup"><span data-stu-id="80239-114">\<add></span></span>](add-of-baseaddressprefixfilter.md)|<span data-ttu-id="80239-115">Dodaje element konfiguracji, który określa filtr prefiksu dla adresów bazowych używanych przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="80239-115">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="80239-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="80239-116">Parent Elements</span></span>  
  
|<span data-ttu-id="80239-117">Element</span><span class="sxs-lookup"><span data-stu-id="80239-117">Element</span></span>|<span data-ttu-id="80239-118">Opis</span><span class="sxs-lookup"><span data-stu-id="80239-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80239-119">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="80239-119">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="80239-120">Definiuje typ tworzenia wystąpień środowiska hostingu usługi dla określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="80239-120">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80239-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80239-121">Remarks</span></span>  
 <span data-ttu-id="80239-122">Filtr prefiksów umożliwia dostawcom hostingu współużytkowanie Określanie identyfikatorów URI, które mają być używane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="80239-122">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="80239-123">Umożliwia hostom udostępnionym hostowanie wielu aplikacji z różnymi adresami podstawowymi dla tego samego schematu w tej samej lokacji.</span><span class="sxs-lookup"><span data-stu-id="80239-123">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="80239-124">Witryny sieci Web usług IIS są kontenerami dla aplikacji wirtualnych, które zawierają katalogi wirtualne.</span><span class="sxs-lookup"><span data-stu-id="80239-124">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="80239-125">Dostęp do aplikacji w lokacji można uzyskać za pomocą co najmniej jednego powiązania usług IIS.</span><span class="sxs-lookup"><span data-stu-id="80239-125">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="80239-126">Powiązania usług IIS udostępniają dwie informacje: powiązania protokołu i powiązania.</span><span class="sxs-lookup"><span data-stu-id="80239-126">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="80239-127">Protokół powiązania (na przykład HTTP) definiuje schemat, w którym odbywa się komunikacja, a informacje o powiązaniu (na przykład adres IP, port, nagłówek hosta) zawierają dane używane do uzyskiwania dostępu do witryny.</span><span class="sxs-lookup"><span data-stu-id="80239-127">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="80239-128">Usługi IIS obsługują Określanie wielu powiązań usług IIS dla każdej lokacji, co daje w wyniku wiele adresów bazowych dla każdego schematu.</span><span class="sxs-lookup"><span data-stu-id="80239-128">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="80239-129">Ponieważ usługa WCF hostowana w lokacji umożliwia powiązanie tylko z jednym adresem podstawowym dla każdego schematu, można użyć funkcji filtru prefiksu, aby wybrać wymagany podstawowy adres usługi hostowanej.</span><span class="sxs-lookup"><span data-stu-id="80239-129">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="80239-130">Przychodzące adresy podstawowe, dostarczane przez usługi IIS, są filtrowane na podstawie opcjonalnego filtru listy prefiksów.</span><span class="sxs-lookup"><span data-stu-id="80239-130">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="80239-131">Na przykład witryna może zawierać następujące adresy podstawowe.</span><span class="sxs-lookup"><span data-stu-id="80239-131">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="80239-132">Możesz użyć poniższego pliku konfiguracji, aby określić filtr prefiksu na poziomie elementu AppDomain.</span><span class="sxs-lookup"><span data-stu-id="80239-132">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="80239-133">W tym przykładzie `net.tcp://test1.fabrikam.com:8000` i `http://test2.fabrikam.com:9000` są jedynymi adresami podstawowymi dla odpowiednich schematów, które mogą być przesyłane przez program.</span><span class="sxs-lookup"><span data-stu-id="80239-133">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="80239-134">Domyślnie, gdy prefiks nie jest określony, wszystkie adresy są przesyłane przez.</span><span class="sxs-lookup"><span data-stu-id="80239-134">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="80239-135">Określenie prefiksu zezwala tylko na przekazanie zgodnego adresu podstawowego dla tego schematu.</span><span class="sxs-lookup"><span data-stu-id="80239-135">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80239-136">Filtr nie obsługuje żadnych symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="80239-136">The filter does not support any wildcards.</span></span> <span data-ttu-id="80239-137">Ponadto baseAddresses dostarczone przez usługi IIS mogą mieć adresy powiązane z innymi schematami nieobecnymi na `baseAddressPrefixFilters` liście.</span><span class="sxs-lookup"><span data-stu-id="80239-137">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="80239-138">Te adresy nie są odfiltrowane.</span><span class="sxs-lookup"><span data-stu-id="80239-138">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80239-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80239-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="80239-140">Hosting</span><span class="sxs-lookup"><span data-stu-id="80239-140">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
