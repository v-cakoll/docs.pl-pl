---
title: '&lt;źródło&gt; — Element'
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 818324077322fffb40a192c9197efde6e8ff7591
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47231892"
---
# <a name="ltsourcegt-element"></a><span data-ttu-id="fc108-102">&lt;źródło&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="fc108-102">&lt;source&gt; Element</span></span>
<span data-ttu-id="fc108-103">Określa źródło śledzenia, który inicjuje komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fc108-103">Specifies a trace source that initiates tracing messages.</span></span>  
  
 <span data-ttu-id="fc108-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="fc108-104">\<configuration></span></span>  
<span data-ttu-id="fc108-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="fc108-105">\<system.diagnostics></span></span>  
<span data-ttu-id="fc108-106">\<źródła ></span><span class="sxs-lookup"><span data-stu-id="fc108-106">\<sources></span></span>  
<span data-ttu-id="fc108-107">\<źródło ></span><span class="sxs-lookup"><span data-stu-id="fc108-107">\<source></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc108-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc108-108">Syntax</span></span>  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc108-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fc108-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fc108-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fc108-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc108-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fc108-111">Attributes</span></span>  
  
|<span data-ttu-id="fc108-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fc108-112">Attribute</span></span>|<span data-ttu-id="fc108-113">Opis</span><span class="sxs-lookup"><span data-stu-id="fc108-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="fc108-114">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fc108-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fc108-115">Określa nazwę źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fc108-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="fc108-116">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fc108-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fc108-117">Określa nazwę wystąpienia przełącznika śledzenia w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fc108-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="fc108-118">Jeśli przełącznik nie zostanie zidentyfikowany w `<switches>` elementu, a wartość określa poziom przełącznika.</span><span class="sxs-lookup"><span data-stu-id="fc108-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="fc108-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fc108-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fc108-120">Określa typ o przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fc108-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="fc108-121">Jeśli jest obecny, typ musi być prawidłową nazwą klasy i nie może być pustym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="fc108-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="fc108-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fc108-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fc108-123">Określa wartość atrybutu specyficznymi dla źródła śledzenia identyfikowane przez <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> metodę dla tego źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fc108-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc108-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fc108-124">Child Elements</span></span>  
  
|<span data-ttu-id="fc108-125">Element</span><span class="sxs-lookup"><span data-stu-id="fc108-125">Element</span></span>|<span data-ttu-id="fc108-126">Opis</span><span class="sxs-lookup"><span data-stu-id="fc108-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc108-127">\<odbiorniki ></span><span class="sxs-lookup"><span data-stu-id="fc108-127">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|<span data-ttu-id="fc108-128">Zawiera obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów w postaci.</span><span class="sxs-lookup"><span data-stu-id="fc108-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fc108-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fc108-129">Parent Elements</span></span>  
  
|<span data-ttu-id="fc108-130">Element</span><span class="sxs-lookup"><span data-stu-id="fc108-130">Element</span></span>|<span data-ttu-id="fc108-131">Opis</span><span class="sxs-lookup"><span data-stu-id="fc108-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fc108-132">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fc108-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="fc108-133">Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fc108-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="fc108-134">Zawiera źródła śledzenia, które inicjują komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fc108-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc108-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc108-135">Remarks</span></span>  
 <span data-ttu-id="fc108-136">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fc108-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc108-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="fc108-137">Example</span></span>  
 <span data-ttu-id="fc108-138">Poniższy przykład pokazuje, jak używać `<source>` elementu do dodania źródła śledzenia `mySource` i ustaw poziom przełącznik źródła o nazwie `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="fc108-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="fc108-139">Detektor śledzenia konsoli jest dodawany, który zapisuje informacje śledzenia do konsoli.</span><span class="sxs-lookup"><span data-stu-id="fc108-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
        <switches>  
           <add name="sourceSwitch" value="Warning" />  
        </switches>    
  </system.diagnostics>   
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc108-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc108-140">See Also</span></span>  
 [<span data-ttu-id="fc108-141">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="fc108-141">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="fc108-142">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="fc108-142">Trace Switches</span></span>](../../../../../docs/framework/debug-trace-profile/trace-switches.md)
