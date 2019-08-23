---
title: <remove>Element dla <listeners> elementu<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: edd27dd262004aead7db4d81db8ecab0e831dac1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926994"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="5f628-102">\<Usuń element > dla \<odbiorników > \<dla źródła ></span><span class="sxs-lookup"><span data-stu-id="5f628-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="5f628-103">Usuwa odbiornik z `Listeners` kolekcji dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5f628-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="5f628-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5f628-104">\<configuration></span></span>  
<span data-ttu-id="5f628-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="5f628-105">\<system.diagnostics></span></span>  
<span data-ttu-id="5f628-106">\<> źródeł</span><span class="sxs-lookup"><span data-stu-id="5f628-106">\<sources></span></span>  
<span data-ttu-id="5f628-107">\<> źródłowa</span><span class="sxs-lookup"><span data-stu-id="5f628-107">\<source></span></span>  
<span data-ttu-id="5f628-108">\<> odbiorników</span><span class="sxs-lookup"><span data-stu-id="5f628-108">\<listeners></span></span>  
<span data-ttu-id="5f628-109">\<remove></span><span class="sxs-lookup"><span data-stu-id="5f628-109">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f628-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f628-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f628-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5f628-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5f628-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5f628-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f628-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5f628-113">Attributes</span></span>  
  
|<span data-ttu-id="5f628-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5f628-114">Attribute</span></span>|<span data-ttu-id="5f628-115">Opis</span><span class="sxs-lookup"><span data-stu-id="5f628-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="5f628-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="5f628-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="5f628-117">Nazwa odbiornika, który ma zostać usunięty z `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5f628-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f628-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5f628-118">Child Elements</span></span>  
 <span data-ttu-id="5f628-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="5f628-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5f628-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5f628-120">Parent Elements</span></span>  
  
|<span data-ttu-id="5f628-121">Element</span><span class="sxs-lookup"><span data-stu-id="5f628-121">Element</span></span>|<span data-ttu-id="5f628-122">Opis</span><span class="sxs-lookup"><span data-stu-id="5f628-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5f628-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5f628-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="5f628-124">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5f628-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="5f628-125">Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5f628-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="5f628-126">Określa źródło śledzenia, które inicjuje komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5f628-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="5f628-127">Określa detektory, które zbierają, przechowują i rozsyłają komunikaty.</span><span class="sxs-lookup"><span data-stu-id="5f628-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f628-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f628-128">Remarks</span></span>  
 <span data-ttu-id="5f628-129">Element usuwa określony odbiornik `Listeners` z kolekcji dla źródła śledzenia. `<remove>`</span><span class="sxs-lookup"><span data-stu-id="5f628-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="5f628-130">`Listeners` Można usunąć element z kolekcji dla źródła śledzenia programowo, <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> wywołując metodę <xref:System.Diagnostics.TraceSource> we <xref:System.Diagnostics.TraceSource.Listeners%2A> właściwości wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5f628-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="5f628-131">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5f628-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f628-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f628-132">Example</span></span>  
 <span data-ttu-id="5f628-133">Poniższy przykład pokazuje, `<remove>` jak używać elementu przed użyciem elementu, `<add>` aby `Listeners` dodać odbiornik `console` do kolekcji dla źródła `TraceSourceApp`śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5f628-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5f628-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f628-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="5f628-135">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="5f628-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5f628-136">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="5f628-136">\<clear></span></span>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="5f628-137">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="5f628-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
