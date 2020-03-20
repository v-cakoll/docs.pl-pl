---
title: <listeners>, element dla <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 0eee325e01b41a15a19e4f40f479596f9d70f73b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153415"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="a0ea2-102">\<słuchaczy> Element dla \<> źródłowych</span><span class="sxs-lookup"><span data-stu-id="a0ea2-102">\<listeners> Element for \<source></span></span>
<span data-ttu-id="a0ea2-103">Dodaje lub usuwa odbiorników <xref:System.Diagnostics.TraceSource.Listeners%2A> w <xref:System.Diagnostics.TraceSource>kolekcji dla .</span><span class="sxs-lookup"><span data-stu-id="a0ea2-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="a0ea2-104">Odbiornik kieruje dane wyjściowe śledzenia do odpowiedniego obiektu docelowego, takiego jak dziennik, okno lub plik tekstowy.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
[<span data-ttu-id="a0ea2-105">**\<>konfiguracyjne**</span><span class="sxs-lookup"><span data-stu-id="a0ea2-105">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="a0ea2-106">&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="a0ea2-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="a0ea2-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<źródeł>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="a0ea2-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="a0ea2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>źródłowe**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="a0ea2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>  
<span data-ttu-id="a0ea2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<słuchacze>**</span><span class="sxs-lookup"><span data-stu-id="a0ea2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0ea2-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="a0ea2-110">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0ea2-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a0ea2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a0ea2-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0ea2-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a0ea2-113">Attributes</span></span>  
 <span data-ttu-id="a0ea2-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a0ea2-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a0ea2-115">Child Elements</span></span>  
  
|<span data-ttu-id="a0ea2-116">Element</span><span class="sxs-lookup"><span data-stu-id="a0ea2-116">Element</span></span>|<span data-ttu-id="a0ea2-117">Opis</span><span class="sxs-lookup"><span data-stu-id="a0ea2-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0ea2-118">\<dodaj></span><span class="sxs-lookup"><span data-stu-id="a0ea2-118">\<add></span></span>](add-element-for-listeners-for-source.md)|<span data-ttu-id="a0ea2-119">Dodaje odbiornik do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="a0ea2-120">\<usuń></span><span class="sxs-lookup"><span data-stu-id="a0ea2-120">\<remove></span></span>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="a0ea2-121">Usuwa odbiornik z kolekcji. `Listeners`</span><span class="sxs-lookup"><span data-stu-id="a0ea2-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="a0ea2-122">\<wyraźne></span><span class="sxs-lookup"><span data-stu-id="a0ea2-122">\<clear></span></span>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="a0ea2-123">Czyści `Listeners` kolekcję dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a0ea2-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a0ea2-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a0ea2-125">Element</span><span class="sxs-lookup"><span data-stu-id="a0ea2-125">Element</span></span>|<span data-ttu-id="a0ea2-126">Opis</span><span class="sxs-lookup"><span data-stu-id="a0ea2-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a0ea2-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a0ea2-128">Określa odbiorniki śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, na którym ustawiony jest przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="a0ea2-129">Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="a0ea2-130">Określa źródło śledzenia, które inicjuje śledzenie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0ea2-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a0ea2-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="a0ea2-132">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a0ea2-132">Configuration File</span></span>  
 <span data-ttu-id="a0ea2-133">Ten element może być używany w pliku konfiguracyjnym komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0ea2-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0ea2-134">Example</span></span>  
 <span data-ttu-id="a0ea2-135">W poniższym przykładzie `<listeners>` pokazano, jak użyć elementu, `mySource` aby dodać odbiornik śledzenia konsoli do źródła i usunąć domyślny odbiornik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a0ea2-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0ea2-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a0ea2-136">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="a0ea2-137">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="a0ea2-137">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a0ea2-138">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="a0ea2-138">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
