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
ms.openlocfilehash: b37b05bdf90630251cbfcf86751243a3a8b77663
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152844"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="2b93f-102">\<element> system.web (ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="2b93f-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="2b93f-103">Zawiera informacje o tym, jak warstwa hostingu ASP.NET zarządza zachowaniem całego procesu.</span><span class="sxs-lookup"><span data-stu-id="2b93f-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
[<span data-ttu-id="2b93f-104">**\<>konfiguracyjne**</span><span class="sxs-lookup"><span data-stu-id="2b93f-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="2b93f-105">&nbsp;&nbsp;**\<>system.web**</span><span class="sxs-lookup"><span data-stu-id="2b93f-105">&nbsp;&nbsp;**\<system.web>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b93f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b93f-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b93f-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2b93f-107">Attributes and Elements</span></span>  

<span data-ttu-id="2b93f-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2b93f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b93f-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2b93f-109">Attributes</span></span>  

<span data-ttu-id="2b93f-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="2b93f-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2b93f-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2b93f-111">Child Elements</span></span>  
  
|<span data-ttu-id="2b93f-112">Element</span><span class="sxs-lookup"><span data-stu-id="2b93f-112">Element</span></span>|<span data-ttu-id="2b93f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="2b93f-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b93f-114">\<aplikacja></span><span class="sxs-lookup"><span data-stu-id="2b93f-114">\<applicationPool></span></span>](applicationpool-element-web-settings.md)|<span data-ttu-id="2b93f-115">Określa ustawienia konfiguracji pul aplikacji usług IIS w pliku aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="2b93f-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2b93f-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2b93f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="2b93f-117">Element</span><span class="sxs-lookup"><span data-stu-id="2b93f-117">Element</span></span>|<span data-ttu-id="2b93f-118">Opis</span><span class="sxs-lookup"><span data-stu-id="2b93f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b93f-119">\<>konfiguracyjne</span><span class="sxs-lookup"><span data-stu-id="2b93f-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="2b93f-120">Określa element główny w każdym pliku konfiguracyjnym używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b93f-120">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b93f-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b93f-121">Remarks</span></span>  

<span data-ttu-id="2b93f-122">Element `system.web` i jego `applicationPool` element podrzędny zostały dodane do .NET Framework w ramach .NET Framework 3.5 SP1.</span><span class="sxs-lookup"><span data-stu-id="2b93f-122">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="2b93f-123">Po uruchomieniu usług IIS 7.0 lub nowszych wersji w trybie zintegrowanym ta kombinacja elementów umożliwia skonfigurowanie sposobu zarządzania wątkami ASP.NET i sposobu kolejkowania żądań, gdy ASP.NET jest hostowany w puli aplikacji usług IIS.</span><span class="sxs-lookup"><span data-stu-id="2b93f-123">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="2b93f-124">Jeśli uruchomisz usługi IIS 7.0 lub nowsze w trybie klasycznym lub ISAPI, te ustawienia zostaną zignorowane.</span><span class="sxs-lookup"><span data-stu-id="2b93f-124">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b93f-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="2b93f-125">Example</span></span>  

<span data-ttu-id="2b93f-126">W poniższym przykładzie pokazano, jak skonfigurować zachowanie ASP.NET całego procesu w pliku aspnet.config, gdy ASP.NET jest hostowany w puli aplikacji usług IIS.</span><span class="sxs-lookup"><span data-stu-id="2b93f-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="2b93f-127">W przykładzie przyjęto założenie, że usługi IIS są uruchomione w trybie zintegrowanym i że aplikacja korzysta z dodatku SP1 programu .NET Framework 3.5 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="2b93f-127">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="2b93f-128">To zachowanie nie występuje w wersjach programu .NET Framework wcześniej niż dodatek SP1 .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="2b93f-128">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="2b93f-129">Wartości w przykładzie są wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="2b93f-129">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="2b93f-130">Informacje o elementach</span><span class="sxs-lookup"><span data-stu-id="2b93f-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2b93f-131">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="2b93f-131">Namespace</span></span>||  
|<span data-ttu-id="2b93f-132">Nazwa schematu</span><span class="sxs-lookup"><span data-stu-id="2b93f-132">Schema Name</span></span>||  
|<span data-ttu-id="2b93f-133">Plik sprawdzania poprawności</span><span class="sxs-lookup"><span data-stu-id="2b93f-133">Validation File</span></span>||  
|<span data-ttu-id="2b93f-134">Może być pusty</span><span class="sxs-lookup"><span data-stu-id="2b93f-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="2b93f-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b93f-135">See also</span></span>

- [<span data-ttu-id="2b93f-136">\<Element> aplikacji (ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="2b93f-136">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)
