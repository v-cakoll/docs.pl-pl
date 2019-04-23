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
ms.openlocfilehash: 5dea238629b282776cb45f7b388e655fa557d084
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078983"
---
# <a name="clear-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="43e3a-102">\<Wyczyść >, Element dla webRequestModules (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="43e3a-102">\<clear> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="43e3a-103">Usuwa wszystkie zarejestrowane moduły żądania sieci Web z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="43e3a-103">Removes all registered Web request modules from the application.</span></span>  
  
 <span data-ttu-id="43e3a-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="43e3a-104">\<configuration></span></span>  
<span data-ttu-id="43e3a-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="43e3a-105">\<system.net></span></span>  
<span data-ttu-id="43e3a-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="43e3a-106">\<webRequestModules></span></span>  
<span data-ttu-id="43e3a-107">\<clear></span><span class="sxs-lookup"><span data-stu-id="43e3a-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43e3a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="43e3a-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43e3a-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="43e3a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="43e3a-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="43e3a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43e3a-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="43e3a-111">Attributes</span></span>  
 <span data-ttu-id="43e3a-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="43e3a-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="43e3a-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="43e3a-113">Child Elements</span></span>  
 <span data-ttu-id="43e3a-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="43e3a-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43e3a-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="43e3a-115">Parent Elements</span></span>  
  
|<span data-ttu-id="43e3a-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="43e3a-116">**Element**</span></span>|<span data-ttu-id="43e3a-117">**Opis**</span><span class="sxs-lookup"><span data-stu-id="43e3a-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="43e3a-118">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="43e3a-118">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="43e3a-119">Określa moduły do użycia na żądanie informacji z hostów w sieci.</span><span class="sxs-lookup"><span data-stu-id="43e3a-119">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43e3a-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43e3a-120">Remarks</span></span>  
 <span data-ttu-id="43e3a-121">`clear` Elementu usuwa wszystkie zarejestrowane moduły żądania sieci Web, które zostały wcześniej zdefiniowane w pliku konfiguracji lub wyższego poziomu w hierarchii konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="43e3a-121">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="43e3a-122">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="43e3a-122">Configuration Files</span></span>  
 <span data-ttu-id="43e3a-123">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="43e3a-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="43e3a-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="43e3a-124">Example</span></span>  
 <span data-ttu-id="43e3a-125">Poniższy przykład czyści wszystkie moduły żądania sieci Web, a następnie rejestruje moduł żądania sieci Web do obsługi protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="43e3a-125">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43e3a-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43e3a-126">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="43e3a-127">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="43e3a-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
