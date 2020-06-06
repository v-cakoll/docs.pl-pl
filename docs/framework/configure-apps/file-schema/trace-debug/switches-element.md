---
title: <switches> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
ms.openlocfilehash: 15cc9680d7a20341eb5d1d1df302c1e034e70e02
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153233"
---
# <a name="switches-element"></a><span data-ttu-id="346a2-102">\<switches> Element</span><span class="sxs-lookup"><span data-stu-id="346a2-102">\<switches> Element</span></span>
<span data-ttu-id="346a2-103">Zawiera przełączniki śledzenia i poziom, w którym są ustawione przełączniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="346a2-103">Contains trace switches and the level where the trace switches are set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**

## <a name="syntax"></a><span data-ttu-id="346a2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="346a2-104">Syntax</span></span>  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="346a2-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="346a2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="346a2-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="346a2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="346a2-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="346a2-107">Attributes</span></span>  
 <span data-ttu-id="346a2-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="346a2-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="346a2-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="346a2-109">Child Elements</span></span>  
  
|<span data-ttu-id="346a2-110">Element</span><span class="sxs-lookup"><span data-stu-id="346a2-110">Element</span></span>|<span data-ttu-id="346a2-111">Opis</span><span class="sxs-lookup"><span data-stu-id="346a2-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-switches.md)|<span data-ttu-id="346a2-112">Określa poziom, w którym jest ustawiony przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="346a2-112">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="346a2-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="346a2-113">Parent Elements</span></span>  
  
|<span data-ttu-id="346a2-114">Element</span><span class="sxs-lookup"><span data-stu-id="346a2-114">Element</span></span>|<span data-ttu-id="346a2-115">Opis</span><span class="sxs-lookup"><span data-stu-id="346a2-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="346a2-116">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="346a2-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="346a2-117">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="346a2-117">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="346a2-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="346a2-118">Remarks</span></span>  
 <span data-ttu-id="346a2-119">Możesz zmienić poziom przełącznika śledzenia, umieszczając go w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="346a2-119">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="346a2-120">Jeśli przełącznik jest, możesz <xref:System.Diagnostics.BooleanSwitch> go włączyć i wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="346a2-120">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="346a2-121">Jeśli przełącznik jest <xref:System.Diagnostics.TraceSwitch> , można przypisać do niego różne poziomy, aby określić typy komunikatów śledzenia lub debugowania, które są wyprowadzane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="346a2-121">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="346a2-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="346a2-122">Example</span></span>  
 <span data-ttu-id="346a2-123">Poniższy przykład pokazuje, jak używać **\<switch>** elementu do ustawiania `General` przełącznika śledzenia na <xref:System.Diagnostics.TraceLevel> poziomie i włączania `Data` logicznego przełącznika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="346a2-123">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="346a2-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="346a2-124">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="346a2-125">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="346a2-125">Trace and Debug Settings Schema</span></span>](index.md)
