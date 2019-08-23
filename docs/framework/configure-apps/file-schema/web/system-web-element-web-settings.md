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
ms.openlocfilehash: 41a638afa93e605221d5ef8172e243b1c61676bf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941384"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="15517-102">\<System. Web >, element (Ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="15517-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="15517-103">Zawiera informacje o sposobie zarządzania zachowaniem całego procesu przez warstwę hostingu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="15517-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
 <span data-ttu-id="15517-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="15517-104">\<configuration></span></span>  
<span data-ttu-id="15517-105">\<System. Web >, element (Ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="15517-105">\<system.web> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15517-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="15517-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15517-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="15517-107">Attributes and Elements</span></span>  
 <span data-ttu-id="15517-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="15517-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15517-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="15517-109">Attributes</span></span>  
 <span data-ttu-id="15517-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="15517-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="15517-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="15517-111">Child Elements</span></span>  
  
|<span data-ttu-id="15517-112">Element</span><span class="sxs-lookup"><span data-stu-id="15517-112">Element</span></span>|<span data-ttu-id="15517-113">Opis</span><span class="sxs-lookup"><span data-stu-id="15517-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15517-114">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="15517-114">\<applicationPool></span></span>](applicationpool-element-web-settings.md)|<span data-ttu-id="15517-115">Określa ustawienia konfiguracji dla pul aplikacji usług IIS w pliku aspnet. config.</span><span class="sxs-lookup"><span data-stu-id="15517-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="15517-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="15517-116">Parent Elements</span></span>  
  
|<span data-ttu-id="15517-117">Element</span><span class="sxs-lookup"><span data-stu-id="15517-117">Element</span></span>|<span data-ttu-id="15517-118">Opis</span><span class="sxs-lookup"><span data-stu-id="15517-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15517-119">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="15517-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="15517-120">Określa element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="15517-120">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15517-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15517-121">Remarks</span></span>  
 <span data-ttu-id="15517-122">Element i jego element podrzędny `applicationPool` zostały dodane do .NET Framework w ramach .NET Framework 3,5 SP1. `system.web`</span><span class="sxs-lookup"><span data-stu-id="15517-122">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="15517-123">W przypadku uruchamiania usług IIS 7,0 lub nowszych w trybie zintegrowanym Ta kombinacja elementów umożliwia skonfigurowanie sposobu, w jaki program ASP.NET zarządza wątkami i w jaki sposób kolejki są wysyłane w puli aplikacji usług IIS.</span><span class="sxs-lookup"><span data-stu-id="15517-123">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="15517-124">W przypadku uruchomienia usług IIS 7,0 lub nowszych w trybie klasycznym lub ISAPI te ustawienia zostaną zignorowane.</span><span class="sxs-lookup"><span data-stu-id="15517-124">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15517-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="15517-125">Example</span></span>  
 <span data-ttu-id="15517-126">Poniższy przykład pokazuje, jak skonfigurować zachowanie ASP.NET całego procesu w pliku aspnet. config, gdy ASP.NET jest hostowany w puli aplikacji IIS.</span><span class="sxs-lookup"><span data-stu-id="15517-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="15517-127">W przykładzie przyjęto założenie, że usługi IIS działają w trybie zintegrowanym i że aplikacja korzysta z .NET Framework 3,5 z dodatkiem SP1 lub nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="15517-127">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="15517-128">To zachowanie nie występuje w wersjach .NET Framework starszych niż .NET Framework 3,5 SP1.</span><span class="sxs-lookup"><span data-stu-id="15517-128">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="15517-129">Wartości w przykładzie są wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="15517-129">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="15517-130">Informacje o elementach</span><span class="sxs-lookup"><span data-stu-id="15517-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="15517-131">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="15517-131">Namespace</span></span>||  
|<span data-ttu-id="15517-132">Nazwa schematu</span><span class="sxs-lookup"><span data-stu-id="15517-132">Schema Name</span></span>||  
|<span data-ttu-id="15517-133">Plik walidacji</span><span class="sxs-lookup"><span data-stu-id="15517-133">Validation File</span></span>||  
|<span data-ttu-id="15517-134">Może być puste</span><span class="sxs-lookup"><span data-stu-id="15517-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="15517-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15517-135">See also</span></span>

- [<span data-ttu-id="15517-136">\<applicationPool >, element (Ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="15517-136">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)
