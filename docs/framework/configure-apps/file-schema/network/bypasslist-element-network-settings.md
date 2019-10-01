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
ms.openlocfilehash: 1dda43be8c0e0c94bdf7b57b67aa4d403b547f97
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699542"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="506f7-102">\<bypasslist >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="506f7-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="506f7-103">Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="506f7-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  
  
[<span data-ttu-id="506f7-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="506f7-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="506f7-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="506f7-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="506f7-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="506f7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="506f7-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<bypasslist >**</span><span class="sxs-lookup"><span data-stu-id="506f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="506f7-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="506f7-108">Syntax</span></span>  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="506f7-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="506f7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="506f7-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="506f7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="506f7-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="506f7-111">Attributes</span></span>  
 <span data-ttu-id="506f7-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="506f7-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="506f7-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="506f7-113">Child Elements</span></span>  
  
|<span data-ttu-id="506f7-114">**Element**</span><span class="sxs-lookup"><span data-stu-id="506f7-114">**Element**</span></span>|<span data-ttu-id="506f7-115">**Opis**</span><span class="sxs-lookup"><span data-stu-id="506f7-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="506f7-116">add</span><span class="sxs-lookup"><span data-stu-id="506f7-116">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="506f7-117">Dodaje adres IP lub nazwę DNS do listy obejścia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="506f7-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="506f7-118">Wyczyść</span><span class="sxs-lookup"><span data-stu-id="506f7-118">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="506f7-119">Czyści listę pomijania.</span><span class="sxs-lookup"><span data-stu-id="506f7-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="506f7-120">remove</span><span class="sxs-lookup"><span data-stu-id="506f7-120">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="506f7-121">Usuwa adres IP lub nazwę DNS z listy obejścia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="506f7-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="506f7-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="506f7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="506f7-123">**Element**</span><span class="sxs-lookup"><span data-stu-id="506f7-123">**Element**</span></span>|<span data-ttu-id="506f7-124">**Opis**</span><span class="sxs-lookup"><span data-stu-id="506f7-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="506f7-125">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="506f7-125">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="506f7-126">Konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="506f7-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="506f7-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="506f7-127">Remarks</span></span>  
 <span data-ttu-id="506f7-128">Lista obejścia zawiera wyrażenia regularne, które opisują identyfikatory URI, których wystąpienia <xref:System.Net.WebRequest> uzyskują dostęp bezpośrednio, a nie za pomocą serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="506f7-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="506f7-129">Należy zachować ostrożność podczas określania wyrażenia regularnego dla tego elementu.</span><span class="sxs-lookup"><span data-stu-id="506f7-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="506f7-130">Wyrażenie regularne "[a-z] + @no__t -0.contoso\\.com" jest zgodne z dowolnym hostem w domenie contoso.com, ale również jest zgodne z dowolnym hostem w domenie contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="506f7-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="506f7-131">Aby dopasować tylko hosta w domenie contoso.com, użyj kotwicy ("$"): "[a-z] + @no__t -0.contoso\\.com $".</span><span class="sxs-lookup"><span data-stu-id="506f7-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="506f7-132">Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz. [.NET Framework wyrażeń regularnych](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="506f7-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="506f7-133">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="506f7-133">Configuration Files</span></span>  
 <span data-ttu-id="506f7-134">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="506f7-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="506f7-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="506f7-135">Example</span></span>  
 <span data-ttu-id="506f7-136">Poniższy przykład dodaje dwa adresy do listy pomijania.</span><span class="sxs-lookup"><span data-stu-id="506f7-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="506f7-137">Najpierw pomija serwer proxy dla wszystkich serwerów w domenie contoso.com; drugi pomija serwer proxy dla wszystkich serwerów, których adresy IP zaczynają się od 192,168.</span><span class="sxs-lookup"><span data-stu-id="506f7-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="506f7-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="506f7-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="506f7-139">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="506f7-139">Network Settings Schema</span></span>](index.md)
