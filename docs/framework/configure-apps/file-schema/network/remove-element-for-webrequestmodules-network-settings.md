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
ms.openlocfilehash: f8209ea89ac8cd214389feddee8c475e10bc939a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697819"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="f719e-102">\<remove > elementu webRequestModules (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="f719e-102">\<remove> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="f719e-103">Usuwa niestandardowy moduł żądania sieci Web z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f719e-103">Removes a custom Web request module from the application.</span></span>  
  
[<span data-ttu-id="f719e-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="f719e-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="f719e-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f719e-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="f719e-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<webRequestModules >** ](webrequestmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f719e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span></span>  
<span data-ttu-id="f719e-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<remove >**</span><span class="sxs-lookup"><span data-stu-id="f719e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f719e-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f719e-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f719e-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f719e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f719e-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f719e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f719e-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f719e-111">Attributes</span></span>  
  
|<span data-ttu-id="f719e-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="f719e-112">**Attribute**</span></span>|<span data-ttu-id="f719e-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="f719e-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="f719e-114">Prefiks identyfikatora URI dla żądań obsłużonych przez ten moduł żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f719e-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f719e-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f719e-115">Child Elements</span></span>  
 <span data-ttu-id="f719e-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="f719e-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f719e-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f719e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f719e-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="f719e-118">**Element**</span></span>|<span data-ttu-id="f719e-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="f719e-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f719e-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="f719e-120">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="f719e-121">Określa moduły, które mają być używane do żądania informacji z hostów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="f719e-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f719e-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f719e-122">Remarks</span></span>  
 <span data-ttu-id="f719e-123">Element `remove` usuwa zarejestrowany moduł żądania sieci Web dla określonego prefiksu URI.</span><span class="sxs-lookup"><span data-stu-id="f719e-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="f719e-124">Wartość atrybutu `prefix` powinna być wiodącymi znakami prawidłowego identyfikatora URI — na przykład "`http`" lub "`http://www.contoso.com`".</span><span class="sxs-lookup"><span data-stu-id="f719e-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f719e-125">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f719e-125">Configuration Files</span></span>  
 <span data-ttu-id="f719e-126">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="f719e-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f719e-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="f719e-127">Example</span></span>  

<span data-ttu-id="f719e-128">Poniższy przykład usuwa istniejący moduł żądania sieci Web dla protokołu HTTP, a następnie rejestruje nowy niestandardowy moduł żądania sieci Web dla żądań HTTP do `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="f719e-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="f719e-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f719e-129">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="f719e-130">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="f719e-130">Network Settings Schema</span></span>](index.md)
