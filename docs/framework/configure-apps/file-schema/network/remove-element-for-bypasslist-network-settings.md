---
title: '&lt;Usuń&gt; elementu bypasslist — (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove elemment, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5c7918048743d53d8523ec399d1a11c67152a2bf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltremovegt-element-for-bypasslist-network-settings"></a><span data-ttu-id="87945-102">&lt;Usuń&gt; elementu bypasslist — (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="87945-102">&lt;remove&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="87945-103">Usuwa adres IP lub nazwa DNS lista obejść serwerów proxy.</span><span class="sxs-lookup"><span data-stu-id="87945-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>  
  
 <span data-ttu-id="87945-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="87945-104">\<configuration></span></span>  
<span data-ttu-id="87945-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="87945-105">\<system.net></span></span>  
<span data-ttu-id="87945-106">\<defaultProxy — ></span><span class="sxs-lookup"><span data-stu-id="87945-106">\<defaultProxy></span></span>  
<span data-ttu-id="87945-107">\<bypasslist — ></span><span class="sxs-lookup"><span data-stu-id="87945-107">\<bypasslist></span></span>  
<span data-ttu-id="87945-108">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="87945-108">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87945-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="87945-109">Syntax</span></span>  
  
```xml  
<remove   
  address="regular expression"   
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87945-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="87945-110">Attributes and Elements</span></span>  
 <span data-ttu-id="87945-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="87945-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87945-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="87945-112">Attributes</span></span>  
  
|<span data-ttu-id="87945-113">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="87945-113">**Attribute**</span></span>|<span data-ttu-id="87945-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="87945-114">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="87945-115">Wyrażenie regularne opisujące adresu IP lub nazwy DNS.</span><span class="sxs-lookup"><span data-stu-id="87945-115">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87945-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="87945-116">Child Elements</span></span>  
 <span data-ttu-id="87945-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="87945-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87945-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="87945-118">Parent Elements</span></span>  
  
|<span data-ttu-id="87945-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="87945-119">**Element**</span></span>|<span data-ttu-id="87945-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="87945-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="87945-121">bypasslist —</span><span class="sxs-lookup"><span data-stu-id="87945-121">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="87945-122">Zawiera zestaw wyrażeń regularnych, opisujących adresów, które nie korzystają z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="87945-122">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87945-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87945-123">Remarks</span></span>  
 <span data-ttu-id="87945-124">`remove` Wyrażeń regularnych opisujące adresy IP lub nazwy serwera DNS z listy adresów, które Obejdź serwer proxy usuwa element.</span><span class="sxs-lookup"><span data-stu-id="87945-124">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="87945-125">Adresy zostały zdefiniowane wcześniej w pliku konfiguracji lub wyższego poziomu w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="87945-125">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="87945-126">Wartość `address` atrybutu powinna być wyrażenie regularne opisuje zestaw adresów IP lub nazwy hosta.</span><span class="sxs-lookup"><span data-stu-id="87945-126">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="87945-127">Aby uzyskać więcej informacji na temat wyrażeń regularnych Zobacz. [Wyrażeń regularnych programu .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="87945-127">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="87945-128">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="87945-128">Configuration Files</span></span>  
 <span data-ttu-id="87945-129">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="87945-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="87945-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="87945-130">Example</span></span>  
 <span data-ttu-id="87945-131">Poniższy przykład usuwa wszelkie poprzednie definicji dla domeny firmy adventure works.com, a następnie dodanie domeny contoso.com, do listy obejścia.</span><span class="sxs-lookup"><span data-stu-id="87945-131">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <remove address="[a-z]+\.adventure-works\.com$" />  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="87945-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87945-132">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="87945-133">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="87945-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
