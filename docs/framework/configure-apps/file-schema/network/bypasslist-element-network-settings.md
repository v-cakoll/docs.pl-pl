---
title: <bypasslist>, element (ustawienia sieci)
description: <bypasslist>Element ustawień sieci zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie używają serwera proxy w .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 42b6ddf4c3d09bcf8ef0ada105cefedccc63b505
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504631"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="3e5fc-103">\<bypasslist>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="3e5fc-103">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="3e5fc-104">Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="3e5fc-104">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**

## <a name="syntax"></a><span data-ttu-id="3e5fc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e5fc-105">Syntax</span></span>  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e5fc-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3e5fc-106">Attributes and Elements</span></span>  
 <span data-ttu-id="3e5fc-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3e5fc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e5fc-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3e5fc-108">Attributes</span></span>  
 <span data-ttu-id="3e5fc-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="3e5fc-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3e5fc-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3e5fc-110">Child Elements</span></span>  
  
|<span data-ttu-id="3e5fc-111">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="3e5fc-111">**Element**</span></span>|<span data-ttu-id="3e5fc-112">**Opis**</span><span class="sxs-lookup"><span data-stu-id="3e5fc-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3e5fc-113">add</span><span class="sxs-lookup"><span data-stu-id="3e5fc-113">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="3e5fc-114">Dodaje adres IP lub nazwę DNS do listy obejścia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="3e5fc-114">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="3e5fc-115">Wyczyść</span><span class="sxs-lookup"><span data-stu-id="3e5fc-115">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="3e5fc-116">Czyści listę pomijania.</span><span class="sxs-lookup"><span data-stu-id="3e5fc-116">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="3e5fc-117">usuwa</span><span class="sxs-lookup"><span data-stu-id="3e5fc-117">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="3e5fc-118">Usuwa adres IP lub nazwę DNS z listy obejścia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="3e5fc-118">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3e5fc-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3e5fc-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3e5fc-120">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="3e5fc-120">**Element**</span></span>|<span data-ttu-id="3e5fc-121">**Opis**</span><span class="sxs-lookup"><span data-stu-id="3e5fc-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3e5fc-122">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="3e5fc-122">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="3e5fc-123">Konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="3e5fc-123">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e5fc-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e5fc-124">Remarks</span></span>  
 <span data-ttu-id="3e5fc-125">Lista obejścia zawiera wyrażenia regularne, które opisują identyfikatory URI, które <xref:System.Net.WebRequest> uzyskują dostęp bezpośrednio, zamiast za pomocą serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="3e5fc-125">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="3e5fc-126">Należy zachować ostrożność podczas określania wyrażenia regularnego dla tego elementu.</span><span class="sxs-lookup"><span data-stu-id="3e5fc-126">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="3e5fc-127">Wyrażenie regularne "[a-z] + \\ . contoso \\ . com" dopasowuje dowolny host w domenie contoso.com, ale również jest zgodny z dowolnym hostem w domenie contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="3e5fc-127">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="3e5fc-128">Aby dopasować tylko hosta w domenie contoso.com, użyj kotwicy ("$"): "[a-z] + \\ . contoso \\ . com $".</span><span class="sxs-lookup"><span data-stu-id="3e5fc-128">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="3e5fc-129">Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz. [.NET Framework wyrażeń regularnych](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="3e5fc-129">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3e5fc-130">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3e5fc-130">Configuration Files</span></span>  
 <span data-ttu-id="3e5fc-131">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="3e5fc-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e5fc-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e5fc-132">Example</span></span>  
 <span data-ttu-id="3e5fc-133">Poniższy przykład dodaje dwa adresy do listy pomijania.</span><span class="sxs-lookup"><span data-stu-id="3e5fc-133">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="3e5fc-134">Najpierw pomija serwer proxy dla wszystkich serwerów w domenie contoso.com; drugi pomija serwer proxy dla wszystkich serwerów, których adresy IP zaczynają się od 192,168.</span><span class="sxs-lookup"><span data-stu-id="3e5fc-134">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3e5fc-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e5fc-135">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="3e5fc-136">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="3e5fc-136">Network Settings Schema</span></span>](index.md)
