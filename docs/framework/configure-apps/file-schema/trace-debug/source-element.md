---
title: <source> Element
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: 417722ce2f3865350158413307495e3ab435d386
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153298"
---
# <a name="source-element"></a><span data-ttu-id="4a505-102">\<source> Element</span><span class="sxs-lookup"><span data-stu-id="4a505-102">\<source> Element</span></span>
<span data-ttu-id="4a505-103">Określa źródło śledzenia, które inicjuje komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4a505-103">Specifies a trace source that initiates tracing messages.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<source>**

## <a name="syntax"></a><span data-ttu-id="4a505-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a505-104">Syntax</span></span>  
  
```xml  
<source>
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a505-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4a505-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4a505-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4a505-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a505-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4a505-107">Attributes</span></span>  
  
|<span data-ttu-id="4a505-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4a505-108">Attribute</span></span>|<span data-ttu-id="4a505-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4a505-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="4a505-110">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4a505-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4a505-111">Określa nazwę źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4a505-111">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="4a505-112">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4a505-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4a505-113">Określa nazwę wystąpienia przełącznika śledzenia w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4a505-113">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="4a505-114">Jeśli przełącznik nie zostanie zidentyfikowany w `<switches>` elemencie, wartość określa poziom przełącznika.</span><span class="sxs-lookup"><span data-stu-id="4a505-114">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="4a505-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4a505-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4a505-116">Określa typ przełącznika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4a505-116">Specifies the type of the trace switch.</span></span> <span data-ttu-id="4a505-117">Jeśli jest obecny, typ musi być prawidłową nazwą klasy i nie może być pustym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="4a505-117">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="4a505-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4a505-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4a505-119">Określa wartość dla atrybutu specyficznego dla źródła śledzenia identyfikowanego przez <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> metodę dla tego źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4a505-119">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a505-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4a505-120">Child Elements</span></span>  
  
|<span data-ttu-id="4a505-121">Element</span><span class="sxs-lookup"><span data-stu-id="4a505-121">Element</span></span>|<span data-ttu-id="4a505-122">Opis</span><span class="sxs-lookup"><span data-stu-id="4a505-122">Description</span></span>|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-source.md)|<span data-ttu-id="4a505-123">Zawiera detektory, które zbierają, przechowują i rozsyłają komunikaty.</span><span class="sxs-lookup"><span data-stu-id="4a505-123">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a505-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4a505-124">Parent Elements</span></span>  
  
|<span data-ttu-id="4a505-125">Element</span><span class="sxs-lookup"><span data-stu-id="4a505-125">Element</span></span>|<span data-ttu-id="4a505-126">Opis</span><span class="sxs-lookup"><span data-stu-id="4a505-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4a505-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4a505-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4a505-128">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4a505-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="4a505-129">Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4a505-129">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a505-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a505-130">Remarks</span></span>  
 <span data-ttu-id="4a505-131">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4a505-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a505-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="4a505-132">Example</span></span>  
 <span data-ttu-id="4a505-133">Poniższy przykład pokazuje, jak użyć elementu, `<source>` Aby dodać Źródło śledzenia `mySource` i ustawić poziom dla przełącznika źródła o nazwie `sourceSwitch` .</span><span class="sxs-lookup"><span data-stu-id="4a505-133">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="4a505-134">Dodano odbiornik śledzenia konsoli, który zapisuje informacje o śledzeniu do konsoli.</span><span class="sxs-lookup"><span data-stu-id="4a505-134">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4a505-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a505-135">See also</span></span>

- [<span data-ttu-id="4a505-136">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="4a505-136">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4a505-137">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="4a505-137">Trace Switches</span></span>](../../../debug-trace-profile/trace-switches.md)
