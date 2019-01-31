---
title: <sharedListeners>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
ms.openlocfilehash: 56a4111f2e0fd290321756c43c7f245e46044b02
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254941"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="0a243-102">\<sharedListeners > Element</span><span class="sxs-lookup"><span data-stu-id="0a243-102">\<sharedListeners> Element</span></span>
<span data-ttu-id="0a243-103">Zawiera dowolnego źródła i elementu śledzenia można odwoływać się do obiektów nasłuchujących.</span><span class="sxs-lookup"><span data-stu-id="0a243-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="0a243-104">Te odbiorniki nie otrzymasz żadnych śladów domyślnie i nie jest możliwe pobrać te odbiorniki w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0a243-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="0a243-105">Odbiorniki zidentyfikowane jako współdzielonych detektorów można dodać do źródła lub śledzenie według nazwy.</span><span class="sxs-lookup"><span data-stu-id="0a243-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
 <span data-ttu-id="0a243-106">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="0a243-106">\<configuration></span></span>  
<span data-ttu-id="0a243-107">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="0a243-107">\<system.diagnostics></span></span>  
<span data-ttu-id="0a243-108">\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="0a243-108">\<sharedListeners></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a243-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="0a243-109">Syntax</span></span>  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a243-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0a243-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0a243-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0a243-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a243-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0a243-112">Attributes</span></span>  
 <span data-ttu-id="0a243-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="0a243-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0a243-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0a243-114">Child Elements</span></span>  
  
|<span data-ttu-id="0a243-115">Element</span><span class="sxs-lookup"><span data-stu-id="0a243-115">Element</span></span>|<span data-ttu-id="0a243-116">Opis</span><span class="sxs-lookup"><span data-stu-id="0a243-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a243-117">\<add></span><span class="sxs-lookup"><span data-stu-id="0a243-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|<span data-ttu-id="0a243-118">Dodaje odbiornik do `sharedListeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0a243-118">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0a243-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0a243-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0a243-120">Element</span><span class="sxs-lookup"><span data-stu-id="0a243-120">Element</span></span>|<span data-ttu-id="0a243-121">Opis</span><span class="sxs-lookup"><span data-stu-id="0a243-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="0a243-122">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0a243-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="0a243-123">Określa element root dla sekcji konfiguracyjnej platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0a243-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a243-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0a243-124">Remarks</span></span>  
 <span data-ttu-id="0a243-125">Dodanie detektora do kolekcji współdzielonych detektorów nie powoduje on aktywny odbiornik.</span><span class="sxs-lookup"><span data-stu-id="0a243-125">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="0a243-126">Jego musi nadal będzie dodawany do źródła śledzenia lub śledzenia przez dodanie jej do `Listeners` kolekcji dla tego elementu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0a243-126">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="0a243-127">Klasy odbiornika w programie .NET Framework pochodzić od <xref:System.Diagnostics.TraceListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="0a243-127">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="0a243-128">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0a243-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a243-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="0a243-129">Example</span></span>  
 <span data-ttu-id="0a243-130">Poniższy przykład pokazuje, jak używać `<sharedListeners>` elementu do dodania odbiornika `console` do `Listeners` kolekcji dla obu <xref:System.Diagnostics.TraceSource> i <xref:System.Diagnostics.Trace> klasy.</span><span class="sxs-lookup"><span data-stu-id="0a243-130">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="0a243-131">Odbiornik śledzenia konsoli zapisuje informacje śledzenia do konsoli, za pośrednictwem wywołania do jednej <xref:System.Diagnostics.TraceSource> lub <xref:System.Diagnostics.Trace>.</span><span class="sxs-lookup"><span data-stu-id="0a243-131">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration></system.diagnostics>   
```  
  
## <a name="see-also"></a><span data-ttu-id="0a243-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a243-132">See also</span></span>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="0a243-133">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="0a243-133">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="0a243-134">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="0a243-134">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
