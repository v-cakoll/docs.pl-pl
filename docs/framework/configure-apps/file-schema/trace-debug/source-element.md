---
title: <source> Element
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: c4f7e31422ccd8129599db1120f9b0cb327d9319
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697211"
---
# <a name="source-element"></a><span data-ttu-id="369ab-102">\<source > elementu</span><span class="sxs-lookup"><span data-stu-id="369ab-102">\<source> Element</span></span>
<span data-ttu-id="369ab-103">Określa źródło śledzenia, które inicjuje komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="369ab-103">Specifies a trace source that initiates tracing messages.</span></span>  
  
[<span data-ttu-id="369ab-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="369ab-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="369ab-105">&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="369ab-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="369ab-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sources >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="369ab-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="369ab-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<source >**</span><span class="sxs-lookup"><span data-stu-id="369ab-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<source>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="369ab-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="369ab-108">Syntax</span></span>  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="369ab-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="369ab-109">Attributes and Elements</span></span>  
 <span data-ttu-id="369ab-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="369ab-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="369ab-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="369ab-111">Attributes</span></span>  
  
|<span data-ttu-id="369ab-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="369ab-112">Attribute</span></span>|<span data-ttu-id="369ab-113">Opis</span><span class="sxs-lookup"><span data-stu-id="369ab-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="369ab-114">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="369ab-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="369ab-115">Określa nazwę źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="369ab-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="369ab-116">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="369ab-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="369ab-117">Określa nazwę wystąpienia przełącznika śledzenia w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="369ab-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="369ab-118">Jeśli przełącznik nie zostanie zidentyfikowany w elemencie `<switches>`, wartość określa poziom przełącznika.</span><span class="sxs-lookup"><span data-stu-id="369ab-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="369ab-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="369ab-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="369ab-120">Określa typ przełącznika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="369ab-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="369ab-121">Jeśli jest obecny, typ musi być prawidłową nazwą klasy i nie może być pustym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="369ab-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="369ab-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="369ab-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="369ab-123">Określa wartość dla atrybutu specyficznego dla źródła śledzenia identyfikowanego przez metodę <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> dla tego źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="369ab-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="369ab-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="369ab-124">Child Elements</span></span>  
  
|<span data-ttu-id="369ab-125">Element</span><span class="sxs-lookup"><span data-stu-id="369ab-125">Element</span></span>|<span data-ttu-id="369ab-126">Opis</span><span class="sxs-lookup"><span data-stu-id="369ab-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="369ab-127">@no__t — 1listeners ></span><span class="sxs-lookup"><span data-stu-id="369ab-127">\<listeners></span></span>](listeners-element-for-source.md)|<span data-ttu-id="369ab-128">Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty.</span><span class="sxs-lookup"><span data-stu-id="369ab-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="369ab-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="369ab-129">Parent Elements</span></span>  
  
|<span data-ttu-id="369ab-130">Element</span><span class="sxs-lookup"><span data-stu-id="369ab-130">Element</span></span>|<span data-ttu-id="369ab-131">Opis</span><span class="sxs-lookup"><span data-stu-id="369ab-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="369ab-132">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="369ab-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="369ab-133">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="369ab-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="369ab-134">Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="369ab-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="369ab-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="369ab-135">Remarks</span></span>  
 <span data-ttu-id="369ab-136">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="369ab-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="369ab-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="369ab-137">Example</span></span>  
 <span data-ttu-id="369ab-138">Poniższy przykład pokazuje, jak za pomocą elementu `<source>` dodać Źródło śledzenia `mySource` i ustawić poziom dla przełącznika źródłowego o nazwie `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="369ab-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="369ab-139">Dodano odbiornik śledzenia konsoli, który zapisuje informacje o śledzeniu do konsoli.</span><span class="sxs-lookup"><span data-stu-id="369ab-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="369ab-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="369ab-140">See also</span></span>

- [<span data-ttu-id="369ab-141">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="369ab-141">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="369ab-142">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="369ab-142">Trace Switches</span></span>](../../../debug-trace-profile/trace-switches.md)
