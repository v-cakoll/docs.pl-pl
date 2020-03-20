---
title: <clear>Element <listeners> dla<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 905dad8274fede80f4809ff3c7a014049f9df450
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153545"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="ad0b4-102">\<clear> Element dla \<słuchaczy>> \<śledzenia</span><span class="sxs-lookup"><span data-stu-id="ad0b4-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="ad0b4-103">Czyści `Listeners` kolekcję do śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ad0b4-103">Clears the `Listeners` collection for trace.</span></span>  

<span data-ttu-id="ad0b4-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ad0b4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ad0b4-105">&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="ad0b4-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="ad0b4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>śledzenia**](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="ad0b4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="ad0b4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<słuchacze>**](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="ad0b4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="ad0b4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wyraźne>**</span><span class="sxs-lookup"><span data-stu-id="ad0b4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ad0b4-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad0b4-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad0b4-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ad0b4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ad0b4-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ad0b4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad0b4-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ad0b4-112">Attributes</span></span>  
 <span data-ttu-id="ad0b4-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="ad0b4-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ad0b4-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ad0b4-114">Child Elements</span></span>  
 <span data-ttu-id="ad0b4-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="ad0b4-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad0b4-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ad0b4-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ad0b4-117">Element</span><span class="sxs-lookup"><span data-stu-id="ad0b4-117">Element</span></span>|<span data-ttu-id="ad0b4-118">Opis</span><span class="sxs-lookup"><span data-stu-id="ad0b4-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ad0b4-119">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ad0b4-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="ad0b4-120">Określa odbiorniki śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, na którym ustawiony jest przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ad0b4-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="ad0b4-121">Zawiera odbiorniki, które zbierają, przechowują i trasy śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ad0b4-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="ad0b4-122">Zawiera odbiorniki, które zbierają, przechowują i rozsyłają wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ad0b4-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="ad0b4-123">Detektory kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="ad0b4-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad0b4-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad0b4-124">Remarks</span></span>  
 <span data-ttu-id="ad0b4-125">Element `<clear>` usuwa wszystkie odbiorniki `Listeners` z kolekcji do śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ad0b4-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="ad0b4-126">Można użyć `<clear>` elementu przed `<add>` użyciem elementu, aby mieć pewność, że nie ma żadnych innych aktywnych odbiorników w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ad0b4-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="ad0b4-127">Kolekcję `Listeners` można wyczyścić programowo, <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> wywołując <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> metodę`System.Diagnostics.Trace.Listeners.Clear()`we właściwości ( ).</span><span class="sxs-lookup"><span data-stu-id="ad0b4-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="ad0b4-128">Ten element może być używany w pliku konfiguracyjnym komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ad0b4-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad0b4-129">Element `<clear>` <xref:System.Diagnostics.DefaultTraceListener> usuwa `Listeners` z kolekcji, zmieniając zachowanie <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>i <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ad0b4-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="ad0b4-130">Wywołanie `Assert` `Fail` lub metoda zwykle powoduje wyświetlenie okna komunikatu.</span><span class="sxs-lookup"><span data-stu-id="ad0b4-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="ad0b4-131">Jednak okno komunikatu nie jest <xref:System.Diagnostics.DefaultTraceListener> wyświetlany, jeśli `Listeners` nie jest w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ad0b4-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad0b4-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad0b4-132">Example</span></span>  
 <span data-ttu-id="ad0b4-133">W poniższym przykładzie `<clear>` pokazano, jak `<add>` używać elementu przed `console` użyciem elementu, aby dodać odbiornika do `Listeners` kolekcji do śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ad0b4-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ad0b4-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad0b4-134">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="ad0b4-135">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="ad0b4-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ad0b4-136">\<usuń></span><span class="sxs-lookup"><span data-stu-id="ad0b4-136">\<remove></span></span>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="ad0b4-137">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="ad0b4-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
