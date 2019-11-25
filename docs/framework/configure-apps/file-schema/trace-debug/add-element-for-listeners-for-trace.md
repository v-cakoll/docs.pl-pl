---
title: Element <add> dla <listeners> <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: eb3e9cf4a6d138998cfde865cda8ed4146be26d0
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088981"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="de08e-102">\<dodać elementu > dla odbiorników \<> \<śledzenia ></span><span class="sxs-lookup"><span data-stu-id="de08e-102">\<add> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="de08e-103">Dodaje odbiornik do kolekcji **odbiorników** .</span><span class="sxs-lookup"><span data-stu-id="de08e-103">Adds a listener to the **Listeners** collection.</span></span>  

<span data-ttu-id="de08e-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="de08e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="de08e-105">&nbsp;&nbsp;[ **\<system. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="de08e-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="de08e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Trace**](trace-element.md) ></span><span class="sxs-lookup"><span data-stu-id="de08e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="de08e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**odbiorników**](listeners-element-for-trace.md) ></span><span class="sxs-lookup"><span data-stu-id="de08e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="de08e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dodaj >**</span><span class="sxs-lookup"><span data-stu-id="de08e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="de08e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="de08e-109">Syntax</span></span>  
  
```xml  
<add name="name"   
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de08e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="de08e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="de08e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="de08e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de08e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="de08e-112">Attributes</span></span>  
  
|<span data-ttu-id="de08e-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="de08e-113">Attribute</span></span>|<span data-ttu-id="de08e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="de08e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="de08e-115">**Wprowadź**</span><span class="sxs-lookup"><span data-stu-id="de08e-115">**type**</span></span>|<span data-ttu-id="de08e-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="de08e-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="de08e-117">Określa typ odbiornika.</span><span class="sxs-lookup"><span data-stu-id="de08e-117">Specifies the type of the listener.</span></span> <span data-ttu-id="de08e-118">Należy użyć ciągu, który spełnia wymagania określone w podaniu w [pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="de08e-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="de08e-119">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="de08e-119">**initializeData**</span></span>|<span data-ttu-id="de08e-120">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="de08e-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="de08e-121">Ciąg przesłany do konstruktora dla określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="de08e-121">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="de08e-122">**Nazwij**</span><span class="sxs-lookup"><span data-stu-id="de08e-122">**name**</span></span>|<span data-ttu-id="de08e-123">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="de08e-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="de08e-124">Określa nazwę odbiornika.</span><span class="sxs-lookup"><span data-stu-id="de08e-124">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de08e-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="de08e-125">Child Elements</span></span>  
  
|<span data-ttu-id="de08e-126">Element</span><span class="sxs-lookup"><span data-stu-id="de08e-126">Element</span></span>|<span data-ttu-id="de08e-127">Opis</span><span class="sxs-lookup"><span data-stu-id="de08e-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de08e-128">Filtr \<</span><span class="sxs-lookup"><span data-stu-id="de08e-128">\<filter></span></span>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="de08e-129">Dodaje filtr do odbiornika w kolekcji `Listeners` do śledzenia.</span><span class="sxs-lookup"><span data-stu-id="de08e-129">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="de08e-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="de08e-130">Parent Elements</span></span>  
  
|<span data-ttu-id="de08e-131">Element</span><span class="sxs-lookup"><span data-stu-id="de08e-131">Element</span></span>|<span data-ttu-id="de08e-132">Opis</span><span class="sxs-lookup"><span data-stu-id="de08e-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="de08e-133">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="de08e-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="de08e-134">Określa odbiornik, który zbiera, przechowuje i kieruje komunikaty.</span><span class="sxs-lookup"><span data-stu-id="de08e-134">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="de08e-135">Odbiorniki kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="de08e-135">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="de08e-136">Określa element główny dla sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="de08e-136">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="de08e-137">Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="de08e-137">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de08e-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de08e-138">Remarks</span></span>  
 <span data-ttu-id="de08e-139">Klasy <xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace> współdzielą tę samą kolekcję **detektorów** .</span><span class="sxs-lookup"><span data-stu-id="de08e-139">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="de08e-140">Jeśli dodasz obiekt odbiornika do kolekcji w jednej z tych klas, inna Klasa używa tego samego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="de08e-140">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="de08e-141">Klasy odbiornika pochodzą z <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="de08e-141">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="de08e-142">Jeśli nie określisz atrybutu `name` detektora śledzenia, <xref:System.Diagnostics.TraceListener.Name%2A> odbiornik śledzenia domyślnie będzie pustym ciągiem ("").</span><span class="sxs-lookup"><span data-stu-id="de08e-142">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="de08e-143">Jeśli aplikacja ma tylko jeden odbiornik, możesz ją dodać bez określania nazwy i usunąć ją, określając pusty ciąg w polu Nazwa.</span><span class="sxs-lookup"><span data-stu-id="de08e-143">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="de08e-144">Jeśli jednak aplikacja ma więcej niż jeden odbiornik, należy określić unikatowe nazwy dla każdego odbiornika śledzenia, co pozwala identyfikować poszczególne detektory śledzenia i zarządzać nimi w ramach kolekcji <xref:System.Diagnostics.Debug.Listeners%2A> i <xref:System.Diagnostics.Trace.Listeners%2A>.</span><span class="sxs-lookup"><span data-stu-id="de08e-144">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de08e-145">Dodanie więcej niż jednego odbiornika śledzenia tego samego typu i z tą samą nazwą powoduje tylko jeden odbiornik śledzenia tego typu i nazwę dodawane do kolekcji `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="de08e-145">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="de08e-146">Można jednak programowo dodać wiele identycznych odbiorników do kolekcji `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="de08e-146">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="de08e-147">Wartość atrybutu **initializeData** zależy od typu tworzonego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="de08e-147">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="de08e-148">Nie wszystkie detektory śledzenia wymagają określenia **initializeData**.</span><span class="sxs-lookup"><span data-stu-id="de08e-148">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de08e-149">W przypadku korzystania z atrybutu `initializeData` można uzyskać Ostrzeżenie kompilatora "atrybut" initializeData "nie jest zadeklarowany."</span><span class="sxs-lookup"><span data-stu-id="de08e-149">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="de08e-150">To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są weryfikowane względem abstrakcyjnej klasy bazowej <xref:System.Diagnostics.TraceListener>, która nie rozpoznaje atrybutu `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="de08e-150">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="de08e-151">Zazwyczaj można zignorować to ostrzeżenie dla implementacji detektorów śledzenia, które mają konstruktora, który pobiera parametr.</span><span class="sxs-lookup"><span data-stu-id="de08e-151">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="de08e-152">W poniższej tabeli przedstawiono detektory śledzenia, które są dołączone do .NET Framework i opisano wartość ich atrybutów **initializeData** .</span><span class="sxs-lookup"><span data-stu-id="de08e-152">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="de08e-153">Trace — Klasa odbiornika</span><span class="sxs-lookup"><span data-stu-id="de08e-153">Trace listener class</span></span>|<span data-ttu-id="de08e-154">wartość atrybutu initializeData</span><span class="sxs-lookup"><span data-stu-id="de08e-154">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="de08e-155">Wartość `useErrorStream` konstruktora <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>.</span><span class="sxs-lookup"><span data-stu-id="de08e-155">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="de08e-156">Ustaw atrybut `initializeData` na "`true`", aby zapisać dane wyjściowe śledzenia i debugowania w <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`", aby zapisać w <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="de08e-156">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="de08e-157">Nazwa pliku, do którego <xref:System.Diagnostics.DelimitedListTraceListener> zapisu.</span><span class="sxs-lookup"><span data-stu-id="de08e-157">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="de08e-158">Nazwa istniejącego źródła dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="de08e-158">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="de08e-159">Nazwa pliku, w którym <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje dane.</span><span class="sxs-lookup"><span data-stu-id="de08e-159">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="de08e-160">Nazwa pliku, w którym <xref:System.Diagnostics.TextWriterTraceListener> zapisuje dane.</span><span class="sxs-lookup"><span data-stu-id="de08e-160">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="de08e-161">Nazwa pliku, w którym <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje dane.</span><span class="sxs-lookup"><span data-stu-id="de08e-161">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="de08e-162">Przykład</span><span class="sxs-lookup"><span data-stu-id="de08e-162">Example</span></span>  
 <span data-ttu-id="de08e-163">W poniższym przykładzie pokazano, jak za pomocą **\<dodawać elementy >** , aby dodać odbiorniki `MyListener` i `MyEventListener` do kolekcji **odbiorników** .</span><span class="sxs-lookup"><span data-stu-id="de08e-163">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="de08e-164">`MyListener` tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku.</span><span class="sxs-lookup"><span data-stu-id="de08e-164">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="de08e-165">`MyEventListener` tworzy wpis w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="de08e-165">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="de08e-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de08e-166">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="de08e-167">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="de08e-167">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="de08e-168">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="de08e-168">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
