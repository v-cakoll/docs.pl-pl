---
title: <sharedListeners> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
ms.openlocfilehash: b419ecf451b79808e545525c7b8761175f390200
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699304"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="918ab-102">\<sharedListeners > elementu</span><span class="sxs-lookup"><span data-stu-id="918ab-102">\<sharedListeners> Element</span></span>
<span data-ttu-id="918ab-103">Zawiera detektory, do których może odwoływać się każdy element źródłowy lub Trace.</span><span class="sxs-lookup"><span data-stu-id="918ab-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="918ab-104">Te odbiorniki nie odbierają domyślnie żadnych śladów i nie można ich pobrać w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="918ab-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="918ab-105">Odbiorniki identyfikowane jako odbiorniki udostępnione mogą być dodawane do źródeł lub śladów według nazwy.</span><span class="sxs-lookup"><span data-stu-id="918ab-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
[<span data-ttu-id="918ab-106"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="918ab-106">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="918ab-107">&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="918ab-107">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="918ab-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<sharedListeners >**</span><span class="sxs-lookup"><span data-stu-id="918ab-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="918ab-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="918ab-109">Syntax</span></span>  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="918ab-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="918ab-110">Attributes and Elements</span></span>  
 <span data-ttu-id="918ab-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="918ab-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="918ab-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="918ab-112">Attributes</span></span>  
 <span data-ttu-id="918ab-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="918ab-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="918ab-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="918ab-114">Child Elements</span></span>  
  
|<span data-ttu-id="918ab-115">Element</span><span class="sxs-lookup"><span data-stu-id="918ab-115">Element</span></span>|<span data-ttu-id="918ab-116">Opis</span><span class="sxs-lookup"><span data-stu-id="918ab-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="918ab-117">@no__t — 1add ></span><span class="sxs-lookup"><span data-stu-id="918ab-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="918ab-118">Dodaje odbiornik do kolekcji `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="918ab-118">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="918ab-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="918ab-119">Parent Elements</span></span>  
  
|<span data-ttu-id="918ab-120">Element</span><span class="sxs-lookup"><span data-stu-id="918ab-120">Element</span></span>|<span data-ttu-id="918ab-121">Opis</span><span class="sxs-lookup"><span data-stu-id="918ab-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="918ab-122">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="918ab-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="918ab-123">Określa element główny dla sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="918ab-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="918ab-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="918ab-124">Remarks</span></span>  
 <span data-ttu-id="918ab-125">Dodanie odbiornika do kolekcji udostępnionych odbiorników nie powoduje aktywnego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="918ab-125">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="918ab-126">Nadal musi być dodany do źródła śledzenia lub śledzenia przez dodanie go do kolekcji `Listeners` dla tego elementu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="918ab-126">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="918ab-127">Klasy odbiornika w .NET Framework pochodzą od klasy <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="918ab-127">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="918ab-128">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="918ab-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="918ab-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="918ab-129">Example</span></span>  
 <span data-ttu-id="918ab-130">Poniższy przykład pokazuje, jak za pomocą elementu `<sharedListeners>` dodać odbiornik `console` do kolekcji `Listeners` dla klas <xref:System.Diagnostics.TraceSource> i <xref:System.Diagnostics.Trace>.</span><span class="sxs-lookup"><span data-stu-id="918ab-130">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="918ab-131">Odbiornik śledzenia konsoli zapisuje informacje o śledzeniu do konsoli za pomocą wywołań do <xref:System.Diagnostics.TraceSource> lub <xref:System.Diagnostics.Trace>.</span><span class="sxs-lookup"><span data-stu-id="918ab-131">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="918ab-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="918ab-132">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="918ab-133">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="918ab-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="918ab-134">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="918ab-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
