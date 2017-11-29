---
title: "&lt;Throwunobservedtaskexceptions —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d171c2058a79476d99c5952cc6a697f126af81c4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltthrowunobservedtaskexceptionsgt-element"></a><span data-ttu-id="d8100-102">&lt;Throwunobservedtaskexceptions —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="d8100-102">&lt;ThrowUnobservedTaskExceptions&gt; Element</span></span>
<span data-ttu-id="d8100-103">Określa, czy zadanie nieobsługiwanych wyjątków powinny przerwanie uruchomiony proces.</span><span class="sxs-lookup"><span data-stu-id="d8100-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
 <span data-ttu-id="d8100-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="d8100-104">\<configuration></span></span>  
<span data-ttu-id="d8100-105">\<Runtime ></span><span class="sxs-lookup"><span data-stu-id="d8100-105">\<runtime></span></span>  
<span data-ttu-id="d8100-106">\<Throwunobservedtaskexceptions — ></span><span class="sxs-lookup"><span data-stu-id="d8100-106">\<ThrowUnobservedTaskExceptions></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8100-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="d8100-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8100-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d8100-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d8100-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d8100-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8100-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d8100-110">Attributes</span></span>  
  
|<span data-ttu-id="d8100-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d8100-111">Attribute</span></span>|<span data-ttu-id="d8100-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d8100-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d8100-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="d8100-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d8100-114">Określa, czy zadanie nieobsługiwanych wyjątków powinny przerwanie uruchomiony proces.</span><span class="sxs-lookup"><span data-stu-id="d8100-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d8100-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="d8100-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d8100-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="d8100-116">Value</span></span>|<span data-ttu-id="d8100-117">Opis</span><span class="sxs-lookup"><span data-stu-id="d8100-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="d8100-118">Nie kończy proces uruchomione zadania nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d8100-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="d8100-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="d8100-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="d8100-120">Kończy proces uruchomione zadania nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d8100-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8100-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d8100-121">Child Elements</span></span>  
 <span data-ttu-id="d8100-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="d8100-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8100-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d8100-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d8100-124">Element</span><span class="sxs-lookup"><span data-stu-id="d8100-124">Element</span></span>|<span data-ttu-id="d8100-125">Opis</span><span class="sxs-lookup"><span data-stu-id="d8100-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d8100-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d8100-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d8100-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d8100-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="d8100-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d8100-128">Remarks</span></span>  
 <span data-ttu-id="d8100-129">Jeśli wyjątek, który jest skojarzony z <xref:System.Threading.Tasks.Task> nie zostało spełnione, brak nie <xref:System.Threading.Tasks.Task.Wait%2A> operacji, element nadrzędny nie jest dołączony i <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> właściwości nie została przeczytana zadania wyjątek jest uznawany za niezaobserwowany.</span><span class="sxs-lookup"><span data-stu-id="d8100-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="d8100-130">W [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], przez domyślne, jeśli <xref:System.Threading.Tasks.Task> mający niezaobserwowany wyjątek bezużytecznych, finalizator zgłasza wyjątek i kończy proces.</span><span class="sxs-lookup"><span data-stu-id="d8100-130">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="d8100-131">Zakończenie procesu jest określana przez czas wyrzucanie elementów bezużytecznych i finalizacji.</span><span class="sxs-lookup"><span data-stu-id="d8100-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="d8100-132">Aby ułatwić deweloperom pisanie kodu asynchroniczny oparty na zadaniach, [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] zmieni to domyślne zachowanie dla wyznaczonego wyjątków.</span><span class="sxs-lookup"><span data-stu-id="d8100-132">To make it easier for developers to write asynchronous code based on tasks, the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="d8100-133">Być niezauważalna wyjątki nadal powodują <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> się zdarzenia, ale domyślnie nie zakończyć proces.</span><span class="sxs-lookup"><span data-stu-id="d8100-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="d8100-134">Zamiast tego wyjątku została zignorowana po wywołaniu zdarzenia, niezależnie od tego, czy program obsługi zdarzeń przestrzega wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d8100-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="d8100-135">W [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], można użyć [ \<throwunobservedtaskexceptions — > element](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) w pliku konfiguracji aplikacji, aby włączyć [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] zachowanie Zgłaszanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="d8100-135">In the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], you can use the [\<ThrowUnobservedTaskExceptions> element](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) in an application configuration file to enable the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="d8100-136">Można również określić zachowanie wyjątek w jednym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="d8100-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
-   <span data-ttu-id="d8100-137">Przez ustawienie zmiennej środowiskowej `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span><span class="sxs-lookup"><span data-stu-id="d8100-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
-   <span data-ttu-id="d8100-138">Przez ustawienie rejestru DWORD wartość throwunobservedtaskexceptions — = 1 w HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. Klucz NETFramework.</span><span class="sxs-lookup"><span data-stu-id="d8100-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8100-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8100-139">Example</span></span>  
 <span data-ttu-id="d8100-140">Poniższy przykład pokazuje, jak można włączyć zgłaszanie wyjątków w zadania przy użyciu pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d8100-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="d8100-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8100-141">Example</span></span>  
 <span data-ttu-id="d8100-142">W poniższym przykładzie pokazano, jak niezaobserwowany wyjątek zadania.</span><span class="sxs-lookup"><span data-stu-id="d8100-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="d8100-143">Kod musi być uruchamiany jako wydanych program działał prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="d8100-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d8100-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8100-144">See Also</span></span>  
 [<span data-ttu-id="d8100-145">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="d8100-145">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="d8100-146">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d8100-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
