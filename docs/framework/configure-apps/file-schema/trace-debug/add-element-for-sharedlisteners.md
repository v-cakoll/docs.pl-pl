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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153610"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="3e4b0-102">\<dodaj element> dla \<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="3e4b0-102">\<add> Element for \<sharedListeners></span></span>
<span data-ttu-id="3e4b0-103">Dodaje odbiornik do `sharedListeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="3e4b0-104">`sharedListeners`jest zbiorem odbiorników, do których można odwoływać [ \<się>](source-element.md) lub [ \<śledzenia>.](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="3e4b0-104">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="3e4b0-105">Domyślnie odbiorniki w `sharedListeners` kolekcji nie `Listeners` są umieszczane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="3e4b0-106">Należy je dodać według nazwy do [ \<>źródłowego](source-element.md) lub [ \<>śledzenia ](trace-element.md).</span><span class="sxs-lookup"><span data-stu-id="3e4b0-106">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="3e4b0-107">Nie jest możliwe, aby uzyskać `sharedListeners` odbiorników w kolekcji w kodzie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  

<span data-ttu-id="3e4b0-108">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3e4b0-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3e4b0-109">&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="3e4b0-109">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="3e4b0-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span><span class="sxs-lookup"><span data-stu-id="3e4b0-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span></span>\
<span data-ttu-id="3e4b0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dodaj>**</span><span class="sxs-lookup"><span data-stu-id="3e4b0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3e4b0-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e4b0-112">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e4b0-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3e4b0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="3e4b0-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e4b0-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3e4b0-115">Attributes</span></span>  
  
|<span data-ttu-id="3e4b0-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3e4b0-116">Attribute</span></span>|<span data-ttu-id="3e4b0-117">Opis</span><span class="sxs-lookup"><span data-stu-id="3e4b0-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="3e4b0-118">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="3e4b0-119">Określa nazwę odbiornika, który jest używany do dodawania `Listeners` udostępnionego odbiornika do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="3e4b0-120">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="3e4b0-121">Określa typ odbiornika.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-121">Specifies the type of the listener.</span></span> <span data-ttu-id="3e4b0-122">Należy użyć ciągu spełniającego wymagania określone w określaniu w [pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="3e4b0-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="3e4b0-123">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3e4b0-124">Ciąg przekazany do konstruktora dla określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-124">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="3e4b0-125">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-125">Optional attribute.</span></span><br/><br/><span data-ttu-id="3e4b0-126">Reprezentacja ciągu jednego <xref:System.Diagnostics.TraceOptions> lub więcej elementów członkowskich wyliczenia, który wskazuje dane, które mają być zapisywane do danych wyjściowych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-126">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="3e4b0-127">Wiele elementów jest oddzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-127">Multiple items are separated by commas.</span></span> <span data-ttu-id="3e4b0-128">Wartością domyślną jest "Brak".</span><span class="sxs-lookup"><span data-stu-id="3e4b0-128">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="3e4b0-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3e4b0-129">Child Elements</span></span>  
  
|<span data-ttu-id="3e4b0-130">Element</span><span class="sxs-lookup"><span data-stu-id="3e4b0-130">Element</span></span>|<span data-ttu-id="3e4b0-131">Opis</span><span class="sxs-lookup"><span data-stu-id="3e4b0-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e4b0-132">\<>filtra</span><span class="sxs-lookup"><span data-stu-id="3e4b0-132">\<filter></span></span>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="3e4b0-133">Dodaje filtr do odbiornika `sharedListeners` w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-133">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3e4b0-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3e4b0-134">Parent Elements</span></span>  
  
|<span data-ttu-id="3e4b0-135">Element</span><span class="sxs-lookup"><span data-stu-id="3e4b0-135">Element</span></span>|<span data-ttu-id="3e4b0-136">Opis</span><span class="sxs-lookup"><span data-stu-id="3e4b0-136">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3e4b0-137">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-137">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="3e4b0-138">Określa odbiorniki śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, na którym ustawiony jest przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-138">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="3e4b0-139">Kolekcja odbiorników, do których można odwoływać się do dowolnego źródła lub elementu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-139">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e4b0-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e4b0-140">Remarks</span></span>  
 <span data-ttu-id="3e4b0-141">Klasy odbiornika dostarczane z .NET Framework pochodzą <xref:System.Diagnostics.TraceListener> z klasy.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-141">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="3e4b0-142">Wartość atrybutu `name` jest używana do dodawania udostępnionego `Listeners` odbiornika do kolekcji dla śledzenia lub źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-142">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="3e4b0-143">Wartość atrybutu `initializeData` zależy od typu odbiornika, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="3e4b0-144">Nie wszystkie detektory śledzenia `initializeData`wymagają określenia .</span><span class="sxs-lookup"><span data-stu-id="3e4b0-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e4b0-145">Korzystając z `initializeData` atrybutu, może pojawić się ostrzeżenie kompilatora "Atrybut 'initializeData' nie jest zadeklarowany."</span><span class="sxs-lookup"><span data-stu-id="3e4b0-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="3e4b0-146">To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są <xref:System.Diagnostics.TraceListener>sprawdzane względem abstrakcyjnej klasy podstawowej, która nie rozpoznaje atrybutu. `initializeData`</span><span class="sxs-lookup"><span data-stu-id="3e4b0-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="3e4b0-147">Zazwyczaj można zignorować to ostrzeżenie dla implementacji odbiornika śledzenia, które mają konstruktora, który przyjmuje parametr.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="3e4b0-148">W poniższej tabeli przedstawiono detektory śledzenia, które są dołączone `initializeData` do programu .NET Framework i opisano wartość ich atrybutów.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="3e4b0-149">Śledzenie klasy detektora</span><span class="sxs-lookup"><span data-stu-id="3e4b0-149">Trace listener class</span></span>|<span data-ttu-id="3e4b0-150">initializeDane wartość atrybutu</span><span class="sxs-lookup"><span data-stu-id="3e4b0-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="3e4b0-151">Wartość `useErrorStream` konstruktora. <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="3e4b0-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="3e4b0-152">Ustaw `initializeData` atrybut na`true`" ", aby zapisać śledzenie i debugowanie danych wyjściowych do standardowego strumienia błędów; ustawić go`false`na " ", aby zapisać do standardowego strumienia wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="3e4b0-153">Nazwa pliku, do <xref:System.Diagnostics.DelimitedListTraceListener> który zapisuje się.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3e4b0-154">Nazwa istniejącego źródła dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3e4b0-155">Nazwa pliku, który <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3e4b0-156">Nazwa pliku, który <xref:System.Diagnostics.TextWriterTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="3e4b0-157">Nazwa pliku, który <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="3e4b0-158">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3e4b0-158">Configuration File</span></span>  
 <span data-ttu-id="3e4b0-159">Ten element może być używany w pliku konfiguracyjnym komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e4b0-160">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e4b0-160">Example</span></span>  
 <span data-ttu-id="3e4b0-161">W poniższym przykładzie `<add>` pokazano, <xref:System.Diagnostics.TextWriterTraceListener> `textListener` jak `sharedListeners` używać elementów, aby dodać do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-161">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="3e4b0-162">`textListener`jest dodawany według `Listeners` nazwy do `TraceSourceApp`kolekcji dla źródła śledzenia .</span><span class="sxs-lookup"><span data-stu-id="3e4b0-162">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="3e4b0-163">Odbiornik `textListener` zapisuje dane wyjściowe śledzenia do pliku myListener.log.</span><span class="sxs-lookup"><span data-stu-id="3e4b0-163">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3e4b0-164">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e4b0-164">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="3e4b0-165">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="3e4b0-165">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3e4b0-166">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="3e4b0-166">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
