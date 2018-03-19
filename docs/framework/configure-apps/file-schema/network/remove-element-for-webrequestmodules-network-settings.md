---
title: "&lt;Usuń&gt; elementu webRequestModules — (ustawienia sieciowe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
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
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 391e5f2a7d9d8076ba9e9a3057e3d8899e2ce672
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="ltremovegt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="d5b10-102">&lt;Usuń&gt; elementu webRequestModules — (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="d5b10-102">&lt;remove&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="d5b10-103">Usuwa niestandardowego modułu żądania sieci Web z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d5b10-103">Removes a custom Web request module from the application.</span></span>  
  
 <span data-ttu-id="d5b10-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d5b10-104">\<configuration></span></span>  
<span data-ttu-id="d5b10-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="d5b10-105">\<system.net></span></span>  
<span data-ttu-id="d5b10-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="d5b10-106">\<webRequestModules></span></span>  
<span data-ttu-id="d5b10-107">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="d5b10-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5b10-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5b10-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5b10-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d5b10-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d5b10-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d5b10-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5b10-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d5b10-111">Attributes</span></span>  
  
|<span data-ttu-id="d5b10-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="d5b10-112">**Attribute**</span></span>|<span data-ttu-id="d5b10-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="d5b10-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="d5b10-114">Prefiks identyfikatora URI dla żądań obsługiwanych przez ten moduł żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d5b10-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d5b10-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d5b10-115">Child Elements</span></span>  
 <span data-ttu-id="d5b10-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="d5b10-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d5b10-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d5b10-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d5b10-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="d5b10-118">**Element**</span></span>|<span data-ttu-id="d5b10-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="d5b10-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d5b10-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="d5b10-120">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="d5b10-121">Określa moduły służące do żądania informacji z hostów w sieci.</span><span class="sxs-lookup"><span data-stu-id="d5b10-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5b10-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d5b10-122">Remarks</span></span>  
 <span data-ttu-id="d5b10-123">`remove` Element usuwa zarejestrowanego modułu żądania sieci Web dla określonego prefiksu identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="d5b10-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="d5b10-124">Wartość `prefix` atrybutu powinna być pierwszych znaków z prawidłowym identyfikatorem URI — na przykład "http" lub "http://www.contoso.com".</span><span class="sxs-lookup"><span data-stu-id="d5b10-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "http", or "http://www.contoso.com".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d5b10-125">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d5b10-125">Configuration Files</span></span>  
 <span data-ttu-id="d5b10-126">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="d5b10-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5b10-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5b10-127">Example</span></span>  
 <span data-ttu-id="d5b10-128">Poniższy przykład usuwa istniejący moduł żądania sieci Web do obsługi protokołu HTTP, a następnie rejestruje nowego niestandardowego sieci Web żądania modułu HTTP żądań www.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="d5b10-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to www.contoso.com.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d5b10-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5b10-129">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="d5b10-130">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="d5b10-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
