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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154936"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="31f56-102">\<clear>, element dla bypasslist (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="31f56-102">\<clear> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="31f56-103">Czyści listę pomijania proxy.</span><span class="sxs-lookup"><span data-stu-id="31f56-103">Clears the proxy bypass list.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="31f56-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="31f56-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31f56-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="31f56-105">Attributes and Elements</span></span>  
 <span data-ttu-id="31f56-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="31f56-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31f56-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="31f56-107">Attributes</span></span>  
 <span data-ttu-id="31f56-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="31f56-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="31f56-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="31f56-109">Child Elements</span></span>  
 <span data-ttu-id="31f56-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="31f56-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="31f56-111">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="31f56-111">Parent Elements</span></span>  
  
|<span data-ttu-id="31f56-112">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="31f56-112">**Element**</span></span>|<span data-ttu-id="31f56-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="31f56-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="31f56-114">bypasslist</span><span class="sxs-lookup"><span data-stu-id="31f56-114">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="31f56-115">Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="31f56-115">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31f56-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="31f56-116">Remarks</span></span>  
 <span data-ttu-id="31f56-117">`clear`Element czyści wszystkie wpisy z listy pomijania.</span><span class="sxs-lookup"><span data-stu-id="31f56-117">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="31f56-118">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="31f56-118">Configuration Files</span></span>  
 <span data-ttu-id="31f56-119">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="31f56-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="31f56-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="31f56-120">Example</span></span>  
 <span data-ttu-id="31f56-121">Poniższy przykład czyści listę pomijania, a następnie dodaje dwa adresy do listy pomijania.</span><span class="sxs-lookup"><span data-stu-id="31f56-121">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="31f56-122">Najpierw pomija serwer proxy dla wszystkich serwerów w domenie contoso.com; drugi pomija serwer proxy dla wszystkich serwerów, których adres IP rozpoczyna się od 192,168.</span><span class="sxs-lookup"><span data-stu-id="31f56-122">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="31f56-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31f56-123">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="31f56-124">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="31f56-124">Network Settings Schema</span></span>](index.md)
