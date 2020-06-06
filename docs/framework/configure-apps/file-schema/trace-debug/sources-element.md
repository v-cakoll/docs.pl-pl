---
title: <sources> Element
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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153272"
---
# <a name="sources-element"></a><span data-ttu-id="1c06d-102">\<sources> Element</span><span class="sxs-lookup"><span data-stu-id="1c06d-102">\<sources> Element</span></span>
<span data-ttu-id="1c06d-103">Określa źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1c06d-103">Specifies trace sources that initiate tracing messages.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<sources>**

## <a name="syntax"></a><span data-ttu-id="1c06d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c06d-104">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c06d-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1c06d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1c06d-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1c06d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c06d-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1c06d-107">Attributes</span></span>  
 <span data-ttu-id="1c06d-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="1c06d-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1c06d-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1c06d-109">Child Elements</span></span>  
  
|<span data-ttu-id="1c06d-110">Element</span><span class="sxs-lookup"><span data-stu-id="1c06d-110">Element</span></span>|<span data-ttu-id="1c06d-111">Opis</span><span class="sxs-lookup"><span data-stu-id="1c06d-111">Description</span></span>|  
|-------------|-----------------|  
|[\<source>](source-element.md)|<span data-ttu-id="1c06d-112">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="1c06d-112">Required element.</span></span><br /><br /> <span data-ttu-id="1c06d-113">Określa źródło śledzenia, które inicjuje komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1c06d-113">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1c06d-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1c06d-114">Parent Elements</span></span>  
  
|<span data-ttu-id="1c06d-115">Element</span><span class="sxs-lookup"><span data-stu-id="1c06d-115">Element</span></span>|<span data-ttu-id="1c06d-116">Opis</span><span class="sxs-lookup"><span data-stu-id="1c06d-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1c06d-117">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1c06d-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="1c06d-118">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1c06d-118">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c06d-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c06d-119">Remarks</span></span>  
 <span data-ttu-id="1c06d-120">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1c06d-120">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c06d-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c06d-121">Example</span></span>  
 <span data-ttu-id="1c06d-122">Poniższy przykład pokazuje, jak użyć elementu, `<sources>` Aby dodać Źródło śledzenia `mySource` i ustawić poziom dla przełącznika źródła o nazwie `sourceSwitch` .</span><span class="sxs-lookup"><span data-stu-id="1c06d-122">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="1c06d-123">Dodano odbiornik śledzenia konsoli, który zapisuje informacje o śledzeniu do konsoli.</span><span class="sxs-lookup"><span data-stu-id="1c06d-123">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1c06d-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c06d-124">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="1c06d-125">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="1c06d-125">Trace and Debug Settings Schema</span></span>](index.md)
- [\<source>](source-element.md)
