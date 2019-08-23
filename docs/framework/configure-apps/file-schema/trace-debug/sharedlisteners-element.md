---
title: <sharedListeners>, element
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
ms.openlocfilehash: 41cabcbce13409b0842cbbd625028b51d32d59d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926983"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="a324c-102">\<sharedListeners, element ></span><span class="sxs-lookup"><span data-stu-id="a324c-102">\<sharedListeners> Element</span></span>
<span data-ttu-id="a324c-103">Zawiera detektory, do których może odwoływać się każdy element źródłowy lub Trace.</span><span class="sxs-lookup"><span data-stu-id="a324c-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="a324c-104">Te odbiorniki nie odbierają domyślnie żadnych śladów i nie można ich pobrać w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a324c-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="a324c-105">Odbiorniki identyfikowane jako odbiorniki udostępnione mogą być dodawane do źródeł lub śladów według nazwy.</span><span class="sxs-lookup"><span data-stu-id="a324c-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
 <span data-ttu-id="a324c-106">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a324c-106">\<configuration></span></span>  
<span data-ttu-id="a324c-107">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="a324c-107">\<system.diagnostics></span></span>  
<span data-ttu-id="a324c-108">\<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="a324c-108">\<sharedListeners></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a324c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="a324c-109">Syntax</span></span>  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a324c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a324c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a324c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a324c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a324c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a324c-112">Attributes</span></span>  
 <span data-ttu-id="a324c-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="a324c-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a324c-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a324c-114">Child Elements</span></span>  
  
|<span data-ttu-id="a324c-115">Element</span><span class="sxs-lookup"><span data-stu-id="a324c-115">Element</span></span>|<span data-ttu-id="a324c-116">Opis</span><span class="sxs-lookup"><span data-stu-id="a324c-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a324c-117">\<add></span><span class="sxs-lookup"><span data-stu-id="a324c-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="a324c-118">Dodaje odbiornik do `sharedListeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a324c-118">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a324c-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a324c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a324c-120">Element</span><span class="sxs-lookup"><span data-stu-id="a324c-120">Element</span></span>|<span data-ttu-id="a324c-121">Opis</span><span class="sxs-lookup"><span data-stu-id="a324c-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="a324c-122">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a324c-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a324c-123">Określa element główny dla sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a324c-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a324c-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a324c-124">Remarks</span></span>  
 <span data-ttu-id="a324c-125">Dodanie odbiornika do kolekcji udostępnionych odbiorników nie powoduje aktywnego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="a324c-125">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="a324c-126">Nadal musi być dodany do źródła śledzenia lub śledzenia przez dodanie go do `Listeners` kolekcji dla tego elementu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a324c-126">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="a324c-127">Klasy odbiornika w .NET Framework pochodne od <xref:System.Diagnostics.TraceListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="a324c-127">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="a324c-128">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a324c-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a324c-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="a324c-129">Example</span></span>  
 <span data-ttu-id="a324c-130">Poniższy przykład pokazuje, jak użyć elementu, `<sharedListeners>` aby dodać odbiornik `console` do `Listeners` kolekcji dla <xref:System.Diagnostics.TraceSource> klas i <xref:System.Diagnostics.Trace> .</span><span class="sxs-lookup"><span data-stu-id="a324c-130">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="a324c-131">Odbiornik śledzenia konsoli zapisuje informacje o śledzeniu do konsoli za pomocą wywołań do <xref:System.Diagnostics.TraceSource> lub <xref:System.Diagnostics.Trace>.</span><span class="sxs-lookup"><span data-stu-id="a324c-131">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a324c-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a324c-132">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="a324c-133">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="a324c-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a324c-134">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="a324c-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
