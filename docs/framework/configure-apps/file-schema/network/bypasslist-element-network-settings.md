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
ms.openlocfilehash: 97e69a4978aa4700d13a994619a65312cf70aeaa
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154949"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="a73d9-102">\<bypasslist>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="a73d9-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="a73d9-103">Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="a73d9-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**

## <a name="syntax"></a><span data-ttu-id="a73d9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a73d9-104">Syntax</span></span>  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a73d9-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a73d9-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a73d9-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a73d9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a73d9-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a73d9-107">Attributes</span></span>  
 <span data-ttu-id="a73d9-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="a73d9-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a73d9-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a73d9-109">Child Elements</span></span>  
  
|<span data-ttu-id="a73d9-110">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="a73d9-110">**Element**</span></span>|<span data-ttu-id="a73d9-111">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a73d9-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a73d9-112">add</span><span class="sxs-lookup"><span data-stu-id="a73d9-112">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="a73d9-113">Dodaje adres IP lub nazwę DNS do listy obejścia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="a73d9-113">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="a73d9-114">Wyczyść</span><span class="sxs-lookup"><span data-stu-id="a73d9-114">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="a73d9-115">Czyści listę pomijania.</span><span class="sxs-lookup"><span data-stu-id="a73d9-115">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="a73d9-116">usuwa</span><span class="sxs-lookup"><span data-stu-id="a73d9-116">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="a73d9-117">Usuwa adres IP lub nazwę DNS z listy obejścia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="a73d9-117">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a73d9-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a73d9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a73d9-119">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="a73d9-119">**Element**</span></span>|<span data-ttu-id="a73d9-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a73d9-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a73d9-121">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="a73d9-121">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="a73d9-122">Konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="a73d9-122">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a73d9-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a73d9-123">Remarks</span></span>  
 <span data-ttu-id="a73d9-124">Lista obejścia zawiera wyrażenia regularne, które opisują identyfikatory URI, które <xref:System.Net.WebRequest> uzyskują dostęp bezpośrednio, zamiast za pomocą serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="a73d9-124">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="a73d9-125">Należy zachować ostrożność podczas określania wyrażenia regularnego dla tego elementu.</span><span class="sxs-lookup"><span data-stu-id="a73d9-125">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="a73d9-126">Wyrażenie regularne "[a-z] + \\ . contoso \\ . com" dopasowuje dowolny host w domenie contoso.com, ale również jest zgodny z dowolnym hostem w domenie contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="a73d9-126">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="a73d9-127">Aby dopasować tylko hosta w domenie contoso.com, użyj kotwicy ("$"): "[a-z] + \\ . contoso \\ . com $".</span><span class="sxs-lookup"><span data-stu-id="a73d9-127">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="a73d9-128">Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz. [.NET Framework wyrażeń regularnych](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a73d9-128">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a73d9-129">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a73d9-129">Configuration Files</span></span>  
 <span data-ttu-id="a73d9-130">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="a73d9-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a73d9-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="a73d9-131">Example</span></span>  
 <span data-ttu-id="a73d9-132">Poniższy przykład dodaje dwa adresy do listy pomijania.</span><span class="sxs-lookup"><span data-stu-id="a73d9-132">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="a73d9-133">Najpierw pomija serwer proxy dla wszystkich serwerów w domenie contoso.com; drugi pomija serwer proxy dla wszystkich serwerów, których adresy IP zaczynają się od 192,168.</span><span class="sxs-lookup"><span data-stu-id="a73d9-133">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a73d9-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a73d9-134">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="a73d9-135">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="a73d9-135">Network Settings Schema</span></span>](index.md)
