---
title: <sharedListeners> Element
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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153324"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="ba11b-102">\<sharedListeners> Element</span><span class="sxs-lookup"><span data-stu-id="ba11b-102">\<sharedListeners> Element</span></span>
<span data-ttu-id="ba11b-103">Zawiera detektory, do których może odwoływać się każdy element źródłowy lub Trace.</span><span class="sxs-lookup"><span data-stu-id="ba11b-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="ba11b-104">Te odbiorniki nie odbierają domyślnie żadnych śladów i nie można ich pobrać w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ba11b-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="ba11b-105">Odbiorniki identyfikowane jako odbiorniki udostępnione mogą być dodawane do źródeł lub śladów według nazwy.</span><span class="sxs-lookup"><span data-stu-id="ba11b-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**  
  
## <a name="syntax"></a><span data-ttu-id="ba11b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba11b-106">Syntax</span></span>  
  
```xml  
<sharedListeners>
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba11b-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ba11b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="ba11b-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ba11b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba11b-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ba11b-109">Attributes</span></span>  
 <span data-ttu-id="ba11b-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="ba11b-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ba11b-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ba11b-111">Child Elements</span></span>  
  
|<span data-ttu-id="ba11b-112">Element</span><span class="sxs-lookup"><span data-stu-id="ba11b-112">Element</span></span>|<span data-ttu-id="ba11b-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ba11b-113">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="ba11b-114">Dodaje odbiornik do `sharedListeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ba11b-114">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ba11b-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ba11b-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ba11b-116">Element</span><span class="sxs-lookup"><span data-stu-id="ba11b-116">Element</span></span>|<span data-ttu-id="ba11b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ba11b-117">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="ba11b-118">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ba11b-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="ba11b-119">Określa element główny dla sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ba11b-119">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba11b-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ba11b-120">Remarks</span></span>  
 <span data-ttu-id="ba11b-121">Dodanie odbiornika do kolekcji udostępnionych odbiorników nie powoduje aktywnego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="ba11b-121">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="ba11b-122">Nadal musi być dodany do źródła śledzenia lub śledzenia przez dodanie go do `Listeners` kolekcji dla tego elementu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ba11b-122">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="ba11b-123">Klasy odbiornika w .NET Framework pochodne od <xref:System.Diagnostics.TraceListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="ba11b-123">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="ba11b-124">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ba11b-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba11b-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="ba11b-125">Example</span></span>  
 <span data-ttu-id="ba11b-126">Poniższy przykład pokazuje, jak użyć elementu, `<sharedListeners>` Aby dodać odbiornik `console` do `Listeners` kolekcji dla <xref:System.Diagnostics.TraceSource> <xref:System.Diagnostics.Trace> klas i.</span><span class="sxs-lookup"><span data-stu-id="ba11b-126">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="ba11b-127">Odbiornik śledzenia konsoli zapisuje informacje o śledzeniu do konsoli za pomocą wywołań do <xref:System.Diagnostics.TraceSource> lub <xref:System.Diagnostics.Trace> .</span><span class="sxs-lookup"><span data-stu-id="ba11b-127">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ba11b-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ba11b-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="ba11b-129">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="ba11b-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ba11b-130">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="ba11b-130">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
