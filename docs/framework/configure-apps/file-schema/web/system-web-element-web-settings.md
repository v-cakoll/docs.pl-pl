---
title: <system.web>, element (ustawienia internetowe)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: 50566422c5e28585e93171c991144cf12a6866eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698502"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="a3e53-102">\<System.Web >, Element (ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="a3e53-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="a3e53-103">Zawiera informacje o sposobie zarządzania zachowanie całego procesu w warstwie hostingu platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a3e53-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
 <span data-ttu-id="a3e53-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="a3e53-104">\<configuration></span></span>  
<span data-ttu-id="a3e53-105">\<System.Web >, Element (ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="a3e53-105">\<system.web> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3e53-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3e53-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3e53-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a3e53-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a3e53-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a3e53-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3e53-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a3e53-109">Attributes</span></span>  
 <span data-ttu-id="a3e53-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="a3e53-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a3e53-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a3e53-111">Child Elements</span></span>  
  
|<span data-ttu-id="a3e53-112">Element</span><span class="sxs-lookup"><span data-stu-id="a3e53-112">Element</span></span>|<span data-ttu-id="a3e53-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a3e53-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3e53-114">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="a3e53-114">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="a3e53-115">Określa ustawienia konfiguracji dla pul aplikacji usług IIS w plikach aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="a3e53-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a3e53-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a3e53-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a3e53-117">Element</span><span class="sxs-lookup"><span data-stu-id="a3e53-117">Element</span></span>|<span data-ttu-id="a3e53-118">Opis</span><span class="sxs-lookup"><span data-stu-id="a3e53-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3e53-119">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="a3e53-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="a3e53-120">Określa element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a3e53-120">Specifies the root element in every configuration file that is used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3e53-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a3e53-121">Remarks</span></span>  
 <span data-ttu-id="a3e53-122">`system.web` Elementu i jego podrzędny `applicationPool` element zostały dodane do [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] w [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a3e53-122">The `system.web` element and its child `applicationPool` element were added to the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] as of [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="a3e53-123">Po uruchomieniu [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] lub nowsze wersje w trybie zintegrowanym, ta kombinacja element umożliwia skonfigurowanie sposobu ASP.NET zarządza wątków i jak go umieszcza w kolejce żądań gdy ASP.NET jest hostowany w puli aplikacji usług IIS.</span><span class="sxs-lookup"><span data-stu-id="a3e53-123">When you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="a3e53-124">Jeśli uruchamiasz [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] lub nowsze wersje w trybie klasycznym lub ISAPI, te ustawienia są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a3e53-124">If you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3e53-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="a3e53-125">Example</span></span>  
 <span data-ttu-id="a3e53-126">Poniższy przykład pokazuje, jak skonfigurować sposób działania całego procesu ASP.NET w pliku konfigurację aspnet.config ASP.NET znajduje się w puli aplikacji IIS.</span><span class="sxs-lookup"><span data-stu-id="a3e53-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="a3e53-127">W przykładzie założono, że uruchomieniu usług IIS w zintegrowany tryb i że aplikacja używa [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="a3e53-127">The example assumes that IIS is running in Integrated mode and that the application is using the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] or a later version.</span></span> <span data-ttu-id="a3e53-128">To zachowanie nie występuje w wersjach [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] wcześniejszy niż [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a3e53-128">This behavior does not occur in versions of the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] earlier than the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="a3e53-129">Wartości w przykładzie są wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="a3e53-129">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="a3e53-130">Informacje o elementach</span><span class="sxs-lookup"><span data-stu-id="a3e53-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a3e53-131">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="a3e53-131">Namespace</span></span>||  
|<span data-ttu-id="a3e53-132">Nazwa schematu</span><span class="sxs-lookup"><span data-stu-id="a3e53-132">Schema Name</span></span>||  
|<span data-ttu-id="a3e53-133">Plik walidacji</span><span class="sxs-lookup"><span data-stu-id="a3e53-133">Validation File</span></span>||  
|<span data-ttu-id="a3e53-134">Może być pusta</span><span class="sxs-lookup"><span data-stu-id="a3e53-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="a3e53-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3e53-135">See also</span></span>

- [<span data-ttu-id="a3e53-136">\<applicationPool >, Element (ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="a3e53-136">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
