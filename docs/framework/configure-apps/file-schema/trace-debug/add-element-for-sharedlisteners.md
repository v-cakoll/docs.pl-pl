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
ms.openlocfilehash: 5588892ec75a791eda1eb043936c0af95e79354e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153610"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="77c2f-102">\<add>, element dla \<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="77c2f-102">\<add> Element for \<sharedListeners></span></span>
<span data-ttu-id="77c2f-103">Dodaje odbiornik do `sharedListeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="77c2f-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="77c2f-104">`sharedListeners`jest kolekcją odbiorników, do których dowolnych [\<source>](source-element.md) lub [\<trace>](trace-element.md) mogą się odwoływać.</span><span class="sxs-lookup"><span data-stu-id="77c2f-104">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="77c2f-105">Domyślnie odbiorniki w `sharedListeners` kolekcji nie są umieszczane w `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="77c2f-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="77c2f-106">Muszą być dodawane przez nazwę do [\<source>](source-element.md) lub [\<trace>](trace-element.md) .</span><span class="sxs-lookup"><span data-stu-id="77c2f-106">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="77c2f-107">Nie można uzyskać odbiorników w `sharedListeners` kolekcji w kodzie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="77c2f-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="77c2f-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="77c2f-108">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77c2f-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="77c2f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="77c2f-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="77c2f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77c2f-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="77c2f-111">Attributes</span></span>  
  
|<span data-ttu-id="77c2f-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="77c2f-112">Attribute</span></span>|<span data-ttu-id="77c2f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="77c2f-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="77c2f-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="77c2f-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="77c2f-115">Określa nazwę odbiornika, który jest używany do dodawania udostępnionego odbiornika do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="77c2f-115">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="77c2f-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="77c2f-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="77c2f-117">Określa typ odbiornika.</span><span class="sxs-lookup"><span data-stu-id="77c2f-117">Specifies the type of the listener.</span></span> <span data-ttu-id="77c2f-118">Należy użyć ciągu, który spełnia wymagania określone w podaniu w [pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="77c2f-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="77c2f-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="77c2f-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="77c2f-120">Ciąg przesłany do konstruktora dla określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="77c2f-120">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="77c2f-121">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="77c2f-121">Optional attribute.</span></span><br/><br/><span data-ttu-id="77c2f-122">Ciąg reprezentujący co najmniej jeden <xref:System.Diagnostics.TraceOptions> element członkowski wyliczenia wskazujący dane, które mają być zapisywane w danych wyjściowych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="77c2f-122">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="77c2f-123">Wiele elementów jest oddzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="77c2f-123">Multiple items are separated by commas.</span></span> <span data-ttu-id="77c2f-124">Wartość domyślna to "Brak".</span><span class="sxs-lookup"><span data-stu-id="77c2f-124">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="77c2f-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="77c2f-125">Child Elements</span></span>  
  
|<span data-ttu-id="77c2f-126">Element</span><span class="sxs-lookup"><span data-stu-id="77c2f-126">Element</span></span>|<span data-ttu-id="77c2f-127">Opis</span><span class="sxs-lookup"><span data-stu-id="77c2f-127">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="77c2f-128">Dodaje filtr do odbiornika w `sharedListeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="77c2f-128">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="77c2f-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="77c2f-129">Parent Elements</span></span>  
  
|<span data-ttu-id="77c2f-130">Element</span><span class="sxs-lookup"><span data-stu-id="77c2f-130">Element</span></span>|<span data-ttu-id="77c2f-131">Opis</span><span class="sxs-lookup"><span data-stu-id="77c2f-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="77c2f-132">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="77c2f-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="77c2f-133">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="77c2f-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="77c2f-134">Kolekcja detektorów, które mogą odwoływać się do każdego elementu źródłowego lub śledzenia.</span><span class="sxs-lookup"><span data-stu-id="77c2f-134">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77c2f-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="77c2f-135">Remarks</span></span>  
 <span data-ttu-id="77c2f-136">Klasy odbiornika dostarczane z .NET Framework pochodzą od <xref:System.Diagnostics.TraceListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="77c2f-136">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="77c2f-137">Wartość `name` atrybutu służy do dodawania udostępnionego odbiornika do `Listeners` kolekcji dla śladu lub źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="77c2f-137">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="77c2f-138">Wartość `initializeData` atrybutu zależy od typu tworzonego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="77c2f-138">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="77c2f-139">Nie wszystkie detektory śledzenia wymagają określenia `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="77c2f-139">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77c2f-140">W przypadku korzystania z `initializeData` atrybutu może zostać wyświetlone ostrzeżenie kompilatora "initializeData" nie jest zadeklarowany. "</span><span class="sxs-lookup"><span data-stu-id="77c2f-140">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="77c2f-141">To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są weryfikowane względem abstrakcyjnej klasy bazowej <xref:System.Diagnostics.TraceListener> , która nie rozpoznaje `initializeData` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="77c2f-141">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="77c2f-142">Zazwyczaj można zignorować to ostrzeżenie dla implementacji detektorów śledzenia, które mają konstruktora, który pobiera parametr.</span><span class="sxs-lookup"><span data-stu-id="77c2f-142">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="77c2f-143">W poniższej tabeli przedstawiono detektory śledzenia, które są dołączone do .NET Framework i opisano wartości ich `initializeData` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="77c2f-143">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="77c2f-144">Trace — Klasa odbiornika</span><span class="sxs-lookup"><span data-stu-id="77c2f-144">Trace listener class</span></span>|<span data-ttu-id="77c2f-145">wartość atrybutu initializeData</span><span class="sxs-lookup"><span data-stu-id="77c2f-145">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="77c2f-146">`useErrorStream`Wartość dla <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="77c2f-146">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="77c2f-147">Ustaw `initializeData` atrybut na " `true` ", aby zapisać dane wyjściowe śledzenia i debugowania do strumienia błędu standardowego; Ustaw dla niego wartość " `false` ", aby zapisać w standardowym strumieniu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="77c2f-147">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="77c2f-148">Nazwa pliku, w którym są <xref:System.Diagnostics.DelimitedListTraceListener> zapisywane dane.</span><span class="sxs-lookup"><span data-stu-id="77c2f-148">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="77c2f-149">Nazwa istniejącego źródła dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="77c2f-149">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="77c2f-150">Nazwa pliku, w którym zapisuje dane <xref:System.Diagnostics.EventSchemaTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="77c2f-150">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="77c2f-151">Nazwa pliku, w którym zapisuje dane <xref:System.Diagnostics.TextWriterTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="77c2f-151">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="77c2f-152">Nazwa pliku, w którym zapisuje dane <xref:System.Diagnostics.XmlWriterTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="77c2f-152">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="77c2f-153">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="77c2f-153">Configuration File</span></span>  
 <span data-ttu-id="77c2f-154">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="77c2f-154">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77c2f-155">Przykład</span><span class="sxs-lookup"><span data-stu-id="77c2f-155">Example</span></span>  
 <span data-ttu-id="77c2f-156">Poniższy przykład pokazuje, jak za pomocą `<add>` elementów dodać <xref:System.Diagnostics.TextWriterTraceListener> `textListener` do `sharedListeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="77c2f-156">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="77c2f-157">`textListener`jest dodawany przez nazwę do `Listeners` kolekcji dla źródła śledzenia `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="77c2f-157">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="77c2f-158">`textListener`Odbiornik zapisuje dane wyjściowe śledzenia do pliku listen. log.</span><span class="sxs-lookup"><span data-stu-id="77c2f-158">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="77c2f-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77c2f-159">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="77c2f-160">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="77c2f-160">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="77c2f-161">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="77c2f-161">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
