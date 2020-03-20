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
ms.openlocfilehash: 69f15cc9583b397017ac30a0c567914495867c18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153324"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="8ff11-102">\<SharedListeners> Element</span><span class="sxs-lookup"><span data-stu-id="8ff11-102">\<sharedListeners> Element</span></span>
<span data-ttu-id="8ff11-103">Zawiera detektory, do których może odwoływać się dowolne źródło lub element śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8ff11-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="8ff11-104">Te odbiorniki nie otrzymują żadnych śladów domyślnie i nie jest możliwe do pobrania tych odbiorników w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8ff11-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="8ff11-105">Detektory zidentyfikowane jako detektory udostępnione można dodać do źródeł lub śladów według nazwy.</span><span class="sxs-lookup"><span data-stu-id="8ff11-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
[<span data-ttu-id="8ff11-106">**\<>konfiguracyjne**</span><span class="sxs-lookup"><span data-stu-id="8ff11-106">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="8ff11-107">&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="8ff11-107">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="8ff11-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**</span><span class="sxs-lookup"><span data-stu-id="8ff11-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ff11-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ff11-109">Syntax</span></span>  
  
```xml  
<sharedListeners>
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ff11-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8ff11-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8ff11-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8ff11-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ff11-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8ff11-112">Attributes</span></span>  
 <span data-ttu-id="8ff11-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="8ff11-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8ff11-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8ff11-114">Child Elements</span></span>  
  
|<span data-ttu-id="8ff11-115">Element</span><span class="sxs-lookup"><span data-stu-id="8ff11-115">Element</span></span>|<span data-ttu-id="8ff11-116">Opis</span><span class="sxs-lookup"><span data-stu-id="8ff11-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ff11-117">\<dodaj></span><span class="sxs-lookup"><span data-stu-id="8ff11-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="8ff11-118">Dodaje odbiornik do `sharedListeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8ff11-118">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8ff11-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8ff11-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8ff11-120">Element</span><span class="sxs-lookup"><span data-stu-id="8ff11-120">Element</span></span>|<span data-ttu-id="8ff11-121">Opis</span><span class="sxs-lookup"><span data-stu-id="8ff11-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="8ff11-122">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ff11-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="8ff11-123">Określa element główny sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8ff11-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ff11-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ff11-124">Remarks</span></span>  
 <span data-ttu-id="8ff11-125">Dodanie odbiornika do kolekcji odbiorników udostępnionych nie czyni go aktywnym odbiornikiem.</span><span class="sxs-lookup"><span data-stu-id="8ff11-125">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="8ff11-126">Nadal musi być dodawany do źródła śledzenia lub `Listeners` śledzenia, dodając go do kolekcji dla tego elementu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8ff11-126">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="8ff11-127">Klasy detektora w .NET Framework pochodzą <xref:System.Diagnostics.TraceListener> z klasy.</span><span class="sxs-lookup"><span data-stu-id="8ff11-127">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="8ff11-128">Ten element może być używany w pliku konfiguracyjnym komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ff11-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ff11-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ff11-129">Example</span></span>  
 <span data-ttu-id="8ff11-130">W poniższym przykładzie `<sharedListeners>` pokazano, jak użyć `console` elementu, aby dodać odbiornik do `Listeners` kolekcji dla <xref:System.Diagnostics.TraceSource> i <xref:System.Diagnostics.Trace> klas.</span><span class="sxs-lookup"><span data-stu-id="8ff11-130">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="8ff11-131">Detektor śledzenia konsoli zapisuje informacje śledzenia do konsoli <xref:System.Diagnostics.TraceSource> za <xref:System.Diagnostics.Trace>pośrednictwem wywołań do jednego lub .</span><span class="sxs-lookup"><span data-stu-id="8ff11-131">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
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
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="8ff11-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ff11-132">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="8ff11-133">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="8ff11-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="8ff11-134">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="8ff11-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
