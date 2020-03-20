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
ms.openlocfilehash: afa1aef8ea71f43a136987ec5b6e1925c6d9fb40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154728"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="07177-102">\<usuń element> dla webRequestModules (Ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="07177-102">\<remove> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="07177-103">Usuwa niestandardowy moduł żądania sieci Web z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="07177-103">Removes a custom Web request module from the application.</span></span>  
  
<span data-ttu-id="07177-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="07177-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="07177-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="07177-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="07177-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="07177-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="07177-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<usuń>**</span><span class="sxs-lookup"><span data-stu-id="07177-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="07177-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="07177-108">Syntax</span></span>  
  
```xml  
<remove
  prefix="URI prefix"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07177-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="07177-109">Attributes and Elements</span></span>  
 <span data-ttu-id="07177-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="07177-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07177-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="07177-111">Attributes</span></span>  
  
|<span data-ttu-id="07177-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="07177-112">**Attribute**</span></span>|<span data-ttu-id="07177-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="07177-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="07177-114">Prefiks identyfikatora URI dla żądań obsługiwanych przez ten moduł żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="07177-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="07177-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="07177-115">Child Elements</span></span>  
 <span data-ttu-id="07177-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="07177-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="07177-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="07177-117">Parent Elements</span></span>  
  
|<span data-ttu-id="07177-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="07177-118">**Element**</span></span>|<span data-ttu-id="07177-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="07177-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="07177-120">webRequestModules (WebRequestModules)</span><span class="sxs-lookup"><span data-stu-id="07177-120">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="07177-121">Określa moduły, za pomocą których mają być wymagane informacje od hostów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="07177-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07177-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="07177-122">Remarks</span></span>  
 <span data-ttu-id="07177-123">Element `remove` usuwa zarejestrowany moduł żądania sieci Web dla określonego prefiksu URI.</span><span class="sxs-lookup"><span data-stu-id="07177-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="07177-124">Wartość atrybutu `prefix` powinna być znakami wiodącymi prawidłowego identyfikatora URI , na przykład " "`http`lub "`http://www.contoso.com`".</span><span class="sxs-lookup"><span data-stu-id="07177-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="07177-125">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="07177-125">Configuration Files</span></span>  
 <span data-ttu-id="07177-126">Ten element może być używany w pliku konfiguracyjnym aplikacji lub pliku konfiguracyjnym komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="07177-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="07177-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="07177-127">Example</span></span>  

<span data-ttu-id="07177-128">Poniższy przykład usuwa istniejący moduł żądania sieci Web dla protokołu HTTP, a `www.contoso.com`następnie rejestruje nowy niestandardowy moduł żądania sieci Web dla żądań HTTP do .</span><span class="sxs-lookup"><span data-stu-id="07177-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="07177-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07177-129">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="07177-130">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="07177-130">Network Settings Schema</span></span>](index.md)
