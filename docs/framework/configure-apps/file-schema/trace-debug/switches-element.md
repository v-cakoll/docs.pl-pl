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
ms.openlocfilehash: c161f842192396101dcc6850f3b3da328958eac3
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697082"
---
# <a name="switches-element"></a><span data-ttu-id="aefb5-102">\<switches > elementu</span><span class="sxs-lookup"><span data-stu-id="aefb5-102">\<switches> Element</span></span>
<span data-ttu-id="aefb5-103">Zawiera przełączniki śledzenia i poziom, w którym są ustawione przełączniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="aefb5-103">Contains trace switches and the level where the trace switches are set.</span></span>  
  
[<span data-ttu-id="aefb5-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="aefb5-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="aefb5-105">&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="aefb5-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="aefb5-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<switches >**</span><span class="sxs-lookup"><span data-stu-id="aefb5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aefb5-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="aefb5-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aefb5-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="aefb5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="aefb5-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="aefb5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aefb5-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="aefb5-110">Attributes</span></span>  
 <span data-ttu-id="aefb5-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="aefb5-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="aefb5-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="aefb5-112">Child Elements</span></span>  
  
|<span data-ttu-id="aefb5-113">Element</span><span class="sxs-lookup"><span data-stu-id="aefb5-113">Element</span></span>|<span data-ttu-id="aefb5-114">Opis</span><span class="sxs-lookup"><span data-stu-id="aefb5-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aefb5-115">@no__t — 1add ></span><span class="sxs-lookup"><span data-stu-id="aefb5-115">\<add></span></span>](add-element-for-switches.md)|<span data-ttu-id="aefb5-116">Określa poziom, w którym jest ustawiony przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="aefb5-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aefb5-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="aefb5-117">Parent Elements</span></span>  
  
|<span data-ttu-id="aefb5-118">Element</span><span class="sxs-lookup"><span data-stu-id="aefb5-118">Element</span></span>|<span data-ttu-id="aefb5-119">Opis</span><span class="sxs-lookup"><span data-stu-id="aefb5-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="aefb5-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aefb5-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="aefb5-121">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="aefb5-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aefb5-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aefb5-122">Remarks</span></span>  
 <span data-ttu-id="aefb5-123">Możesz zmienić poziom przełącznika śledzenia, umieszczając go w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="aefb5-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="aefb5-124">Jeśli przełącznik jest <xref:System.Diagnostics.BooleanSwitch>, można go włączyć i wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="aefb5-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="aefb5-125">Jeśli przełącznik jest <xref:System.Diagnostics.TraceSwitch>, można przypisać do niego różne poziomy, aby określić typy komunikatów śledzenia lub debugowania, które są wyprowadzane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="aefb5-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aefb5-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="aefb5-126">Example</span></span>  
 <span data-ttu-id="aefb5-127">W poniższym przykładzie pokazano, jak użyć elementu **\<switch >** , aby ustawić przełącznik śledzenia `General` na poziomie <xref:System.Diagnostics.TraceLevel> i włączyć przełącznik śledzenia wartości logicznej `Data`.</span><span class="sxs-lookup"><span data-stu-id="aefb5-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aefb5-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aefb5-128">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="aefb5-129">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="aefb5-129">Trace and Debug Settings Schema</span></span>](index.md)
 