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
ms.openlocfilehash: 3ed1e66c4aadab656455686a7a1e5028b035676a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252266"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="ce736-102">\<ThrowUnobservedTaskExceptions> Element</span><span class="sxs-lookup"><span data-stu-id="ce736-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="ce736-103">Określa, czy Nieobsłużone wyjątki zadań powinny kończyć uruchomiony proces.</span><span class="sxs-lookup"><span data-stu-id="ce736-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
<span data-ttu-id="ce736-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ce736-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ce736-105">&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="ce736-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="ce736-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<ThrowUnobservedTaskExceptions >**</span><span class="sxs-lookup"><span data-stu-id="ce736-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce736-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce736-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce736-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ce736-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ce736-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ce736-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce736-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ce736-110">Attributes</span></span>  
  
|<span data-ttu-id="ce736-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ce736-111">Attribute</span></span>|<span data-ttu-id="ce736-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ce736-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ce736-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="ce736-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ce736-114">Określa, czy Nieobsłużone wyjątki zadań powinny kończyć uruchomiony proces.</span><span class="sxs-lookup"><span data-stu-id="ce736-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ce736-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="ce736-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="ce736-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="ce736-116">Value</span></span>|<span data-ttu-id="ce736-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ce736-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ce736-118">Nie przerywa uruchomionego procesu dla nieobsłużonego wyjątku zadania.</span><span class="sxs-lookup"><span data-stu-id="ce736-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="ce736-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="ce736-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="ce736-120">Kończy uruchomiony proces dla nieobsłużonego wyjątku zadania.</span><span class="sxs-lookup"><span data-stu-id="ce736-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce736-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ce736-121">Child Elements</span></span>  
 <span data-ttu-id="ce736-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="ce736-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ce736-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ce736-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ce736-124">Element</span><span class="sxs-lookup"><span data-stu-id="ce736-124">Element</span></span>|<span data-ttu-id="ce736-125">Opis</span><span class="sxs-lookup"><span data-stu-id="ce736-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ce736-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ce736-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ce736-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ce736-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="ce736-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ce736-128">Remarks</span></span>  
 <span data-ttu-id="ce736-129">Jeśli nie zaobserwowano wyjątku, który jest <xref:System.Threading.Tasks.Task> skojarzony z programem, nie ma żadnej <xref:System.Threading.Tasks.Task.Wait%2A> operacji, element nadrzędny <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> nie jest dołączony i właściwość nie została odczytana, ponieważ wyjątek zadania jest traktowany jako nieobserwowany.</span><span class="sxs-lookup"><span data-stu-id="ce736-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="ce736-130">W .NET Framework 4 domyślnie, jeśli dla <xref:System.Threading.Tasks.Task> , który ma niezauważalny wyjątek jest odzyskiwany, finalizator zgłasza wyjątek i kończy proces.</span><span class="sxs-lookup"><span data-stu-id="ce736-130">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="ce736-131">Zakończenie procesu zależy od chronometrażu wyrzucania elementów bezużytecznych i finalizacji.</span><span class="sxs-lookup"><span data-stu-id="ce736-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="ce736-132">Aby ułatwić deweloperom pisanie kodu asynchronicznego na podstawie zadań, .NET Framework 4,5 zmienia to zachowanie domyślne dla nieobserwowanych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="ce736-132">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="ce736-133">Niezauważalne wyjątki nadal powodują <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> , że zdarzenie zostanie wywołane, ale domyślnie proces nie zostanie zakończony.</span><span class="sxs-lookup"><span data-stu-id="ce736-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="ce736-134">Zamiast tego wyjątek jest ignorowany po wywołaniu zdarzenia, niezależnie od tego, czy program obsługi zdarzeń obserwuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ce736-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="ce736-135">W .NET Framework 4,5 można użyć [ \<elementu > ThrowUnobservedTaskExceptions](throwunobservedtaskexceptions-element.md) w pliku konfiguracyjnym aplikacji, aby włączyć funkcję .NET Framework 4 Zgłaszanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ce736-135">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="ce736-136">Możesz również określić zachowanie wyjątku w jeden z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="ce736-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="ce736-137">Ustawiając zmienną `COMPlus_ThrowUnobservedTaskExceptions` środowiskową (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span><span class="sxs-lookup"><span data-stu-id="ce736-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="ce736-138">Ustawiając wartość DWORD rejestru ThrowUnobservedTaskExceptions = 1 w HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. Klucz NETFramework.</span><span class="sxs-lookup"><span data-stu-id="ce736-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce736-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce736-139">Example</span></span>  
 <span data-ttu-id="ce736-140">Poniższy przykład pokazuje, jak włączyć zgłaszanie wyjątków w zadaniach przy użyciu pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce736-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="ce736-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce736-141">Example</span></span>  
 <span data-ttu-id="ce736-142">Poniższy przykład demonstruje, jak wyjątek niezauważalny jest generowany z zadania.</span><span class="sxs-lookup"><span data-stu-id="ce736-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="ce736-143">Aby program działał prawidłowo, kod musi być uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="ce736-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ce736-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce736-144">See also</span></span>

- [<span data-ttu-id="ce736-145">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ce736-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ce736-146">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ce736-146">Configuration File Schema</span></span>](../index.md)
