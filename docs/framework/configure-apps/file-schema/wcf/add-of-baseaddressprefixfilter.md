---
title: <add> z <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: 9179abfb26229a845d9618afe30b088252c9c2db
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267662"
---
# <a name="add-of-baseaddressprefixfilter"></a><span data-ttu-id="e1b78-102">\<add> of \<baseAddressPrefixFilter></span><span class="sxs-lookup"><span data-stu-id="e1b78-102">\<add> of \<baseAddressPrefixFilter></span></span>
<span data-ttu-id="e1b78-103">Reprezentuje element konfiguracji, który określa przekazywanego filtr, który udostępnia mechanizm wyboru odpowiednich powiązań usług Internet Information Services (IIS) w przypadku hostowania aplikacji Windows Communication Foundation (WCF), w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="e1b78-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
 <span data-ttu-id="e1b78-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e1b78-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e1b78-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="e1b78-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="e1b78-106">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="e1b78-106">\<baseAddressPrefixFilters></span></span>  
<span data-ttu-id="e1b78-107">\<add></span><span class="sxs-lookup"><span data-stu-id="e1b78-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1b78-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1b78-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1b78-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e1b78-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e1b78-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e1b78-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1b78-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e1b78-111">Attributes</span></span>  
  
|<span data-ttu-id="e1b78-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e1b78-112">Attribute</span></span>|<span data-ttu-id="e1b78-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e1b78-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e1b78-114">Prefiks</span><span class="sxs-lookup"><span data-stu-id="e1b78-114">prefix</span></span>|<span data-ttu-id="e1b78-115">Identyfikator URI, który jest używany do dopasowywania część adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="e1b78-115">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1b78-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e1b78-116">Child Elements</span></span>  
 <span data-ttu-id="e1b78-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="e1b78-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1b78-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e1b78-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e1b78-119">Element</span><span class="sxs-lookup"><span data-stu-id="e1b78-119">Element</span></span>|<span data-ttu-id="e1b78-120">Opis</span><span class="sxs-lookup"><span data-stu-id="e1b78-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1b78-121">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="e1b78-121">\<baseAddressPrefixFilters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|<span data-ttu-id="e1b78-122">Kolekcja elementów konfiguracji, które określają filtry przekazywania zawierające mechanizm wyboru odpowiednich powiązań usług IIS, w przypadku hostowania aplikacji Windows Communication Foundation (WCF), w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="e1b78-122">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1b78-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1b78-123">Remarks</span></span>  
 <span data-ttu-id="e1b78-124">Filtr prefiksu umożliwia udostępniony dostawcy hostingu określić, które identyfikatory URI, które mają być używane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="e1b78-124">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="e1b78-125">Dzięki temu hosty udostępnione do hostowania wielu aplikacji przy użyciu różnych adresami podstawowymi dla tego samego schematu w tej samej lokacji.</span><span class="sxs-lookup"><span data-stu-id="e1b78-125">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="e1b78-126">Witryn sieci Web IIS są kontenerami dla aplikacji wirtualnych, które zawierają katalogów wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="e1b78-126">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="e1b78-127">Aplikacja w lokacji jest możliwy za pośrednictwem jednego lub więcej powiązań usług IIS.</span><span class="sxs-lookup"><span data-stu-id="e1b78-127">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="e1b78-128">Powiązania usługi IIS zapewniają dwóch rodzajów informacji: Protokół powiązania i informacje o powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="e1b78-128">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="e1b78-129">Powiązanie protokołu (na przykład HTTP) definiuje schemat, przez który dane są przesyłane i informacje (na przykład adres IP, portu, nagłówka hosta) zawiera dane używane do uzyskiwania dostępu do witryny.</span><span class="sxs-lookup"><span data-stu-id="e1b78-129">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="e1b78-130">Program IIS obsługuje Określanie wielu powiązań usług IIS dla każdej lokacji, co skutkuje z wieloma adresami podstawowymi dla każdego schematu.</span><span class="sxs-lookup"><span data-stu-id="e1b78-130">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="e1b78-131">Ponieważ usługi WCF hostowanej przez witrynę pozwala na powiązanie tylko jeden adres podstawowy dla każdego schematu, można użyć funkcji filtrowania prefiksu i wybierz wymagany adres podstawowy usługi hostowanej.</span><span class="sxs-lookup"><span data-stu-id="e1b78-131">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="e1b78-132">Przychodzące adres podstawowy, dostarczone przez usługi IIS, są filtrowane w oparciu o filtr list opcjonalny prefiks.</span><span class="sxs-lookup"><span data-stu-id="e1b78-132">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="e1b78-133">Na przykład witryna może zawierać następujące adresy podstawowy.</span><span class="sxs-lookup"><span data-stu-id="e1b78-133">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="e1b78-134">Następujący plik konfiguracji służy do określania prefiksu filtr na poziomie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1b78-134">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="e1b78-135">W tym przykładzie `net.tcp://test1.fabrikam.com:8000` i `http://test2.fabrikam.com:9000` są tylko podstawowy adres ich systemów, które mogą być przekazywane.</span><span class="sxs-lookup"><span data-stu-id="e1b78-135">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="e1b78-136">Domyślnie jeśli nie określono prefiksu, wszystkie adresy są przekazywane.</span><span class="sxs-lookup"><span data-stu-id="e1b78-136">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="e1b78-137">Umożliwia określenie prefiksu tylko pasujących adres podstawowy dla tego schematu, które zostaną przekazane za pośrednictwem.</span><span class="sxs-lookup"><span data-stu-id="e1b78-137">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1b78-138">Filtr nie obsługuje żadnych symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="e1b78-138">The filter does not support any wildcards.</span></span> <span data-ttu-id="e1b78-139">Ponadto baseAddresses dostarczane przez usługi IIS wiążące adresy powiązany z innych systemów, które nie znajduje się w `baseAddressPrefixFilters` listy.</span><span class="sxs-lookup"><span data-stu-id="e1b78-139">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="e1b78-140">Te adresy nie są odfiltrowywane.</span><span class="sxs-lookup"><span data-stu-id="e1b78-140">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1b78-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1b78-141">See also</span></span>
- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="e1b78-142">Hosting</span><span class="sxs-lookup"><span data-stu-id="e1b78-142">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
