---
title: <remove>Element <listeners> dla<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 657e6db2af9b99b3bbf03afc6aab02c58a830f2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153338"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="feea2-102">\<usuń element> dla \<> słuchaczy do \<> źródłowego</span><span class="sxs-lookup"><span data-stu-id="feea2-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="feea2-103">Usuwa odbiornik z kolekcji `Listeners` dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="feea2-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="feea2-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="feea2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="feea2-105">&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="feea2-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="feea2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<źródeł>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="feea2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="feea2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>źródłowe**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="feea2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="feea2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<słuchacze>**](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="feea2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="feea2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<usuń>**</span><span class="sxs-lookup"><span data-stu-id="feea2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="feea2-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="feea2-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="feea2-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="feea2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="feea2-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="feea2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="feea2-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="feea2-113">Attributes</span></span>  
  
|<span data-ttu-id="feea2-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="feea2-114">Attribute</span></span>|<span data-ttu-id="feea2-115">Opis</span><span class="sxs-lookup"><span data-stu-id="feea2-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="feea2-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="feea2-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="feea2-117">Nazwa odbiornika do usunięcia z `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="feea2-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="feea2-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="feea2-118">Child Elements</span></span>  
 <span data-ttu-id="feea2-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="feea2-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="feea2-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="feea2-120">Parent Elements</span></span>  
  
|<span data-ttu-id="feea2-121">Element</span><span class="sxs-lookup"><span data-stu-id="feea2-121">Element</span></span>|<span data-ttu-id="feea2-122">Opis</span><span class="sxs-lookup"><span data-stu-id="feea2-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="feea2-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="feea2-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="feea2-124">Określa odbiorniki śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, na którym ustawiony jest przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="feea2-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="feea2-125">Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="feea2-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="feea2-126">Określa źródło śledzenia, które inicjuje śledzenie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="feea2-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="feea2-127">Określa odbiorniki, które zbierają, przechowują i rozsyłają wiadomości.</span><span class="sxs-lookup"><span data-stu-id="feea2-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="feea2-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="feea2-128">Remarks</span></span>  
 <span data-ttu-id="feea2-129">Element `<remove>` usuwa określonego odbiornika `Listeners` z kolekcji dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="feea2-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="feea2-130">Można usunąć element z `Listeners` kolekcji dla źródła śledzenia programowo <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> wywołując <xref:System.Diagnostics.TraceSource.Listeners%2A> metodę <xref:System.Diagnostics.TraceSource> na właściwości wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="feea2-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="feea2-131">Ten element może być używany w pliku konfiguracyjnym komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="feea2-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="feea2-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="feea2-132">Example</span></span>  
 <span data-ttu-id="feea2-133">W poniższym przykładzie `<remove>` pokazano, jak `<add>` użyć elementu przed `console` użyciem elementu, aby dodać odbiornika do `Listeners` kolekcji dla źródła `TraceSourceApp`śledzenia .</span><span class="sxs-lookup"><span data-stu-id="feea2-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="feea2-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="feea2-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="feea2-135">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="feea2-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="feea2-136">\<wyraźne></span><span class="sxs-lookup"><span data-stu-id="feea2-136">\<clear></span></span>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="feea2-137">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="feea2-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
