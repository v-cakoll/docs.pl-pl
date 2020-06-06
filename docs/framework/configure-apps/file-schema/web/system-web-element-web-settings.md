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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152844"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="ddc68-102">\<system.web>, element (ustawienia internetowe)</span><span class="sxs-lookup"><span data-stu-id="ddc68-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="ddc68-103">Zawiera informacje o sposobie zarządzania zachowaniem całego procesu przez warstwę hostingu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ddc68-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.web>**  
  
## <a name="syntax"></a><span data-ttu-id="ddc68-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ddc68-104">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ddc68-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ddc68-105">Attributes and Elements</span></span>  

<span data-ttu-id="ddc68-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ddc68-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ddc68-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ddc68-107">Attributes</span></span>  

<span data-ttu-id="ddc68-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="ddc68-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ddc68-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ddc68-109">Child Elements</span></span>  
  
|<span data-ttu-id="ddc68-110">Element</span><span class="sxs-lookup"><span data-stu-id="ddc68-110">Element</span></span>|<span data-ttu-id="ddc68-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ddc68-111">Description</span></span>|  
|-------------|-----------------|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|<span data-ttu-id="ddc68-112">Określa ustawienia konfiguracji dla pul aplikacji usług IIS w pliku aspnet. config.</span><span class="sxs-lookup"><span data-stu-id="ddc68-112">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ddc68-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ddc68-113">Parent Elements</span></span>  
  
|<span data-ttu-id="ddc68-114">Element</span><span class="sxs-lookup"><span data-stu-id="ddc68-114">Element</span></span>|<span data-ttu-id="ddc68-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ddc68-115">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="ddc68-116">Określa element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ddc68-116">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddc68-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ddc68-117">Remarks</span></span>  

<span data-ttu-id="ddc68-118">`system.web`Element i jego element podrzędny `applicationPool` zostały dodane do .NET Framework w ramach .NET Framework 3,5 SP1.</span><span class="sxs-lookup"><span data-stu-id="ddc68-118">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="ddc68-119">W przypadku uruchamiania usług IIS 7,0 lub nowszych w trybie zintegrowanym Ta kombinacja elementów umożliwia skonfigurowanie sposobu, w jaki program ASP.NET zarządza wątkami i w jaki sposób kolejki są wysyłane w puli aplikacji usług IIS.</span><span class="sxs-lookup"><span data-stu-id="ddc68-119">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="ddc68-120">W przypadku uruchomienia usług IIS 7,0 lub nowszych w trybie klasycznym lub ISAPI te ustawienia zostaną zignorowane.</span><span class="sxs-lookup"><span data-stu-id="ddc68-120">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddc68-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="ddc68-121">Example</span></span>  

<span data-ttu-id="ddc68-122">Poniższy przykład pokazuje, jak skonfigurować zachowanie ASP.NET całego procesu w pliku aspnet. config, gdy ASP.NET jest hostowany w puli aplikacji IIS.</span><span class="sxs-lookup"><span data-stu-id="ddc68-122">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="ddc68-123">W przykładzie przyjęto założenie, że usługi IIS działają w trybie zintegrowanym i że aplikacja korzysta z .NET Framework 3,5 z dodatkiem SP1 lub nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="ddc68-123">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="ddc68-124">To zachowanie nie występuje w wersjach .NET Framework starszych niż .NET Framework 3,5 SP1.</span><span class="sxs-lookup"><span data-stu-id="ddc68-124">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="ddc68-125">Wartości w przykładzie są wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="ddc68-125">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="ddc68-126">Informacje o elementach</span><span class="sxs-lookup"><span data-stu-id="ddc68-126">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ddc68-127">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="ddc68-127">Namespace</span></span>||  
|<span data-ttu-id="ddc68-128">Nazwa schematu</span><span class="sxs-lookup"><span data-stu-id="ddc68-128">Schema Name</span></span>||  
|<span data-ttu-id="ddc68-129">Plik walidacji</span><span class="sxs-lookup"><span data-stu-id="ddc68-129">Validation File</span></span>||  
|<span data-ttu-id="ddc68-130">Może być puste</span><span class="sxs-lookup"><span data-stu-id="ddc68-130">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="ddc68-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddc68-131">See also</span></span>

- [<span data-ttu-id="ddc68-132">\<applicationPool>— Element (Ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="ddc68-132">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)
