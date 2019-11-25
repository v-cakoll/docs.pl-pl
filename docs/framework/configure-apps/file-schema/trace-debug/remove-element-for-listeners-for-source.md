---
title: Element <remove> dla <listeners> <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 75db45d4e868ce88e030ec6a43c8bdaf788a1102
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088850"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="1480e-102">\<usunąć elementu > dla odbiorników \<> dla \<źródła ></span><span class="sxs-lookup"><span data-stu-id="1480e-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="1480e-103">Usuwa odbiornik z kolekcji `Listeners` dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1480e-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="1480e-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="1480e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1480e-105">&nbsp;&nbsp;[ **\<system. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="1480e-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="1480e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sources**](sources-element.md) ></span><span class="sxs-lookup"><span data-stu-id="1480e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="1480e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**Source**](source-element.md) ></span><span class="sxs-lookup"><span data-stu-id="1480e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="1480e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<odbiorników**](listeners-element-for-source.md) ></span><span class="sxs-lookup"><span data-stu-id="1480e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="1480e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<usuń >**</span><span class="sxs-lookup"><span data-stu-id="1480e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="1480e-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="1480e-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1480e-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1480e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1480e-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1480e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1480e-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1480e-113">Attributes</span></span>  
  
|<span data-ttu-id="1480e-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1480e-114">Attribute</span></span>|<span data-ttu-id="1480e-115">Opis</span><span class="sxs-lookup"><span data-stu-id="1480e-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="1480e-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="1480e-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="1480e-117">Nazwa odbiornika, który ma zostać usunięty z kolekcji `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="1480e-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1480e-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1480e-118">Child Elements</span></span>  
 <span data-ttu-id="1480e-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="1480e-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1480e-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1480e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1480e-121">Element</span><span class="sxs-lookup"><span data-stu-id="1480e-121">Element</span></span>|<span data-ttu-id="1480e-122">Opis</span><span class="sxs-lookup"><span data-stu-id="1480e-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1480e-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1480e-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="1480e-124">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1480e-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="1480e-125">Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1480e-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="1480e-126">Określa źródło śledzenia, które inicjuje komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1480e-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="1480e-127">Określa detektory, które zbierają, przechowują i rozsyłają komunikaty.</span><span class="sxs-lookup"><span data-stu-id="1480e-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1480e-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1480e-128">Remarks</span></span>  
 <span data-ttu-id="1480e-129">Element `<remove>` usuwa określony odbiornik z kolekcji `Listeners` dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1480e-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="1480e-130">Można usunąć element z kolekcji `Listeners` dla źródła śledzenia programowo, wywołując metodę <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> na właściwości <xref:System.Diagnostics.TraceSource.Listeners%2A> wystąpienia <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="1480e-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="1480e-131">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1480e-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1480e-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="1480e-132">Example</span></span>  
 <span data-ttu-id="1480e-133">Poniższy przykład pokazuje, jak używać elementu `<remove>` przed użyciem elementu `<add>` do dodawania `console` odbiornika do kolekcji `Listeners` dla źródła śledzenia `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="1480e-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1480e-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1480e-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="1480e-135">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="1480e-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1480e-136">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="1480e-136">\<clear></span></span>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="1480e-137">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="1480e-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
