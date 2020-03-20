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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154949"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="e50e7-102">\<bypasslist> Element (Ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="e50e7-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="e50e7-103">Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie używają serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="e50e7-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

<span data-ttu-id="e50e7-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e50e7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e50e7-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e50e7-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="e50e7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e50e7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="e50e7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>obwodnicy**</span><span class="sxs-lookup"><span data-stu-id="e50e7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e50e7-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="e50e7-108">Syntax</span></span>  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e50e7-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e50e7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e50e7-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e50e7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e50e7-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e50e7-111">Attributes</span></span>  
 <span data-ttu-id="e50e7-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="e50e7-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e50e7-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e50e7-113">Child Elements</span></span>  
  
|<span data-ttu-id="e50e7-114">**Element**</span><span class="sxs-lookup"><span data-stu-id="e50e7-114">**Element**</span></span>|<span data-ttu-id="e50e7-115">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e50e7-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e50e7-116">Dodaj</span><span class="sxs-lookup"><span data-stu-id="e50e7-116">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="e50e7-117">Dodaje adres IP lub nazwę DNS do listy pomijania serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="e50e7-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="e50e7-118">Wyczyść</span><span class="sxs-lookup"><span data-stu-id="e50e7-118">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="e50e7-119">Czyści listę pomijania.</span><span class="sxs-lookup"><span data-stu-id="e50e7-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="e50e7-120">Usunąć</span><span class="sxs-lookup"><span data-stu-id="e50e7-120">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="e50e7-121">Usuwa adres IP lub nazwę DNS z listy pomijania serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="e50e7-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e50e7-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e50e7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e50e7-123">**Element**</span><span class="sxs-lookup"><span data-stu-id="e50e7-123">**Element**</span></span>|<span data-ttu-id="e50e7-124">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e50e7-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e50e7-125">Defaultproxy</span><span class="sxs-lookup"><span data-stu-id="e50e7-125">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="e50e7-126">Konfiguruje serwer proxy Protokołu transferu hipertekstu (HTTP).</span><span class="sxs-lookup"><span data-stu-id="e50e7-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e50e7-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e50e7-127">Remarks</span></span>  
 <span data-ttu-id="e50e7-128">Lista pomijania zawiera wyrażenia regularne opisujące <xref:System.Net.WebRequest> identyfikatory URI, do których wystąpienia uzyskują dostęp bezpośrednio, a nie za pośrednictwem serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="e50e7-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="e50e7-129">Należy zachować ostrożność podczas określania wyrażenia regularnego dla tego elementu.</span><span class="sxs-lookup"><span data-stu-id="e50e7-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="e50e7-130">Wyrażenie regularne "[a-z]+\\.contoso\\.com" pasuje do dowolnego hosta w domenie contoso.com, ale pasuje również do dowolnego hosta w domenie contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="e50e7-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="e50e7-131">Aby dopasować tylko hosta w domenie contoso.com, użyj kotwicy ("$"): "[a-z]+\\.contoso\\.com$".</span><span class="sxs-lookup"><span data-stu-id="e50e7-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="e50e7-132">Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz . [Wyrażenia regularne programu .NET Framework](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e50e7-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e50e7-133">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e50e7-133">Configuration Files</span></span>  
 <span data-ttu-id="e50e7-134">Ten element może być używany w pliku konfiguracyjnym aplikacji lub pliku konfiguracyjnym komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="e50e7-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e50e7-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="e50e7-135">Example</span></span>  
 <span data-ttu-id="e50e7-136">Poniższy przykład dodaje dwa adresy do listy pomijania.</span><span class="sxs-lookup"><span data-stu-id="e50e7-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="e50e7-137">Pierwszy omija serwer proxy dla wszystkich serwerów w domenie contoso.com; drugi omija serwer proxy dla wszystkich serwerów, których adresy IP zaczynają się od 192.168.</span><span class="sxs-lookup"><span data-stu-id="e50e7-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e50e7-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e50e7-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="e50e7-139">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="e50e7-139">Network Settings Schema</span></span>](index.md)
