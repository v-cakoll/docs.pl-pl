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
ms.openlocfilehash: 2a76816ee73f516b3c7544877a77531acaa8e09c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153272"
---
# <a name="sources-element"></a><span data-ttu-id="7d8b0-102">\<źródła> Element</span><span class="sxs-lookup"><span data-stu-id="7d8b0-102">\<sources> Element</span></span>
<span data-ttu-id="7d8b0-103">Określa źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="7d8b0-103">Specifies trace sources that initiate tracing messages.</span></span>  

<span data-ttu-id="7d8b0-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7d8b0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7d8b0-105">&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="7d8b0-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="7d8b0-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<źródeł>**</span><span class="sxs-lookup"><span data-stu-id="7d8b0-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sources>**</span></span>

## <a name="syntax"></a><span data-ttu-id="7d8b0-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d8b0-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d8b0-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7d8b0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7d8b0-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7d8b0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d8b0-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7d8b0-110">Attributes</span></span>  
 <span data-ttu-id="7d8b0-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="7d8b0-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7d8b0-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7d8b0-112">Child Elements</span></span>  
  
|<span data-ttu-id="7d8b0-113">Element</span><span class="sxs-lookup"><span data-stu-id="7d8b0-113">Element</span></span>|<span data-ttu-id="7d8b0-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7d8b0-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d8b0-115">\<>źródłowe</span><span class="sxs-lookup"><span data-stu-id="7d8b0-115">\<source></span></span>](source-element.md)|<span data-ttu-id="7d8b0-116">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="7d8b0-116">Required element.</span></span><br /><br /> <span data-ttu-id="7d8b0-117">Określa źródło śledzenia, które inicjuje śledzenie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="7d8b0-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7d8b0-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7d8b0-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7d8b0-119">Element</span><span class="sxs-lookup"><span data-stu-id="7d8b0-119">Element</span></span>|<span data-ttu-id="7d8b0-120">Opis</span><span class="sxs-lookup"><span data-stu-id="7d8b0-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7d8b0-121">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7d8b0-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="7d8b0-122">Określa odbiorniki śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, na którym ustawiony jest przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="7d8b0-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d8b0-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d8b0-123">Remarks</span></span>  
 <span data-ttu-id="7d8b0-124">Ten element może być używany w pliku konfiguracyjnym komputera (Machine.config) i pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7d8b0-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d8b0-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d8b0-125">Example</span></span>  
 <span data-ttu-id="7d8b0-126">W poniższym przykładzie `<sources>` pokazano, jak użyć `mySource` elementu, aby dodać źródło `sourceSwitch`śledzenia i ustawić poziom dla przełącznika źródłowego o nazwie .</span><span class="sxs-lookup"><span data-stu-id="7d8b0-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="7d8b0-127">Dodano odbiornik śledzenia konsoli, który zapisuje informacje śledzenia do konsoli.</span><span class="sxs-lookup"><span data-stu-id="7d8b0-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7d8b0-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d8b0-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="7d8b0-129">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="7d8b0-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7d8b0-130">\<>źródłowe</span><span class="sxs-lookup"><span data-stu-id="7d8b0-130">\<source></span></span>](source-element.md)
