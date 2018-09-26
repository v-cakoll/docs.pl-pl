---
title: '&lt;źródła&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sources
helpviewer_keywords:
- sources element
- trace sources
- <sources> element
ms.assetid: c727b2e2-423a-4463-a223-013f40ff16a3
author: mcleblanc
ms.author: markl
ms.openlocfilehash: a9c5c5529e349eca2ba089ed6fb71da4bd48430a
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084452"
---
# <a name="ltsourcesgt-element"></a><span data-ttu-id="afcce-102">&lt;źródła&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="afcce-102">&lt;sources&gt; Element</span></span>
<span data-ttu-id="afcce-103">Określa źródła śledzenia, które inicjują komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="afcce-103">Specifies trace sources that initiate tracing messages.</span></span>  
  
 <span data-ttu-id="afcce-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="afcce-104">\<configuration></span></span>  
<span data-ttu-id="afcce-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="afcce-105">\<system.diagnostics></span></span>  
<span data-ttu-id="afcce-106">\<źródła ></span><span class="sxs-lookup"><span data-stu-id="afcce-106">\<sources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afcce-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="afcce-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afcce-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="afcce-108">Attributes and Elements</span></span>  
 <span data-ttu-id="afcce-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="afcce-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afcce-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="afcce-110">Attributes</span></span>  
 <span data-ttu-id="afcce-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="afcce-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="afcce-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="afcce-112">Child Elements</span></span>  
  
|<span data-ttu-id="afcce-113">Element</span><span class="sxs-lookup"><span data-stu-id="afcce-113">Element</span></span>|<span data-ttu-id="afcce-114">Opis</span><span class="sxs-lookup"><span data-stu-id="afcce-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afcce-115">\<źródło ></span><span class="sxs-lookup"><span data-stu-id="afcce-115">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|<span data-ttu-id="afcce-116">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="afcce-116">Required element.</span></span><br /><br /> <span data-ttu-id="afcce-117">Określa źródło śledzenia, który inicjuje komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="afcce-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="afcce-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="afcce-118">Parent Elements</span></span>  
  
|<span data-ttu-id="afcce-119">Element</span><span class="sxs-lookup"><span data-stu-id="afcce-119">Element</span></span>|<span data-ttu-id="afcce-120">Opis</span><span class="sxs-lookup"><span data-stu-id="afcce-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="afcce-121">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="afcce-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="afcce-122">Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="afcce-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afcce-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="afcce-123">Remarks</span></span>  
 <span data-ttu-id="afcce-124">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="afcce-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afcce-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="afcce-125">Example</span></span>  
 <span data-ttu-id="afcce-126">Poniższy przykład pokazuje, jak używać `<sources>` elementu do dodania źródła śledzenia `mySource` i ustaw poziom przełącznik źródła o nazwie `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="afcce-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="afcce-127">Detektor śledzenia konsoli jest dodawany, który zapisuje informacje śledzenia do konsoli.</span><span class="sxs-lookup"><span data-stu-id="afcce-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
         <source name="mySource" switchName="sourceSwitch"   
            switchType="System.Diagnostics.SourceSwitch"  >  
            <listeners>  
               <add name="console"   
                  type="System.Diagnostics.ConsoleTraceListener" >  
                  <filter type="System.Diagnostics.EventTypeFilter"   
                     initializeData="Error" />  
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
  
## <a name="see-also"></a><span data-ttu-id="afcce-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afcce-128">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.XmlWriterTraceListener>  
 [<span data-ttu-id="afcce-129">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="afcce-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="afcce-130">\<źródło ></span><span class="sxs-lookup"><span data-stu-id="afcce-130">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)
