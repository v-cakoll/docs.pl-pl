---
title: <add>, element dla <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: c4b83834fb7aaf64a696b85bd2c8da47cfba2397
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927214"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="4f6ed-102">\<Dodaj element > dla \<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="4f6ed-102">\<add> Element for \<sharedListeners></span></span>
<span data-ttu-id="4f6ed-103">Dodaje odbiornik do `sharedListeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="4f6ed-104">`sharedListeners`jest kolekcją odbiorników, które mogą odwoływać się [ \<do > źródłowych](source-element.md) lub [ \<> śledzenia](trace-element.md) .</span><span class="sxs-lookup"><span data-stu-id="4f6ed-104">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="4f6ed-105">Domyślnie odbiorniki w `sharedListeners` kolekcji nie są umieszczane `Listeners` w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="4f6ed-106">Muszą one być dodawane przez nazwę do [ \<źródła >](source-element.md) lub [ \<> śledzenia](trace-element.md).</span><span class="sxs-lookup"><span data-stu-id="4f6ed-106">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="4f6ed-107">Nie można uzyskać odbiorników w `sharedListeners` kolekcji w kodzie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  
  
 <span data-ttu-id="4f6ed-108">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4f6ed-108">\<configuration></span></span>  
<span data-ttu-id="4f6ed-109">&nbsp;&nbsp;\<> System. Diagnostics</span><span class="sxs-lookup"><span data-stu-id="4f6ed-109">&nbsp;&nbsp;\<system.diagnostics></span></span>  
<span data-ttu-id="4f6ed-110">&nbsp;&nbsp;&nbsp;&nbsp;\<sharedListeners, element ></span><span class="sxs-lookup"><span data-stu-id="4f6ed-110">&nbsp;&nbsp;&nbsp;&nbsp;\<sharedListeners> Element</span></span>  
<span data-ttu-id="4f6ed-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<add></span><span class="sxs-lookup"><span data-stu-id="4f6ed-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f6ed-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f6ed-112">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f6ed-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4f6ed-113">Attributes and Elements</span></span>  
 <span data-ttu-id="4f6ed-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f6ed-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4f6ed-115">Attributes</span></span>  
  
|<span data-ttu-id="4f6ed-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4f6ed-116">Attribute</span></span>|<span data-ttu-id="4f6ed-117">Opis</span><span class="sxs-lookup"><span data-stu-id="4f6ed-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="4f6ed-118">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="4f6ed-119">Określa nazwę odbiornika, który jest używany do dodawania udostępnionego odbiornika do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="4f6ed-120">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="4f6ed-121">Określa typ odbiornika.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-121">Specifies the type of the listener.</span></span> <span data-ttu-id="4f6ed-122">Należy użyć ciągu, który spełnia wymagania określone w podaniu w [pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="4f6ed-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="4f6ed-123">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4f6ed-124">Ciąg przesłany do konstruktora dla określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-124">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="4f6ed-125">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-125">Optional attribute.</span></span><br/><br/><span data-ttu-id="4f6ed-126">Ciąg reprezentujący co najmniej jeden <xref:System.Diagnostics.TraceOptions> element członkowski wyliczenia wskazujący dane, które mają być zapisywane w danych wyjściowych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-126">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="4f6ed-127">Wiele elementów jest oddzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-127">Multiple items are separated by commas.</span></span> <span data-ttu-id="4f6ed-128">Wartość domyślna to "Brak".</span><span class="sxs-lookup"><span data-stu-id="4f6ed-128">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="4f6ed-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4f6ed-129">Child Elements</span></span>  
  
|<span data-ttu-id="4f6ed-130">Element</span><span class="sxs-lookup"><span data-stu-id="4f6ed-130">Element</span></span>|<span data-ttu-id="4f6ed-131">Opis</span><span class="sxs-lookup"><span data-stu-id="4f6ed-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f6ed-132">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="4f6ed-132">\<filter></span></span>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="4f6ed-133">Dodaje filtr do odbiornika w `sharedListeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-133">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4f6ed-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4f6ed-134">Parent Elements</span></span>  
  
|<span data-ttu-id="4f6ed-135">Element</span><span class="sxs-lookup"><span data-stu-id="4f6ed-135">Element</span></span>|<span data-ttu-id="4f6ed-136">Opis</span><span class="sxs-lookup"><span data-stu-id="4f6ed-136">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4f6ed-137">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-137">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4f6ed-138">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-138">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="4f6ed-139">Kolekcja detektorów, które mogą odwoływać się do każdego elementu źródłowego lub śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-139">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f6ed-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4f6ed-140">Remarks</span></span>  
 <span data-ttu-id="4f6ed-141">Klasy odbiornika dostarczane z .NET Framework pochodzą od <xref:System.Diagnostics.TraceListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-141">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="4f6ed-142">Wartość `name` atrybutu służy do dodawania udostępnionego odbiornika `Listeners` do kolekcji dla śladu lub źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-142">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="4f6ed-143">Wartość `initializeData` atrybutu zależy od typu tworzonego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="4f6ed-144">Nie wszystkie detektory śledzenia wymagają określenia `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f6ed-145">W przypadku korzystania z `initializeData` atrybutu może zostać wyświetlone ostrzeżenie kompilatora "initializeData" nie jest zadeklarowany. "</span><span class="sxs-lookup"><span data-stu-id="4f6ed-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="4f6ed-146">To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są weryfikowane względem abstrakcyjnej klasy <xref:System.Diagnostics.TraceListener>bazowej, która nie `initializeData` rozpoznaje atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="4f6ed-147">Zazwyczaj można zignorować to ostrzeżenie dla implementacji detektorów śledzenia, które mają konstruktora, który pobiera parametr.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="4f6ed-148">W poniższej tabeli przedstawiono detektory śledzenia, które są dołączone do .NET Framework i opisano wartości ich `initializeData` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="4f6ed-149">Trace — Klasa odbiornika</span><span class="sxs-lookup"><span data-stu-id="4f6ed-149">Trace listener class</span></span>|<span data-ttu-id="4f6ed-150">wartość atrybutu initializeData</span><span class="sxs-lookup"><span data-stu-id="4f6ed-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="4f6ed-151">`useErrorStream` Wartość<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> dla konstruktora.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="4f6ed-152">Ustaw atrybut na "`true`", aby zapisać dane wyjściowe śledzenia i debugowania do strumienia błędu standardowego; Ustaw dla niego wartość`false`"", aby zapisać w standardowym strumieniu wyjściowym. `initializeData`</span><span class="sxs-lookup"><span data-stu-id="4f6ed-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="4f6ed-153">Nazwa pliku, w którym są <xref:System.Diagnostics.DelimitedListTraceListener> zapisywane dane.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="4f6ed-154">Nazwa istniejącego źródła dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="4f6ed-155">Nazwa pliku, w którym zapisuje dane <xref:System.Diagnostics.EventSchemaTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="4f6ed-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="4f6ed-156">Nazwa pliku, w którym zapisuje dane <xref:System.Diagnostics.TextWriterTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="4f6ed-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="4f6ed-157">Nazwa pliku, w którym zapisuje dane <xref:System.Diagnostics.XmlWriterTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="4f6ed-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="4f6ed-158">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4f6ed-158">Configuration File</span></span>  
 <span data-ttu-id="4f6ed-159">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f6ed-160">Przykład</span><span class="sxs-lookup"><span data-stu-id="4f6ed-160">Example</span></span>  
 <span data-ttu-id="4f6ed-161">`<add>` Poniższy przykład pokazuje, <xref:System.Diagnostics.TextWriterTraceListener> `textListener` jak za pomocą elementów dodać do `sharedListeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-161">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="4f6ed-162">`textListener`jest dodawany przez nazwę do `Listeners` kolekcji dla źródła `TraceSourceApp`śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-162">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="4f6ed-163">`textListener` Odbiornik zapisuje dane wyjściowe śledzenia do pliku listen. log.</span><span class="sxs-lookup"><span data-stu-id="4f6ed-163">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="4f6ed-164">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f6ed-164">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="4f6ed-165">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="4f6ed-165">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4f6ed-166">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="4f6ed-166">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
