---
title: "&lt;Wyczyść&gt; elementu &lt;odbiorników&gt; dla &lt;śledzenia&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 34e6e7c505dab135452664fdb815ee3e905a2ad0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="bf94c-102">&lt;Wyczyść&gt; elementu &lt;odbiorników&gt; dla &lt;śledzenia&gt;</span><span class="sxs-lookup"><span data-stu-id="bf94c-102">&lt;clear&gt; Element for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="bf94c-103">Czyści `Listeners` kolekcji do śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bf94c-103">Clears the `Listeners` collection for trace.</span></span>  
  
 <span data-ttu-id="bf94c-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="bf94c-104">\<configuration></span></span>  
<span data-ttu-id="bf94c-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="bf94c-105">\<system.diagnostics></span></span>  
<span data-ttu-id="bf94c-106">\<śledzenia ></span><span class="sxs-lookup"><span data-stu-id="bf94c-106">\<trace></span></span>  
<span data-ttu-id="bf94c-107">\<obiekty nasłuchujące ></span><span class="sxs-lookup"><span data-stu-id="bf94c-107">\<listeners></span></span>  
<span data-ttu-id="bf94c-108">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="bf94c-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf94c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf94c-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf94c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bf94c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bf94c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bf94c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf94c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bf94c-112">Attributes</span></span>  
 <span data-ttu-id="bf94c-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="bf94c-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bf94c-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bf94c-114">Child Elements</span></span>  
 <span data-ttu-id="bf94c-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="bf94c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf94c-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bf94c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="bf94c-117">Element</span><span class="sxs-lookup"><span data-stu-id="bf94c-117">Element</span></span>|<span data-ttu-id="bf94c-118">Opis</span><span class="sxs-lookup"><span data-stu-id="bf94c-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bf94c-119">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bf94c-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="bf94c-120">Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bf94c-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="bf94c-121">Zawiera nasłuchujących zbierania, przechowywania i trasy śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="bf94c-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="bf94c-122">Zawiera nasłuchujących zbierania, przechowywania i kierowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="bf94c-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="bf94c-123">Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="bf94c-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf94c-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf94c-124">Remarks</span></span>  
 <span data-ttu-id="bf94c-125">`<clear>` Elementu spowoduje usunięcie wszystkich odbiorników z `Listeners` kolekcji do śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bf94c-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="bf94c-126">Można użyć `<clear>` element, aby można było używać `<add>` elementu, aby mieć pewność, istnieją inne odbiorników active w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="bf94c-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="bf94c-127">Możesz wyczyścić `Listeners` kolekcji programowo przez wywołanie metody <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> metoda <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> właściwości (`System.Diagnostics.Trace.Listeners.Clear()`).</span><span class="sxs-lookup"><span data-stu-id="bf94c-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="bf94c-128">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf94c-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf94c-129">`<clear>` Usuwa element <xref:System.Diagnostics.DefaultTraceListener> z `Listeners` kolekcji zmianę zachowania <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, i <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="bf94c-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="bf94c-130">Wywoływanie `Assert` lub `Fail` metody zwykle powoduje wyświetlanie okna komunikatu.</span><span class="sxs-lookup"><span data-stu-id="bf94c-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="bf94c-131">Jednak w oknie komunikatu nie jest wyświetlane, gdy <xref:System.Diagnostics.DefaultTraceListener> nie znajduje się w `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="bf94c-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf94c-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="bf94c-132">Example</span></span>  
 <span data-ttu-id="bf94c-133">Poniższy przykład przedstawia użycie `<clear>` element, aby można było używać `<add>` elementu do dodania odbiornika `console` do `Listeners` kolekcji do śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bf94c-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="bf94c-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bf94c-134">See Also</span></span>  
 <xref:System.Diagnostics.Trace.Listeners%2A>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 <xref:System.Diagnostics.TraceSource>  
 [<span data-ttu-id="bf94c-135">Schemat ustawień debugowania i śledzenia</span><span class="sxs-lookup"><span data-stu-id="bf94c-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="bf94c-136">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="bf94c-136">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)  
 [<span data-ttu-id="bf94c-137">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="bf94c-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
