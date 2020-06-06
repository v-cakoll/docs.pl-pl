---
title: <ThrowUnobservedTaskExceptions> Element
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
ms.openlocfilehash: de5a686bcbd88fc52173b488103f033575623d62
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153818"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="b4f6a-102">\<ThrowUnobservedTaskExceptions> Element</span><span class="sxs-lookup"><span data-stu-id="b4f6a-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="b4f6a-103">Określa, czy Nieobsłużone wyjątki zadań powinny kończyć uruchomiony proces.</span><span class="sxs-lookup"><span data-stu-id="b4f6a-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**  
  
## <a name="syntax"></a><span data-ttu-id="b4f6a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4f6a-104">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4f6a-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b4f6a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b4f6a-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b4f6a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4f6a-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b4f6a-107">Attributes</span></span>  
  
|<span data-ttu-id="b4f6a-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b4f6a-108">Attribute</span></span>|<span data-ttu-id="b4f6a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="b4f6a-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="b4f6a-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="b4f6a-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="b4f6a-111">Określa, czy Nieobsłużone wyjątki zadań powinny kończyć uruchomiony proces.</span><span class="sxs-lookup"><span data-stu-id="b4f6a-111">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b4f6a-112">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="b4f6a-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="b4f6a-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="b4f6a-113">Value</span></span>|<span data-ttu-id="b4f6a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b4f6a-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="b4f6a-115">Nie przerywa uruchomionego procesu dla nieobsłużonego wyjątku zadania.</span><span class="sxs-lookup"><span data-stu-id="b4f6a-115">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="b4f6a-116">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="b4f6a-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="b4f6a-117">Kończy uruchomiony proces dla nieobsłużonego wyjątku zadania.</span><span class="sxs-lookup"><span data-stu-id="b4f6a-117">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b4f6a-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b4f6a-118">Child Elements</span></span>  
 <span data-ttu-id="b4f6a-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="b4f6a-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b4f6a-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b4f6a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b4f6a-121">Element</span><span class="sxs-lookup"><span data-stu-id="b4f6a-121">Element</span></span>|<span data-ttu-id="b4f6a-122">Opis</span><span class="sxs-lookup"><span data-stu-id="b4f6a-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b4f6a-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b4f6a-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b4f6a-124">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b4f6a-124">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="b4f6a-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4f6a-125">Remarks</span></span>  
 <span data-ttu-id="b4f6a-126">Jeśli nie zaobserwowano wyjątku, który jest skojarzony z programem, nie ma <xref:System.Threading.Tasks.Task> żadnej <xref:System.Threading.Tasks.Task.Wait%2A> operacji, element nadrzędny nie jest dołączony i <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> Właściwość nie została odczytana, ponieważ wyjątek zadania jest traktowany jako nieobserwowany.</span><span class="sxs-lookup"><span data-stu-id="b4f6a-126">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="b4f6a-127">W .NET Framework 4 domyślnie, jeśli dla, <xref:System.Threading.Tasks.Task> który ma niezauważalny wyjątek jest odzyskiwany, finalizator zgłasza wyjątek i kończy proces.</span><span class="sxs-lookup"><span data-stu-id="b4f6a-127">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="b4f6a-128">Zakończenie procesu zależy od chronometrażu wyrzucania elementów bezużytecznych i finalizacji.</span><span class="sxs-lookup"><span data-stu-id="b4f6a-128">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="b4f6a-129">Aby ułatwić deweloperom pisanie kodu asynchronicznego na podstawie zadań, .NET Framework 4,5 zmienia to zachowanie domyślne dla nieobserwowanych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="b4f6a-129">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="b4f6a-130">Niezauważalne wyjątki nadal powodują <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> , że zdarzenie zostanie wywołane, ale domyślnie proces nie zostanie zakończony.</span><span class="sxs-lookup"><span data-stu-id="b4f6a-130">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="b4f6a-131">Zamiast tego wyjątek jest ignorowany po wywołaniu zdarzenia, niezależnie od tego, czy program obsługi zdarzeń obserwuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b4f6a-131">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="b4f6a-132">W .NET Framework 4,5 można użyć [ \<ThrowUnobservedTaskExceptions> elementu](throwunobservedtaskexceptions-element.md) w pliku konfiguracyjnym aplikacji, aby włączyć .NET Framework 4 zachowanie zgłaszania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b4f6a-132">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="b4f6a-133">Możesz również określić zachowanie wyjątku w jeden z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="b4f6a-133">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="b4f6a-134">Ustawiając zmienną środowiskową `COMPlus_ThrowUnobservedTaskExceptions` ( `set COMPlus_ThrowUnobservedTaskExceptions=1` ).</span><span class="sxs-lookup"><span data-stu-id="b4f6a-134">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="b4f6a-135">Ustawiając wartość DWORD rejestru ThrowUnobservedTaskExceptions = 1 w HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . Klucz NETFramework.</span><span class="sxs-lookup"><span data-stu-id="b4f6a-135">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4f6a-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4f6a-136">Example</span></span>  
 <span data-ttu-id="b4f6a-137">Poniższy przykład pokazuje, jak włączyć zgłaszanie wyjątków w zadaniach przy użyciu pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b4f6a-137">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="b4f6a-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4f6a-138">Example</span></span>  
 <span data-ttu-id="b4f6a-139">Poniższy przykład demonstruje, jak wyjątek niezauważalny jest generowany z zadania.</span><span class="sxs-lookup"><span data-stu-id="b4f6a-139">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="b4f6a-140">Aby program działał prawidłowo, kod musi być uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="b4f6a-140">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b4f6a-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4f6a-141">See also</span></span>

- [<span data-ttu-id="b4f6a-142">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="b4f6a-142">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b4f6a-143">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b4f6a-143">Configuration File Schema</span></span>](../index.md)
