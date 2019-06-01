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
ms.openlocfilehash: cb6cfc8e1c3f0409d99d31efa0a645476b47e45e
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456253"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="f2fee-102">\<ThrowUnobservedTaskExceptions> Element</span><span class="sxs-lookup"><span data-stu-id="f2fee-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="f2fee-103">Określa, czy zadanie nieobsługiwanych wyjątków powinien wygasają uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="f2fee-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
 <span data-ttu-id="f2fee-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="f2fee-104">\<configuration></span></span>  
<span data-ttu-id="f2fee-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="f2fee-105">\<runtime></span></span>  
<span data-ttu-id="f2fee-106">\<ThrowUnobservedTaskExceptions></span><span class="sxs-lookup"><span data-stu-id="f2fee-106">\<ThrowUnobservedTaskExceptions></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2fee-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2fee-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2fee-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f2fee-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f2fee-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f2fee-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2fee-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f2fee-110">Attributes</span></span>  
  
|<span data-ttu-id="f2fee-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f2fee-111">Attribute</span></span>|<span data-ttu-id="f2fee-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f2fee-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="f2fee-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="f2fee-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="f2fee-114">Określa, czy zadanie nieobsługiwanych wyjątków powinien wygasają uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="f2fee-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f2fee-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="f2fee-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="f2fee-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="f2fee-116">Value</span></span>|<span data-ttu-id="f2fee-117">Opis</span><span class="sxs-lookup"><span data-stu-id="f2fee-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="f2fee-118">Nie kończy proces uruchomiony nieobsłużony wyjątek zadania.</span><span class="sxs-lookup"><span data-stu-id="f2fee-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="f2fee-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="f2fee-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="f2fee-120">Kończy proces uruchomiony nieobsłużony wyjątek zadania.</span><span class="sxs-lookup"><span data-stu-id="f2fee-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f2fee-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f2fee-121">Child Elements</span></span>  
 <span data-ttu-id="f2fee-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="f2fee-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f2fee-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f2fee-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f2fee-124">Element</span><span class="sxs-lookup"><span data-stu-id="f2fee-124">Element</span></span>|<span data-ttu-id="f2fee-125">Opis</span><span class="sxs-lookup"><span data-stu-id="f2fee-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f2fee-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f2fee-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f2fee-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="f2fee-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="f2fee-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f2fee-128">Remarks</span></span>  
 <span data-ttu-id="f2fee-129">Jeśli wyjątek, który jest skojarzony z <xref:System.Threading.Tasks.Task> nie zostało spełnione, istnieje nie <xref:System.Threading.Tasks.Task.Wait%2A> operacji, element nadrzędny nie jest podłączony i <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> właściwości nie została ona odczytana wyjątek zadania jest uważany za niewidocznego.</span><span class="sxs-lookup"><span data-stu-id="f2fee-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="f2fee-130">W [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], domyślnie, jeśli <xref:System.Threading.Tasks.Task> ma niewidocznego wyjątek bezużyteczne, finalizator zgłasza wyjątek i kończy proces.</span><span class="sxs-lookup"><span data-stu-id="f2fee-130">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="f2fee-131">Przed zakończeniem procesu jest określany przez chronometrażu wyrzucania elementów bezużytecznych i finalizacji jest zakończona.</span><span class="sxs-lookup"><span data-stu-id="f2fee-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="f2fee-132">Aby ułatwić programistom pisanie kodu asynchronicznego, na podstawie zadań programu .NET Framework 4.5, zmienia to zachowanie domyślne, niewidocznego wyjątków.</span><span class="sxs-lookup"><span data-stu-id="f2fee-132">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="f2fee-133">Niezauważalne wyjątki, które nadal powodują <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> zdarzenia, ale domyślnie nie zakończyć proces.</span><span class="sxs-lookup"><span data-stu-id="f2fee-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="f2fee-134">Zamiast tego wyjątek jest ignorowany, po wywołaniu zdarzenia, niezależnie od tego, czy program obsługi zdarzeń przestrzega wyjątku.</span><span class="sxs-lookup"><span data-stu-id="f2fee-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="f2fee-135">W .NET Framework 4.5, można użyć [ \<throwunobservedtaskexceptions — > element](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) w pliku konfiguracyjnym aplikacji, aby umożliwić działanie platformy .NET Framework 4 zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f2fee-135">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="f2fee-136">Można również określić zachowanie wyjątek w jednym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="f2fee-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="f2fee-137">Przez ustawienie zmiennej środowiskowej `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span><span class="sxs-lookup"><span data-stu-id="f2fee-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="f2fee-138">Przez ustawienie rejestru DWORD wartości throwunobservedtaskexceptions — = 1 w HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. Klucz NETFramework.</span><span class="sxs-lookup"><span data-stu-id="f2fee-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2fee-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="f2fee-139">Example</span></span>  
 <span data-ttu-id="f2fee-140">Poniższy przykład pokazuje, jak włączyć zgłaszanie wyjątków w zadaniach przy użyciu pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f2fee-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="f2fee-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="f2fee-141">Example</span></span>  
 <span data-ttu-id="f2fee-142">W poniższym przykładzie pokazano, jak niewidocznego wyjątku z zadania.</span><span class="sxs-lookup"><span data-stu-id="f2fee-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="f2fee-143">Kod musi działać jako wydana program działał prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="f2fee-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f2fee-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2fee-144">See also</span></span>

- [<span data-ttu-id="f2fee-145">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="f2fee-145">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="f2fee-146">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f2fee-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
