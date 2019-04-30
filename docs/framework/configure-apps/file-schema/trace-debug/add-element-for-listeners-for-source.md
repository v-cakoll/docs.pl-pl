---
title: <add> Element <listeners> dla <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 4d2952e29b09fcf9f81624317e30caf301a61a51
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701492"
---
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="4ffd4-102">\<Dodaj >, Element dla \<odbiorników > dla \<źródła ></span><span class="sxs-lookup"><span data-stu-id="4ffd4-102">\<add> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="4ffd4-103">Dodaje odbiornik do `Listeners` kolekcję dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="4ffd4-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="4ffd4-104">\<configuration></span></span>  
<span data-ttu-id="4ffd4-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="4ffd4-105">\<system.diagnostics></span></span>  
<span data-ttu-id="4ffd4-106">\<źródła ></span><span class="sxs-lookup"><span data-stu-id="4ffd4-106">\<sources></span></span>  
<span data-ttu-id="4ffd4-107">\<source></span><span class="sxs-lookup"><span data-stu-id="4ffd4-107">\<source></span></span>  
<span data-ttu-id="4ffd4-108">\<listeners></span><span class="sxs-lookup"><span data-stu-id="4ffd4-108">\<listeners></span></span>  
<span data-ttu-id="4ffd4-109">\<add></span><span class="sxs-lookup"><span data-stu-id="4ffd4-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ffd4-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ffd4-110">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ffd4-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4ffd4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4ffd4-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ffd4-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4ffd4-113">Attributes</span></span>  
  
|<span data-ttu-id="4ffd4-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4ffd4-114">Attribute</span></span>|<span data-ttu-id="4ffd4-115">Opis</span><span class="sxs-lookup"><span data-stu-id="4ffd4-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="4ffd4-116">Wymagany atrybut, chyba że masz odwołanie do odbiornika w `sharedListeners` kolekcji, w którym sprawa jest konieczne tylko odwołanie do niego za pomocą nazwy (zobacz [przykład](#example)).</span><span class="sxs-lookup"><span data-stu-id="4ffd4-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="4ffd4-117">Określa typ odbiornika.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-117">Specifies the type of the listener.</span></span> <span data-ttu-id="4ffd4-118">Należy użyć ciągu, który spełnia wymagania określone w [określanie w pełni kwalifikowanej nazwy typu](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="4ffd4-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="4ffd4-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4ffd4-120">Ciąg przekazany do konstruktora dla określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="4ffd4-121">Element <xref:System.Configuration.ConfigurationException> jest generowany, jeśli klasa nie ma konstruktora, który przyjmuje ciąg.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="4ffd4-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4ffd4-123">Określa nazwę odbiornika.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="4ffd4-124">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4ffd4-125">Określa <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> wartości właściwości dla odbiornika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="4ffd4-126">[niestandardowe atrybuty]</span><span class="sxs-lookup"><span data-stu-id="4ffd4-126">[custom attributes]</span></span>|<span data-ttu-id="4ffd4-127">Opcjonalne atrybuty.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="4ffd4-128">Określa wartość dla atrybutów specyficzne dla odbiornika identyfikowane przez <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> metody dla tego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="4ffd4-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> jest przykładem atrybut dodatkowe unikatowego dla <xref:System.Diagnostics.DelimitedListTraceListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4ffd4-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4ffd4-130">Child Elements</span></span>  
  
|<span data-ttu-id="4ffd4-131">Element</span><span class="sxs-lookup"><span data-stu-id="4ffd4-131">Element</span></span>|<span data-ttu-id="4ffd4-132">Opis</span><span class="sxs-lookup"><span data-stu-id="4ffd4-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ffd4-133">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="4ffd4-133">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="4ffd4-134">Dodaje filtr do odbiornika w `Listeners` kolekcję dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4ffd4-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4ffd4-135">Parent Elements</span></span>  
  
|<span data-ttu-id="4ffd4-136">Element</span><span class="sxs-lookup"><span data-stu-id="4ffd4-136">Element</span></span>|<span data-ttu-id="4ffd4-137">Opis</span><span class="sxs-lookup"><span data-stu-id="4ffd4-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4ffd4-138">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4ffd4-139">Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="4ffd4-140">Zawiera źródła śledzenia, które inicjują komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="4ffd4-141">Określa źródło śledzenia, który inicjuje komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="4ffd4-142">Określa obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów w postaci.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ffd4-143">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ffd4-143">Remarks</span></span>  
 <span data-ttu-id="4ffd4-144">Klasy odbiornika dostarczane z programem .NET Framework pochodzić od <xref:System.Diagnostics.TraceListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="4ffd4-145">Jeśli nie określisz `name` atrybut odbiornik śledzenia <xref:System.Diagnostics.TraceListener.Name%2A> właściwość odbiornik śledzenia wartość domyślna to ciąg pusty ("").</span><span class="sxs-lookup"><span data-stu-id="4ffd4-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="4ffd4-146">Jeśli aplikacja ma tylko jeden odbiornik, dodać go bez określenia nazwy i można go usunąć, określając pusty ciąg jako nazwę.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="4ffd4-147">Jednakże, jeśli aplikacja ma więcej niż jeden odbiornik, należy określić unikatową nazwę dla każdego odbiornika śledzenia, dzięki czemu można zidentyfikować i zarządzanie nimi poszczególnych śledzenia słuchaczy w <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ffd4-148">Dodawanie więcej niż jeden odbiornik śledzenia tego samego typu i o takiej samej nazwij skutkuje odbiornik śledzenia tylko jeden tego typu i dodawane do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="4ffd4-149">Jednak można programowo dodać wiele odbiorników identyczne do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="4ffd4-150">Wartość `initializeData` atrybutu zależy od typu tworzenia odbiornika.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="4ffd4-151">Nie wszystkie obiekty nasłuchujące śledzenia wymagają określenia `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ffd4-152">Kiedy używasz `initializeData` atrybutu, może wystąpić kompilatora ostrzeżenie "atrybut"initializeData"nie został zadeklarowany."</span><span class="sxs-lookup"><span data-stu-id="4ffd4-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="4ffd4-153">To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są weryfikowane względem abstrakcyjna klasa bazowa <xref:System.Diagnostics.TraceListener>, który nie rozpoznaje `initializeData` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="4ffd4-154">Zazwyczaj można zignorować to ostrzeżenie dla implementacji odbiornik śledzenia, które ma konstruktora, który przyjmuje parametr.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="4ffd4-155">W poniższej tabeli przedstawiono detektorów śledzenia, które są dołączone do programu .NET Framework i przedstawiono zalety ich `initializeData` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="4ffd4-156">Klasa odbiornik śledzenia</span><span class="sxs-lookup"><span data-stu-id="4ffd4-156">Trace listener class</span></span>|<span data-ttu-id="4ffd4-157">wartość atrybutu initializeData</span><span class="sxs-lookup"><span data-stu-id="4ffd4-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="4ffd4-158">`useErrorStream` Wartość <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="4ffd4-159">Ustaw `initializeData` atrybutu "`true`"do zapisu śledzenia i debugowania danych wyjściowych w strumieniu standard error; ustaw ją "`false`" do zapisu do strumienia wyjścia standardowego.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="4ffd4-160">Nazwa pliku <xref:System.Diagnostics.DelimitedListTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="4ffd4-161">Nazwa istniejącej źródło dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="4ffd4-162">Nazwę pliku, który <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="4ffd4-163">Nazwę pliku, który <xref:System.Diagnostics.TextWriterTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="4ffd4-164">Nazwę pliku, który <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="4ffd4-165">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4ffd4-165">Configuration File</span></span>  
 <span data-ttu-id="4ffd4-166">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ffd4-167">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ffd4-167">Example</span></span>  
 <span data-ttu-id="4ffd4-168">Poniższy przykład pokazuje, jak używać `<add>` elementy do dodania odbiorniki `console` i `textListener` do `Listeners` kolekcji dla źródła śledzenia `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="4ffd4-169">`textListener` Odbiornika zapisuje dane wyjściowe śledzenia myListener.log pliku.</span><span class="sxs-lookup"><span data-stu-id="4ffd4-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4ffd4-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ffd4-170">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="4ffd4-171">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="4ffd4-171">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="4ffd4-172">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="4ffd4-172">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
