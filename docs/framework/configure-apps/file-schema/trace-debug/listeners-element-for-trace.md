---
title: <listeners>, element dla <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: 10530cfadf2e182f912c699e50294af4b57f47b5
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088861"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="9c519-102">Elementy \<detektory > do śledzenia \<</span><span class="sxs-lookup"><span data-stu-id="9c519-102">\<listeners> Element for \<trace></span></span>
<span data-ttu-id="9c519-103">Określa odbiornik, który zbiera, przechowuje i kieruje komunikaty.</span><span class="sxs-lookup"><span data-stu-id="9c519-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="9c519-104">Odbiorniki kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="9c519-104">Listeners direct the tracing output to an appropriate target.</span></span>  

<span data-ttu-id="9c519-105">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="9c519-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9c519-106">&nbsp;&nbsp;[ **\<system. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="9c519-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="9c519-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Trace**](trace-element.md) ></span><span class="sxs-lookup"><span data-stu-id="9c519-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="9c519-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**odbiorników >**</span><span class="sxs-lookup"><span data-stu-id="9c519-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9c519-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c519-109">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c519-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9c519-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9c519-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9c519-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c519-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9c519-112">Attributes</span></span>  
 <span data-ttu-id="9c519-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="9c519-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9c519-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9c519-114">Child Elements</span></span>  
  
|<span data-ttu-id="9c519-115">Element</span><span class="sxs-lookup"><span data-stu-id="9c519-115">Element</span></span>|<span data-ttu-id="9c519-116">Opis</span><span class="sxs-lookup"><span data-stu-id="9c519-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c519-117">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="9c519-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="9c519-118">Dodaje odbiornik do kolekcji `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="9c519-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="9c519-119">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="9c519-119">\<clear></span></span>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="9c519-120">Czyści kolekcję `Listeners` na potrzeby śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9c519-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="9c519-121">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="9c519-121">\<remove></span></span>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="9c519-122">Usuwa odbiornik z kolekcji `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="9c519-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9c519-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9c519-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9c519-124">Element</span><span class="sxs-lookup"><span data-stu-id="9c519-124">Element</span></span>|<span data-ttu-id="9c519-125">Opis</span><span class="sxs-lookup"><span data-stu-id="9c519-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9c519-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9c519-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="9c519-127">Określa element główny dla sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9c519-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="9c519-128">Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9c519-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c519-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9c519-129">Remarks</span></span>  
 <span data-ttu-id="9c519-130">Klasy <xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace> współdzielą tę samą kolekcję **detektorów** .</span><span class="sxs-lookup"><span data-stu-id="9c519-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="9c519-131">Jeśli dodasz obiekt odbiornika do kolekcji w jednej z tych klas, inna Klasa używa tego samego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="9c519-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="9c519-132">Klasy odbiornika dostarczane z .NET Framework pochodzą z klasy <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="9c519-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="9c519-133">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9c519-133">Configuration File</span></span>  
 <span data-ttu-id="9c519-134">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9c519-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c519-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c519-135">Example</span></span>  
 <span data-ttu-id="9c519-136">Poniższy przykład pokazuje, jak używać **\<detektory >** elementu, aby dodać odbiorniki `MyListener` i `MyEventListener` do kolekcji **detektorów** .</span><span class="sxs-lookup"><span data-stu-id="9c519-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="9c519-137">`MyListener` tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku.</span><span class="sxs-lookup"><span data-stu-id="9c519-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="9c519-138">`MyEventListener` tworzy wpis w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9c519-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9c519-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9c519-139">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="9c519-140">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="9c519-140">Trace and Debug Settings Schema</span></span>](index.md)
