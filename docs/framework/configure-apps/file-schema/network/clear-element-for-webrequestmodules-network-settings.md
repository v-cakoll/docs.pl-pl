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
ms.openlocfilehash: 5832d120824df75d374fc94cb0aa4e08189cb965
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088497"
---
# <a name="clear-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="6fcd2-102">\<clear>, element dla webRequestModules (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="6fcd2-102">\<clear> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="6fcd2-103">Usuwa wszystkie zarejestrowane moduły żądania sieci Web z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6fcd2-103">Removes all registered Web request modules from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="6fcd2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6fcd2-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6fcd2-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6fcd2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6fcd2-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6fcd2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6fcd2-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6fcd2-107">Attributes</span></span>  
 <span data-ttu-id="6fcd2-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="6fcd2-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6fcd2-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6fcd2-109">Child Elements</span></span>  
 <span data-ttu-id="6fcd2-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="6fcd2-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6fcd2-111">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6fcd2-111">Parent Elements</span></span>  
  
|<span data-ttu-id="6fcd2-112">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="6fcd2-112">**Element**</span></span>|<span data-ttu-id="6fcd2-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="6fcd2-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6fcd2-114">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="6fcd2-114">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="6fcd2-115">Określa moduły, które mają być używane do żądania informacji z hostów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="6fcd2-115">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fcd2-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6fcd2-116">Remarks</span></span>  
 <span data-ttu-id="6fcd2-117">`clear`Element usuwa wszystkie zarejestrowane moduły żądania sieci Web, które zostały zdefiniowane wcześniej w pliku konfiguracyjnym lub na wyższym poziomie w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6fcd2-117">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6fcd2-118">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6fcd2-118">Configuration Files</span></span>  
 <span data-ttu-id="6fcd2-119">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="6fcd2-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fcd2-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="6fcd2-120">Example</span></span>  
 <span data-ttu-id="6fcd2-121">Poniższy przykład czyści wszystkie moduły żądania sieci Web, a następnie rejestruje moduł żądania sieci Web dla protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="6fcd2-121">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6fcd2-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6fcd2-122">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="6fcd2-123">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="6fcd2-123">Network Settings Schema</span></span>](index.md)
