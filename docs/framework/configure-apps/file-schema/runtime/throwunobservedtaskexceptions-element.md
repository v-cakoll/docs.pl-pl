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
ms.openlocfilehash: de5a686bcbd88fc52173b488103f033575623d62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153818"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="44e82-102">\<ThrowUnobservedZamykacień> element</span><span class="sxs-lookup"><span data-stu-id="44e82-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="44e82-103">Określa, czy nieobsługiwalne wyjątki zadań powinny zakończyć uruchomiony proces.</span><span class="sxs-lookup"><span data-stu-id="44e82-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
<span data-ttu-id="44e82-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="44e82-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="44e82-105">&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="44e82-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="44e82-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedZadkustawy>**</span><span class="sxs-lookup"><span data-stu-id="44e82-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44e82-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="44e82-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44e82-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="44e82-108">Attributes and Elements</span></span>  
 <span data-ttu-id="44e82-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="44e82-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44e82-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="44e82-110">Attributes</span></span>  
  
|<span data-ttu-id="44e82-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="44e82-111">Attribute</span></span>|<span data-ttu-id="44e82-112">Opis</span><span class="sxs-lookup"><span data-stu-id="44e82-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="44e82-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="44e82-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="44e82-114">Określa, czy nieobsługiwalne wyjątki zadań powinny zakończyć uruchomiony proces.</span><span class="sxs-lookup"><span data-stu-id="44e82-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="44e82-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="44e82-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="44e82-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="44e82-116">Value</span></span>|<span data-ttu-id="44e82-117">Opis</span><span class="sxs-lookup"><span data-stu-id="44e82-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="44e82-118">Nie kończy uruchomionego procesu dla nieobsługiwał wyjątku zadania.</span><span class="sxs-lookup"><span data-stu-id="44e82-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="44e82-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="44e82-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="44e82-120">Kończy uruchomiony proces dla nieobsługiwał wyjątku zadania.</span><span class="sxs-lookup"><span data-stu-id="44e82-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44e82-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="44e82-121">Child Elements</span></span>  
 <span data-ttu-id="44e82-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="44e82-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44e82-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="44e82-123">Parent Elements</span></span>  
  
|<span data-ttu-id="44e82-124">Element</span><span class="sxs-lookup"><span data-stu-id="44e82-124">Element</span></span>|<span data-ttu-id="44e82-125">Opis</span><span class="sxs-lookup"><span data-stu-id="44e82-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="44e82-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44e82-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="44e82-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="44e82-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="44e82-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="44e82-128">Remarks</span></span>  
 <span data-ttu-id="44e82-129">Jeśli wyjątek, który jest <xref:System.Threading.Tasks.Task> skojarzony z a <xref:System.Threading.Tasks.Task.Wait%2A> nie została zaobserwowana, nie ma <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> operacji, nadrzędny nie jest dołączony, a właściwość nie została odczytana wyjątek zadania jest uważany za niezaobserwowany.</span><span class="sxs-lookup"><span data-stu-id="44e82-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="44e82-130">W .NET Framework 4, domyślnie, <xref:System.Threading.Tasks.Task> jeśli, który ma niezaobserwowany wyjątek jest zbierane śmieci, finalizatora zgłasza wyjątek i kończy proces.</span><span class="sxs-lookup"><span data-stu-id="44e82-130">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="44e82-131">Zakończenie procesu zależy od czasu wyrzucania elementów bezużytecznych i finalizacji.</span><span class="sxs-lookup"><span data-stu-id="44e82-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="44e82-132">Aby ułatwić deweloperom pisanie kodu asynchronicznego na podstawie zadań, program .NET Framework 4.5 zmienia to domyślne zachowanie dla niezaobserwowanych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="44e82-132">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="44e82-133">Niezaobserwowane wyjątki nadal powodują, że <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> zdarzenie ma zostać zwodowane, ale domyślnie proces nie kończy się.</span><span class="sxs-lookup"><span data-stu-id="44e82-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="44e82-134">Zamiast tego wyjątek jest ignorowany po zdarzenia jest wywoływana, niezależnie od tego, czy program obsługi zdarzeń przestrzega wyjątku.</span><span class="sxs-lookup"><span data-stu-id="44e82-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="44e82-135">W .NET Framework 4.5 można użyć [ \<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) w pliku konfiguracji aplikacji, aby włączyć zachowanie .NET Framework 4 zgłaszania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="44e82-135">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="44e82-136">Zachowanie wyjątku można również określić w jeden z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="44e82-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="44e82-137">Ustawiając zmienną `COMPlus_ThrowUnobservedTaskExceptions` `set COMPlus_ThrowUnobservedTaskExceptions=1`środowiskową ( ).</span><span class="sxs-lookup"><span data-stu-id="44e82-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="44e82-138">Ustawiając wartość rejestru DWORD ThrowUnobservedTaskExceptions = 1 w HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework.</span><span class="sxs-lookup"><span data-stu-id="44e82-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44e82-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="44e82-139">Example</span></span>  
 <span data-ttu-id="44e82-140">W poniższym przykładzie pokazano, jak włączyć zgłaszanie wyjątków w zadaniach przy użyciu pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="44e82-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="44e82-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="44e82-141">Example</span></span>  
 <span data-ttu-id="44e82-142">W poniższym przykładzie pokazano, jak nieobserwowany wyjątek jest generowany z zadania.</span><span class="sxs-lookup"><span data-stu-id="44e82-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="44e82-143">Kod musi być uruchomiony jako zwolniony program, aby działał poprawnie.</span><span class="sxs-lookup"><span data-stu-id="44e82-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="44e82-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="44e82-144">See also</span></span>

- [<span data-ttu-id="44e82-145">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="44e82-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="44e82-146">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="44e82-146">Configuration File Schema</span></span>](../index.md)
