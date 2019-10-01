---
title: <remove>, element dla bypasslist (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove element, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
ms.openlocfilehash: 97b49a8a520d6a4f72945366874991d2deb18710
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697898"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="217d8-102">\<remove > elementu BypassList (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="217d8-102">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="217d8-103">Usuwa adres IP lub nazwę DNS z listy obejścia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="217d8-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>

[<span data-ttu-id="217d8-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="217d8-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="217d8-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="217d8-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="217d8-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="217d8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="217d8-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<bypasslist >** ](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="217d8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>  
<span data-ttu-id="217d8-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<remove >**</span><span class="sxs-lookup"><span data-stu-id="217d8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="217d8-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="217d8-109">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="217d8-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="217d8-110">Attributes and Elements</span></span>

<span data-ttu-id="217d8-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="217d8-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="217d8-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="217d8-112">Attributes</span></span>

|<span data-ttu-id="217d8-113">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="217d8-113">**Attribute**</span></span>|<span data-ttu-id="217d8-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="217d8-114">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="217d8-115">Wyrażenie regularne opisujące adres IP lub nazwę DNS.</span><span class="sxs-lookup"><span data-stu-id="217d8-115">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="217d8-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="217d8-116">Child Elements</span></span>

<span data-ttu-id="217d8-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="217d8-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="217d8-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="217d8-118">Parent Elements</span></span>

|<span data-ttu-id="217d8-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="217d8-119">**Element**</span></span>|<span data-ttu-id="217d8-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="217d8-120">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="217d8-121">bypasslist</span><span class="sxs-lookup"><span data-stu-id="217d8-121">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="217d8-122">Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="217d8-122">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="217d8-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="217d8-123">Remarks</span></span>

<span data-ttu-id="217d8-124">Element `remove` usuwa wyrażenia regularne opisujące adresy IP lub nazwy serwerów DNS z listy adresów, które pomijają serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="217d8-124">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="217d8-125">Adresy zostały zdefiniowane wcześniej w pliku konfiguracyjnym lub na wyższym poziomie w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="217d8-125">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="217d8-126">Wartość atrybutu `address` powinna być wyrażeniem regularnym opisującym zestaw adresów IP lub nazw hostów.</span><span class="sxs-lookup"><span data-stu-id="217d8-126">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="217d8-127">Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz. [.NET Framework wyrażeń regularnych](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="217d8-127">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="217d8-128">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="217d8-128">Configuration Files</span></span>

<span data-ttu-id="217d8-129">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="217d8-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="217d8-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="217d8-130">Example</span></span>

<span data-ttu-id="217d8-131">Poniższy przykład usuwa wszystkie poprzednie definicje domeny adventure-works.com, a następnie dodaje domenę contoso.com do listy pomijania.</span><span class="sxs-lookup"><span data-stu-id="217d8-131">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="217d8-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="217d8-132">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="217d8-133">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="217d8-133">Network Settings Schema</span></span>](index.md)
