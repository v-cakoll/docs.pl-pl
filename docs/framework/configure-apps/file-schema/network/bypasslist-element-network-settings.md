---
title: <bypasslist>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: d3d986dae478f49504dae21b9f39574b7887b4d2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674626"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="9eb86-102">\<bypasslist >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="9eb86-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="9eb86-103">Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="9eb86-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  
  
 <span data-ttu-id="9eb86-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="9eb86-104">\<configuration></span></span>  
<span data-ttu-id="9eb86-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="9eb86-105">\<system.net></span></span>  
<span data-ttu-id="9eb86-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="9eb86-106">\<defaultProxy></span></span>  
<span data-ttu-id="9eb86-107">\<bypasslist></span><span class="sxs-lookup"><span data-stu-id="9eb86-107">\<bypasslist></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eb86-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="9eb86-108">Syntax</span></span>  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9eb86-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9eb86-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9eb86-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9eb86-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9eb86-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9eb86-111">Attributes</span></span>  
 <span data-ttu-id="9eb86-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="9eb86-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9eb86-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9eb86-113">Child Elements</span></span>  
  
|<span data-ttu-id="9eb86-114">**Element**</span><span class="sxs-lookup"><span data-stu-id="9eb86-114">**Element**</span></span>|<span data-ttu-id="9eb86-115">**Opis**</span><span class="sxs-lookup"><span data-stu-id="9eb86-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9eb86-116">add</span><span class="sxs-lookup"><span data-stu-id="9eb86-116">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="9eb86-117">Dodaje adres IP lub nazwę DNS do listy pomijania proxy.</span><span class="sxs-lookup"><span data-stu-id="9eb86-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="9eb86-118">Usuń zaznaczenie</span><span class="sxs-lookup"><span data-stu-id="9eb86-118">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="9eb86-119">Czyści listę obejścia.</span><span class="sxs-lookup"><span data-stu-id="9eb86-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="9eb86-120">remove</span><span class="sxs-lookup"><span data-stu-id="9eb86-120">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="9eb86-121">Usuwa adres IP lub nazwa DNS z listy obejścia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="9eb86-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9eb86-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9eb86-122">Parent Elements</span></span>  
  
|<span data-ttu-id="9eb86-123">**Element**</span><span class="sxs-lookup"><span data-stu-id="9eb86-123">**Element**</span></span>|<span data-ttu-id="9eb86-124">**Opis**</span><span class="sxs-lookup"><span data-stu-id="9eb86-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9eb86-125">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="9eb86-125">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="9eb86-126">Umożliwia skonfigurowanie serwera proxy protokołu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="9eb86-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9eb86-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9eb86-127">Remarks</span></span>  
 <span data-ttu-id="9eb86-128">Lista pomijania zawiera wyrażeń regularnych, które opisują identyfikatory URI, <xref:System.Net.WebRequest> wystąpień dostęp do bezpośrednio zamiast za pośrednictwem serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="9eb86-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="9eb86-129">Należy zachować ostrożność podczas określania wyrażenia regularnego dla tego elementu.</span><span class="sxs-lookup"><span data-stu-id="9eb86-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="9eb86-130">Wyrażenie regularne "[a-z] +\\.contoso\\.com" dopasowań dowolnego hosta w domenie contoso.com, ale również pasuje do dowolnego hosta w domenie contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="9eb86-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="9eb86-131">Aby dopasować tylko na hoście w domenie contoso.com, użyj elementu zakotwiczenia ("$"): "[a-z] +\\.contoso\\.com$".</span><span class="sxs-lookup"><span data-stu-id="9eb86-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="9eb86-132">Aby uzyskać więcej informacji na temat wyrażeń regularnych Zobacz. [Wyrażeń regularnych programu .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="9eb86-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="9eb86-133">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9eb86-133">Configuration Files</span></span>  
 <span data-ttu-id="9eb86-134">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="9eb86-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9eb86-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="9eb86-135">Example</span></span>  
 <span data-ttu-id="9eb86-136">Poniższy przykład dodaje dwa adresy do listy pomijania.</span><span class="sxs-lookup"><span data-stu-id="9eb86-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="9eb86-137">Pierwszy pomija serwera proxy dla wszystkich serwerów w domenie contoso.com. drugi pomija serwera proxy dla wszystkich serwerom rozpocząć których adresy IP 192.168.</span><span class="sxs-lookup"><span data-stu-id="9eb86-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9eb86-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9eb86-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="9eb86-139">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="9eb86-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
