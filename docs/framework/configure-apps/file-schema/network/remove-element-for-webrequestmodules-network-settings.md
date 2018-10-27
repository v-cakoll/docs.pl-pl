---
title: '&lt;Usuń&gt; Element dla webRequestModules (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
ms.openlocfilehash: 2f787206c503c047a34383e12c5676296e39c1fe
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190752"
---
# <a name="ltremovegt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="bc527-102">&lt;Usuń&gt; Element dla webRequestModules (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="bc527-102">&lt;remove&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="bc527-103">Usuwa niestandardowego modułu żądania sieci Web z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bc527-103">Removes a custom Web request module from the application.</span></span>  
  
 <span data-ttu-id="bc527-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="bc527-104">\<configuration></span></span>  
<span data-ttu-id="bc527-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="bc527-105">\<system.net></span></span>  
<span data-ttu-id="bc527-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="bc527-106">\<webRequestModules></span></span>  
<span data-ttu-id="bc527-107">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="bc527-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc527-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc527-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc527-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bc527-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bc527-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bc527-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc527-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bc527-111">Attributes</span></span>  
  
|<span data-ttu-id="bc527-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="bc527-112">**Attribute**</span></span>|<span data-ttu-id="bc527-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="bc527-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="bc527-114">Prefiks identyfikatora URI dla żądań obsługiwanych przez ten moduł żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="bc527-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc527-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bc527-115">Child Elements</span></span>  
 <span data-ttu-id="bc527-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="bc527-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc527-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bc527-117">Parent Elements</span></span>  
  
|<span data-ttu-id="bc527-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="bc527-118">**Element**</span></span>|<span data-ttu-id="bc527-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="bc527-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="bc527-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="bc527-120">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="bc527-121">Określa moduły do użycia na żądanie informacji z hostów w sieci.</span><span class="sxs-lookup"><span data-stu-id="bc527-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc527-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc527-122">Remarks</span></span>  
 <span data-ttu-id="bc527-123">`remove` Elementu usuwa zarejestrowanego modułu żądania sieci Web dla określonego prefiksu identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="bc527-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="bc527-124">Wartość `prefix` atrybut powinien być wiodące znaki prawidłowy identyfikator URI — na przykład "`http`", lub "`http://www.contoso.com`".</span><span class="sxs-lookup"><span data-stu-id="bc527-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="bc527-125">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bc527-125">Configuration Files</span></span>  
 <span data-ttu-id="bc527-126">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="bc527-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc527-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="bc527-127">Example</span></span>  

<span data-ttu-id="bc527-128">Poniższy przykład usuwa istniejący moduł żądania sieci Web do obsługi protokołu HTTP, a następnie rejestruje nowy niestandardowy moduł sieci Web żądania dla protokołu HTTP żądania `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="bc527-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix="http">  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc527-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc527-129">See Also</span></span>  
- <xref:System.Net.WebRequest>  
- [<span data-ttu-id="bc527-130">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="bc527-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
