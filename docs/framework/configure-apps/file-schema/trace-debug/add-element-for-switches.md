---
title: <add>, element dla <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: 2edc890049d62913d693ad61d8d814d012c0f482
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697175"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="7715c-102">\<add > elementu \<switches ></span><span class="sxs-lookup"><span data-stu-id="7715c-102">\<add> Element for \<switches></span></span>
<span data-ttu-id="7715c-103">Określa poziom, w którym jest ustawiony przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="7715c-103">Specifies the level where a trace switch is set.</span></span>  
  
[<span data-ttu-id="7715c-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="7715c-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="7715c-105">&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="7715c-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="7715c-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<switches >** ](switches-element.md)</span><span class="sxs-lookup"><span data-stu-id="7715c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)</span></span>  
<span data-ttu-id="7715c-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<add >**</span><span class="sxs-lookup"><span data-stu-id="7715c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7715c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="7715c-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7715c-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7715c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7715c-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7715c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7715c-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7715c-111">Attributes</span></span>  
  
|<span data-ttu-id="7715c-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7715c-112">Attribute</span></span>|<span data-ttu-id="7715c-113">Opis</span><span class="sxs-lookup"><span data-stu-id="7715c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7715c-114">**Nazwij**</span><span class="sxs-lookup"><span data-stu-id="7715c-114">**name**</span></span>|<span data-ttu-id="7715c-115">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="7715c-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="7715c-116">Określa nazwę przełącznika.</span><span class="sxs-lookup"><span data-stu-id="7715c-116">Specifies the name of the switch.</span></span> <span data-ttu-id="7715c-117">Wartość tego atrybutu odpowiada parametrowi *DisplayName* , który jest przesyłany do konstruktora przełącznika.</span><span class="sxs-lookup"><span data-stu-id="7715c-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="7715c-118">**value**</span><span class="sxs-lookup"><span data-stu-id="7715c-118">**value**</span></span>|<span data-ttu-id="7715c-119">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="7715c-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="7715c-120">Określa poziom przełącznika.</span><span class="sxs-lookup"><span data-stu-id="7715c-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7715c-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7715c-121">Child Elements</span></span>  
 <span data-ttu-id="7715c-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="7715c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7715c-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7715c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7715c-124">Element</span><span class="sxs-lookup"><span data-stu-id="7715c-124">Element</span></span>|<span data-ttu-id="7715c-125">Opis</span><span class="sxs-lookup"><span data-stu-id="7715c-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7715c-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7715c-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="7715c-127">Zawiera przełączniki śledzenia i poziom, w którym są ustawione przełączniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="7715c-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="7715c-128">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="7715c-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7715c-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7715c-129">Remarks</span></span>  
 <span data-ttu-id="7715c-130">Możesz zmienić poziom przełącznika śledzenia, umieszczając go w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7715c-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="7715c-131">Jeśli przełącznik jest <xref:System.Diagnostics.BooleanSwitch>, można go włączyć i wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="7715c-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="7715c-132">Jeśli przełącznik jest <xref:System.Diagnostics.TraceSwitch>, można przypisać do niego różne poziomy, aby określić typy komunikatów śledzenia lub debugowania, które są wyprowadzane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="7715c-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7715c-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="7715c-133">Example</span></span>  
 <span data-ttu-id="7715c-134">W poniższym przykładzie pokazano, jak użyć elementu **\<add >** , aby ustawić przełącznik śledzenia `General` na poziomie <xref:System.Diagnostics.TraceLevel> i włączyć przełącznik śledzenia wartości logicznej `Data`.</span><span class="sxs-lookup"><span data-stu-id="7715c-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7715c-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7715c-135">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="7715c-136">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="7715c-136">Trace and Debug Settings Schema</span></span>](index.md)
