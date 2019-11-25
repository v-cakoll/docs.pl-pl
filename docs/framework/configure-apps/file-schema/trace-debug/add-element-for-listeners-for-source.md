---
title: Element <add> dla <listeners> <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: c32205310f9fc451a5a55a943f925ee52f65c8a8
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088998"
---
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="780be-102">\<dodać elementu > dla odbiorników \<> dla \<źródła ></span><span class="sxs-lookup"><span data-stu-id="780be-102">\<add> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="780be-103">Dodaje odbiornik do kolekcji `Listeners` dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="780be-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="780be-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="780be-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="780be-105">&nbsp;&nbsp;[ **\<system. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="780be-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="780be-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sources**](sources-element.md) ></span><span class="sxs-lookup"><span data-stu-id="780be-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="780be-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**Source**](source-element.md) ></span><span class="sxs-lookup"><span data-stu-id="780be-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="780be-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<odbiorników**](listeners-element-for-source.md) ></span><span class="sxs-lookup"><span data-stu-id="780be-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="780be-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dodawanie >**</span><span class="sxs-lookup"><span data-stu-id="780be-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="780be-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="780be-110">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="780be-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="780be-111">Attributes and Elements</span></span>  
 <span data-ttu-id="780be-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="780be-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="780be-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="780be-113">Attributes</span></span>  
  
|<span data-ttu-id="780be-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="780be-114">Attribute</span></span>|<span data-ttu-id="780be-115">Opis</span><span class="sxs-lookup"><span data-stu-id="780be-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="780be-116">Wymagany atrybut, chyba że odwołujesz się do odbiornika w kolekcji `sharedListeners`, w takim przypadku należy tylko odwołać się do niego według nazwy (zobacz [przykład](#example)).</span><span class="sxs-lookup"><span data-stu-id="780be-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="780be-117">Określa typ odbiornika.</span><span class="sxs-lookup"><span data-stu-id="780be-117">Specifies the type of the listener.</span></span> <span data-ttu-id="780be-118">Należy użyć ciągu, który spełnia wymagania określone w podaniu w [pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="780be-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="780be-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="780be-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="780be-120">Ciąg przesłany do konstruktora dla określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="780be-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="780be-121"><xref:System.Configuration.ConfigurationException> jest generowany, jeśli Klasa nie ma konstruktora, który przyjmuje ciąg.</span><span class="sxs-lookup"><span data-stu-id="780be-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="780be-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="780be-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="780be-123">Określa nazwę odbiornika.</span><span class="sxs-lookup"><span data-stu-id="780be-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="780be-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="780be-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="780be-125">Określa <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> wartość właściwości dla odbiornika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="780be-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="780be-126">[atrybuty niestandardowe]</span><span class="sxs-lookup"><span data-stu-id="780be-126">[custom attributes]</span></span>|<span data-ttu-id="780be-127">Atrybuty opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="780be-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="780be-128">Określa wartość dla atrybutów specyficznych dla odbiornika identyfikowanych przez metodę <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> dla tego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="780be-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="780be-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> jest przykładem dodatkowego atrybutu unikatowego dla klasy <xref:System.Diagnostics.DelimitedListTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="780be-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="780be-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="780be-130">Child Elements</span></span>  
  
|<span data-ttu-id="780be-131">Element</span><span class="sxs-lookup"><span data-stu-id="780be-131">Element</span></span>|<span data-ttu-id="780be-132">Opis</span><span class="sxs-lookup"><span data-stu-id="780be-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="780be-133">Filtr \<</span><span class="sxs-lookup"><span data-stu-id="780be-133">\<filter></span></span>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="780be-134">Dodaje filtr do odbiornika w kolekcji `Listeners` dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="780be-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="780be-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="780be-135">Parent Elements</span></span>  
  
|<span data-ttu-id="780be-136">Element</span><span class="sxs-lookup"><span data-stu-id="780be-136">Element</span></span>|<span data-ttu-id="780be-137">Opis</span><span class="sxs-lookup"><span data-stu-id="780be-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="780be-138">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="780be-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="780be-139">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="780be-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="780be-140">Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="780be-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="780be-141">Określa źródło śledzenia, które inicjuje komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="780be-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="780be-142">Określa detektory, które zbierają, przechowują i rozsyłają komunikaty.</span><span class="sxs-lookup"><span data-stu-id="780be-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="780be-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="780be-143">Remarks</span></span>  
 <span data-ttu-id="780be-144">Klasy odbiornika dostarczane z .NET Framework pochodzą z klasy <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="780be-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="780be-145">Jeśli nie określisz atrybutu `name` odbiornika śledzenia, właściwość <xref:System.Diagnostics.TraceListener.Name%2A> odbiornika śledzenia domyślnie będzie pustym ciągiem ("").</span><span class="sxs-lookup"><span data-stu-id="780be-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="780be-146">Jeśli aplikacja ma tylko jeden odbiornik, możesz ją dodać bez określenia nazwy i można ją usunąć, określając pusty ciąg w polu Nazwa.</span><span class="sxs-lookup"><span data-stu-id="780be-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="780be-147">Jeśli jednak aplikacja ma więcej niż jeden odbiornik, należy określić unikatową nazwę dla każdego odbiornika śledzenia, co pozwala identyfikować poszczególne detektory śledzenia i zarządzać nimi w kolekcji <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="780be-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="780be-148">Dodanie więcej niż jednego odbiornika śledzenia tego samego typu i z tą samą nazwą powoduje tylko jeden odbiornik śledzenia tego typu i nazwę dodawane do kolekcji `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="780be-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="780be-149">Można jednak programowo dodać wiele identycznych odbiorników do kolekcji `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="780be-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="780be-150">Wartość atrybutu `initializeData` zależy od typu tworzonego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="780be-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="780be-151">Nie wszystkie detektory śledzenia wymagają określenia `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="780be-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="780be-152">W przypadku korzystania z atrybutu `initializeData` można uzyskać Ostrzeżenie kompilatora "atrybut" initializeData "nie jest zadeklarowany."</span><span class="sxs-lookup"><span data-stu-id="780be-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="780be-153">To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są weryfikowane względem abstrakcyjnej klasy bazowej <xref:System.Diagnostics.TraceListener>, która nie rozpoznaje atrybutu `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="780be-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="780be-154">Zazwyczaj można zignorować to ostrzeżenie dla implementacji detektorów śledzenia, które mają konstruktora, który pobiera parametr.</span><span class="sxs-lookup"><span data-stu-id="780be-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="780be-155">W poniższej tabeli przedstawiono detektory śledzenia, które są dołączone do .NET Framework i opisano wartości atrybutów `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="780be-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="780be-156">Trace — Klasa odbiornika</span><span class="sxs-lookup"><span data-stu-id="780be-156">Trace listener class</span></span>|<span data-ttu-id="780be-157">wartość atrybutu initializeData</span><span class="sxs-lookup"><span data-stu-id="780be-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="780be-158">Wartość `useErrorStream` konstruktora <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>.</span><span class="sxs-lookup"><span data-stu-id="780be-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="780be-159">Ustaw atrybut `initializeData` na "`true`", aby zapisać dane wyjściowe śledzenia i debugowania do strumienia błędu standardowego; Ustaw dla niego wartość "`false`", aby zapisać w standardowym strumieniu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="780be-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="780be-160">Nazwa pliku, do którego <xref:System.Diagnostics.DelimitedListTraceListener> zapisu.</span><span class="sxs-lookup"><span data-stu-id="780be-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="780be-161">Nazwa istniejącego źródła dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="780be-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="780be-162">Nazwa pliku, w którym <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje dane.</span><span class="sxs-lookup"><span data-stu-id="780be-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="780be-163">Nazwa pliku, w którym <xref:System.Diagnostics.TextWriterTraceListener> zapisuje dane.</span><span class="sxs-lookup"><span data-stu-id="780be-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="780be-164">Nazwa pliku, w którym <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje dane.</span><span class="sxs-lookup"><span data-stu-id="780be-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="780be-165">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="780be-165">Configuration File</span></span>  
 <span data-ttu-id="780be-166">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="780be-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="780be-167">Przykład</span><span class="sxs-lookup"><span data-stu-id="780be-167">Example</span></span>  
 <span data-ttu-id="780be-168">Poniższy przykład pokazuje, jak używać elementów `<add>`, aby dodać detektory `console` i `textListener` do kolekcji `Listeners` dla źródła śledzenia `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="780be-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="780be-169">Odbiornik `textListener` zapisuje dane wyjściowe śledzenia do pliku listen. log.</span><span class="sxs-lookup"><span data-stu-id="780be-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="780be-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="780be-170">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="780be-171">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="780be-171">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="780be-172">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="780be-172">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
