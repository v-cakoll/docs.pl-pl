---
title: <applicationPool>, element (ustawienia internetowe)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 548f7de2753ef0c30aa787f4c879af87987bfbde
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621506"
---
# <a name="applicationpool-element-web-settings"></a><span data-ttu-id="2dc32-102">\<applicationPool >, Element (ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="2dc32-102">\<applicationPool> Element (Web Settings)</span></span>
<span data-ttu-id="2dc32-103">Określa ustawienia konfiguracyjne, które są używane przez program ASP.NET do zarządzania zachowaniem całego procesu, gdy aplikacja ASP.NET działa w trybie zintegrowanym z [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="2dc32-103">Specifies configuration settings that are used by ASP.NET to manage process-wide behavior when an ASP.NET application is running in Integrated mode on [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or a later version.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2dc32-104">Ten element i funkcja obsługuje działają tylko, jeśli Twoja aplikacja ASP.NET jest hostowana w [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] lub nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="2dc32-104">This element and the feature it supports only work if your ASP.NET application is hosted on [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions.</span></span>  
  
 <span data-ttu-id="2dc32-105">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="2dc32-105">\<configuration></span></span>  
<span data-ttu-id="2dc32-106">\<System.Web >, Element (ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="2dc32-106">\<system.web> Element (Web Settings)</span></span>  
<span data-ttu-id="2dc32-107">\<applicationPool >, Element (ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="2dc32-107">\<applicationPool> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dc32-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="2dc32-108">Syntax</span></span>  
  
```xml  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2dc32-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2dc32-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2dc32-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2dc32-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2dc32-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2dc32-111">Attributes</span></span>  
  
|<span data-ttu-id="2dc32-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2dc32-112">Attribute</span></span>|<span data-ttu-id="2dc32-113">Opis</span><span class="sxs-lookup"><span data-stu-id="2dc32-113">Description</span></span>|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|<span data-ttu-id="2dc32-114">Określa liczbę równoczesnych żądań ASP.NET umożliwia dla każdego procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="2dc32-114">Specifies how many simultaneous requests ASP.NET allows per CPU.</span></span>|  
|`maxConcurrentThreadsPerCPU`|<span data-ttu-id="2dc32-115">Określa, jak wiele wątków jednocześnie może być uruchomiony dla puli aplikacji dla każdego Procesora.</span><span class="sxs-lookup"><span data-stu-id="2dc32-115">Specifies how many simultaneous threads can be running for an application pool for each CPU.</span></span> <span data-ttu-id="2dc32-116">Zapewnia alternatywny sposób sterowania współbieżnością ASP.NET, ponieważ pozwala ograniczyć liczbę zarządzanych wątkach, których można użyć na procesor CPU, aby obsłużyć żądania.</span><span class="sxs-lookup"><span data-stu-id="2dc32-116">This provides an alternative way to control ASP.NET concurrency, because you can limit the number of managed threads that can be used per CPU to serve requests.</span></span> <span data-ttu-id="2dc32-117">Domyślnie to ustawienie jest 0, co oznacza, że ASP.NET nie ogranicza liczbę wątków, które mogą być tworzone dla każdego Procesora, mimo że ogranicza liczbę wątków, które można utworzyć puli wątków CLR.</span><span class="sxs-lookup"><span data-stu-id="2dc32-117">By default this setting is 0, which means that ASP.NET does not limit the number of threads that can be created per CPU, although the CLR thread pool also limits the number of threads that can be created.</span></span>|  
|`requestQueueLimit`|<span data-ttu-id="2dc32-118">Określa maksymalną liczbę żądań, które można umieścić w kolejce dla platformy ASP.NET w pojedynczym procesie.</span><span class="sxs-lookup"><span data-stu-id="2dc32-118">Specifies the maximum number of requests that can be queued for ASP.NET in a single process.</span></span> <span data-ttu-id="2dc32-119">Po uruchomieniu co najmniej dwóch aplikacji ASP.NET w jednej puli aplikacji zbiorczego zestawu żądań wysyłanych do dowolnej aplikacji w puli podlega tego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="2dc32-119">When two or more ASP.NET applications run in a single application pool, the cumulative set of requests being made to any application in the application pool is subject to this setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2dc32-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2dc32-120">Child Elements</span></span>  
 <span data-ttu-id="2dc32-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="2dc32-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2dc32-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2dc32-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2dc32-123">Element</span><span class="sxs-lookup"><span data-stu-id="2dc32-123">Element</span></span>|<span data-ttu-id="2dc32-124">Opis</span><span class="sxs-lookup"><span data-stu-id="2dc32-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2dc32-125">\<system.web></span><span class="sxs-lookup"><span data-stu-id="2dc32-125">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="2dc32-126">Zawiera informacje na temat współdziałania platformy ASP.NET z aplikacją hosta.</span><span class="sxs-lookup"><span data-stu-id="2dc32-126">Contains information about how ASP.NET interacts with a host application.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2dc32-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2dc32-127">Remarks</span></span>  
 <span data-ttu-id="2dc32-128">Po uruchomieniu [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] lub jego nowsza wersja w trybie zintegrowanym tej kombinacji elementu umożliwia skonfigurowanie, jak ASP.NET zarządza żądaniami wątków i kolejki, gdy aplikacja jest obsługiwana w puli aplikacji usług IIS.</span><span class="sxs-lookup"><span data-stu-id="2dc32-128">When you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or a later version in Integrated mode, this element combination lets you configure how ASP.NET manages threads and queues requests when the application is hosted in an IIS application pool.</span></span> <span data-ttu-id="2dc32-129">Jeśli uruchomienie usług IIS 6 lub uruchomiony [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] w trybie klasycznym lub trybu ISAPI, te ustawienia są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="2dc32-129">If you run IIS 6 or you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] in Classic mode or in ISAPI mode, these settings are ignored.</span></span>  
  
 <span data-ttu-id="2dc32-130">`applicationPool` Ustawienia mają zastosowanie do wszystkich pul aplikacji działających w określonej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2dc32-130">The `applicationPool` settings apply to all application pools that run on a particular version of the .NET Framework.</span></span> <span data-ttu-id="2dc32-131">Ustawienia są zawarte w plikach aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="2dc32-131">The settings are contained in an aspnet.config file.</span></span> <span data-ttu-id="2dc32-132">Dostępna jest wersja tego pliku dla wersji 2.0 i 4.0 programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2dc32-132">There is a version of this file for versions 2.0 and 4.0 of the .NET Framework.</span></span> <span data-ttu-id="2dc32-133">(W wersji 3.0 i 3.5 programu .NET Framework Udostępnij plik aspnet.config w wersji 2.0).</span><span class="sxs-lookup"><span data-stu-id="2dc32-133">(Versions 3.0 and 3.5 of the .NET Framework share the aspnet.config file with version 2.0.)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2dc32-134">Jeśli uruchamiasz [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] na [!INCLUDE[win7](../../../../../includes/win7-md.md)], można skonfigurować plik aspnet.config osobne dla każdej puli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2dc32-134">If you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] on [!INCLUDE[win7](../../../../../includes/win7-md.md)], you can configure a separate aspnet.config file for every application pool.</span></span> <span data-ttu-id="2dc32-135">Dzięki temu można dostosować wydajność wątków dla każdej puli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2dc32-135">This lets you tailor the performance of the threads for each application pool.</span></span>  
  
 <span data-ttu-id="2dc32-136">Aby uzyskać `maxConcurrentRequestsPerCPU` ustawienie domyślne ustawienie "5000" [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] skutecznie wyłącza ograniczanie żądań, oznacza to kontrolowane przez platformę ASP.NET, chyba że faktycznie mieć co najmniej 5000 żądań na CPU.</span><span class="sxs-lookup"><span data-stu-id="2dc32-136">For the `maxConcurrentRequestsPerCPU` setting, the default setting of "5000" in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] effectively turns off request throttling that is controlled by ASP.NET, unless you actually have 5000 or more requests per CPU.</span></span> <span data-ttu-id="2dc32-137">Domyślne ustawienie zależy od zamiast puli wątków CLR automatycznie zarządzać współbieżności dla każdego procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="2dc32-137">The default setting depends instead on the CLR thread-pool to automatically manage concurrency per CPU.</span></span> <span data-ttu-id="2dc32-138">Aplikacji, które składają się zwiększone użycie asynchronicznego przetwarzania żądania lub wiele długotrwałych żądań, zablokowane na We/Wy, sieci będą mogli korzystać z zwiększenia domyślnego limitu w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2dc32-138">Applications that make extensive use of asynchronous request processing, or that have many long-running requests blocked on network I/O, will benefit from the increased default limit in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="2dc32-139">Ustawienie `maxConcurrentRequestsPerCPU` na zero spowoduje wyłączenie korzystanie z zarządzanych wątków do przetwarzania żądań ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2dc32-139">Setting `maxConcurrentRequestsPerCPU` to zero turns off the use of managed threads for processing ASP.NET requests.</span></span> <span data-ttu-id="2dc32-140">Po uruchomieniu aplikacji w puli aplikacji usług IIS, żądań, pozostają w wątku usługi IIS operacji We/Wy i w związku z tym współbieżności jest ograniczany przez usługi IIS wątek ustawienia.</span><span class="sxs-lookup"><span data-stu-id="2dc32-140">When an application runs in an IIS application pool, requests stay on the IIS I/O thread and therefore concurrency is throttled by IIS thread settings.</span></span>  
  
 <span data-ttu-id="2dc32-141">`requestQueueLimit` Ustawienie działa w taki sam sposób jak `requestQueueLimit` atrybutu [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, który jest ustawiony w plikach Web.config dla aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2dc32-141">The `requestQueueLimit` setting works the same way as the `requestQueueLimit` attribute of the [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, which is set in the Web.config files for ASP.NET applications.</span></span> <span data-ttu-id="2dc32-142">Jednak `requestQueueLimit` zastępuje ustawienia w pliku konfigurację aspnet.config `requestQueueLimit` ustawienia w pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="2dc32-142">However, the `requestQueueLimit` setting in an aspnet.config file overrides the `requestQueueLimit` setting in a Web.config file.</span></span> <span data-ttu-id="2dc32-143">Innymi słowy Jeśli ustawiono obu atrybutów (domyślnie jest to wartość true,) `requestQueueLimit` pierwszeństwo ma ustawienie w pliku konfigurację aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="2dc32-143">In other words, if both attributes are set (by default, this is true), the `requestQueueLimit` setting in the aspnet.config file takes precedence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2dc32-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="2dc32-144">Example</span></span>  
 <span data-ttu-id="2dc32-145">Poniższy przykład pokazuje, jak skonfigurować zachowanie całego procesu ASP.NET w pliku konfigurację aspnet.config w następujących okolicznościach:</span><span class="sxs-lookup"><span data-stu-id="2dc32-145">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file in the following circumstances:</span></span>  
  
- <span data-ttu-id="2dc32-146">Aplikacja jest obsługiwana w [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] puli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2dc32-146">The application is hosted in an [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] application pool.</span></span>  
  
- [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] <span data-ttu-id="2dc32-147">działa w trybie zintegrowanym.</span><span class="sxs-lookup"><span data-stu-id="2dc32-147">is running in Integrated mode.</span></span>  
  
- <span data-ttu-id="2dc32-148">Aplikacja używa [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="2dc32-148">The application is using the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] or a later version.</span></span>  
  
 <span data-ttu-id="2dc32-149">Wartości w przykładzie są wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="2dc32-149">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="2dc32-150">Informacje o elementach</span><span class="sxs-lookup"><span data-stu-id="2dc32-150">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2dc32-151">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="2dc32-151">Namespace</span></span>||  
|<span data-ttu-id="2dc32-152">Nazwa schematu</span><span class="sxs-lookup"><span data-stu-id="2dc32-152">Schema Name</span></span>||  
|<span data-ttu-id="2dc32-153">Plik walidacji</span><span class="sxs-lookup"><span data-stu-id="2dc32-153">Validation File</span></span>||  
|<span data-ttu-id="2dc32-154">Może być pusta</span><span class="sxs-lookup"><span data-stu-id="2dc32-154">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="2dc32-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2dc32-155">See also</span></span>

- [<span data-ttu-id="2dc32-156">\<System.Web >, Element (ustawienia sieci Web)</span><span class="sxs-lookup"><span data-stu-id="2dc32-156">\<system.web> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)
