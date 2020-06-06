---
title: <add>Element dla <listeners> elementu<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: c64673908dc9afe67d97c08f93e5b9d9533bd34d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153675"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="83388-102">\<add>Element dla \<listeners> elementu\<trace></span><span class="sxs-lookup"><span data-stu-id="83388-102">\<add> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="83388-103">Dodaje odbiornik do kolekcji **odbiorników** .</span><span class="sxs-lookup"><span data-stu-id="83388-103">Adds a listener to the **Listeners** collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="83388-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="83388-104">Syntax</span></span>  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83388-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="83388-105">Attributes and Elements</span></span>  
 <span data-ttu-id="83388-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="83388-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83388-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="83388-107">Attributes</span></span>  
  
|<span data-ttu-id="83388-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="83388-108">Attribute</span></span>|<span data-ttu-id="83388-109">Opis</span><span class="sxs-lookup"><span data-stu-id="83388-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="83388-110">**Wprowadź**</span><span class="sxs-lookup"><span data-stu-id="83388-110">**type**</span></span>|<span data-ttu-id="83388-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="83388-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="83388-112">Określa typ odbiornika.</span><span class="sxs-lookup"><span data-stu-id="83388-112">Specifies the type of the listener.</span></span> <span data-ttu-id="83388-113">Należy użyć ciągu, który spełnia wymagania określone w podaniu w [pełni kwalifikowanych nazw typów](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="83388-113">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="83388-114">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="83388-114">**initializeData**</span></span>|<span data-ttu-id="83388-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="83388-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="83388-116">Ciąg przesłany do konstruktora dla określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="83388-116">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="83388-117">**Nazwij**</span><span class="sxs-lookup"><span data-stu-id="83388-117">**name**</span></span>|<span data-ttu-id="83388-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="83388-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="83388-119">Określa nazwę odbiornika.</span><span class="sxs-lookup"><span data-stu-id="83388-119">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83388-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="83388-120">Child Elements</span></span>  
  
|<span data-ttu-id="83388-121">Element</span><span class="sxs-lookup"><span data-stu-id="83388-121">Element</span></span>|<span data-ttu-id="83388-122">Opis</span><span class="sxs-lookup"><span data-stu-id="83388-122">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="83388-123">Dodaje filtr do odbiornika w `Listeners` kolekcji w celu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="83388-123">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="83388-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="83388-124">Parent Elements</span></span>  
  
|<span data-ttu-id="83388-125">Element</span><span class="sxs-lookup"><span data-stu-id="83388-125">Element</span></span>|<span data-ttu-id="83388-126">Opis</span><span class="sxs-lookup"><span data-stu-id="83388-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="83388-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="83388-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="83388-128">Określa odbiornik, który zbiera, przechowuje i kieruje komunikaty.</span><span class="sxs-lookup"><span data-stu-id="83388-128">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="83388-129">Odbiorniki kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="83388-129">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="83388-130">Określa element główny dla sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="83388-130">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="83388-131">Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="83388-131">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83388-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="83388-132">Remarks</span></span>  
 <span data-ttu-id="83388-133"><xref:System.Diagnostics.Debug>Klasy i <xref:System.Diagnostics.Trace> współużytkują tę samą kolekcję **detektorów** .</span><span class="sxs-lookup"><span data-stu-id="83388-133">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="83388-134">Jeśli dodasz obiekt odbiornika do kolekcji w jednej z tych klas, inna Klasa używa tego samego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="83388-134">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="83388-135">Klasy odbiornika pochodzą od <xref:System.Diagnostics.TraceListener> .</span><span class="sxs-lookup"><span data-stu-id="83388-135">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="83388-136">Jeśli nie określisz `name` atrybutu odbiornika śledzenia, wartość <xref:System.Diagnostics.TraceListener.Name%2A> Ustawienia odbiornik śledzenia domyślnie będzie pustym ciągiem ("").</span><span class="sxs-lookup"><span data-stu-id="83388-136">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="83388-137">Jeśli aplikacja ma tylko jeden odbiornik, możesz ją dodać bez określania nazwy i usunąć ją, określając pusty ciąg w polu Nazwa.</span><span class="sxs-lookup"><span data-stu-id="83388-137">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="83388-138">Jeśli jednak aplikacja ma więcej niż jeden odbiornik, należy określić unikatowe nazwy dla każdego odbiornika śledzenia, co pozwala identyfikować poszczególne detektory śledzenia i zarządzać nimi w ramach <xref:System.Diagnostics.Debug.Listeners%2A> <xref:System.Diagnostics.Trace.Listeners%2A> kolekcji i.</span><span class="sxs-lookup"><span data-stu-id="83388-138">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="83388-139">Dodanie więcej niż jednego odbiornika śledzenia tego samego typu i z tą samą nazwą powoduje tylko jeden odbiornik śledzenia tego typu i nazwę dodawane do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="83388-139">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="83388-140">Można jednak programowo dodać wiele identycznych odbiorników do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="83388-140">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="83388-141">Wartość atrybutu **initializeData** zależy od typu tworzonego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="83388-141">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="83388-142">Nie wszystkie detektory śledzenia wymagają określenia **initializeData**.</span><span class="sxs-lookup"><span data-stu-id="83388-142">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="83388-143">W przypadku korzystania z `initializeData` atrybutu może zostać wyświetlone ostrzeżenie kompilatora "initializeData" nie jest zadeklarowany. "</span><span class="sxs-lookup"><span data-stu-id="83388-143">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="83388-144">To ostrzeżenie występuje, ponieważ ustawienia konfiguracji są weryfikowane względem abstrakcyjnej klasy bazowej <xref:System.Diagnostics.TraceListener> , która nie rozpoznaje `initializeData` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="83388-144">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="83388-145">Zazwyczaj można zignorować to ostrzeżenie dla implementacji detektorów śledzenia, które mają konstruktora, który pobiera parametr.</span><span class="sxs-lookup"><span data-stu-id="83388-145">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="83388-146">W poniższej tabeli przedstawiono detektory śledzenia, które są dołączone do .NET Framework i opisano wartość ich atrybutów **initializeData** .</span><span class="sxs-lookup"><span data-stu-id="83388-146">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="83388-147">Trace — Klasa odbiornika</span><span class="sxs-lookup"><span data-stu-id="83388-147">Trace listener class</span></span>|<span data-ttu-id="83388-148">wartość atrybutu initializeData</span><span class="sxs-lookup"><span data-stu-id="83388-148">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="83388-149">`useErrorStream`Wartość dla <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="83388-149">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="83388-150">Ustaw `initializeData` atrybut na " `true` ", aby zapisać dane wyjściowe śledzenia i debugowania do <xref:System.Console.Error%2A?displayProperty=nameWithType> ; " `false` " do zapisu <xref:System.Console.Out%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="83388-150">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="83388-151">Nazwa pliku, w którym są <xref:System.Diagnostics.DelimitedListTraceListener> zapisywane dane.</span><span class="sxs-lookup"><span data-stu-id="83388-151">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="83388-152">Nazwa istniejącego źródła dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="83388-152">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="83388-153">Nazwa pliku, w którym zapisuje dane <xref:System.Diagnostics.EventSchemaTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="83388-153">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="83388-154">Nazwa pliku, w którym zapisuje dane <xref:System.Diagnostics.TextWriterTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="83388-154">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="83388-155">Nazwa pliku, w którym zapisuje dane <xref:System.Diagnostics.XmlWriterTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="83388-155">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="83388-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="83388-156">Example</span></span>  
 <span data-ttu-id="83388-157">Poniższy przykład pokazuje, jak używać **\<add>** elementów do dodawania odbiorników `MyListener` i `MyEventListener` do kolekcji **odbiorników** .</span><span class="sxs-lookup"><span data-stu-id="83388-157">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="83388-158">`MyListener`tworzy plik o nazwie `MyListener.log` i zapisuje dane wyjściowe do pliku.</span><span class="sxs-lookup"><span data-stu-id="83388-158">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="83388-159">`MyEventListener`tworzy wpis w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="83388-159">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="83388-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83388-160">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="83388-161">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="83388-161">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="83388-162">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="83388-162">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
