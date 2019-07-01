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
ms.openlocfilehash: b9a43c5f5141e364ab9aac1cfdff577a8fb8a161
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486678"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="29128-102">\<System.Web >, Element (ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="29128-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="29128-103">Zawiera informacje o sposobie zarządzania zachowanie całego procesu w warstwie hostingu platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="29128-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
 <span data-ttu-id="29128-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="29128-104">\<configuration></span></span>  
<span data-ttu-id="29128-105">\<System.Web >, Element (ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="29128-105">\<system.web> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29128-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="29128-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29128-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="29128-107">Attributes and Elements</span></span>  
 <span data-ttu-id="29128-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="29128-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29128-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="29128-109">Attributes</span></span>  
 <span data-ttu-id="29128-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="29128-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="29128-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="29128-111">Child Elements</span></span>  
  
|<span data-ttu-id="29128-112">Element</span><span class="sxs-lookup"><span data-stu-id="29128-112">Element</span></span>|<span data-ttu-id="29128-113">Opis</span><span class="sxs-lookup"><span data-stu-id="29128-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29128-114">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="29128-114">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="29128-115">Określa ustawienia konfiguracji dla pul aplikacji usług IIS w plikach aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="29128-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="29128-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="29128-116">Parent Elements</span></span>  
  
|<span data-ttu-id="29128-117">Element</span><span class="sxs-lookup"><span data-stu-id="29128-117">Element</span></span>|<span data-ttu-id="29128-118">Opis</span><span class="sxs-lookup"><span data-stu-id="29128-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29128-119">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="29128-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="29128-120">Określa element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="29128-120">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29128-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="29128-121">Remarks</span></span>  
 <span data-ttu-id="29128-122">`system.web` Elementu i jego podrzędny `applicationPool` element zostały dodane do programu .NET Framework, począwszy od programu .NET Framework 3.5 z dodatkiem SP1.</span><span class="sxs-lookup"><span data-stu-id="29128-122">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="29128-123">Po uruchomieniu usług IIS 7.0 lub nowsze wersje w trybie zintegrowanym tej kombinacji elementu umożliwia skonfigurowanie sposobu ASP.NET zarządza wątków i jak go umieszcza w kolejce żądań gdy ASP.NET jest hostowany w puli aplikacji usług IIS.</span><span class="sxs-lookup"><span data-stu-id="29128-123">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="29128-124">Po uruchomieniu usług IIS 7.0 lub nowsze wersje w trybie klasycznym lub ISAPI, te ustawienia są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="29128-124">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29128-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="29128-125">Example</span></span>  
 <span data-ttu-id="29128-126">Poniższy przykład pokazuje, jak skonfigurować sposób działania całego procesu ASP.NET w pliku konfigurację aspnet.config ASP.NET znajduje się w puli aplikacji IIS.</span><span class="sxs-lookup"><span data-stu-id="29128-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="29128-127">W przykładzie założono, że uruchomieniu usług IIS w zintegrowany tryb i że aplikacja używa .NET Framework 3.5 z dodatkiem SP1 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="29128-127">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="29128-128">To zachowanie nie występuje w wersjach programu .NET Framework wcześniejszych niż .NET Framework 3.5 SP1.</span><span class="sxs-lookup"><span data-stu-id="29128-128">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="29128-129">Wartości w przykładzie są wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="29128-129">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="29128-130">Informacje o elementach</span><span class="sxs-lookup"><span data-stu-id="29128-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="29128-131">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="29128-131">Namespace</span></span>||  
|<span data-ttu-id="29128-132">Nazwa schematu</span><span class="sxs-lookup"><span data-stu-id="29128-132">Schema Name</span></span>||  
|<span data-ttu-id="29128-133">Plik walidacji</span><span class="sxs-lookup"><span data-stu-id="29128-133">Validation File</span></span>||  
|<span data-ttu-id="29128-134">Może być pusta</span><span class="sxs-lookup"><span data-stu-id="29128-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="29128-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29128-135">See also</span></span>

- [<span data-ttu-id="29128-136">\<applicationPool >, Element (ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="29128-136">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
