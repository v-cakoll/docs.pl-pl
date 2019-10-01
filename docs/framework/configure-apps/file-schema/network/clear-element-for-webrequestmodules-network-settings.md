---
title: <clear>, element dla webRequestModules (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, webRequestModules
- <webRequestModules>, clear element
- webRequestModules, clear element
- clear element, webRequestModules
ms.assetid: 48f38bcb-f30c-4b74-a8f0-1a3caf1aa96f
ms.openlocfilehash: 95a190dac3a9512b404a054c60c48de9c4574790
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698342"
---
# <a name="clear-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="e7ec6-102">\<clear > elementu webRequestModules (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="e7ec6-102">\<clear> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="e7ec6-103">Usuwa wszystkie zarejestrowane moduły żądania sieci Web z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e7ec6-103">Removes all registered Web request modules from the application.</span></span>  
  
[<span data-ttu-id="e7ec6-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="e7ec6-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="e7ec6-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e7ec6-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="e7ec6-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<webRequestModules >** ](webrequestmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e7ec6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span></span>  
<span data-ttu-id="e7ec6-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="e7ec6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7ec6-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7ec6-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7ec6-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e7ec6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e7ec6-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e7ec6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7ec6-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e7ec6-111">Attributes</span></span>  
 <span data-ttu-id="e7ec6-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="e7ec6-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e7ec6-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e7ec6-113">Child Elements</span></span>  
 <span data-ttu-id="e7ec6-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="e7ec6-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e7ec6-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e7ec6-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e7ec6-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="e7ec6-116">**Element**</span></span>|<span data-ttu-id="e7ec6-117">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e7ec6-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e7ec6-118">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="e7ec6-118">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="e7ec6-119">Określa moduły, które mają być używane do żądania informacji z hostów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="e7ec6-119">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7ec6-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e7ec6-120">Remarks</span></span>  
 <span data-ttu-id="e7ec6-121">Element `clear` usuwa wszystkie zarejestrowane moduły żądania sieci Web, które zostały zdefiniowane wcześniej w pliku konfiguracyjnym lub na wyższym poziomie w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e7ec6-121">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e7ec6-122">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e7ec6-122">Configuration Files</span></span>  
 <span data-ttu-id="e7ec6-123">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="e7ec6-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7ec6-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="e7ec6-124">Example</span></span>  
 <span data-ttu-id="e7ec6-125">Poniższy przykład czyści wszystkie moduły żądania sieci Web, a następnie rejestruje moduł żądania sieci Web dla protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="e7ec6-125">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <clear/>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7ec6-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7ec6-126">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="e7ec6-127">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="e7ec6-127">Network Settings Schema</span></span>](index.md)
