---
title: <clear>, element dla bypasslist (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, bypasslist
- <clear> element, bypasslist
- <bypasslist>, clear element
- bypasslist, clear element
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
ms.openlocfilehash: c25477c2c99be66b34b07e1f7e50115bfa8d14e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154936"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="e26b8-102">\<wyczyść> element dla bypasslist (Ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="e26b8-102">\<clear> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="e26b8-103">Czyści listę pomijania serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="e26b8-103">Clears the proxy bypass list.</span></span>  
  
<span data-ttu-id="e26b8-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e26b8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e26b8-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e26b8-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="e26b8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e26b8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="e26b8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>obwodnicy**](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e26b8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>\
<span data-ttu-id="e26b8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wyraźne>**</span><span class="sxs-lookup"><span data-stu-id="e26b8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e26b8-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="e26b8-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e26b8-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e26b8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e26b8-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e26b8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e26b8-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e26b8-112">Attributes</span></span>  
 <span data-ttu-id="e26b8-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="e26b8-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e26b8-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e26b8-114">Child Elements</span></span>  
 <span data-ttu-id="e26b8-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="e26b8-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e26b8-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e26b8-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e26b8-117">**Element**</span><span class="sxs-lookup"><span data-stu-id="e26b8-117">**Element**</span></span>|<span data-ttu-id="e26b8-118">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e26b8-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e26b8-119">Bypasslist</span><span class="sxs-lookup"><span data-stu-id="e26b8-119">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="e26b8-120">Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie używają serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="e26b8-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e26b8-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e26b8-121">Remarks</span></span>  
 <span data-ttu-id="e26b8-122">Element `clear` czyści wszystkie wpisy z listy pomijania.</span><span class="sxs-lookup"><span data-stu-id="e26b8-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e26b8-123">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e26b8-123">Configuration Files</span></span>  
 <span data-ttu-id="e26b8-124">Ten element może być używany w pliku konfiguracyjnym aplikacji lub pliku konfiguracyjnym komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="e26b8-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e26b8-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="e26b8-125">Example</span></span>  
 <span data-ttu-id="e26b8-126">Poniższy przykład czyści listę pomijania, a następnie dodaje dwa adresy do listy pomijania.</span><span class="sxs-lookup"><span data-stu-id="e26b8-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="e26b8-127">Pierwszy omija serwer proxy dla wszystkich serwerów w domenie contoso.com; drugi omija serwer proxy dla wszystkich serwerów, których adres IP zaczyna się od 192.168.</span><span class="sxs-lookup"><span data-stu-id="e26b8-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
         <clear/>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="e26b8-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e26b8-128">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="e26b8-129">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="e26b8-129">Network Settings Schema</span></span>](index.md)
