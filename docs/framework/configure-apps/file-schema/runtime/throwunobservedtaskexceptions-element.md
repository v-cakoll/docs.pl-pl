---
title: <ThrowUnobservedTaskExceptions>, element
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3bc2bffa11c3205c265ca21a9d4c4caa9b31d4e9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281505"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="b9612-102">\<ThrowUnobservedTaskExceptions> Element</span><span class="sxs-lookup"><span data-stu-id="b9612-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="b9612-103">Określa, czy zadanie nieobsługiwanych wyjątków powinien wygasają uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="b9612-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
 <span data-ttu-id="b9612-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="b9612-104">\<configuration></span></span>  
<span data-ttu-id="b9612-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="b9612-105">\<runtime></span></span>  
<span data-ttu-id="b9612-106">\<ThrowUnobservedTaskExceptions></span><span class="sxs-lookup"><span data-stu-id="b9612-106">\<ThrowUnobservedTaskExceptions></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9612-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="b9612-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9612-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b9612-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b9612-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b9612-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9612-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b9612-110">Attributes</span></span>  
  
|<span data-ttu-id="b9612-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b9612-111">Attribute</span></span>|<span data-ttu-id="b9612-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b9612-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="b9612-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="b9612-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="b9612-114">Określa, czy zadanie nieobsługiwanych wyjątków powinien wygasają uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="b9612-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b9612-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="b9612-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="b9612-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="b9612-116">Value</span></span>|<span data-ttu-id="b9612-117">Opis</span><span class="sxs-lookup"><span data-stu-id="b9612-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="b9612-118">Nie kończy proces uruchomiony nieobsłużony wyjątek zadania.</span><span class="sxs-lookup"><span data-stu-id="b9612-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="b9612-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="b9612-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="b9612-120">Kończy proces uruchomiony nieobsłużony wyjątek zadania.</span><span class="sxs-lookup"><span data-stu-id="b9612-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9612-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b9612-121">Child Elements</span></span>  
 <span data-ttu-id="b9612-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="b9612-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b9612-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b9612-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b9612-124">Element</span><span class="sxs-lookup"><span data-stu-id="b9612-124">Element</span></span>|<span data-ttu-id="b9612-125">Opis</span><span class="sxs-lookup"><span data-stu-id="b9612-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b9612-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b9612-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b9612-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b9612-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="b9612-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b9612-128">Remarks</span></span>  
 <span data-ttu-id="b9612-129">Jeśli wyjątek, który jest skojarzony z <xref:System.Threading.Tasks.Task> nie zostało spełnione, istnieje nie <xref:System.Threading.Tasks.Task.Wait%2A> operacji, element nadrzędny nie jest podłączony i <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> właściwości nie została ona odczytana wyjątek zadania jest uważany za niewidocznego.</span><span class="sxs-lookup"><span data-stu-id="b9612-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="b9612-130">W [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], domyślnie, jeśli <xref:System.Threading.Tasks.Task> ma niewidocznego wyjątek bezużyteczne, finalizator zgłasza wyjątek i kończy proces.</span><span class="sxs-lookup"><span data-stu-id="b9612-130">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="b9612-131">Przed zakończeniem procesu jest określany przez chronometrażu wyrzucania elementów bezużytecznych i finalizacji jest zakończona.</span><span class="sxs-lookup"><span data-stu-id="b9612-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="b9612-132">Aby ułatwić programistom pisanie kodu asynchronicznego, na podstawie zadań, [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] zmienia to zachowanie domyślne niewidocznego wyjątków.</span><span class="sxs-lookup"><span data-stu-id="b9612-132">To make it easier for developers to write asynchronous code based on tasks, the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="b9612-133">Niezauważalne wyjątki, które nadal powodują <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> zdarzenia, ale domyślnie nie zakończyć proces.</span><span class="sxs-lookup"><span data-stu-id="b9612-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="b9612-134">Zamiast tego wyjątek jest ignorowany, po wywołaniu zdarzenia, niezależnie od tego, czy program obsługi zdarzeń przestrzega wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b9612-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="b9612-135">W [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], możesz użyć [ \<throwunobservedtaskexceptions — > element](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) w pliku konfiguracyjnym aplikacji, aby umożliwić [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] zachowanie zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b9612-135">In the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], you can use the [\<ThrowUnobservedTaskExceptions> element](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) in an application configuration file to enable the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="b9612-136">Można również określić zachowanie wyjątek w jednym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="b9612-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
-   <span data-ttu-id="b9612-137">Przez ustawienie zmiennej środowiskowej `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span><span class="sxs-lookup"><span data-stu-id="b9612-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
-   <span data-ttu-id="b9612-138">Przez ustawienie rejestru DWORD wartości throwunobservedtaskexceptions — = 1 w HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. Klucz NETFramework.</span><span class="sxs-lookup"><span data-stu-id="b9612-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9612-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9612-139">Example</span></span>  
 <span data-ttu-id="b9612-140">Poniższy przykład pokazuje, jak włączyć zgłaszanie wyjątków w zadaniach przy użyciu pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b9612-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="b9612-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9612-141">Example</span></span>  
 <span data-ttu-id="b9612-142">W poniższym przykładzie pokazano, jak niewidocznego wyjątku z zadania.</span><span class="sxs-lookup"><span data-stu-id="b9612-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="b9612-143">Kod musi działać jako wydana program działał prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="b9612-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b9612-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9612-144">See also</span></span>
- [<span data-ttu-id="b9612-145">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="b9612-145">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="b9612-146">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b9612-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
