---
title: <add> element dla <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: e7934ed5e71005cfd28271298ff6ce1eb8829a0d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095636"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="8bf82-102">\<Dodaj >, Element dla \<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="8bf82-102">\<add> Element for \<sharedListeners></span></span>
<span data-ttu-id="8bf82-103">Dodaje odbiornik do `sharedListeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8bf82-103">Adds a listener to the `sharedListeners` collection.</span></span> `sharedListeners` <span data-ttu-id="8bf82-104">wszystkie to kolekcja obiektów nasłuchujących [ \<źródło >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) lub [ \<śledzenia >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) może odwoływać się.</span><span class="sxs-lookup"><span data-stu-id="8bf82-104">is a collection of listeners that any [\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) or [\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) can reference.</span></span>  <span data-ttu-id="8bf82-105">Domyślnie słuchaczy w `sharedListeners` kolekcji nie są umieszczane w `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8bf82-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="8bf82-106">Musi zostać dodany przez nazwę, aby [ \<źródło >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) lub [ \<śledzenia >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md).</span><span class="sxs-lookup"><span data-stu-id="8bf82-106">They must be added by name to the [\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) or [\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md).</span></span> <span data-ttu-id="8bf82-107">Nie jest możliwe do pobrania odbiorniki w `sharedListeners` kolekcji w kodzie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8bf82-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  
  
 <span data-ttu-id="8bf82-108">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="8bf82-108">\<configuration></span></span>  
<span data-ttu-id="8bf82-109">&nbsp;&nbsp;\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="8bf82-109">&nbsp;&nbsp;\<system.diagnostics></span></span>  
<span data-ttu-id="8bf82-110">&nbsp;&nbsp;&nbsp;&nbsp;\<sharedListeners > Element</span><span class="sxs-lookup"><span data-stu-id="8bf82-110">&nbsp;&nbsp;&nbsp;&nbsp;\<sharedListeners> Element</span></span>  
<span data-ttu-id="8bf82-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<add></span><span class="sxs-lookup"><span data-stu-id="8bf82-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bf82-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="8bf82-112">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8bf82-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8bf82-113">Attributes and Elements</span></span>  
 <span data-ttu-id="8bf82-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8bf82-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8bf82-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8bf82-115">Attributes</span></span>  
  
|<span data-ttu-id="8bf82-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8bf82-116">Attribute</span></span>|<span data-ttu-id="8bf82-117">Opis</span><span class="sxs-lookup"><span data-stu-id="8bf82-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="8bf82-118">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bf82-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="8bf82-119">Określa nazwę odbiornik, który służy do dodawania udostępnionych odbiornika do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8bf82-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="8bf82-120">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bf82-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="8bf82-121">Określa typ odbiornika.</span><span class="sxs-lookup"><span data-stu-id="8bf82-121">Specifies the type of the listener.</span></span> <span data-ttu-id="8bf82-122">Należy użyć ciągu, który spełnia wymagania określone w [określanie w pełni kwalifikowanej nazwy typu](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="8bf82-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="8bf82-123">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8bf82-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="8bf82-124">Ciąg przekazany do konstruktora dla określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="8bf82-124">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="8bf82-125">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8bf82-125">Optional attribute.</span></span><br/><br/><span data-ttu-id="8bf82-126">Ciąg reprezentujący co najmniej jednego <xref:System.Diagnostics.TraceOptions> elementów członkowskich wyliczenia, które wskazują dane, które ma zostać zapisana w danych wyjściowych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8bf82-126">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="8bf82-127">Wiele elementów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="8bf82-127">Multiple items are separated by commas.</span></span> <span data-ttu-id="8bf82-128">Wartość domyślna to "None".</span><span class="sxs-lookup"><span data-stu-id="8bf82-128">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8bf82-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8bf82-129">Child Elements</span></span>  
  
|<span data-ttu-id="8bf82-130">Element</span><span class="sxs-lookup"><span data-stu-id="8bf82-130">Element</span></span>|<span data-ttu-id="8bf82-131">Opis</span><span class="sxs-lookup"><span data-stu-id="8bf82-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8bf82-132">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="8bf82-132">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="8bf82-133">Dodaje filtr do odbiornika w `sharedListeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8bf82-133">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8bf82-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8bf82-134">Parent Elements</span></span>  
  
|<span data-ttu-id="8bf82-135">Element</span><span class="sxs-lookup"><span data-stu-id="8bf82-135">Element</span></span>|<span data-ttu-id="8bf82-136">Opis</span><span class="sxs-lookup"><span data-stu-id="8bf82-136">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8bf82-137">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8bf82-137">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="8bf82-138">Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8bf82-138">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="8bf82-139">Kolekcja obiektów nasłuchujących dowolnego źródła i elementu śledzenia można odwoływać się do.</span><span class="sxs-lookup"><span data-stu-id="8bf82-139">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bf82-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8bf82-140">Remarks</span></span>  
 <span data-ttu-id="8bf82-141">Klasy odbiornika dostarczane z programem .NET Framework pochodzić od <xref:System.Diagnostics.TraceListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="8bf82-141">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="8bf82-142">Wartość `name` atrybut służy do dodawania udostępnionych odbiornika do `Listeners` zbierania śladu lub źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8bf82-142">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="8bf82-143">Wartość `initializeData` atrybutu zależy od typu tworzenia odbiornika.</span><span class="sxs-lookup"><span data-stu-id="8bf82-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="8bf82-144">Nie wszystkie obiekty nasłuchujące śledzenia wymagają określenia `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="8bf82-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8bf82-145">Kiedy używasz `initializeData` atrybutu, może wystąpić kompilatora ostrzeżenie "atrybut"initializeData"nie został zadeklarowany."</span><span class="sxs-lookup"><span data-stu-id="8bf82-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="8bf82-146">To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są weryfikowane względem abstrakcyjna klasa bazowa <xref:System.Diagnostics.TraceListener>, który nie rozpoznaje `initializeData` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8bf82-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="8bf82-147">Zazwyczaj można zignorować to ostrzeżenie dla implementacji odbiornik śledzenia, które ma konstruktora, który przyjmuje parametr.</span><span class="sxs-lookup"><span data-stu-id="8bf82-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="8bf82-148">W poniższej tabeli przedstawiono detektorów śledzenia, które są dołączone do programu .NET Framework i przedstawiono zalety ich `initializeData` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="8bf82-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="8bf82-149">Klasa odbiornik śledzenia</span><span class="sxs-lookup"><span data-stu-id="8bf82-149">Trace listener class</span></span>|<span data-ttu-id="8bf82-150">wartość atrybutu initializeData</span><span class="sxs-lookup"><span data-stu-id="8bf82-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="8bf82-151">`useErrorStream` Wartość <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="8bf82-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="8bf82-152">Ustaw `initializeData` atrybutu "`true`"do zapisu śledzenia i debugowania danych wyjściowych w strumieniu standard error; ustaw ją "`false`" do zapisu do strumienia wyjścia standardowego.</span><span class="sxs-lookup"><span data-stu-id="8bf82-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="8bf82-153">Nazwa pliku <xref:System.Diagnostics.DelimitedListTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="8bf82-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="8bf82-154">Nazwa istniejącej źródło dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bf82-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="8bf82-155">Nazwę pliku, który <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="8bf82-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="8bf82-156">Nazwę pliku, który <xref:System.Diagnostics.TextWriterTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="8bf82-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="8bf82-157">Nazwę pliku, który <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="8bf82-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="8bf82-158">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8bf82-158">Configuration File</span></span>  
 <span data-ttu-id="8bf82-159">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bf82-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bf82-160">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bf82-160">Example</span></span>  
 <span data-ttu-id="8bf82-161">Poniższy przykład pokazuje, jak używać `<add>` elementy do dodania <xref:System.Diagnostics.TextWriterTraceListener>`textListener` do `sharedListeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8bf82-161">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   `textListener` <span data-ttu-id="8bf82-162">jest dodawany przez nazwę, aby `Listeners` kolekcji dla źródła śledzenia `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="8bf82-162">is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="8bf82-163">`textListener` Odbiornika zapisuje dane wyjściowe śledzenia myListener.log pliku.</span><span class="sxs-lookup"><span data-stu-id="8bf82-163">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8bf82-164">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8bf82-164">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="8bf82-165">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="8bf82-165">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="8bf82-166">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="8bf82-166">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
