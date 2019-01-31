---
title: <remove> — Element dla listy obejść (Ustawienia sieci)
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
ms.openlocfilehash: c1e5d9a6726e1ae21d0ab449886b1074e399a655
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256982"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="9fb1c-102">\<Usuń >, Element dla bypasslist (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="9fb1c-102">\<remove> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="9fb1c-103">Usuwa adres IP lub nazwa DNS z listy obejścia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="9fb1c-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>  
  
 <span data-ttu-id="9fb1c-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="9fb1c-104">\<configuration></span></span>  
<span data-ttu-id="9fb1c-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="9fb1c-105">\<system.net></span></span>  
<span data-ttu-id="9fb1c-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="9fb1c-106">\<defaultProxy></span></span>  
<span data-ttu-id="9fb1c-107">\<bypasslist></span><span class="sxs-lookup"><span data-stu-id="9fb1c-107">\<bypasslist></span></span>  
<span data-ttu-id="9fb1c-108">\<remove></span><span class="sxs-lookup"><span data-stu-id="9fb1c-108">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fb1c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="9fb1c-109">Syntax</span></span>  
  
```xml  
<remove   
  address="regular expression"   
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9fb1c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9fb1c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9fb1c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9fb1c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9fb1c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9fb1c-112">Attributes</span></span>  
  
|<span data-ttu-id="9fb1c-113">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="9fb1c-113">**Attribute**</span></span>|<span data-ttu-id="9fb1c-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="9fb1c-114">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="9fb1c-115">Wyrażenie regularne, zawierająca opis, adres IP lub nazwę DNS.</span><span class="sxs-lookup"><span data-stu-id="9fb1c-115">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9fb1c-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9fb1c-116">Child Elements</span></span>  
 <span data-ttu-id="9fb1c-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="9fb1c-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9fb1c-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9fb1c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9fb1c-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="9fb1c-119">**Element**</span></span>|<span data-ttu-id="9fb1c-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="9fb1c-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9fb1c-121">bypasslist</span><span class="sxs-lookup"><span data-stu-id="9fb1c-121">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="9fb1c-122">Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="9fb1c-122">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fb1c-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9fb1c-123">Remarks</span></span>  
 <span data-ttu-id="9fb1c-124">`remove` Elementu usuwa wyrażeń regularnych, opisujący adresy IP lub nazwy serwera DNS z listy adresów, które pomijają serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="9fb1c-124">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="9fb1c-125">Adresy zostały zdefiniowane wcześniej w pliku konfiguracji lub wyższego poziomu w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9fb1c-125">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="9fb1c-126">Wartość `address` atrybut powinien być wyrażenie regularne, które opisuje zestaw adresów IP lub nazw hostów.</span><span class="sxs-lookup"><span data-stu-id="9fb1c-126">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="9fb1c-127">Aby uzyskać więcej informacji na temat wyrażeń regularnych Zobacz. [Wyrażeń regularnych programu .NET framework](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="9fb1c-127">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="9fb1c-128">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9fb1c-128">Configuration Files</span></span>  
 <span data-ttu-id="9fb1c-129">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="9fb1c-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fb1c-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="9fb1c-130">Example</span></span>  
 <span data-ttu-id="9fb1c-131">Poniższy przykład usuwa wszelkie poprzednią definicję dla domeny adventure works.com, a następnie dodaje domeny contoso.com do listy pomijania.</span><span class="sxs-lookup"><span data-stu-id="9fb1c-131">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9fb1c-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9fb1c-132">See also</span></span>
- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="9fb1c-133">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="9fb1c-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
