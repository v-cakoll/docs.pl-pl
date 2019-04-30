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
ms.openlocfilehash: 7499d15f1d57887ffc3e78b83ed686c0c0f46cf4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674639"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="55da9-102">\<Wyczyść >, Element dla bypasslist (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="55da9-102">\<clear> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="55da9-103">Czyści listę obejścia serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="55da9-103">Clears the proxy bypass list.</span></span>  
  
 <span data-ttu-id="55da9-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="55da9-104">\<configuration></span></span>  
<span data-ttu-id="55da9-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="55da9-105">\<system.net></span></span>  
<span data-ttu-id="55da9-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="55da9-106">\<defaultProxy></span></span>  
<span data-ttu-id="55da9-107">\<bypasslist></span><span class="sxs-lookup"><span data-stu-id="55da9-107">\<bypasslist></span></span>  
<span data-ttu-id="55da9-108">\<clear></span><span class="sxs-lookup"><span data-stu-id="55da9-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55da9-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="55da9-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55da9-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="55da9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="55da9-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="55da9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55da9-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="55da9-112">Attributes</span></span>  
 <span data-ttu-id="55da9-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="55da9-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="55da9-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="55da9-114">Child Elements</span></span>  
 <span data-ttu-id="55da9-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="55da9-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55da9-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="55da9-116">Parent Elements</span></span>  
  
|<span data-ttu-id="55da9-117">**Element**</span><span class="sxs-lookup"><span data-stu-id="55da9-117">**Element**</span></span>|<span data-ttu-id="55da9-118">**Opis**</span><span class="sxs-lookup"><span data-stu-id="55da9-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="55da9-119">bypasslist</span><span class="sxs-lookup"><span data-stu-id="55da9-119">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="55da9-120">Zawiera zestaw wyrażeń regularnych, które opisują adresy, które nie korzystają z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="55da9-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55da9-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="55da9-121">Remarks</span></span>  
 <span data-ttu-id="55da9-122">`clear` Element czyści wszystkie wpisy z listy obejścia.</span><span class="sxs-lookup"><span data-stu-id="55da9-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="55da9-123">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="55da9-123">Configuration Files</span></span>  
 <span data-ttu-id="55da9-124">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="55da9-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55da9-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="55da9-125">Example</span></span>  
 <span data-ttu-id="55da9-126">Poniższy przykład czyści listę obejścia, a następnie dodaje dwa adresy do listy pomijania.</span><span class="sxs-lookup"><span data-stu-id="55da9-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="55da9-127">Pierwszy pomija serwera proxy dla wszystkich serwerów w domenie contoso.com. drugi pomija serwera proxy dla wszystkich serwerom rozpoczyna się których adresy IP 192.168.</span><span class="sxs-lookup"><span data-stu-id="55da9-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="55da9-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55da9-128">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="55da9-129">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="55da9-129">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
