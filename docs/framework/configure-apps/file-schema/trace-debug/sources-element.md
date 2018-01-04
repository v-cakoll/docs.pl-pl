---
title: "&lt;źródeł&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sources
helpviewer_keywords:
- sources element
- trace sources
- <sources> element
ms.assetid: c727b2e2-423a-4463-a223-013f40ff16a3
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 7abe1f4a536d9f321e0a8b300f9542255433c030
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltsourcesgt-element"></a><span data-ttu-id="0ab91-102">&lt;źródeł&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="0ab91-102">&lt;sources&gt; Element</span></span>
<span data-ttu-id="0ab91-103">Określa źródła śledzenia, które inicjują śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0ab91-103">Specifies trace sources that initiate tracing messages.</span></span>  
  
 <span data-ttu-id="0ab91-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="0ab91-104">\<configuration></span></span>  
<span data-ttu-id="0ab91-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="0ab91-105">\<system.diagnostics></span></span>  
<span data-ttu-id="0ab91-106">\<źródeł ></span><span class="sxs-lookup"><span data-stu-id="0ab91-106">\<sources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ab91-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ab91-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ab91-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0ab91-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0ab91-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0ab91-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ab91-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0ab91-110">Attributes</span></span>  
 <span data-ttu-id="0ab91-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="0ab91-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0ab91-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0ab91-112">Child Elements</span></span>  
  
|<span data-ttu-id="0ab91-113">Element</span><span class="sxs-lookup"><span data-stu-id="0ab91-113">Element</span></span>|<span data-ttu-id="0ab91-114">Opis</span><span class="sxs-lookup"><span data-stu-id="0ab91-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0ab91-115">\<źródło ></span><span class="sxs-lookup"><span data-stu-id="0ab91-115">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|<span data-ttu-id="0ab91-116">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="0ab91-116">Required element.</span></span><br /><br /> <span data-ttu-id="0ab91-117">Określa źródło śledzenia, który inicjuje śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0ab91-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0ab91-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0ab91-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0ab91-119">Element</span><span class="sxs-lookup"><span data-stu-id="0ab91-119">Element</span></span>|<span data-ttu-id="0ab91-120">Opis</span><span class="sxs-lookup"><span data-stu-id="0ab91-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0ab91-121">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0ab91-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="0ab91-122">Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0ab91-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ab91-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ab91-123">Remarks</span></span>  
 <span data-ttu-id="0ab91-124">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0ab91-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ab91-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ab91-125">Example</span></span>  
 <span data-ttu-id="0ab91-126">Poniższy przykład przedstawia użycie `<sources>` elementu do dodania źródła śledzenia `mySource` i ustaw poziom przełącznik źródła o nazwie `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="0ab91-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="0ab91-127">Odbiornik śledzenia konsoli są dodawane który zapisuje informacje śledzenia do konsoli.</span><span class="sxs-lookup"><span data-stu-id="0ab91-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0ab91-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ab91-128">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.XmlWriterTraceListener>  
 [<span data-ttu-id="0ab91-129">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="0ab91-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="0ab91-130">\<źródło ></span><span class="sxs-lookup"><span data-stu-id="0ab91-130">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)
