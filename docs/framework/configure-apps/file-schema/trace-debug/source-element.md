---
title: <source>, element
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: 417722ce2f3865350158413307495e3ab435d386
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153298"
---
# <a name="source-element"></a><span data-ttu-id="d2fe9-102">\<element> źródłowego</span><span class="sxs-lookup"><span data-stu-id="d2fe9-102">\<source> Element</span></span>
<span data-ttu-id="d2fe9-103">Określa źródło śledzenia, które inicjuje śledzenie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d2fe9-103">Specifies a trace source that initiates tracing messages.</span></span>  

<span data-ttu-id="d2fe9-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d2fe9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d2fe9-105">&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="d2fe9-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="d2fe9-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<źródeł>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="d2fe9-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="d2fe9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>źródłowe**</span><span class="sxs-lookup"><span data-stu-id="d2fe9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<source>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d2fe9-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2fe9-108">Syntax</span></span>  
  
```xml  
<source>
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2fe9-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d2fe9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d2fe9-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d2fe9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2fe9-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d2fe9-111">Attributes</span></span>  
  
|<span data-ttu-id="d2fe9-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d2fe9-112">Attribute</span></span>|<span data-ttu-id="d2fe9-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d2fe9-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="d2fe9-114">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d2fe9-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d2fe9-115">Określa nazwę źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d2fe9-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="d2fe9-116">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d2fe9-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d2fe9-117">Określa nazwę wystąpienia przełącznika śledzenia w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d2fe9-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="d2fe9-118">Jeśli przełącznik nie jest identyfikowany w elemencie, `<switches>` wartość określa poziom przełącznika.</span><span class="sxs-lookup"><span data-stu-id="d2fe9-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="d2fe9-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d2fe9-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d2fe9-120">Określa typ przełącznika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d2fe9-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="d2fe9-121">Jeśli jest obecny, typ musi być prawidłową nazwą klasy i nie może być pustym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="d2fe9-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="d2fe9-122">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d2fe9-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d2fe9-123">Określa wartość atrybutu specyficznego dla źródła śledzenia <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> identyfikowanego przez metodę dla tego źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d2fe9-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2fe9-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d2fe9-124">Child Elements</span></span>  
  
|<span data-ttu-id="d2fe9-125">Element</span><span class="sxs-lookup"><span data-stu-id="d2fe9-125">Element</span></span>|<span data-ttu-id="d2fe9-126">Opis</span><span class="sxs-lookup"><span data-stu-id="d2fe9-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2fe9-127">\<słuchacze></span><span class="sxs-lookup"><span data-stu-id="d2fe9-127">\<listeners></span></span>](listeners-element-for-source.md)|<span data-ttu-id="d2fe9-128">Zawiera odbiorniki, które zbierają, przechowują i rozsyłają wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d2fe9-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d2fe9-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d2fe9-129">Parent Elements</span></span>  
  
|<span data-ttu-id="d2fe9-130">Element</span><span class="sxs-lookup"><span data-stu-id="d2fe9-130">Element</span></span>|<span data-ttu-id="d2fe9-131">Opis</span><span class="sxs-lookup"><span data-stu-id="d2fe9-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d2fe9-132">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d2fe9-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d2fe9-133">Określa odbiorniki śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, na którym ustawiony jest przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d2fe9-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="d2fe9-134">Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d2fe9-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2fe9-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2fe9-135">Remarks</span></span>  
 <span data-ttu-id="d2fe9-136">Ten element może być używany w pliku konfiguracyjnym komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d2fe9-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2fe9-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2fe9-137">Example</span></span>  
 <span data-ttu-id="d2fe9-138">W poniższym przykładzie `<source>` pokazano, jak użyć `mySource` elementu, aby dodać źródło `sourceSwitch`śledzenia i ustawić poziom dla przełącznika źródłowego o nazwie .</span><span class="sxs-lookup"><span data-stu-id="d2fe9-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="d2fe9-139">Dodano odbiornik śledzenia konsoli, który zapisuje informacje śledzenia do konsoli.</span><span class="sxs-lookup"><span data-stu-id="d2fe9-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d2fe9-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2fe9-140">See also</span></span>

- [<span data-ttu-id="d2fe9-141">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="d2fe9-141">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d2fe9-142">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="d2fe9-142">Trace Switches</span></span>](../../../debug-trace-profile/trace-switches.md)
