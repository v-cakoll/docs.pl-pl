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
ms.openlocfilehash: 73d4eb2741bdbe5a07704ca0f3b2f779706e66dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926952"
---
# <a name="sources-element"></a><span data-ttu-id="45c7c-102">\<Elementy > źródła</span><span class="sxs-lookup"><span data-stu-id="45c7c-102">\<sources> Element</span></span>
<span data-ttu-id="45c7c-103">Określa źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="45c7c-103">Specifies trace sources that initiate tracing messages.</span></span>  
  
 <span data-ttu-id="45c7c-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="45c7c-104">\<configuration></span></span>  
<span data-ttu-id="45c7c-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="45c7c-105">\<system.diagnostics></span></span>  
<span data-ttu-id="45c7c-106">\<> źródeł</span><span class="sxs-lookup"><span data-stu-id="45c7c-106">\<sources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45c7c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="45c7c-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45c7c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="45c7c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="45c7c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="45c7c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45c7c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="45c7c-110">Attributes</span></span>  
 <span data-ttu-id="45c7c-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="45c7c-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="45c7c-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="45c7c-112">Child Elements</span></span>  
  
|<span data-ttu-id="45c7c-113">Element</span><span class="sxs-lookup"><span data-stu-id="45c7c-113">Element</span></span>|<span data-ttu-id="45c7c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="45c7c-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45c7c-115">\<> źródłowa</span><span class="sxs-lookup"><span data-stu-id="45c7c-115">\<source></span></span>](source-element.md)|<span data-ttu-id="45c7c-116">Element wymagany.</span><span class="sxs-lookup"><span data-stu-id="45c7c-116">Required element.</span></span><br /><br /> <span data-ttu-id="45c7c-117">Określa źródło śledzenia, które inicjuje komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="45c7c-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="45c7c-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="45c7c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="45c7c-119">Element</span><span class="sxs-lookup"><span data-stu-id="45c7c-119">Element</span></span>|<span data-ttu-id="45c7c-120">Opis</span><span class="sxs-lookup"><span data-stu-id="45c7c-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="45c7c-121">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="45c7c-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="45c7c-122">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="45c7c-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45c7c-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="45c7c-123">Remarks</span></span>  
 <span data-ttu-id="45c7c-124">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45c7c-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45c7c-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="45c7c-125">Example</span></span>  
 <span data-ttu-id="45c7c-126">Poniższy przykład pokazuje, jak użyć elementu, `<sources>` aby dodać źródło `mySource` śledzenia i ustawić poziom dla przełącznika źródła o nazwie `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="45c7c-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="45c7c-127">Dodano odbiornik śledzenia konsoli, który zapisuje informacje o śledzeniu do konsoli.</span><span class="sxs-lookup"><span data-stu-id="45c7c-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="45c7c-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45c7c-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="45c7c-129">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="45c7c-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="45c7c-130">\<> źródłowa</span><span class="sxs-lookup"><span data-stu-id="45c7c-130">\<source></span></span>](source-element.md)
