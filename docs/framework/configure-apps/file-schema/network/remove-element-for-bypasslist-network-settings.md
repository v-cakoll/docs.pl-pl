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
ms.openlocfilehash: 99c18bd5b779845d52831b4a9591eaf4d5e5530b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920965"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="2107b-102">\<Usuń element > dla BypassList (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="2107b-102">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="2107b-103">Usuwa adres IP lub nazwę DNS z listy obejścia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="2107b-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>

<span data-ttu-id="2107b-104">\<> konfiguracji </span><span class="sxs-lookup"><span data-stu-id="2107b-104">\<configuration></span></span>\
<span data-ttu-id="2107b-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="2107b-105">\<system.net></span></span>\
<span data-ttu-id="2107b-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="2107b-106">\<defaultProxy></span></span>\
<span data-ttu-id="2107b-107">\<BypassList > </span><span class="sxs-lookup"><span data-stu-id="2107b-107">\<bypasslist></span></span>\
<span data-ttu-id="2107b-108">\<remove></span><span class="sxs-lookup"><span data-stu-id="2107b-108">\<remove></span></span>

## <a name="syntax"></a><span data-ttu-id="2107b-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="2107b-109">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2107b-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2107b-110">Attributes and Elements</span></span>

<span data-ttu-id="2107b-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2107b-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2107b-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2107b-112">Attributes</span></span>

|<span data-ttu-id="2107b-113">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="2107b-113">**Attribute**</span></span>|<span data-ttu-id="2107b-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="2107b-114">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="2107b-115">Wyrażenie regularne opisujące adres IP lub nazwę DNS.</span><span class="sxs-lookup"><span data-stu-id="2107b-115">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="2107b-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2107b-116">Child Elements</span></span>

<span data-ttu-id="2107b-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="2107b-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2107b-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2107b-118">Parent Elements</span></span>

|<span data-ttu-id="2107b-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="2107b-119">**Element**</span></span>|<span data-ttu-id="2107b-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="2107b-120">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="2107b-121">bypasslist</span><span class="sxs-lookup"><span data-stu-id="2107b-121">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="2107b-122">Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="2107b-122">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2107b-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2107b-123">Remarks</span></span>

<span data-ttu-id="2107b-124">`remove` Element usuwa wyrażenia regularne opisujące adresy IP lub nazwy serwerów DNS z listy adresów, które pomijają serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="2107b-124">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="2107b-125">Adresy zostały zdefiniowane wcześniej w pliku konfiguracyjnym lub na wyższym poziomie w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2107b-125">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="2107b-126">Wartość `address` atrybutu powinna być wyrażeniem regularnym opisującym zestaw adresów IP lub nazw hostów.</span><span class="sxs-lookup"><span data-stu-id="2107b-126">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="2107b-127">Aby uzyskać więcej informacji na temat wyrażeń regularnych, zobacz. [.NET Framework wyrażeń regularnych](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="2107b-127">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="2107b-128">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2107b-128">Configuration Files</span></span>

<span data-ttu-id="2107b-129">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="2107b-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="2107b-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="2107b-130">Example</span></span>

<span data-ttu-id="2107b-131">Poniższy przykład usuwa wszystkie poprzednie definicje domeny adventure-works.com, a następnie dodaje domenę contoso.com do listy pomijania.</span><span class="sxs-lookup"><span data-stu-id="2107b-131">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2107b-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2107b-132">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="2107b-133">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="2107b-133">Network Settings Schema</span></span>](index.md)
