---
title: "&lt;Usuń&gt; elementu webRequestModules — (ustawienia sieciowe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 43f0d30f8c18c4755f31d0c851c773207bc15b78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltremovegt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="eb2f0-102">&lt;Usuń&gt; elementu webRequestModules — (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="eb2f0-102">&lt;remove&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="eb2f0-103">Usuwa niestandardowego modułu żądania sieci Web z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eb2f0-103">Removes a custom Web request module from the application.</span></span>  
  
 <span data-ttu-id="eb2f0-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="eb2f0-104">\<configuration></span></span>  
<span data-ttu-id="eb2f0-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="eb2f0-105">\<system.net></span></span>  
<span data-ttu-id="eb2f0-106">\<webRequestModules — ></span><span class="sxs-lookup"><span data-stu-id="eb2f0-106">\<webRequestModules></span></span>  
<span data-ttu-id="eb2f0-107">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="eb2f0-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb2f0-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb2f0-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb2f0-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="eb2f0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="eb2f0-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="eb2f0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb2f0-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="eb2f0-111">Attributes</span></span>  
  
|<span data-ttu-id="eb2f0-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="eb2f0-112">**Attribute**</span></span>|<span data-ttu-id="eb2f0-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="eb2f0-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="eb2f0-114">Prefiks identyfikatora URI dla żądań obsługiwanych przez ten moduł żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="eb2f0-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb2f0-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="eb2f0-115">Child Elements</span></span>  
 <span data-ttu-id="eb2f0-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="eb2f0-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eb2f0-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="eb2f0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="eb2f0-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="eb2f0-118">**Element**</span></span>|<span data-ttu-id="eb2f0-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="eb2f0-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="eb2f0-120">webRequestModules —</span><span class="sxs-lookup"><span data-stu-id="eb2f0-120">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="eb2f0-121">Określa moduły służące do żądania informacji z hostów w sieci.</span><span class="sxs-lookup"><span data-stu-id="eb2f0-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb2f0-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb2f0-122">Remarks</span></span>  
 <span data-ttu-id="eb2f0-123">`remove` Element usuwa zarejestrowanego modułu żądania sieci Web dla określonego prefiksu identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="eb2f0-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="eb2f0-124">Wartość `prefix` atrybut powinien być pierwszych znaków z prawidłowym identyfikatorem URI — na przykład "http" lub "http://www.contoso.com".</span><span class="sxs-lookup"><span data-stu-id="eb2f0-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "http", or "http://www.contoso.com".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="eb2f0-125">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="eb2f0-125">Configuration Files</span></span>  
 <span data-ttu-id="eb2f0-126">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="eb2f0-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb2f0-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="eb2f0-127">Example</span></span>  
 <span data-ttu-id="eb2f0-128">Poniższy przykład usuwa istniejący moduł żądania sieci Web do obsługi protokołu HTTP, a następnie rejestruje nowego niestandardowego sieci Web żądania modułu HTTP żądań www.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="eb2f0-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to www.contoso.com.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eb2f0-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb2f0-129">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="eb2f0-130">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="eb2f0-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
