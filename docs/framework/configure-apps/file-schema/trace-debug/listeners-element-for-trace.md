---
title: <listeners>, element dla <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: fd12be1b775d7611ef3f16d23147470313bf9866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153376"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="8563e-102">\<słuchaczy> Element do \<śledzenia></span><span class="sxs-lookup"><span data-stu-id="8563e-102">\<listeners> Element for \<trace></span></span>
<span data-ttu-id="8563e-103">Określa odbiornik, który zbiera, przechowuje i kieruje wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8563e-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="8563e-104">Detektory kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="8563e-104">Listeners direct the tracing output to an appropriate target.</span></span>  

<span data-ttu-id="8563e-105">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8563e-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8563e-106">&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="8563e-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="8563e-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>śledzenia**](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="8563e-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="8563e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<słuchacze>**</span><span class="sxs-lookup"><span data-stu-id="8563e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**</span></span>

## <a name="syntax"></a><span data-ttu-id="8563e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="8563e-109">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8563e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8563e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8563e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8563e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8563e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8563e-112">Attributes</span></span>  
 <span data-ttu-id="8563e-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="8563e-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8563e-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8563e-114">Child Elements</span></span>  
  
|<span data-ttu-id="8563e-115">Element</span><span class="sxs-lookup"><span data-stu-id="8563e-115">Element</span></span>|<span data-ttu-id="8563e-116">Opis</span><span class="sxs-lookup"><span data-stu-id="8563e-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8563e-117">\<dodaj></span><span class="sxs-lookup"><span data-stu-id="8563e-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="8563e-118">Dodaje odbiornik do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8563e-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="8563e-119">\<wyraźne></span><span class="sxs-lookup"><span data-stu-id="8563e-119">\<clear></span></span>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="8563e-120">Czyści `Listeners` kolekcję do śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8563e-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="8563e-121">\<usuń></span><span class="sxs-lookup"><span data-stu-id="8563e-121">\<remove></span></span>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="8563e-122">Usuwa odbiornik z kolekcji. `Listeners`</span><span class="sxs-lookup"><span data-stu-id="8563e-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8563e-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8563e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8563e-124">Element</span><span class="sxs-lookup"><span data-stu-id="8563e-124">Element</span></span>|<span data-ttu-id="8563e-125">Opis</span><span class="sxs-lookup"><span data-stu-id="8563e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8563e-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8563e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="8563e-127">Określa element główny sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8563e-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="8563e-128">Zawiera odbiorniki, które zbierają, przechowują i trasy śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8563e-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8563e-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8563e-129">Remarks</span></span>  
 <span data-ttu-id="8563e-130">I <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> klasy współużytkuje tę samą kolekcję **odbiorników.**</span><span class="sxs-lookup"><span data-stu-id="8563e-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="8563e-131">Jeśli dodasz obiekt odbiornika do kolekcji w jednej z tych klas, druga klasa używa tego samego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="8563e-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="8563e-132">Klasy odbiornika dostarczane z .NET Framework pochodzą <xref:System.Diagnostics.TraceListener> z klasy.</span><span class="sxs-lookup"><span data-stu-id="8563e-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="8563e-133">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8563e-133">Configuration File</span></span>  
 <span data-ttu-id="8563e-134">Ten element może być używany w pliku konfiguracyjnym komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8563e-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8563e-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="8563e-135">Example</span></span>  
 <span data-ttu-id="8563e-136">W poniższym przykładzie pokazano, jak używać \*\* \<detektorów\*\*>`MyListener` `MyEventListener` element, aby dodać odbiorników i **odbiorników** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8563e-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="8563e-137">`MyListener`tworzy plik `MyListener.log` wywoływany i zapisuje dane wyjściowe do pliku.</span><span class="sxs-lookup"><span data-stu-id="8563e-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="8563e-138">`MyEventListener`tworzy wpis w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8563e-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"
          type="System.Diagnostics.TextWriterTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8563e-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8563e-139">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="8563e-140">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="8563e-140">Trace and Debug Settings Schema</span></span>](index.md)
