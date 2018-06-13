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
manager: markl
ms.openlocfilehash: b7c2a71b129a0ad7d1c2a72b18b8a69a111f9495
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752575"
---
# <a name="ltsourcegt-element"></a><span data-ttu-id="2454a-102">&lt;źródło&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="2454a-102">&lt;source&gt; Element</span></span>
<span data-ttu-id="2454a-103">Określa źródło śledzenia, który inicjuje śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2454a-103">Specifies a trace source that initiates tracing messages.</span></span>  
  
 <span data-ttu-id="2454a-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="2454a-104">\<configuration></span></span>  
<span data-ttu-id="2454a-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="2454a-105">\<system.diagnostics></span></span>  
<span data-ttu-id="2454a-106">\<źródeł ></span><span class="sxs-lookup"><span data-stu-id="2454a-106">\<sources></span></span>  
<span data-ttu-id="2454a-107">\<źródło ></span><span class="sxs-lookup"><span data-stu-id="2454a-107">\<source></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2454a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="2454a-108">Syntax</span></span>  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2454a-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2454a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2454a-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2454a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2454a-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2454a-111">Attributes</span></span>  
  
|<span data-ttu-id="2454a-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2454a-112">Attribute</span></span>|<span data-ttu-id="2454a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="2454a-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="2454a-114">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2454a-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2454a-115">Określa nazwę źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2454a-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="2454a-116">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2454a-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2454a-117">Określa nazwę wystąpienia przełącznika śledzenia w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2454a-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="2454a-118">Jeśli przełącznik nie zostanie zidentyfikowana w `<switches>` elementu, wartość określa poziom przełącznika.</span><span class="sxs-lookup"><span data-stu-id="2454a-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="2454a-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2454a-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2454a-120">Określa typ przełącznika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2454a-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="2454a-121">Jeśli jest obecny, typ musi być prawidłową nazwą klasy i nie może być pustym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="2454a-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="2454a-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2454a-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2454a-123">Określa wartość atrybutu określonego źródła śledzenia identyfikowane przez <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> metodę dla tego źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2454a-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2454a-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2454a-124">Child Elements</span></span>  
  
|<span data-ttu-id="2454a-125">Element</span><span class="sxs-lookup"><span data-stu-id="2454a-125">Element</span></span>|<span data-ttu-id="2454a-126">Opis</span><span class="sxs-lookup"><span data-stu-id="2454a-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2454a-127">\<obiekty nasłuchujące ></span><span class="sxs-lookup"><span data-stu-id="2454a-127">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|<span data-ttu-id="2454a-128">Zawiera nasłuchujących zbierania, przechowywania i kierowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2454a-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2454a-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2454a-129">Parent Elements</span></span>  
  
|<span data-ttu-id="2454a-130">Element</span><span class="sxs-lookup"><span data-stu-id="2454a-130">Element</span></span>|<span data-ttu-id="2454a-131">Opis</span><span class="sxs-lookup"><span data-stu-id="2454a-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2454a-132">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2454a-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="2454a-133">Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2454a-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="2454a-134">Zawiera źródła śledzenia, które inicjują śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2454a-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2454a-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2454a-135">Remarks</span></span>  
 <span data-ttu-id="2454a-136">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2454a-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2454a-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="2454a-137">Example</span></span>  
 <span data-ttu-id="2454a-138">Poniższy przykład przedstawia użycie `<source>` elementu do dodania źródła śledzenia `mySource` i ustaw poziom przełącznik źródła o nazwie `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="2454a-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="2454a-139">Odbiornik śledzenia konsoli są dodawane który zapisuje informacje śledzenia do konsoli.</span><span class="sxs-lookup"><span data-stu-id="2454a-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2454a-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2454a-140">See Also</span></span>  
 [<span data-ttu-id="2454a-141">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="2454a-141">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="2454a-142">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="2454a-142">Trace Switches</span></span>](../../../../../docs/framework/debug-trace-profile/trace-switches.md)
