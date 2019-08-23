---
title: <clear>Element dla <listeners> elementu<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 9816ba0f8e4ddd4c38537eb4e014a4240ff20407
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927170"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="4ae6a-102">\<Wyczyść element > dla \<odbiorników \<> śledzenia ></span><span class="sxs-lookup"><span data-stu-id="4ae6a-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="4ae6a-103">`Listeners` Czyści kolekcję do śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4ae6a-103">Clears the `Listeners` collection for trace.</span></span>  
  
 <span data-ttu-id="4ae6a-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4ae6a-104">\<configuration></span></span>  
<span data-ttu-id="4ae6a-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="4ae6a-105">\<system.diagnostics></span></span>  
<span data-ttu-id="4ae6a-106">\<> śledzenia</span><span class="sxs-lookup"><span data-stu-id="4ae6a-106">\<trace></span></span>  
<span data-ttu-id="4ae6a-107">\<> odbiorników</span><span class="sxs-lookup"><span data-stu-id="4ae6a-107">\<listeners></span></span>  
<span data-ttu-id="4ae6a-108">\<clear></span><span class="sxs-lookup"><span data-stu-id="4ae6a-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ae6a-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ae6a-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ae6a-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4ae6a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4ae6a-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4ae6a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ae6a-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4ae6a-112">Attributes</span></span>  
 <span data-ttu-id="4ae6a-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="4ae6a-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4ae6a-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4ae6a-114">Child Elements</span></span>  
 <span data-ttu-id="4ae6a-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="4ae6a-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4ae6a-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4ae6a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4ae6a-117">Element</span><span class="sxs-lookup"><span data-stu-id="4ae6a-117">Element</span></span>|<span data-ttu-id="4ae6a-118">Opis</span><span class="sxs-lookup"><span data-stu-id="4ae6a-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4ae6a-119">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4ae6a-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4ae6a-120">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4ae6a-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="4ae6a-121">Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4ae6a-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="4ae6a-122">Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty.</span><span class="sxs-lookup"><span data-stu-id="4ae6a-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="4ae6a-123">Odbiorniki kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="4ae6a-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ae6a-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ae6a-124">Remarks</span></span>  
 <span data-ttu-id="4ae6a-125">Element usuwa wszystkie odbiorniki `Listeners` z kolekcji w celu śledzenia. `<clear>`</span><span class="sxs-lookup"><span data-stu-id="4ae6a-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="4ae6a-126">Możesz użyć `<clear>` elementu przed użyciem elementu, `<add>` aby mieć pewność, że w kolekcji nie ma żadnych innych aktywnych odbiorników.</span><span class="sxs-lookup"><span data-stu-id="4ae6a-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="4ae6a-127">Możesz wyczyścić `Listeners` kolekcję programowo, <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> wywołując metodę we <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> właściwości (`System.Diagnostics.Trace.Listeners.Clear()`).</span><span class="sxs-lookup"><span data-stu-id="4ae6a-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="4ae6a-128">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4ae6a-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ae6a-129">`<clear>` Element usuwa<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> z kolekcji`Listeners`, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>zmieniając zachowanie metod<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>,,i. <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.DefaultTraceListener></span><span class="sxs-lookup"><span data-stu-id="4ae6a-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="4ae6a-130">Wywołanie metody `Fail` lub zwykle powoduje wyświetlenie okna komunikatu. `Assert`</span><span class="sxs-lookup"><span data-stu-id="4ae6a-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="4ae6a-131">Jednak okno komunikatu nie jest wyświetlane, jeśli <xref:System.Diagnostics.DefaultTraceListener> nie znajduje się `Listeners` w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4ae6a-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ae6a-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ae6a-132">Example</span></span>  
 <span data-ttu-id="4ae6a-133">Poniższy przykład pokazuje `<clear>` , jak używać elementu przed użyciem elementu, `<add>` aby `Listeners` dodać odbiornik `console` do kolekcji w celu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4ae6a-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4ae6a-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ae6a-134">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="4ae6a-135">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="4ae6a-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4ae6a-136">\<remove></span><span class="sxs-lookup"><span data-stu-id="4ae6a-136">\<remove></span></span>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="4ae6a-137">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="4ae6a-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
