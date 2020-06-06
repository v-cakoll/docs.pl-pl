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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697898"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="01a3c-102">\<remove>, element dla bypasslist (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="01a3c-102">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="01a3c-103">Usuwa adres IP lub nazwę DNS z listy obejścia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="01a3c-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  

## <a name="syntax"></a><span data-ttu-id="01a3c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="01a3c-104">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="01a3c-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="01a3c-105">Attributes and Elements</span></span>

<span data-ttu-id="01a3c-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="01a3c-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="01a3c-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="01a3c-107">Attributes</span></span>

|<span data-ttu-id="01a3c-108">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="01a3c-108">**Attribute**</span></span>|<span data-ttu-id="01a3c-109">**Opis**</span><span class="sxs-lookup"><span data-stu-id="01a3c-109">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="01a3c-110">Wyrażenie regularne opisujące adres IP lub nazwę DNS.</span><span class="sxs-lookup"><span data-stu-id="01a3c-110">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="01a3c-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="01a3c-111">Child Elements</span></span>

<span data-ttu-id="01a3c-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="01a3c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="01a3c-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="01a3c-113">Parent Elements</span></span>

|<span data-ttu-id="01a3c-114">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="01a3c-114">**Element**</span></span>|<span data-ttu-id="01a3c-115">**Opis**</span><span class="sxs-lookup"><span data-stu-id="01a3c-115">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="01a3c-116">bypasslist</span><span class="sxs-lookup"><span data-stu-id="01a3c-116">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="01a3c-117">Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="01a3c-117">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="01a3c-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01a3c-118">Remarks</span></span>

<span data-ttu-id="01a3c-119">`remove`Element usuwa wyrażenia regularne opisujące adresy IP lub nazwy serwerów DNS z listy adresów, które pomijają serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="01a3c-119">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="01a3c-120">Adresy zostały zdefiniowane wcześniej w pliku konfiguracyjnym lub na wyższym poziomie w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="01a3c-120">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="01a3c-121">Wartość `address` atrybutu powinna być wyrażeniem regularnym opisującym zestaw adresów IP lub nazw hostów.</span><span class="sxs-lookup"><span data-stu-id="01a3c-121">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="01a3c-122">Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz. [.NET Framework wyrażeń regularnych](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="01a3c-122">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="01a3c-123">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="01a3c-123">Configuration Files</span></span>

<span data-ttu-id="01a3c-124">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="01a3c-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="01a3c-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="01a3c-125">Example</span></span>

<span data-ttu-id="01a3c-126">Poniższy przykład usuwa wszystkie poprzednie definicje domeny adventure-works.com, a następnie dodaje domenę contoso.com do listy pomijania.</span><span class="sxs-lookup"><span data-stu-id="01a3c-126">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="01a3c-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01a3c-127">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="01a3c-128">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="01a3c-128">Network Settings Schema</span></span>](index.md)
