---
title: <listeners>, element dla <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: f9f12d9e61e2472b897169727bbb4fbf9833efd6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179117"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="29bee-102">\<listeners> Element for \<trace></span><span class="sxs-lookup"><span data-stu-id="29bee-102">\<listeners> Element for \<trace></span></span>
<span data-ttu-id="29bee-103">Określa odbiornik, który zbiera, magazynów i przekazuje komunikaty.</span><span class="sxs-lookup"><span data-stu-id="29bee-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="29bee-104">Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="29bee-104">Listeners direct the tracing output to an appropriate target.</span></span>  
  
 <span data-ttu-id="29bee-105">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="29bee-105">\<configuration> Element</span></span>  
<span data-ttu-id="29bee-106">\<system.diagnostics> Element</span><span class="sxs-lookup"><span data-stu-id="29bee-106">\<system.diagnostics> Element</span></span>  
<span data-ttu-id="29bee-107">\<trace> Element</span><span class="sxs-lookup"><span data-stu-id="29bee-107">\<trace> Element</span></span>  
<span data-ttu-id="29bee-108">\<listeners> Element for \<trace></span><span class="sxs-lookup"><span data-stu-id="29bee-108">\<listeners> Element for \<trace></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29bee-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="29bee-109">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29bee-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="29bee-110">Attributes and Elements</span></span>  
 <span data-ttu-id="29bee-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="29bee-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29bee-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="29bee-112">Attributes</span></span>  
 <span data-ttu-id="29bee-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="29bee-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="29bee-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="29bee-114">Child Elements</span></span>  
  
|<span data-ttu-id="29bee-115">Element</span><span class="sxs-lookup"><span data-stu-id="29bee-115">Element</span></span>|<span data-ttu-id="29bee-116">Opis</span><span class="sxs-lookup"><span data-stu-id="29bee-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29bee-117">\<add></span><span class="sxs-lookup"><span data-stu-id="29bee-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|<span data-ttu-id="29bee-118">Dodaje odbiornik do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="29bee-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="29bee-119">\<clear></span><span class="sxs-lookup"><span data-stu-id="29bee-119">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|<span data-ttu-id="29bee-120">Czyści `Listeners` kolekcji na potrzeby śledzenia.</span><span class="sxs-lookup"><span data-stu-id="29bee-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="29bee-121">\<remove></span><span class="sxs-lookup"><span data-stu-id="29bee-121">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|<span data-ttu-id="29bee-122">Usuwa odbiornik z `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="29bee-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="29bee-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="29bee-123">Parent Elements</span></span>  
  
|<span data-ttu-id="29bee-124">Element</span><span class="sxs-lookup"><span data-stu-id="29bee-124">Element</span></span>|<span data-ttu-id="29bee-125">Opis</span><span class="sxs-lookup"><span data-stu-id="29bee-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="29bee-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="29bee-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="29bee-127">Określa element root dla sekcji konfiguracyjnej platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="29bee-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="29bee-128">Zawiera obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="29bee-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29bee-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="29bee-129">Remarks</span></span>  
 <span data-ttu-id="29bee-130"><xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace> klasy współużytkować ten sam **odbiorników** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="29bee-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="29bee-131">Jeśli dodasz obiektu odbiornika do kolekcji w jednym z tych klas, inne klasy używa tego samego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="29bee-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="29bee-132">Klasy odbiornika dostarczane z programem .NET Framework pochodzić od <xref:System.Diagnostics.TraceListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="29bee-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="29bee-133">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="29bee-133">Configuration File</span></span>  
 <span data-ttu-id="29bee-134">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="29bee-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29bee-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="29bee-135">Example</span></span>  
 <span data-ttu-id="29bee-136">Poniższy przykład pokazuje, jak używać  **\<odbiorników >** elementu do dodania odbiorniki `MyListener` i `MyEventListener` do **odbiorników** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="29bee-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="29bee-137">`MyListener` Tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku.</span><span class="sxs-lookup"><span data-stu-id="29bee-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="29bee-138">`MyEventListener` tworzy wpis w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="29bee-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="29bee-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29bee-139">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="29bee-140">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="29bee-140">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
