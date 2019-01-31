---
title: <sources>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sources
helpviewer_keywords:
- sources element
- trace sources
- <sources> element
ms.assetid: c727b2e2-423a-4463-a223-013f40ff16a3
ms.openlocfilehash: d7d92f91838a8d1914ffe574f018cc701477d767
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262507"
---
# <a name="sources-element"></a><span data-ttu-id="1c7d5-102">\<źródła > Element</span><span class="sxs-lookup"><span data-stu-id="1c7d5-102">\<sources> Element</span></span>
<span data-ttu-id="1c7d5-103">Określa źródła śledzenia, które inicjują komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1c7d5-103">Specifies trace sources that initiate tracing messages.</span></span>  
  
 <span data-ttu-id="1c7d5-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="1c7d5-104">\<configuration></span></span>  
<span data-ttu-id="1c7d5-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="1c7d5-105">\<system.diagnostics></span></span>  
<span data-ttu-id="1c7d5-106">\<źródła ></span><span class="sxs-lookup"><span data-stu-id="1c7d5-106">\<sources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c7d5-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c7d5-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c7d5-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1c7d5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1c7d5-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1c7d5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c7d5-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1c7d5-110">Attributes</span></span>  
 <span data-ttu-id="1c7d5-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="1c7d5-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1c7d5-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1c7d5-112">Child Elements</span></span>  
  
|<span data-ttu-id="1c7d5-113">Element</span><span class="sxs-lookup"><span data-stu-id="1c7d5-113">Element</span></span>|<span data-ttu-id="1c7d5-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1c7d5-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c7d5-115">\<source></span><span class="sxs-lookup"><span data-stu-id="1c7d5-115">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|<span data-ttu-id="1c7d5-116">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="1c7d5-116">Required element.</span></span><br /><br /> <span data-ttu-id="1c7d5-117">Określa źródło śledzenia, który inicjuje komunikatów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1c7d5-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1c7d5-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1c7d5-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1c7d5-119">Element</span><span class="sxs-lookup"><span data-stu-id="1c7d5-119">Element</span></span>|<span data-ttu-id="1c7d5-120">Opis</span><span class="sxs-lookup"><span data-stu-id="1c7d5-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1c7d5-121">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1c7d5-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="1c7d5-122">Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1c7d5-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c7d5-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c7d5-123">Remarks</span></span>  
 <span data-ttu-id="1c7d5-124">Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1c7d5-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c7d5-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c7d5-125">Example</span></span>  
 <span data-ttu-id="1c7d5-126">Poniższy przykład pokazuje, jak używać `<sources>` elementu do dodania źródła śledzenia `mySource` i ustaw poziom przełącznik źródła o nazwie `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="1c7d5-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="1c7d5-127">Detektor śledzenia konsoli jest dodawany, który zapisuje informacje śledzenia do konsoli.</span><span class="sxs-lookup"><span data-stu-id="1c7d5-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1c7d5-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c7d5-128">See also</span></span>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="1c7d5-129">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="1c7d5-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="1c7d5-130">\<source></span><span class="sxs-lookup"><span data-stu-id="1c7d5-130">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)
