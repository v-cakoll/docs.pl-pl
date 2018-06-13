---
title: '&lt;Wyczyść&gt; elementu bypasslist — (ustawienia sieciowe)'
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 9297b68a31117aabfa45328954ccb9c7cdac66c5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742195"
---
# <a name="ltcleargt-element-for-bypasslist-network-settings"></a><span data-ttu-id="0c7ed-102">&lt;Wyczyść&gt; elementu bypasslist — (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="0c7ed-102">&lt;clear&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="0c7ed-103">Czyści Lista obejść serwerów proxy.</span><span class="sxs-lookup"><span data-stu-id="0c7ed-103">Clears the proxy bypass list.</span></span>  
  
 <span data-ttu-id="0c7ed-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="0c7ed-104">\<configuration></span></span>  
<span data-ttu-id="0c7ed-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="0c7ed-105">\<system.net></span></span>  
<span data-ttu-id="0c7ed-106">\<defaultProxy — ></span><span class="sxs-lookup"><span data-stu-id="0c7ed-106">\<defaultProxy></span></span>  
<span data-ttu-id="0c7ed-107">\<bypasslist — ></span><span class="sxs-lookup"><span data-stu-id="0c7ed-107">\<bypasslist></span></span>  
<span data-ttu-id="0c7ed-108">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="0c7ed-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c7ed-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c7ed-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c7ed-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0c7ed-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0c7ed-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0c7ed-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c7ed-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0c7ed-112">Attributes</span></span>  
 <span data-ttu-id="0c7ed-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="0c7ed-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0c7ed-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0c7ed-114">Child Elements</span></span>  
 <span data-ttu-id="0c7ed-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="0c7ed-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c7ed-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0c7ed-116">Parent Elements</span></span>  
  
|<span data-ttu-id="0c7ed-117">**Element**</span><span class="sxs-lookup"><span data-stu-id="0c7ed-117">**Element**</span></span>|<span data-ttu-id="0c7ed-118">**Opis**</span><span class="sxs-lookup"><span data-stu-id="0c7ed-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0c7ed-119">bypasslist —</span><span class="sxs-lookup"><span data-stu-id="0c7ed-119">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="0c7ed-120">Zawiera zestaw wyrażeń regularnych, opisujących adresów, które nie korzystają z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="0c7ed-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c7ed-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c7ed-121">Remarks</span></span>  
 <span data-ttu-id="0c7ed-122">`clear` Element czyści wszystkie wpisy z listy obejścia.</span><span class="sxs-lookup"><span data-stu-id="0c7ed-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0c7ed-123">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0c7ed-123">Configuration Files</span></span>  
 <span data-ttu-id="0c7ed-124">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="0c7ed-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c7ed-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c7ed-125">Example</span></span>  
 <span data-ttu-id="0c7ed-126">Poniższy przykład czyści Lista obejść, a następnie dodaje dwa adresy do obejścia listy.</span><span class="sxs-lookup"><span data-stu-id="0c7ed-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="0c7ed-127">Pierwszy pomija serwera proxy dla wszystkich serwerów w domenie contoso.com. drugi pomija serwera proxy dla wszystkich serwerów rozpoczyna którego adres IP z 192.168.</span><span class="sxs-lookup"><span data-stu-id="0c7ed-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0c7ed-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0c7ed-128">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="0c7ed-129">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="0c7ed-129">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
