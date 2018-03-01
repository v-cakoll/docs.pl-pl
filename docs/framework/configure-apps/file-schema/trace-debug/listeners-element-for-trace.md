---
title: "&lt;obiekty nasłuchujące&gt; elementu &lt;śledzenia&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: b9c1f52f880a38791a9a8d5b5372b2ad53c5569f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltlistenersgt-element-for-lttracegt"></a><span data-ttu-id="cc577-102">&lt;obiekty nasłuchujące&gt; elementu &lt;śledzenia&gt;</span><span class="sxs-lookup"><span data-stu-id="cc577-102">&lt;listeners&gt; Element for &lt;trace&gt;</span></span>
<span data-ttu-id="cc577-103">Określa odbiornika zbiera, magazynów i kieruje komunikaty.</span><span class="sxs-lookup"><span data-stu-id="cc577-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="cc577-104">Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="cc577-104">Listeners direct the tracing output to an appropriate target.</span></span>  
  
 <span data-ttu-id="cc577-105">\<Konfiguracja > — Element</span><span class="sxs-lookup"><span data-stu-id="cc577-105">\<configuration> Element</span></span>  
<span data-ttu-id="cc577-106">\<System.Diagnostics > — Element</span><span class="sxs-lookup"><span data-stu-id="cc577-106">\<system.diagnostics> Element</span></span>  
<span data-ttu-id="cc577-107">\<śledzenia > — Element</span><span class="sxs-lookup"><span data-stu-id="cc577-107">\<trace> Element</span></span>  
<span data-ttu-id="cc577-108">\<obiekty nasłuchujące > elementu \<śledzenia ></span><span class="sxs-lookup"><span data-stu-id="cc577-108">\<listeners> Element for \<trace></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc577-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc577-109">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc577-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cc577-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cc577-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cc577-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc577-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cc577-112">Attributes</span></span>  
 <span data-ttu-id="cc577-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="cc577-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cc577-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cc577-114">Child Elements</span></span>  
  
|<span data-ttu-id="cc577-115">Element</span><span class="sxs-lookup"><span data-stu-id="cc577-115">Element</span></span>|<span data-ttu-id="cc577-116">Opis</span><span class="sxs-lookup"><span data-stu-id="cc577-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc577-117">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="cc577-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|<span data-ttu-id="cc577-118">Dodaje odbiornika do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cc577-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="cc577-119">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="cc577-119">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|<span data-ttu-id="cc577-120">Czyści `Listeners` kolekcji do śledzenia.</span><span class="sxs-lookup"><span data-stu-id="cc577-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="cc577-121">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="cc577-121">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|<span data-ttu-id="cc577-122">Usuwa odbiornik z `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cc577-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cc577-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cc577-123">Parent Elements</span></span>  
  
|<span data-ttu-id="cc577-124">Element</span><span class="sxs-lookup"><span data-stu-id="cc577-124">Element</span></span>|<span data-ttu-id="cc577-125">Opis</span><span class="sxs-lookup"><span data-stu-id="cc577-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cc577-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cc577-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="cc577-127">Określa element root dla sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cc577-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="cc577-128">Zawiera nasłuchujących zbierania, przechowywania i trasy śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="cc577-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc577-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc577-129">Remarks</span></span>  
 <span data-ttu-id="cc577-130"><xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace> klasy udostępnianie takie same **odbiorników** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cc577-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="cc577-131">Jeśli obiekt odbiornika zostanie dodany do kolekcji w jednym z tych klas, inne klasy używa tego samego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="cc577-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="cc577-132">Klasy odbiornika dostarczone z programu .NET Framework pochodzić od <xref:System.Diagnostics.TraceListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="cc577-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="cc577-133">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="cc577-133">Configuration File</span></span>  
 <span data-ttu-id="cc577-134">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cc577-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc577-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc577-135">Example</span></span>  
 <span data-ttu-id="cc577-136">Poniższy przykład przedstawia użycie  **\<odbiorników >** elementu do dodania odbiorniki `MyListener` i `MyEventListener` do **odbiorników** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cc577-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="cc577-137">`MyListener`Tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku.</span><span class="sxs-lookup"><span data-stu-id="cc577-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="cc577-138">`MyEventListener`tworzy wpis w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="cc577-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cc577-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc577-139">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="cc577-140">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="cc577-140">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
