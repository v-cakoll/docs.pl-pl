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
ms.openlocfilehash: 4aeb3cb0cd75f0fb27e3b359b86da61a77b491c7
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088804"
---
# <a name="switches-element"></a><span data-ttu-id="72ff1-102">\<przełączniki > elementu</span><span class="sxs-lookup"><span data-stu-id="72ff1-102">\<switches> Element</span></span>
<span data-ttu-id="72ff1-103">Zawiera przełączniki śledzenia i poziom, w którym są ustawione przełączniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="72ff1-103">Contains trace switches and the level where the trace switches are set.</span></span>  

<span data-ttu-id="72ff1-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="72ff1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="72ff1-105">&nbsp;&nbsp;[ **\<system. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="72ff1-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="72ff1-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<przełączniki** ></span><span class="sxs-lookup"><span data-stu-id="72ff1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**</span></span>

## <a name="syntax"></a><span data-ttu-id="72ff1-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="72ff1-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72ff1-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="72ff1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="72ff1-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="72ff1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72ff1-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="72ff1-110">Attributes</span></span>  
 <span data-ttu-id="72ff1-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="72ff1-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="72ff1-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="72ff1-112">Child Elements</span></span>  
  
|<span data-ttu-id="72ff1-113">Element</span><span class="sxs-lookup"><span data-stu-id="72ff1-113">Element</span></span>|<span data-ttu-id="72ff1-114">Opis</span><span class="sxs-lookup"><span data-stu-id="72ff1-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72ff1-115">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="72ff1-115">\<add></span></span>](add-element-for-switches.md)|<span data-ttu-id="72ff1-116">Określa poziom, w którym jest ustawiony przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="72ff1-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="72ff1-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="72ff1-117">Parent Elements</span></span>  
  
|<span data-ttu-id="72ff1-118">Element</span><span class="sxs-lookup"><span data-stu-id="72ff1-118">Element</span></span>|<span data-ttu-id="72ff1-119">Opis</span><span class="sxs-lookup"><span data-stu-id="72ff1-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="72ff1-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="72ff1-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="72ff1-121">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="72ff1-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72ff1-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="72ff1-122">Remarks</span></span>  
 <span data-ttu-id="72ff1-123">Możesz zmienić poziom przełącznika śledzenia, umieszczając go w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="72ff1-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="72ff1-124">Jeśli przełącznik jest <xref:System.Diagnostics.BooleanSwitch>, można go włączyć i wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="72ff1-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="72ff1-125">Jeśli przełącznik jest <xref:System.Diagnostics.TraceSwitch>, można przypisać do niego różne poziomy, aby określić typy komunikatów śledzenia lub debugowania, które są wyprowadzane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="72ff1-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72ff1-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="72ff1-126">Example</span></span>  
 <span data-ttu-id="72ff1-127">Poniższy przykład pokazuje, jak używać **\<przełącznika >** elementu, aby ustawić przełącznik śledzenia `General` na poziom <xref:System.Diagnostics.TraceLevel> i włączyć `Data` logicznego przełącznika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="72ff1-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="72ff1-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72ff1-128">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="72ff1-129">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="72ff1-129">Trace and Debug Settings Schema</span></span>](index.md)
