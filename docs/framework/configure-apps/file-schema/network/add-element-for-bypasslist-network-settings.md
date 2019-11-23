---
title: <add>, element dla bypasslist (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
ms.openlocfilehash: 1db0ba3b0a213de1175e6e0cee347753d2a413b7
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699612"
---
# <a name="add-element-for-bypasslist-network-settings"></a><span data-ttu-id="08351-102">\<dodać elementu > dla BypassList (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="08351-102">\<add> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="08351-103">Dodaje adres IP lub nazwę DNS do listy obejścia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="08351-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
[<span data-ttu-id="08351-104"> **> konfiguracji \<** </span><span class="sxs-lookup"><span data-stu-id="08351-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="08351-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="08351-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="08351-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="08351-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="08351-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<BypassList >** ](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="08351-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>  
<span data-ttu-id="08351-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dodaj >**</span><span class="sxs-lookup"><span data-stu-id="08351-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08351-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="08351-109">Syntax</span></span>  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08351-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="08351-110">Attributes and Elements</span></span>  
 <span data-ttu-id="08351-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="08351-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08351-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="08351-112">Attributes</span></span>  
  
|<span data-ttu-id="08351-113">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="08351-113">**Attribute**</span></span>|<span data-ttu-id="08351-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="08351-114">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="08351-115">**address**</span><span class="sxs-lookup"><span data-stu-id="08351-115">**address**</span></span>|<span data-ttu-id="08351-116">Wyrażenie regularne opisujące adres IP lub nazwę DNS.</span><span class="sxs-lookup"><span data-stu-id="08351-116">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08351-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="08351-117">Child Elements</span></span>  
 <span data-ttu-id="08351-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="08351-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08351-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="08351-119">Parent Elements</span></span>  
  
|<span data-ttu-id="08351-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="08351-120">**Element**</span></span>|<span data-ttu-id="08351-121">**Opis**</span><span class="sxs-lookup"><span data-stu-id="08351-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="08351-122">bypasslist</span><span class="sxs-lookup"><span data-stu-id="08351-122">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="08351-123">Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="08351-123">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08351-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="08351-124">Remarks</span></span>  
 <span data-ttu-id="08351-125">Element `add` wstawia wyrażenia regularne opisujące adresy IP lub nazwy serwerów DNS do listy adresów, które pomijają serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="08351-125">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="08351-126">Wartość atrybutu `address` powinna być wyrażeniem regularnym opisującym zestaw adresów IP lub nazw hostów.</span><span class="sxs-lookup"><span data-stu-id="08351-126">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="08351-127">Należy zachować ostrożność podczas określania wyrażenia regularnego dla tego elementu.</span><span class="sxs-lookup"><span data-stu-id="08351-127">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="08351-128">Wyrażenie regularne "[a-z] +\\. contoso\\. com" dopasowuje dowolnego hosta w domenie contoso.com, ale również jest zgodne z dowolnym hostem w domenie contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="08351-128">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="08351-129">Aby dopasować tylko hosta w domenie contoso.com, użyj kotwicy ("$"): "[a-z] +\\. contoso\\. com $".</span><span class="sxs-lookup"><span data-stu-id="08351-129">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="08351-130">Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz. [.NET Framework wyrażeń regularnych](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="08351-130">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="08351-131">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="08351-131">Configuration Files</span></span>  
 <span data-ttu-id="08351-132">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="08351-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="08351-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="08351-133">Example</span></span>  
 <span data-ttu-id="08351-134">Poniższy przykład dodaje dwa adresy do listy pomijania.</span><span class="sxs-lookup"><span data-stu-id="08351-134">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="08351-135">Najpierw pomija serwer proxy dla wszystkich serwerów w domenie contoso.com; drugi pomija serwer proxy dla wszystkich serwerów, których adres IP rozpoczyna się od 192,168.</span><span class="sxs-lookup"><span data-stu-id="08351-135">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="08351-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="08351-136">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="08351-137">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="08351-137">Network Settings Schema</span></span>](index.md)
