---
title: <add>Element <listeners> dla<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 883eef32172c5a7f900197995b4c57c3d5a84e19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153688"
---
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="281f5-102">\<dodaj element> dla \<> dla> \<źródłowych</span><span class="sxs-lookup"><span data-stu-id="281f5-102">\<add> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="281f5-103">Dodaje odbiornik do `Listeners` kolekcji dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="281f5-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="281f5-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="281f5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="281f5-105">&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="281f5-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="281f5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<źródeł>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="281f5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="281f5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>źródłowe**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="281f5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="281f5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<słuchacze>**](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="281f5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="281f5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dodaj>**</span><span class="sxs-lookup"><span data-stu-id="281f5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="281f5-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="281f5-110">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="281f5-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="281f5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="281f5-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="281f5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="281f5-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="281f5-113">Attributes</span></span>  
  
|<span data-ttu-id="281f5-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="281f5-114">Attribute</span></span>|<span data-ttu-id="281f5-115">Opis</span><span class="sxs-lookup"><span data-stu-id="281f5-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="281f5-116">Wymagany atrybut, chyba że odwołujesz się do `sharedListeners` odbiornika w kolekcji, w którym to przypadku wystarczy odwołać się do niego tylko według nazwy (zobacz [przykład](#example)).</span><span class="sxs-lookup"><span data-stu-id="281f5-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="281f5-117">Określa typ odbiornika.</span><span class="sxs-lookup"><span data-stu-id="281f5-117">Specifies the type of the listener.</span></span> <span data-ttu-id="281f5-118">Należy użyć ciągu spełniającego wymagania określone w określaniu w [pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="281f5-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="281f5-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="281f5-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="281f5-120">Ciąg przekazany do konstruktora dla określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="281f5-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="281f5-121">A <xref:System.Configuration.ConfigurationException> jest generowany, jeśli klasa nie ma konstruktora, który przyjmuje ciąg.</span><span class="sxs-lookup"><span data-stu-id="281f5-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="281f5-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="281f5-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="281f5-123">Określa nazwę odbiornika.</span><span class="sxs-lookup"><span data-stu-id="281f5-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="281f5-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="281f5-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="281f5-125">Określa wartość <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> właściwości dla odbiornika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="281f5-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="281f5-126">[atrybuty niestandardowe]</span><span class="sxs-lookup"><span data-stu-id="281f5-126">[custom attributes]</span></span>|<span data-ttu-id="281f5-127">Atrybuty opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="281f5-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="281f5-128">Określa wartość atrybutów specyficznych dla odbiornika <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> identyfikowane przez metodę dla tego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="281f5-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="281f5-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>jest przykładem dodatkowego atrybutu <xref:System.Diagnostics.DelimitedListTraceListener> unikatowego dla klasy.</span><span class="sxs-lookup"><span data-stu-id="281f5-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="281f5-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="281f5-130">Child Elements</span></span>  
  
|<span data-ttu-id="281f5-131">Element</span><span class="sxs-lookup"><span data-stu-id="281f5-131">Element</span></span>|<span data-ttu-id="281f5-132">Opis</span><span class="sxs-lookup"><span data-stu-id="281f5-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="281f5-133">\<>filtra</span><span class="sxs-lookup"><span data-stu-id="281f5-133">\<filter></span></span>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="281f5-134">Dodaje filtr do odbiornika `Listeners` w kolekcji dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="281f5-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="281f5-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="281f5-135">Parent Elements</span></span>  
  
|<span data-ttu-id="281f5-136">Element</span><span class="sxs-lookup"><span data-stu-id="281f5-136">Element</span></span>|<span data-ttu-id="281f5-137">Opis</span><span class="sxs-lookup"><span data-stu-id="281f5-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="281f5-138">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="281f5-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="281f5-139">Określa odbiorniki śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, na którym ustawiony jest przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="281f5-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="281f5-140">Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="281f5-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="281f5-141">Określa źródło śledzenia, które inicjuje śledzenie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="281f5-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="281f5-142">Określa odbiorniki, które zbierają, przechowują i rozsyłają wiadomości.</span><span class="sxs-lookup"><span data-stu-id="281f5-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="281f5-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="281f5-143">Remarks</span></span>  
 <span data-ttu-id="281f5-144">Klasy odbiornika dostarczane z .NET Framework pochodzą <xref:System.Diagnostics.TraceListener> z klasy.</span><span class="sxs-lookup"><span data-stu-id="281f5-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="281f5-145">Jeśli nie określisz `name` atrybutu odbiornika śledzenia, <xref:System.Diagnostics.TraceListener.Name%2A> właściwość odbiornika śledzenia domyślnie pusty ciąg ("").</span><span class="sxs-lookup"><span data-stu-id="281f5-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="281f5-146">Jeśli aplikacja ma tylko jeden odbiornik, można dodać go bez określania nazwy i można ją usunąć, określając pusty ciąg dla nazwy.</span><span class="sxs-lookup"><span data-stu-id="281f5-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="281f5-147">Jednak jeśli aplikacja ma więcej niż jeden odbiornik, należy określić unikatową nazwę dla każdego odbiornika śledzenia, <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> który pozwala zidentyfikować i zarządzać poszczególnych odbiorników śledzenia w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="281f5-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="281f5-148">Dodanie więcej niż jednego odbiornika śledzenia tego samego typu i o tej samej nazwie powoduje `Listeners` tylko jeden odbiornik śledzenia tego typu i nazwy dodawane do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="281f5-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="281f5-149">Jednak programowo można dodać wiele identycznych `Listeners` odbiorników do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="281f5-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="281f5-150">Wartość atrybutu `initializeData` zależy od typu odbiornika, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="281f5-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="281f5-151">Nie wszystkie detektory śledzenia `initializeData`wymagają określenia .</span><span class="sxs-lookup"><span data-stu-id="281f5-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="281f5-152">Korzystając z `initializeData` atrybutu, może pojawić się ostrzeżenie kompilatora "Atrybut 'initializeData' nie jest zadeklarowany."</span><span class="sxs-lookup"><span data-stu-id="281f5-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="281f5-153">To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są <xref:System.Diagnostics.TraceListener>sprawdzane względem abstrakcyjnej klasy podstawowej, która nie rozpoznaje atrybutu. `initializeData`</span><span class="sxs-lookup"><span data-stu-id="281f5-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="281f5-154">Zazwyczaj można zignorować to ostrzeżenie dla implementacji odbiornika śledzenia, które mają konstruktora, który przyjmuje parametr.</span><span class="sxs-lookup"><span data-stu-id="281f5-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="281f5-155">W poniższej tabeli przedstawiono detektory śledzenia, które są dołączone `initializeData` do programu .NET Framework i opisano wartość ich atrybutów.</span><span class="sxs-lookup"><span data-stu-id="281f5-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="281f5-156">Śledzenie klasy detektora</span><span class="sxs-lookup"><span data-stu-id="281f5-156">Trace listener class</span></span>|<span data-ttu-id="281f5-157">initializeDane wartość atrybutu</span><span class="sxs-lookup"><span data-stu-id="281f5-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="281f5-158">Wartość `useErrorStream` konstruktora. <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="281f5-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="281f5-159">Ustaw `initializeData` atrybut na`true`" ", aby zapisać śledzenie i debugowanie danych wyjściowych do standardowego strumienia błędów; ustawić go`false`na " ", aby zapisać do standardowego strumienia wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="281f5-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="281f5-160">Nazwa pliku, do <xref:System.Diagnostics.DelimitedListTraceListener> który zapisuje się.</span><span class="sxs-lookup"><span data-stu-id="281f5-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="281f5-161">Nazwa istniejącego źródła dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="281f5-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="281f5-162">Nazwa pliku, który <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="281f5-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="281f5-163">Nazwa pliku, który <xref:System.Diagnostics.TextWriterTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="281f5-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="281f5-164">Nazwa pliku, który <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="281f5-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="281f5-165">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="281f5-165">Configuration File</span></span>  
 <span data-ttu-id="281f5-166">Ten element może być używany w pliku konfiguracyjnym komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="281f5-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="281f5-167">Przykład</span><span class="sxs-lookup"><span data-stu-id="281f5-167">Example</span></span>  
 <span data-ttu-id="281f5-168">W poniższym przykładzie `<add>` pokazano, jak `console` używać `textListener` elementów do dodawania odbiorników i `Listeners` do kolekcji dla źródła `TraceSourceApp`śledzenia .</span><span class="sxs-lookup"><span data-stu-id="281f5-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="281f5-169">Odbiornik `textListener` zapisuje dane wyjściowe śledzenia do pliku myListener.log.</span><span class="sxs-lookup"><span data-stu-id="281f5-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="281f5-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="281f5-170">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="281f5-171">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="281f5-171">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="281f5-172">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="281f5-172">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
