---
title: '&lt;Dodaj&gt; elementu &lt;odbiorników&gt; dla &lt;źródła&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ba8ff652003a9167ec370643797ac9300b83889a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745659"
---
# <a name="ltaddgt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="6bfec-102">&lt;Dodaj&gt; elementu &lt;odbiorników&gt; dla &lt;źródła&gt;</span><span class="sxs-lookup"><span data-stu-id="6bfec-102">&lt;add&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="6bfec-103">Dodaje odbiornika do `Listeners` kolekcji źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="6bfec-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="6bfec-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="6bfec-104">\<configuration></span></span>  
<span data-ttu-id="6bfec-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="6bfec-105">\<system.diagnostics></span></span>  
<span data-ttu-id="6bfec-106">\<źródeł ></span><span class="sxs-lookup"><span data-stu-id="6bfec-106">\<sources></span></span>  
<span data-ttu-id="6bfec-107">\<źródło ></span><span class="sxs-lookup"><span data-stu-id="6bfec-107">\<source></span></span>  
<span data-ttu-id="6bfec-108">\<obiekty nasłuchujące ></span><span class="sxs-lookup"><span data-stu-id="6bfec-108">\<listeners></span></span>  
<span data-ttu-id="6bfec-109">\<add></span><span class="sxs-lookup"><span data-stu-id="6bfec-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bfec-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="6bfec-110">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6bfec-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6bfec-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6bfec-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6bfec-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6bfec-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6bfec-113">Attributes</span></span>  
  
|<span data-ttu-id="6bfec-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6bfec-114">Attribute</span></span>|<span data-ttu-id="6bfec-115">Opis</span><span class="sxs-lookup"><span data-stu-id="6bfec-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="6bfec-116">Wymagany atrybut, chyba że odwołujesz odbiornika w `sharedListeners` kolekcji, w których wielkość liter jest konieczne tylko odwołuje się do niego według nazwy (zobacz [przykład](#example)).</span><span class="sxs-lookup"><span data-stu-id="6bfec-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="6bfec-117">Określa typ odbiornika.</span><span class="sxs-lookup"><span data-stu-id="6bfec-117">Specifies the type of the listener.</span></span> <span data-ttu-id="6bfec-118">Należy użyć ciągu, który spełnia wymagania określone w [określenie pełni kwalifikowane nazwy typów](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="6bfec-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="6bfec-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6bfec-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6bfec-120">Ciąg przekazany do konstruktora dla określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="6bfec-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="6bfec-121">A <xref:System.Configuration.ConfigurationException> jest generowany, jeśli klasa nie ma konstruktora przyjmującego ciąg.</span><span class="sxs-lookup"><span data-stu-id="6bfec-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="6bfec-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6bfec-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6bfec-123">Określa nazwę odbiornika.</span><span class="sxs-lookup"><span data-stu-id="6bfec-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="6bfec-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6bfec-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6bfec-125">Określa <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> wartości właściwości dla obiektu nasłuchującego śledzenia.</span><span class="sxs-lookup"><span data-stu-id="6bfec-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="6bfec-126">[atrybuty niestandardowe]</span><span class="sxs-lookup"><span data-stu-id="6bfec-126">[custom attributes]</span></span>|<span data-ttu-id="6bfec-127">Opcjonalne atrybuty.</span><span class="sxs-lookup"><span data-stu-id="6bfec-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="6bfec-128">Określa wartość atrybuty specyficzne dla odbiornika identyfikowane przez <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> metody dla tego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="6bfec-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="6bfec-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> Przykładem dodatkowe atrybutu jest unikatowa dla <xref:System.Diagnostics.DelimitedListTraceListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="6bfec-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6bfec-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6bfec-130">Child Elements</span></span>  
  
|<span data-ttu-id="6bfec-131">Element</span><span class="sxs-lookup"><span data-stu-id="6bfec-131">Element</span></span>|<span data-ttu-id="6bfec-132">Opis</span><span class="sxs-lookup"><span data-stu-id="6bfec-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6bfec-133">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="6bfec-133">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="6bfec-134">Dodaje filtr do odbiornika w `Listeners` kolekcji źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="6bfec-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6bfec-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6bfec-135">Parent Elements</span></span>  
  
|<span data-ttu-id="6bfec-136">Element</span><span class="sxs-lookup"><span data-stu-id="6bfec-136">Element</span></span>|<span data-ttu-id="6bfec-137">Opis</span><span class="sxs-lookup"><span data-stu-id="6bfec-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6bfec-138">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6bfec-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6bfec-139">Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="6bfec-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="6bfec-140">Zawiera źródła śledzenia, które inicjują śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="6bfec-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="6bfec-141">Określa źródło śledzenia, który inicjuje śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="6bfec-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="6bfec-142">Określa nasłuchujących zbierania, przechowywania i kierowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="6bfec-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bfec-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6bfec-143">Remarks</span></span>  
 <span data-ttu-id="6bfec-144">Klasy odbiornika dostarczone z programu .NET Framework pochodzić od <xref:System.Diagnostics.TraceListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="6bfec-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="6bfec-145">Jeśli nie określisz `name` atrybutu obiektu nasłuchującego śledzenia <xref:System.Diagnostics.TraceListener.Name%2A> właściwości obiektu nasłuchującego śledzenia domyślnie ciąg pusty ("").</span><span class="sxs-lookup"><span data-stu-id="6bfec-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="6bfec-146">Jeśli aplikacja ma tylko jeden odbiornik, dodaj go bez określania nazwy i usuń go przez określenie pustego ciągu w nazwie.</span><span class="sxs-lookup"><span data-stu-id="6bfec-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="6bfec-147">Jednak jeśli aplikacja ma więcej niż jeden odbiornik, należy określić unikatową nazwę dla każdego odbiornika śledzenia, który służy do identyfikowania i zarządzania nim obiekty nasłuchujące śledzenia poszczególnych w <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6bfec-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6bfec-148">Dodanie więcej niż jeden odbiornik śledzenia tego samego typu i o tej samej nazwie wyniki śledzenia tylko jednego odbiornika tego typu i nazwy dodawane do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6bfec-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="6bfec-149">Jednak programowo można dodać wiele odbiorników identyczne do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6bfec-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="6bfec-150">Wartość `initializeData` atrybutu zależy od typu tworzenia odbiornika.</span><span class="sxs-lookup"><span data-stu-id="6bfec-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="6bfec-151">Nie wszystkie obiekty nasłuchujące śledzenia wymagają określenia `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="6bfec-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6bfec-152">Jeśli używasz `initializeData` atrybutu, mogą wystąpić kompilatora ostrzeżenie "atrybutu"initializeData —"nie został zadeklarowany."</span><span class="sxs-lookup"><span data-stu-id="6bfec-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="6bfec-153">To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są sprawdzane w abstrakcyjnej klasy podstawowej <xref:System.Diagnostics.TraceListener>, którego nie rozpoznaje `initializeData` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6bfec-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="6bfec-154">Zazwyczaj można zignorować to ostrzeżenie implementacji odbiornika śledzenia, które mają Konstruktor, który przyjmuje parametr.</span><span class="sxs-lookup"><span data-stu-id="6bfec-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="6bfec-155">Poniższa tabela przedstawia obiekty nasłuchujące śledzenia, które są dołączone do programu .NET Framework oraz opis wartość ich `initializeData` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="6bfec-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="6bfec-156">Klasa odbiornika śledzenia</span><span class="sxs-lookup"><span data-stu-id="6bfec-156">Trace listener class</span></span>|<span data-ttu-id="6bfec-157">initializeData — wartość atrybutu</span><span class="sxs-lookup"><span data-stu-id="6bfec-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6bfec-158">`useErrorStream` Wartość <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="6bfec-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="6bfec-159">Ustaw `initializeData` atrybutu "`true`"zapisu śledzenia i debugowania dane wyjściowe do Standardowy strumień błędów; ustaw go "`false`" można zapisać do standardowego strumienia wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="6bfec-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6bfec-160">Nazwa pliku <xref:System.Diagnostics.DelimitedListTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="6bfec-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6bfec-161">Nazwa istniejącej źródło dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6bfec-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6bfec-162">Nazwa pliku, który <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="6bfec-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6bfec-163">Nazwa pliku, który <xref:System.Diagnostics.TextWriterTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="6bfec-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="6bfec-164">Nazwa pliku, który <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="6bfec-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="6bfec-165">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6bfec-165">Configuration File</span></span>  
 <span data-ttu-id="6bfec-166">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6bfec-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bfec-167">Przykład</span><span class="sxs-lookup"><span data-stu-id="6bfec-167">Example</span></span>  
 <span data-ttu-id="6bfec-168">Poniższy przykład przedstawia użycie `<add>` elementy do dodania odbiorniki `console` i `textListener` do `Listeners` kolekcji źródła śledzenia `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="6bfec-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="6bfec-169">`textListener` Odbiornika zapisuje dane wyjściowe śledzenia myListener.log pliku.</span><span class="sxs-lookup"><span data-stu-id="6bfec-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6bfec-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6bfec-170">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="6bfec-171">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="6bfec-171">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="6bfec-172">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="6bfec-172">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
