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
ms.openlocfilehash: 4d078dac14103560423bfccdd4a1717031e7a60f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699513"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="5650e-102">\<clear > elementu BypassList (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="5650e-102">\<clear> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="5650e-103">Czyści listę pomijania proxy.</span><span class="sxs-lookup"><span data-stu-id="5650e-103">Clears the proxy bypass list.</span></span>  
  
[<span data-ttu-id="5650e-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="5650e-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="5650e-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5650e-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="5650e-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5650e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="5650e-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<bypasslist >** ](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5650e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>  
<span data-ttu-id="5650e-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="5650e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5650e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="5650e-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5650e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5650e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5650e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5650e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5650e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5650e-112">Attributes</span></span>  
 <span data-ttu-id="5650e-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="5650e-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5650e-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5650e-114">Child Elements</span></span>  
 <span data-ttu-id="5650e-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="5650e-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5650e-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5650e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5650e-117">**Element**</span><span class="sxs-lookup"><span data-stu-id="5650e-117">**Element**</span></span>|<span data-ttu-id="5650e-118">**Opis**</span><span class="sxs-lookup"><span data-stu-id="5650e-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5650e-119">bypasslist</span><span class="sxs-lookup"><span data-stu-id="5650e-119">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="5650e-120">Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="5650e-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5650e-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5650e-121">Remarks</span></span>  
 <span data-ttu-id="5650e-122">Element `clear` czyści wszystkie wpisy z listy pomijania.</span><span class="sxs-lookup"><span data-stu-id="5650e-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5650e-123">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5650e-123">Configuration Files</span></span>  
 <span data-ttu-id="5650e-124">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="5650e-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5650e-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="5650e-125">Example</span></span>  
 <span data-ttu-id="5650e-126">Poniższy przykład czyści listę pomijania, a następnie dodaje dwa adresy do listy pomijania.</span><span class="sxs-lookup"><span data-stu-id="5650e-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="5650e-127">Najpierw pomija serwer proxy dla wszystkich serwerów w domenie contoso.com; drugi pomija serwer proxy dla wszystkich serwerów, których adres IP rozpoczyna się od 192,168.</span><span class="sxs-lookup"><span data-stu-id="5650e-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5650e-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5650e-128">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="5650e-129">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="5650e-129">Network Settings Schema</span></span>](index.md)
