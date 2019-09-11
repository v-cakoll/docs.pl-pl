---
title: <add> dla <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: dee2cd482efc841b7320ed2114a05000255466f3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850523"
---
# <a name="add-of-baseaddressprefixfilter"></a><span data-ttu-id="9fdb0-102">\<add> of \<baseAddressPrefixFilter></span><span class="sxs-lookup"><span data-stu-id="9fdb0-102">\<add> of \<baseAddressPrefixFilter></span></span>
<span data-ttu-id="9fdb0-103">Reprezentuje element konfiguracji, który określa filtr przekazywania, który udostępnia mechanizm wybierania odpowiednich powiązań Internet Information Services (IIS) podczas hostowania aplikacji Windows Communication Foundation (WCF) w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
<span data-ttu-id="9fdb0-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9fdb0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9fdb0-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9fdb0-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9fdb0-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="9fdb0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="9fdb0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<baseAddressPrefixFilters >** ](baseaddressprefixfilters.md)</span><span class="sxs-lookup"><span data-stu-id="9fdb0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddressPrefixFilters>**](baseaddressprefixfilters.md)</span></span>\
<span data-ttu-id="9fdb0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="9fdb0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fdb0-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="9fdb0-109">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9fdb0-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9fdb0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9fdb0-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9fdb0-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9fdb0-112">Attributes</span></span>  
  
|<span data-ttu-id="9fdb0-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9fdb0-113">Attribute</span></span>|<span data-ttu-id="9fdb0-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9fdb0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9fdb0-115">prefix</span><span class="sxs-lookup"><span data-stu-id="9fdb0-115">prefix</span></span>|<span data-ttu-id="9fdb0-116">Identyfikator URI, który jest używany do dopasowania części adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-116">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9fdb0-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9fdb0-117">Child Elements</span></span>  
 <span data-ttu-id="9fdb0-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9fdb0-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9fdb0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9fdb0-120">Element</span><span class="sxs-lookup"><span data-stu-id="9fdb0-120">Element</span></span>|<span data-ttu-id="9fdb0-121">Opis</span><span class="sxs-lookup"><span data-stu-id="9fdb0-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9fdb0-122">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="9fdb0-122">\<baseAddressPrefixFilters></span></span>](baseaddressprefixfilters.md)|<span data-ttu-id="9fdb0-123">Kolekcja elementów konfiguracji, które określają filtry przekazywania, które zapewniają mechanizm wybierania odpowiednich powiązań usług IIS podczas hostowania aplikacji Windows Communication Foundation (WCF) w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-123">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fdb0-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9fdb0-124">Remarks</span></span>  
 <span data-ttu-id="9fdb0-125">Filtr prefiksów umożliwia dostawcom hostingu współużytkowanie Określanie identyfikatorów URI, które mają być używane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-125">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="9fdb0-126">Umożliwia hostom udostępnionym hostowanie wielu aplikacji z różnymi adresami podstawowymi dla tego samego schematu w tej samej lokacji.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-126">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="9fdb0-127">Witryny sieci Web usług IIS są kontenerami dla aplikacji wirtualnych, które zawierają katalogi wirtualne.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-127">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="9fdb0-128">Dostęp do aplikacji w lokacji można uzyskać za pomocą jednego lub kilku powiązań usług IIS.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-128">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="9fdb0-129">Powiązania usług IIS udostępniają dwie informacje: powiązania protokołu i powiązania.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-129">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="9fdb0-130">Protokół powiązania (na przykład HTTP) definiuje schemat, w którym odbywa się komunikacja, a informacje o powiązaniu (na przykład adres IP, port, nagłówek hosta) zawierają dane używane do uzyskiwania dostępu do witryny.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-130">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="9fdb0-131">Usługi IIS obsługują Określanie wielu powiązań usług IIS dla każdej lokacji, co daje w wyniku wiele adresów bazowych dla każdego schematu.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-131">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="9fdb0-132">Ponieważ usługa WCF hostowana w lokacji umożliwia powiązanie tylko z jednym adresem podstawowym dla każdego schematu, można użyć funkcji filtru prefiksu, aby wybrać wymagany podstawowy adres usługi hostowanej.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-132">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="9fdb0-133">Przychodzące adresy podstawowe, dostarczane przez usługi IIS, są filtrowane na podstawie opcjonalnego filtru listy prefiksów.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-133">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="9fdb0-134">Na przykład witryna może zawierać następujące adresy podstawowe.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-134">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="9fdb0-135">Możesz użyć poniższego pliku konfiguracji, aby określić filtr prefiksu na poziomie elementu AppDomain.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-135">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="9fdb0-136">W tym przykładzie i `net.tcp://test1.fabrikam.com:8000` `http://test2.fabrikam.com:9000` są jedynymi adresami podstawowymi dla odpowiednich schematów, które mogą być przesyłane przez program.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-136">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="9fdb0-137">Domyślnie, gdy prefiks nie jest określony, wszystkie adresy są przesyłane przez.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-137">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="9fdb0-138">Określenie prefiksu zezwala tylko na przekazanie zgodnego adresu podstawowego dla tego schematu.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-138">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9fdb0-139">Filtr nie obsługuje żadnych symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-139">The filter does not support any wildcards.</span></span> <span data-ttu-id="9fdb0-140">Ponadto baseAddresses dostarczone przez usługi IIS mogą mieć adresy powiązane z innymi schematami nieobecnymi na `baseAddressPrefixFilters` liście.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-140">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="9fdb0-141">Te adresy nie są odfiltrowane.</span><span class="sxs-lookup"><span data-stu-id="9fdb0-141">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fdb0-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9fdb0-142">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="9fdb0-143">Hosting</span><span class="sxs-lookup"><span data-stu-id="9fdb0-143">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
