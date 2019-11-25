---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: cdf3264d1631db8e61bbcc4f6febd7008099251b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968712"
---
# <a name="baseaddressprefixfilters"></a><span data-ttu-id="ab37a-101">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="ab37a-101">\<baseAddressPrefixFilters></span></span>
<span data-ttu-id="ab37a-102">Reprezentuje kolekcję elementów konfiguracji, które określają filtry przekazywania, które zapewniają mechanizm wybierania odpowiednich powiązań Internet Information Services (IIS) podczas hostowania aplikacji Windows Communication Foundation (WCF) w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="ab37a-102">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="ab37a-103">\<baseAddressPrefixFilters > nie rozpoznaje "localhost"; Zamiast tego użyj w pełni kwalifikowanej nazwy komputera.</span><span class="sxs-lookup"><span data-stu-id="ab37a-103">\<baseAddressPrefixFilters> does not recognize "localhost"; use the fully qualified machine name instead.</span></span>  
  
<span data-ttu-id="ab37a-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="ab37a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ab37a-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="ab37a-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ab37a-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="ab37a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="ab37a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<baseAddressPrefixFilters >**</span><span class="sxs-lookup"><span data-stu-id="ab37a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddressPrefixFilters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab37a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab37a-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab37a-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ab37a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ab37a-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ab37a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab37a-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ab37a-111">Attributes</span></span>  
 <span data-ttu-id="ab37a-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="ab37a-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ab37a-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ab37a-113">Child Elements</span></span>  
  
|<span data-ttu-id="ab37a-114">Element</span><span class="sxs-lookup"><span data-stu-id="ab37a-114">Element</span></span>|<span data-ttu-id="ab37a-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ab37a-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab37a-116">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="ab37a-116">\<add></span></span>](add-of-baseaddressprefixfilter.md)|<span data-ttu-id="ab37a-117">Dodaje element konfiguracji, który określa filtr prefiksu dla adresów bazowych używanych przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="ab37a-117">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ab37a-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ab37a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ab37a-119">Element</span><span class="sxs-lookup"><span data-stu-id="ab37a-119">Element</span></span>|<span data-ttu-id="ab37a-120">Opis</span><span class="sxs-lookup"><span data-stu-id="ab37a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab37a-121">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="ab37a-121">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="ab37a-122">Definiuje typ tworzenia wystąpień środowiska hostingu usługi dla określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="ab37a-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab37a-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab37a-123">Remarks</span></span>  
 <span data-ttu-id="ab37a-124">Filtr prefiksów umożliwia dostawcom hostingu współużytkowanie Określanie identyfikatorów URI, które mają być używane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="ab37a-124">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="ab37a-125">Umożliwia hostom udostępnionym hostowanie wielu aplikacji z różnymi adresami podstawowymi dla tego samego schematu w tej samej lokacji.</span><span class="sxs-lookup"><span data-stu-id="ab37a-125">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="ab37a-126">Witryny sieci Web usług IIS są kontenerami dla aplikacji wirtualnych, które zawierają katalogi wirtualne.</span><span class="sxs-lookup"><span data-stu-id="ab37a-126">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="ab37a-127">Dostęp do aplikacji w lokacji można uzyskać za pomocą co najmniej jednego powiązania usług IIS.</span><span class="sxs-lookup"><span data-stu-id="ab37a-127">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="ab37a-128">Powiązania usług IIS udostępniają dwie informacje: powiązania protokołu i powiązania.</span><span class="sxs-lookup"><span data-stu-id="ab37a-128">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="ab37a-129">Protokół powiązania (na przykład HTTP) definiuje schemat, w którym odbywa się komunikacja, a informacje o powiązaniu (na przykład adres IP, port, nagłówek hosta) zawierają dane używane do uzyskiwania dostępu do witryny.</span><span class="sxs-lookup"><span data-stu-id="ab37a-129">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="ab37a-130">Usługi IIS obsługują Określanie wielu powiązań usług IIS dla każdej lokacji, co daje w wyniku wiele adresów bazowych dla każdego schematu.</span><span class="sxs-lookup"><span data-stu-id="ab37a-130">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="ab37a-131">Ponieważ usługa WCF hostowana w lokacji umożliwia powiązanie tylko z jednym adresem podstawowym dla każdego schematu, można użyć funkcji filtru prefiksu, aby wybrać wymagany podstawowy adres usługi hostowanej.</span><span class="sxs-lookup"><span data-stu-id="ab37a-131">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="ab37a-132">Przychodzące adresy podstawowe, dostarczane przez usługi IIS, są filtrowane na podstawie opcjonalnego filtru listy prefiksów.</span><span class="sxs-lookup"><span data-stu-id="ab37a-132">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="ab37a-133">Na przykład witryna może zawierać następujące adresy podstawowe:</span><span class="sxs-lookup"><span data-stu-id="ab37a-133">For example, your site can contain the following base addresses:</span></span>
  
``` 
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="ab37a-134">Możesz użyć poniższego pliku konfiguracji, aby określić filtr prefiksu na poziomie elementu AppDomain.</span><span class="sxs-lookup"><span data-stu-id="ab37a-134">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="ab37a-135">W tym przykładzie `net.tcp://test1.fabrikam.com:8000` i `http://test2.fabrikam.com:9000` są jedynymi adresami podstawowymi dla odpowiednich schematów, które mogą być przesyłane przez program.</span><span class="sxs-lookup"><span data-stu-id="ab37a-135">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="ab37a-136">Domyślnie, gdy prefiks nie jest określony, wszystkie adresy są przesyłane przez.</span><span class="sxs-lookup"><span data-stu-id="ab37a-136">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="ab37a-137">Określenie prefiksu zezwala tylko na przekazanie zgodnego adresu podstawowego dla tego schematu.</span><span class="sxs-lookup"><span data-stu-id="ab37a-137">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab37a-138">Filtr nie obsługuje żadnych symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="ab37a-138">The filter does not support any wildcards.</span></span> <span data-ttu-id="ab37a-139">Ponadto baseAddresses udostępniane przez usługi IIS mogą mieć adresy powiązane z innymi schematami nieobecnymi na liście `baseAddressPrefixFilters`.</span><span class="sxs-lookup"><span data-stu-id="ab37a-139">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="ab37a-140">Te adresy nie są odfiltrowane.</span><span class="sxs-lookup"><span data-stu-id="ab37a-140">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab37a-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab37a-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="ab37a-142">Hosting</span><span class="sxs-lookup"><span data-stu-id="ab37a-142">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
