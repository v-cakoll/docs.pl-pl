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
ms.openlocfilehash: d1258301af903ef5c36df854c7c6dd504d6eef15
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltwebproxyscriptgt-element-network-settings"></a><span data-ttu-id="a57e9-102">&lt;webproxyscript —&gt; — Element (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="a57e9-102">&lt;webProxyScript&gt; Element (Network Settings)</span></span>
<span data-ttu-id="a57e9-103">Konfiguruje właściwości skryptu używana do wykrywania, serwer proxy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a57e9-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="a57e9-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="a57e9-104">\<configuration></span></span>  
<span data-ttu-id="a57e9-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="a57e9-105">\<system.net></span></span>  
<span data-ttu-id="a57e9-106">\<Ustawienia ></span><span class="sxs-lookup"><span data-stu-id="a57e9-106">\<settings></span></span>  
<span data-ttu-id="a57e9-107">\<webproxyscript — ></span><span class="sxs-lookup"><span data-stu-id="a57e9-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a57e9-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="a57e9-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a57e9-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a57e9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a57e9-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a57e9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a57e9-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a57e9-111">Attributes</span></span>  
  
|<span data-ttu-id="a57e9-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a57e9-112">Attribute</span></span>|<span data-ttu-id="a57e9-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a57e9-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="a57e9-114">Określa maksymalny czas, który można pobrać skryptu w godziny, minuty i sekundy.</span><span class="sxs-lookup"><span data-stu-id="a57e9-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="a57e9-115">Wartość domyślna to jedna minuta.</span><span class="sxs-lookup"><span data-stu-id="a57e9-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a57e9-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a57e9-116">Child Elements</span></span>  
 <span data-ttu-id="a57e9-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="a57e9-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a57e9-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a57e9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a57e9-119">Element</span><span class="sxs-lookup"><span data-stu-id="a57e9-119">Element</span></span>|<span data-ttu-id="a57e9-120">Opis</span><span class="sxs-lookup"><span data-stu-id="a57e9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a57e9-121">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="a57e9-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="a57e9-122">Służy do konfigurowania opcji sieci podstawowej dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a57e9-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a57e9-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a57e9-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a57e9-124">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a57e9-124">Configuration Files</span></span>  
 <span data-ttu-id="a57e9-125">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="a57e9-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a57e9-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a57e9-126">See Also</span></span>  
 [<span data-ttu-id="a57e9-127">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="a57e9-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
