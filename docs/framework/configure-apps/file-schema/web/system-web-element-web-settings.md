---
title: '&lt;System.Web&gt; elementu (ustawienia sieci Web)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 59899178fd9fc8da2334883ed62d9f8655eb335b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemwebgt-element-web-settings"></a><span data-ttu-id="03a95-102">&lt;System.Web&gt; elementu (ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="03a95-102">&lt;system.web&gt; Element (Web Settings)</span></span>
<span data-ttu-id="03a95-103">Zawiera informacje o zarządzaniu warstwy hostingu ASP.NET zachowanie całego procesu.</span><span class="sxs-lookup"><span data-stu-id="03a95-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
 <span data-ttu-id="03a95-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="03a95-104">\<configuration></span></span>  
<span data-ttu-id="03a95-105">\<System.Web > elementu (ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="03a95-105">\<system.web> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03a95-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="03a95-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03a95-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="03a95-107">Attributes and Elements</span></span>  
 <span data-ttu-id="03a95-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="03a95-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03a95-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="03a95-109">Attributes</span></span>  
 <span data-ttu-id="03a95-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="03a95-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="03a95-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="03a95-111">Child Elements</span></span>  
  
|<span data-ttu-id="03a95-112">Element</span><span class="sxs-lookup"><span data-stu-id="03a95-112">Element</span></span>|<span data-ttu-id="03a95-113">Opis</span><span class="sxs-lookup"><span data-stu-id="03a95-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03a95-114">\<applicationPool ></span><span class="sxs-lookup"><span data-stu-id="03a95-114">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="03a95-115">Określa ustawienia konfiguracji dla pul aplikacji usług IIS w pliku konfigurację aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="03a95-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="03a95-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="03a95-116">Parent Elements</span></span>  
  
|<span data-ttu-id="03a95-117">Element</span><span class="sxs-lookup"><span data-stu-id="03a95-117">Element</span></span>|<span data-ttu-id="03a95-118">Opis</span><span class="sxs-lookup"><span data-stu-id="03a95-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03a95-119">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="03a95-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="03a95-120">Określa element główny w każdym pliku konfiguracyjnym, który jest używany przez środowisko uruchomieniowe języka wspólnego i [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="03a95-120">Specifies the root element in every configuration file that is used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03a95-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03a95-121">Remarks</span></span>  
 <span data-ttu-id="03a95-122">`system.web` Elementu i jego podrzędny `applicationPool` element zostały dodane do [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] w [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="03a95-122">The `system.web` element and its child `applicationPool` element were added to the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] as of [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="03a95-123">Po uruchomieniu [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] lub nowszy w trybie zintegrowanym, ta kombinacja element umożliwia skonfigurowanie zarządzaniu wątków ASP.NET i jak go kolejki żądań ASP.NET jest obsługiwany w puli aplikacji usług IIS.</span><span class="sxs-lookup"><span data-stu-id="03a95-123">When you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="03a95-124">Po uruchomieniu [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] lub nowszy w trybie klasycznym lub ISAPI, te ustawienia są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="03a95-124">If you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03a95-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="03a95-125">Example</span></span>  
 <span data-ttu-id="03a95-126">Poniższy przykład pokazuje, jak można skonfigurować sposób działania całego procesu ASP.NET w pliku konfigurację aspnet.config ASP.NET znajduje się w puli aplikacji usług IIS.</span><span class="sxs-lookup"><span data-stu-id="03a95-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="03a95-127">W przykładzie założono, że usługi IIS działają w zintegrowanym trybu i że aplikacja używa [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="03a95-127">The example assumes that IIS is running in Integrated mode and that the application is using the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] or a later version.</span></span> <span data-ttu-id="03a95-128">To zachowanie nie występuje w wersjach [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] wcześniejszy niż [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="03a95-128">This behavior does not occur in versions of the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] earlier than the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="03a95-129">Wartości w tym przykładzie są wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="03a95-129">The values in the example are the default values.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"   
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="03a95-130">Informacje o elementach</span><span class="sxs-lookup"><span data-stu-id="03a95-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="03a95-131">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="03a95-131">Namespace</span></span>||  
|<span data-ttu-id="03a95-132">Nazwa schematu</span><span class="sxs-lookup"><span data-stu-id="03a95-132">Schema Name</span></span>||  
|<span data-ttu-id="03a95-133">Sprawdzanie poprawności pliku</span><span class="sxs-lookup"><span data-stu-id="03a95-133">Validation File</span></span>||  
|<span data-ttu-id="03a95-134">Może być pusta</span><span class="sxs-lookup"><span data-stu-id="03a95-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="03a95-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03a95-135">See Also</span></span>  
 [<span data-ttu-id="03a95-136">\<applicationPool > elementu (ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="03a95-136">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
