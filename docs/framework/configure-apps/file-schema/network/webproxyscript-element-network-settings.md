---
title: "&lt;webproxyscript —&gt; — Element (ustawienia sieciowe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4c7d6154d354e806a04ccc9da062db64c534039b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebproxyscriptgt-element-network-settings"></a><span data-ttu-id="41f24-102">&lt;webproxyscript —&gt; — Element (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="41f24-102">&lt;webProxyScript&gt; Element (Network Settings)</span></span>
<span data-ttu-id="41f24-103">Konfiguruje właściwości skryptu używana do wykrywania, serwer proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="41f24-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="41f24-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="41f24-104">\<configuration></span></span>  
<span data-ttu-id="41f24-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="41f24-105">\<system.net></span></span>  
<span data-ttu-id="41f24-106">\<Ustawienia ></span><span class="sxs-lookup"><span data-stu-id="41f24-106">\<settings></span></span>  
<span data-ttu-id="41f24-107">\<webproxyscript — ></span><span class="sxs-lookup"><span data-stu-id="41f24-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41f24-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="41f24-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41f24-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="41f24-109">Attributes and Elements</span></span>  
 <span data-ttu-id="41f24-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="41f24-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41f24-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="41f24-111">Attributes</span></span>  
  
|<span data-ttu-id="41f24-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="41f24-112">Attribute</span></span>|<span data-ttu-id="41f24-113">Opis</span><span class="sxs-lookup"><span data-stu-id="41f24-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="41f24-114">Określa maksymalny czas, który można pobrać skryptu w godziny, minuty i sekundy.</span><span class="sxs-lookup"><span data-stu-id="41f24-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="41f24-115">Wartość domyślna to jedna minuta.</span><span class="sxs-lookup"><span data-stu-id="41f24-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41f24-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="41f24-116">Child Elements</span></span>  
 <span data-ttu-id="41f24-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="41f24-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="41f24-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="41f24-118">Parent Elements</span></span>  
  
|<span data-ttu-id="41f24-119">Element</span><span class="sxs-lookup"><span data-stu-id="41f24-119">Element</span></span>|<span data-ttu-id="41f24-120">Opis</span><span class="sxs-lookup"><span data-stu-id="41f24-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41f24-121">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="41f24-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="41f24-122">Służy do konfigurowania opcji sieci podstawowej dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="41f24-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41f24-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41f24-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="41f24-124">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="41f24-124">Configuration Files</span></span>  
 <span data-ttu-id="41f24-125">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="41f24-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41f24-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41f24-126">See Also</span></span>  
 [<span data-ttu-id="41f24-127">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="41f24-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
