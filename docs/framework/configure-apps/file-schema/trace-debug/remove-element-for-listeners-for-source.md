---
title: "&lt;Usuń&gt; elementu &lt;odbiorników&gt; dla &lt;źródła&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: b983c5eb80f958098b6991970559d077b97a0759
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="4ccfd-102">&lt;Usuń&gt; elementu &lt;odbiorników&gt; dla &lt;źródła&gt;</span><span class="sxs-lookup"><span data-stu-id="4ccfd-102">&lt;remove&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="4ccfd-103">Usuwa odbiornik z `Listeners` kolekcji źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4ccfd-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="4ccfd-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="4ccfd-104">\<configuration></span></span>  
<span data-ttu-id="4ccfd-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="4ccfd-105">\<system.diagnostics></span></span>  
<span data-ttu-id="4ccfd-106">\<źródeł ></span><span class="sxs-lookup"><span data-stu-id="4ccfd-106">\<sources></span></span>  
<span data-ttu-id="4ccfd-107">\<źródło ></span><span class="sxs-lookup"><span data-stu-id="4ccfd-107">\<source></span></span>  
<span data-ttu-id="4ccfd-108">\<obiekty nasłuchujące ></span><span class="sxs-lookup"><span data-stu-id="4ccfd-108">\<listeners></span></span>  
<span data-ttu-id="4ccfd-109">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="4ccfd-109">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ccfd-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ccfd-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ccfd-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4ccfd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4ccfd-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4ccfd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ccfd-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4ccfd-113">Attributes</span></span>  
  
|<span data-ttu-id="4ccfd-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4ccfd-114">Attribute</span></span>|<span data-ttu-id="4ccfd-115">Opis</span><span class="sxs-lookup"><span data-stu-id="4ccfd-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="4ccfd-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="4ccfd-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="4ccfd-117">Nazwa odbiornika do usunięcia z `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4ccfd-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4ccfd-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4ccfd-118">Child Elements</span></span>  
 <span data-ttu-id="4ccfd-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="4ccfd-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4ccfd-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4ccfd-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4ccfd-121">Element</span><span class="sxs-lookup"><span data-stu-id="4ccfd-121">Element</span></span>|<span data-ttu-id="4ccfd-122">Opis</span><span class="sxs-lookup"><span data-stu-id="4ccfd-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4ccfd-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4ccfd-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4ccfd-124">Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4ccfd-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="4ccfd-125">Zawiera źródła śledzenia, które inicjują śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4ccfd-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="4ccfd-126">Określa źródło śledzenia, który inicjuje śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4ccfd-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="4ccfd-127">Określa nasłuchujących zbierania, przechowywania i kierowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4ccfd-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ccfd-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ccfd-128">Remarks</span></span>  
 <span data-ttu-id="4ccfd-129">`<remove>` Element usuwa określony odbiornik z `Listeners` kolekcji źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4ccfd-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="4ccfd-130">Można usunąć elementu z `Listeners` kolekcji źródła śledzenia programowo przez wywołanie metody <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> metoda <xref:System.Diagnostics.TraceSource.Listeners%2A> właściwość <xref:System.Diagnostics.TraceSource> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4ccfd-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="4ccfd-131">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4ccfd-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ccfd-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ccfd-132">Example</span></span>  
 <span data-ttu-id="4ccfd-133">Poniższy przykład przedstawia użycie `<remove>` element, aby można było używać `<add>` elementu do dodania odbiornika `console` do `Listeners` kolekcji źródła śledzenia `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="4ccfd-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4ccfd-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ccfd-134">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource.Listeners%2A>  
 <xref:System.Diagnostics.TraceSource>  
 [<span data-ttu-id="4ccfd-135">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="4ccfd-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="4ccfd-136">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="4ccfd-136">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)  
 [<span data-ttu-id="4ccfd-137">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="4ccfd-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
