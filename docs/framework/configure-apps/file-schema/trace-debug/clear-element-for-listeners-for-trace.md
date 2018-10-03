---
title: '&lt;Wyczyść&gt; elementu &lt;odbiorników&gt; dla &lt;śledzenia&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 91b4b4f132138fa6752c1da9b28e7a3ab7fad006
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48033450"
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="7ac53-102">&lt;Wyczyść&gt; elementu &lt;odbiorników&gt; dla &lt;śledzenia&gt;</span><span class="sxs-lookup"><span data-stu-id="7ac53-102">&lt;clear&gt; Element for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="7ac53-103">Czyści `Listeners` kolekcji na potrzeby śledzenia.</span><span class="sxs-lookup"><span data-stu-id="7ac53-103">Clears the `Listeners` collection for trace.</span></span>  
  
 <span data-ttu-id="7ac53-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="7ac53-104">\<configuration></span></span>  
<span data-ttu-id="7ac53-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="7ac53-105">\<system.diagnostics></span></span>  
<span data-ttu-id="7ac53-106">\<śledzenia ></span><span class="sxs-lookup"><span data-stu-id="7ac53-106">\<trace></span></span>  
<span data-ttu-id="7ac53-107">\<odbiorniki ></span><span class="sxs-lookup"><span data-stu-id="7ac53-107">\<listeners></span></span>  
<span data-ttu-id="7ac53-108">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="7ac53-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ac53-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="7ac53-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ac53-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7ac53-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7ac53-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7ac53-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ac53-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7ac53-112">Attributes</span></span>  
 <span data-ttu-id="7ac53-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="7ac53-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7ac53-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7ac53-114">Child Elements</span></span>  
 <span data-ttu-id="7ac53-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="7ac53-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7ac53-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7ac53-116">Parent Elements</span></span>  
  
|<span data-ttu-id="7ac53-117">Element</span><span class="sxs-lookup"><span data-stu-id="7ac53-117">Element</span></span>|<span data-ttu-id="7ac53-118">Opis</span><span class="sxs-lookup"><span data-stu-id="7ac53-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7ac53-119">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7ac53-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="7ac53-120">Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="7ac53-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="7ac53-121">Zawiera obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="7ac53-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="7ac53-122">Zawiera obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów w postaci.</span><span class="sxs-lookup"><span data-stu-id="7ac53-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="7ac53-123">Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="7ac53-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ac53-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7ac53-124">Remarks</span></span>  
 <span data-ttu-id="7ac53-125">`<clear>` Elementu usuwa wszystkie odbiorniki z `Listeners` kolekcji na potrzeby śledzenia.</span><span class="sxs-lookup"><span data-stu-id="7ac53-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="7ac53-126">Możesz użyć `<clear>` element przed użyciem `<add>` elementu, aby mieć pewność, istnieją nie aktywne odbiorniki w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7ac53-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="7ac53-127">Możesz wyczyścić `Listeners` kolekcji programowo przez wywołanie metody <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> metody <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> właściwości (`System.Diagnostics.Trace.Listeners.Clear()`).</span><span class="sxs-lookup"><span data-stu-id="7ac53-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="7ac53-128">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7ac53-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ac53-129">`<clear>` Usuwa element <xref:System.Diagnostics.DefaultTraceListener> z `Listeners` kolekcji, zmiany zachowania <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, i <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="7ac53-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="7ac53-130">Wywoływanie `Assert` lub `Fail` metoda zwykle powoduje wyświetlanie okna komunikatu.</span><span class="sxs-lookup"><span data-stu-id="7ac53-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="7ac53-131">Jednak okno komunikatu nie jest wyświetlana Jeśli <xref:System.Diagnostics.DefaultTraceListener> nie znajduje się w `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7ac53-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ac53-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="7ac53-132">Example</span></span>  
 <span data-ttu-id="7ac53-133">Poniższy przykład pokazuje, jak używać `<clear>` element przed użyciem `<add>` elementu do dodania odbiornika `console` do `Listeners` kolekcji na potrzeby śledzenia.</span><span class="sxs-lookup"><span data-stu-id="7ac53-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7ac53-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ac53-134">See Also</span></span>  
 <xref:System.Diagnostics.Trace.Listeners%2A>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 <xref:System.Diagnostics.TraceSource>  
 [<span data-ttu-id="7ac53-135">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="7ac53-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="7ac53-136">\<remove></span><span class="sxs-lookup"><span data-stu-id="7ac53-136">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)  
 [<span data-ttu-id="7ac53-137">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="7ac53-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
