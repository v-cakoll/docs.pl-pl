---
title: <remove> — Element do <listeners> dla <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 522319c64ddff6eb6872584937d540a8955b7c8f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260336"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="b0b20-102">\<Usuń >, Element dla \<odbiorników > dla \<źródła ></span><span class="sxs-lookup"><span data-stu-id="b0b20-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="b0b20-103">Usuwa odbiornik z `Listeners` kolekcję dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b0b20-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="b0b20-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="b0b20-104">\<configuration></span></span>  
<span data-ttu-id="b0b20-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="b0b20-105">\<system.diagnostics></span></span>  
<span data-ttu-id="b0b20-106">\<źródła ></span><span class="sxs-lookup"><span data-stu-id="b0b20-106">\<sources></span></span>  
<span data-ttu-id="b0b20-107">\<source></span><span class="sxs-lookup"><span data-stu-id="b0b20-107">\<source></span></span>  
<span data-ttu-id="b0b20-108">\<listeners></span><span class="sxs-lookup"><span data-stu-id="b0b20-108">\<listeners></span></span>  
<span data-ttu-id="b0b20-109">\<remove></span><span class="sxs-lookup"><span data-stu-id="b0b20-109">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0b20-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0b20-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0b20-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b0b20-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b0b20-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b0b20-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0b20-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b0b20-113">Attributes</span></span>  
  
|<span data-ttu-id="b0b20-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b0b20-114">Attribute</span></span>|<span data-ttu-id="b0b20-115">Opis</span><span class="sxs-lookup"><span data-stu-id="b0b20-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="b0b20-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="b0b20-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="b0b20-117">Nazwa odbiornika do usunięcia z `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b0b20-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0b20-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b0b20-118">Child Elements</span></span>  
 <span data-ttu-id="b0b20-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="b0b20-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b0b20-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b0b20-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b0b20-121">Element</span><span class="sxs-lookup"><span data-stu-id="b0b20-121">Element</span></span>|<span data-ttu-id="b0b20-122">Opis</span><span class="sxs-lookup"><span data-stu-id="b0b20-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b0b20-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b0b20-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b0b20-124">Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b0b20-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="b0b20-125">Zawiera źródła śledzenia, które inicjują komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b0b20-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="b0b20-126">Określa źródło śledzenia, który inicjuje komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b0b20-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="b0b20-127">Określa obiektów nasłuchujących zbierać, przechowywać i kierowanie komunikatów w postaci.</span><span class="sxs-lookup"><span data-stu-id="b0b20-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0b20-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0b20-128">Remarks</span></span>  
 <span data-ttu-id="b0b20-129">`<remove>` Elementu usuwa określony odbiornik z `Listeners` kolekcję dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b0b20-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="b0b20-130">Możesz usunąć element z `Listeners` kolekcję dla źródła śledzenia, programowo przez wywołanie metody <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> metody <xref:System.Diagnostics.TraceSource.Listeners%2A> właściwość <xref:System.Diagnostics.TraceSource> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b0b20-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="b0b20-131">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b0b20-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0b20-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0b20-132">Example</span></span>  
 <span data-ttu-id="b0b20-133">Poniższy przykład pokazuje, jak używać `<remove>` element przed użyciem `<add>` elementu do dodania odbiornika `console` do `Listeners` kolekcji dla źródła śledzenia `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="b0b20-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b0b20-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0b20-134">See also</span></span>
- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="b0b20-135">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="b0b20-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="b0b20-136">\<clear></span><span class="sxs-lookup"><span data-stu-id="b0b20-136">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="b0b20-137">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="b0b20-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
