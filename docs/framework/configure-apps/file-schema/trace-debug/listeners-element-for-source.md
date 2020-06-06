---
title: <listeners>, element dla <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 0eee325e01b41a15a19e4f40f479596f9d70f73b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153415"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="117dd-102">\<listeners>, element dla \<source></span><span class="sxs-lookup"><span data-stu-id="117dd-102">\<listeners> Element for \<source></span></span>
<span data-ttu-id="117dd-103">Dodaje lub usuwa detektory w <xref:System.Diagnostics.TraceSource.Listeners%2A> kolekcji dla elementu <xref:System.Diagnostics.TraceSource> .</span><span class="sxs-lookup"><span data-stu-id="117dd-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="117dd-104">Odbiornik kieruje dane wyjściowe śledzenia do odpowiedniego obiektu docelowego, takiego jak dziennik, okno lub plik tekstowy.</span><span class="sxs-lookup"><span data-stu-id="117dd-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**  
  
## <a name="syntax"></a><span data-ttu-id="117dd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="117dd-105">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="117dd-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="117dd-106">Attributes and Elements</span></span>  
 <span data-ttu-id="117dd-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="117dd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="117dd-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="117dd-108">Attributes</span></span>  
 <span data-ttu-id="117dd-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="117dd-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="117dd-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="117dd-110">Child Elements</span></span>  
  
|<span data-ttu-id="117dd-111">Element</span><span class="sxs-lookup"><span data-stu-id="117dd-111">Element</span></span>|<span data-ttu-id="117dd-112">Opis</span><span class="sxs-lookup"><span data-stu-id="117dd-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|<span data-ttu-id="117dd-113">Dodaje odbiornik do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="117dd-113">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="117dd-114">Usuwa odbiornik z `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="117dd-114">Removes a listener from the `Listeners` collection.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="117dd-115">Czyści `Listeners` kolekcję dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="117dd-115">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="117dd-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="117dd-116">Parent Elements</span></span>  
  
|<span data-ttu-id="117dd-117">Element</span><span class="sxs-lookup"><span data-stu-id="117dd-117">Element</span></span>|<span data-ttu-id="117dd-118">Opis</span><span class="sxs-lookup"><span data-stu-id="117dd-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="117dd-119">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="117dd-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="117dd-120">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="117dd-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="117dd-121">Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="117dd-121">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="117dd-122">Określa źródło śledzenia, które inicjuje komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="117dd-122">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="117dd-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="117dd-123">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="117dd-124">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="117dd-124">Configuration File</span></span>  
 <span data-ttu-id="117dd-125">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="117dd-125">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="117dd-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="117dd-126">Example</span></span>  
 <span data-ttu-id="117dd-127">Poniższy przykład pokazuje, jak użyć elementu, `<listeners>` Aby dodać odbiornik śledzenia konsoli do `mySource` źródła i usunąć domyślny odbiornik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="117dd-127">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="117dd-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="117dd-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="117dd-129">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="117dd-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="117dd-130">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="117dd-130">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
