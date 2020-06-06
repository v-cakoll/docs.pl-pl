---
title: <add> dla <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: 8fdae02b558708a9b3f4535123752dce12dd5cf5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153143"
---
# <a name="add-of-baseaddressprefixfilter"></a><span data-ttu-id="3b7f8-102">\<add> dla \<baseAddressPrefixFilter></span><span class="sxs-lookup"><span data-stu-id="3b7f8-102">\<add> of \<baseAddressPrefixFilter></span></span>
<span data-ttu-id="3b7f8-103">Reprezentuje element konfiguracji, który określa filtr przekazywania, który udostępnia mechanizm wybierania odpowiednich powiązań Internet Information Services (IIS) podczas hostowania aplikacji Windows Communication Foundation (WCF) w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddressPrefixFilters>**](baseaddressprefixfilters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="3b7f8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3b7f8-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b7f8-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3b7f8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3b7f8-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b7f8-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3b7f8-107">Attributes</span></span>  
  
|<span data-ttu-id="3b7f8-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3b7f8-108">Attribute</span></span>|<span data-ttu-id="3b7f8-109">Opis</span><span class="sxs-lookup"><span data-stu-id="3b7f8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3b7f8-110">prefiks</span><span class="sxs-lookup"><span data-stu-id="3b7f8-110">prefix</span></span>|<span data-ttu-id="3b7f8-111">Identyfikator URI, który jest używany do dopasowania części adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-111">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b7f8-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3b7f8-112">Child Elements</span></span>  
 <span data-ttu-id="3b7f8-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3b7f8-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3b7f8-114">Parent Elements</span></span>  
  
|<span data-ttu-id="3b7f8-115">Element</span><span class="sxs-lookup"><span data-stu-id="3b7f8-115">Element</span></span>|<span data-ttu-id="3b7f8-116">Opis</span><span class="sxs-lookup"><span data-stu-id="3b7f8-116">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](baseaddressprefixfilters.md)|<span data-ttu-id="3b7f8-117">Kolekcja elementów konfiguracji, które określają filtry przekazywania, które zapewniają mechanizm wybierania odpowiednich powiązań usług IIS podczas hostowania aplikacji Windows Communication Foundation (WCF) w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-117">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b7f8-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3b7f8-118">Remarks</span></span>  
 <span data-ttu-id="3b7f8-119">Filtr prefiksów umożliwia dostawcom hostingu współużytkowanie Określanie identyfikatorów URI, które mają być używane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-119">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="3b7f8-120">Umożliwia hostom udostępnionym hostowanie wielu aplikacji z różnymi adresami podstawowymi dla tego samego schematu w tej samej lokacji.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-120">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="3b7f8-121">Witryny sieci Web usług IIS są kontenerami dla aplikacji wirtualnych, które zawierają katalogi wirtualne.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-121">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="3b7f8-122">Dostęp do aplikacji w lokacji można uzyskać za pomocą jednego lub kilku powiązań usług IIS.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-122">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="3b7f8-123">Powiązania usług IIS udostępniają dwie informacje: powiązania protokołu i powiązania.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-123">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="3b7f8-124">Protokół powiązania (na przykład HTTP) definiuje schemat, w którym odbywa się komunikacja, a informacje o powiązaniu (na przykład adres IP, port, nagłówek hosta) zawierają dane używane do uzyskiwania dostępu do witryny.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-124">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="3b7f8-125">Usługi IIS obsługują Określanie wielu powiązań usług IIS dla każdej lokacji, co daje w wyniku wiele adresów bazowych dla każdego schematu.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-125">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="3b7f8-126">Ponieważ usługa WCF hostowana w lokacji umożliwia powiązanie tylko z jednym adresem podstawowym dla każdego schematu, można użyć funkcji filtru prefiksu, aby wybrać wymagany podstawowy adres usługi hostowanej.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-126">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="3b7f8-127">Przychodzące adresy podstawowe, dostarczane przez usługi IIS, są filtrowane na podstawie opcjonalnego filtru listy prefiksów.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-127">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="3b7f8-128">Na przykład witryna może zawierać następujące adresy podstawowe:</span><span class="sxs-lookup"><span data-stu-id="3b7f8-128">For example, your site can contain the following base addresses:</span></span>
  
```
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="3b7f8-129">Możesz użyć poniższego pliku konfiguracji, aby określić filtr prefiksu na poziomie elementu AppDomain.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-129">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="3b7f8-130">W tym przykładzie `net.tcp://test1.fabrikam.com:8000` i `http://test2.fabrikam.com:9000` są jedynymi adresami podstawowymi dla odpowiednich schematów, które mogą być przesyłane przez program.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-130">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="3b7f8-131">Domyślnie, gdy prefiks nie jest określony, wszystkie adresy są przesyłane przez.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-131">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="3b7f8-132">Określenie prefiksu zezwala tylko na przekazanie zgodnego adresu podstawowego dla tego schematu.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-132">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b7f8-133">Filtr nie obsługuje żadnych symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-133">The filter does not support any wildcards.</span></span> <span data-ttu-id="3b7f8-134">Ponadto baseAddresses dostarczone przez usługi IIS mogą mieć adresy powiązane z innymi schematami nieobecnymi na `baseAddressPrefixFilters` liście.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-134">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="3b7f8-135">Te adresy nie są odfiltrowane.</span><span class="sxs-lookup"><span data-stu-id="3b7f8-135">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b7f8-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b7f8-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="3b7f8-137">Hosting</span><span class="sxs-lookup"><span data-stu-id="3b7f8-137">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
