---
title: Element <remove> dla <listeners> dla <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 4a11308278f755ec8271477352d91d8797d105c5
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699498"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="0b161-102">\<remove > elementu \<listeners > dla @no__t 2source ></span><span class="sxs-lookup"><span data-stu-id="0b161-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="0b161-103">Usuwa odbiornik z kolekcji `Listeners` dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0b161-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
[<span data-ttu-id="0b161-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="0b161-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="0b161-105">&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="0b161-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="0b161-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sources >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="0b161-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="0b161-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<source >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="0b161-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>  
<span data-ttu-id="0b161-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0listeners >** ](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="0b161-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>  
<span data-ttu-id="0b161-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 **&nbsp;1remove >**</span><span class="sxs-lookup"><span data-stu-id="0b161-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b161-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b161-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b161-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0b161-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0b161-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0b161-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b161-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0b161-113">Attributes</span></span>  
  
|<span data-ttu-id="0b161-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0b161-114">Attribute</span></span>|<span data-ttu-id="0b161-115">Opis</span><span class="sxs-lookup"><span data-stu-id="0b161-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="0b161-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="0b161-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="0b161-117">Nazwa odbiornika, który ma zostać usunięty z kolekcji `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="0b161-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b161-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0b161-118">Child Elements</span></span>  
 <span data-ttu-id="0b161-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="0b161-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0b161-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0b161-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0b161-121">Element</span><span class="sxs-lookup"><span data-stu-id="0b161-121">Element</span></span>|<span data-ttu-id="0b161-122">Opis</span><span class="sxs-lookup"><span data-stu-id="0b161-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0b161-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0b161-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="0b161-124">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0b161-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="0b161-125">Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0b161-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="0b161-126">Określa źródło śledzenia, które inicjuje komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0b161-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="0b161-127">Określa detektory, które zbierają, przechowują i rozsyłają komunikaty.</span><span class="sxs-lookup"><span data-stu-id="0b161-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b161-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0b161-128">Remarks</span></span>  
 <span data-ttu-id="0b161-129">Element `<remove>` usuwa określony odbiornik z kolekcji `Listeners` dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0b161-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="0b161-130">Można usunąć element z kolekcji `Listeners` dla źródła śledzenia programowo poprzez wywołanie metody <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> na właściwości <xref:System.Diagnostics.TraceSource.Listeners%2A> wystąpienia <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="0b161-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="0b161-131">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0b161-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b161-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="0b161-132">Example</span></span>  
 <span data-ttu-id="0b161-133">Poniższy przykład pokazuje, jak używać elementu `<remove>` przed użyciem elementu `<add>`, aby dodać odbiornik `console` do kolekcji `Listeners` dla źródła śledzenia `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="0b161-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"   
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="0b161-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b161-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="0b161-135">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="0b161-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0b161-136">@no__t — 1clear ></span><span class="sxs-lookup"><span data-stu-id="0b161-136">\<clear></span></span>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="0b161-137">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="0b161-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
