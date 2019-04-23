---
title: <remove>, element dla webRequestModules (ustawienia sieci)
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
ms.openlocfilehash: c57e2849d608b1706c41beca91ff8026ebd9ca45
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085405"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="30851-102">\<Usuń >, Element dla webRequestModules (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="30851-102">\<remove> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="30851-103">Usuwa niestandardowego modułu żądania sieci Web z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="30851-103">Removes a custom Web request module from the application.</span></span>  
  
 <span data-ttu-id="30851-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="30851-104">\<configuration></span></span>  
<span data-ttu-id="30851-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="30851-105">\<system.net></span></span>  
<span data-ttu-id="30851-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="30851-106">\<webRequestModules></span></span>  
<span data-ttu-id="30851-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="30851-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30851-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="30851-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30851-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="30851-109">Attributes and Elements</span></span>  
 <span data-ttu-id="30851-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="30851-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30851-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="30851-111">Attributes</span></span>  
  
|<span data-ttu-id="30851-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="30851-112">**Attribute**</span></span>|<span data-ttu-id="30851-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="30851-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="30851-114">Prefiks identyfikatora URI dla żądań obsługiwanych przez ten moduł żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="30851-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30851-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="30851-115">Child Elements</span></span>  
 <span data-ttu-id="30851-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="30851-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30851-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="30851-117">Parent Elements</span></span>  
  
|<span data-ttu-id="30851-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="30851-118">**Element**</span></span>|<span data-ttu-id="30851-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="30851-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="30851-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="30851-120">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="30851-121">Określa moduły do użycia na żądanie informacji z hostów w sieci.</span><span class="sxs-lookup"><span data-stu-id="30851-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30851-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="30851-122">Remarks</span></span>  
 <span data-ttu-id="30851-123">`remove` Elementu usuwa zarejestrowanego modułu żądania sieci Web dla określonego prefiksu identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="30851-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="30851-124">Wartość `prefix` atrybut powinien być wiodące znaki prawidłowy identyfikator URI — na przykład "`http`", lub "`http://www.contoso.com`".</span><span class="sxs-lookup"><span data-stu-id="30851-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="30851-125">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="30851-125">Configuration Files</span></span>  
 <span data-ttu-id="30851-126">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="30851-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="30851-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="30851-127">Example</span></span>  

<span data-ttu-id="30851-128">Poniższy przykład usuwa istniejący moduł żądania sieci Web do obsługi protokołu HTTP, a następnie rejestruje nowy niestandardowy moduł sieci Web żądania dla protokołu HTTP żądania `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="30851-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="30851-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30851-129">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="30851-130">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="30851-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
