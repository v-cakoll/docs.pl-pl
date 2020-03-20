---
title: <add>Element <listeners> dla<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: c64673908dc9afe67d97c08f93e5b9d9533bd34d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153675"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="066f7-102">\<dodaj element> dla \<> dla> \<śledzenia</span><span class="sxs-lookup"><span data-stu-id="066f7-102">\<add> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="066f7-103">Dodaje odbiornik do kolekcji **Odbiorniki.**</span><span class="sxs-lookup"><span data-stu-id="066f7-103">Adds a listener to the **Listeners** collection.</span></span>  

<span data-ttu-id="066f7-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="066f7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="066f7-105">&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="066f7-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="066f7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>śledzenia**](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="066f7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="066f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<słuchacze>**](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="066f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="066f7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dodaj>**</span><span class="sxs-lookup"><span data-stu-id="066f7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="066f7-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="066f7-109">Syntax</span></span>  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="066f7-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="066f7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="066f7-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="066f7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="066f7-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="066f7-112">Attributes</span></span>  
  
|<span data-ttu-id="066f7-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="066f7-113">Attribute</span></span>|<span data-ttu-id="066f7-114">Opis</span><span class="sxs-lookup"><span data-stu-id="066f7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="066f7-115">**Typu**</span><span class="sxs-lookup"><span data-stu-id="066f7-115">**type**</span></span>|<span data-ttu-id="066f7-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="066f7-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="066f7-117">Określa typ odbiornika.</span><span class="sxs-lookup"><span data-stu-id="066f7-117">Specifies the type of the listener.</span></span> <span data-ttu-id="066f7-118">Należy użyć ciągu spełniającego wymagania określone w określaniu w [pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="066f7-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="066f7-119">**Initializedata**</span><span class="sxs-lookup"><span data-stu-id="066f7-119">**initializeData**</span></span>|<span data-ttu-id="066f7-120">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="066f7-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="066f7-121">Ciąg przekazany do konstruktora dla określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="066f7-121">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="066f7-122">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="066f7-122">**name**</span></span>|<span data-ttu-id="066f7-123">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="066f7-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="066f7-124">Określa nazwę odbiornika.</span><span class="sxs-lookup"><span data-stu-id="066f7-124">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="066f7-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="066f7-125">Child Elements</span></span>  
  
|<span data-ttu-id="066f7-126">Element</span><span class="sxs-lookup"><span data-stu-id="066f7-126">Element</span></span>|<span data-ttu-id="066f7-127">Opis</span><span class="sxs-lookup"><span data-stu-id="066f7-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="066f7-128">\<>filtra</span><span class="sxs-lookup"><span data-stu-id="066f7-128">\<filter></span></span>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="066f7-129">Dodaje filtr do odbiornika `Listeners` w kolekcji dla śledzenia.</span><span class="sxs-lookup"><span data-stu-id="066f7-129">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="066f7-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="066f7-130">Parent Elements</span></span>  
  
|<span data-ttu-id="066f7-131">Element</span><span class="sxs-lookup"><span data-stu-id="066f7-131">Element</span></span>|<span data-ttu-id="066f7-132">Opis</span><span class="sxs-lookup"><span data-stu-id="066f7-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="066f7-133">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="066f7-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="066f7-134">Określa odbiornik, który zbiera, przechowuje i kieruje wiadomości.</span><span class="sxs-lookup"><span data-stu-id="066f7-134">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="066f7-135">Detektory kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="066f7-135">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="066f7-136">Określa element główny sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="066f7-136">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="066f7-137">Zawiera odbiorniki, które zbierają, przechowują i trasy śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="066f7-137">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="066f7-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="066f7-138">Remarks</span></span>  
 <span data-ttu-id="066f7-139">I <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> klasy współużytkuje tę samą kolekcję **odbiorników.**</span><span class="sxs-lookup"><span data-stu-id="066f7-139">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="066f7-140">Jeśli dodasz obiekt odbiornika do kolekcji w jednej z tych klas, druga klasa używa tego samego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="066f7-140">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="066f7-141">Klasy odbiornika pochodzą z <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="066f7-141">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="066f7-142">Jeśli nie określisz `name` atrybutu odbiornika śledzenia, <xref:System.Diagnostics.TraceListener.Name%2A> odbiornik śledzenia domyślnie pusty ciąg ("").</span><span class="sxs-lookup"><span data-stu-id="066f7-142">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="066f7-143">Jeśli aplikacja ma tylko jeden odbiornik, można dodać go bez określania nazwy i usunąć go, określając pusty ciąg dla nazwy.</span><span class="sxs-lookup"><span data-stu-id="066f7-143">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="066f7-144">Jednak jeśli aplikacja ma więcej niż jeden odbiornik, należy określić unikatowe nazwy dla każdego odbiornika śledzenia, <xref:System.Diagnostics.Debug.Listeners%2A> <xref:System.Diagnostics.Trace.Listeners%2A> co pozwala na identyfikowanie i zarządzanie poszczególnych odbiorników śledzenia w ramach i kolekcji.</span><span class="sxs-lookup"><span data-stu-id="066f7-144">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="066f7-145">Dodanie więcej niż jednego odbiornika śledzenia tego samego typu i o tej samej nazwie powoduje `Listeners` tylko jeden odbiornik śledzenia tego typu i nazwy dodawane do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="066f7-145">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="066f7-146">Jednak programowo można dodać wiele identycznych `Listeners` odbiorników do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="066f7-146">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="066f7-147">Wartość atrybutu **initializeData** zależy od typu odbiornika, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="066f7-147">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="066f7-148">Nie wszystkie detektory śledzenia wymagają określenia **initializeData**.</span><span class="sxs-lookup"><span data-stu-id="066f7-148">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="066f7-149">Korzystając z `initializeData` atrybutu, może pojawić się ostrzeżenie kompilatora "Atrybut 'initializeData' nie jest zadeklarowany."</span><span class="sxs-lookup"><span data-stu-id="066f7-149">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="066f7-150">To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są <xref:System.Diagnostics.TraceListener>sprawdzane względem abstrakcyjnej klasy podstawowej, która nie rozpoznaje atrybutu. `initializeData`</span><span class="sxs-lookup"><span data-stu-id="066f7-150">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="066f7-151">Zazwyczaj można zignorować to ostrzeżenie dla implementacji odbiornika śledzenia, które mają konstruktora, który przyjmuje parametr.</span><span class="sxs-lookup"><span data-stu-id="066f7-151">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="066f7-152">W poniższej tabeli przedstawiono detektory śledzenia, które są dołączone do programu .NET Framework i opisano wartość ich atrybutów **initializeData.**</span><span class="sxs-lookup"><span data-stu-id="066f7-152">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="066f7-153">Śledzenie klasy detektora</span><span class="sxs-lookup"><span data-stu-id="066f7-153">Trace listener class</span></span>|<span data-ttu-id="066f7-154">initializeDane wartość atrybutu</span><span class="sxs-lookup"><span data-stu-id="066f7-154">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="066f7-155">Wartość `useErrorStream` konstruktora. <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="066f7-155">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="066f7-156">Ustaw `initializeData` atrybut na`true`" ", aby zapisać śledzenie <xref:System.Console.Error%2A?displayProperty=nameWithType>i debugowanie danych wyjściowych ; "`false`", aby <xref:System.Console.Out%2A?displayProperty=nameWithType>napisać do .</span><span class="sxs-lookup"><span data-stu-id="066f7-156">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="066f7-157">Nazwa pliku, do <xref:System.Diagnostics.DelimitedListTraceListener> który zapisuje się.</span><span class="sxs-lookup"><span data-stu-id="066f7-157">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="066f7-158">Nazwa nazwy istniejącego źródła dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="066f7-158">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="066f7-159">Nazwa pliku, który <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="066f7-159">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="066f7-160">Nazwa pliku, który <xref:System.Diagnostics.TextWriterTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="066f7-160">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="066f7-161">Nazwa pliku, który <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="066f7-161">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="066f7-162">Przykład</span><span class="sxs-lookup"><span data-stu-id="066f7-162">Example</span></span>  
 <span data-ttu-id="066f7-163">W poniższym przykładzie \*\* \<\*\* pokazano, jak używać dodaj `MyListener`>`MyEventListener` elementów, aby dodać odbiorniki i **odbiorników** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="066f7-163">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="066f7-164">`MyListener`tworzy plik `MyListener.log` wywoływany i zapisuje dane wyjściowe do pliku.</span><span class="sxs-lookup"><span data-stu-id="066f7-164">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="066f7-165">`MyEventListener`tworzy wpis w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="066f7-165">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="066f7-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="066f7-166">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="066f7-167">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="066f7-167">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="066f7-168">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="066f7-168">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
