---
title: <listeners>, element dla <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: e4550d4c4cd9ff37c5937ad366cccf91387c0e3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927020"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="5012d-102">\<> elementu \<odbiorników > śledzenia</span><span class="sxs-lookup"><span data-stu-id="5012d-102">\<listeners> Element for \<trace></span></span>
<span data-ttu-id="5012d-103">Określa odbiornik, który zbiera, przechowuje i kieruje komunikaty.</span><span class="sxs-lookup"><span data-stu-id="5012d-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="5012d-104">Odbiorniki kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="5012d-104">Listeners direct the tracing output to an appropriate target.</span></span>  
  
 <span data-ttu-id="5012d-105">\<> elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5012d-105">\<configuration> Element</span></span>  
<span data-ttu-id="5012d-106">\<Element System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="5012d-106">\<system.diagnostics> Element</span></span>  
<span data-ttu-id="5012d-107">\<Element > śledzenia</span><span class="sxs-lookup"><span data-stu-id="5012d-107">\<trace> Element</span></span>  
<span data-ttu-id="5012d-108">\<> elementu \<odbiorników > śledzenia</span><span class="sxs-lookup"><span data-stu-id="5012d-108">\<listeners> Element for \<trace></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5012d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="5012d-109">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5012d-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5012d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5012d-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5012d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5012d-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5012d-112">Attributes</span></span>  
 <span data-ttu-id="5012d-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="5012d-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5012d-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5012d-114">Child Elements</span></span>  
  
|<span data-ttu-id="5012d-115">Element</span><span class="sxs-lookup"><span data-stu-id="5012d-115">Element</span></span>|<span data-ttu-id="5012d-116">Opis</span><span class="sxs-lookup"><span data-stu-id="5012d-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5012d-117">\<add></span><span class="sxs-lookup"><span data-stu-id="5012d-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="5012d-118">Dodaje odbiornik do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5012d-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="5012d-119">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="5012d-119">\<clear></span></span>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="5012d-120">`Listeners` Czyści kolekcję do śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5012d-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="5012d-121">\<remove></span><span class="sxs-lookup"><span data-stu-id="5012d-121">\<remove></span></span>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="5012d-122">Usuwa odbiornik z `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5012d-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5012d-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5012d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5012d-124">Element</span><span class="sxs-lookup"><span data-stu-id="5012d-124">Element</span></span>|<span data-ttu-id="5012d-125">Opis</span><span class="sxs-lookup"><span data-stu-id="5012d-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5012d-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5012d-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="5012d-127">Określa element główny dla sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5012d-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="5012d-128">Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5012d-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5012d-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5012d-129">Remarks</span></span>  
 <span data-ttu-id="5012d-130">Klasy <xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace> współużytkują tę samą kolekcję detektorów.</span><span class="sxs-lookup"><span data-stu-id="5012d-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="5012d-131">Jeśli dodasz obiekt odbiornika do kolekcji w jednej z tych klas, inna Klasa używa tego samego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="5012d-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="5012d-132">Klasy odbiornika dostarczane z .NET Framework pochodzą od <xref:System.Diagnostics.TraceListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="5012d-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="5012d-133">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5012d-133">Configuration File</span></span>  
 <span data-ttu-id="5012d-134">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5012d-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5012d-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="5012d-135">Example</span></span>  
 <span data-ttu-id="5012d-136">W poniższym przykładzie pokazano, `MyListener` `MyEventListener`  **\<** jak za pomocą elementu odbiorniki > dodać odbiorniki i do kolekcji odbiorników.</span><span class="sxs-lookup"><span data-stu-id="5012d-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="5012d-137">`MyListener`tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku.</span><span class="sxs-lookup"><span data-stu-id="5012d-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="5012d-138">`MyEventListener`tworzy wpis w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5012d-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5012d-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5012d-139">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="5012d-140">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="5012d-140">Trace and Debug Settings Schema</span></span>](index.md)
