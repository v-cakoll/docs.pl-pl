---
title: <add>, element dla <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: 8fcd5cbe63a323a7509f5ff8c615364295c244d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920544"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="30509-102">\<Dodaj element > dla \<przełączników ></span><span class="sxs-lookup"><span data-stu-id="30509-102">\<add> Element for \<switches></span></span>
<span data-ttu-id="30509-103">Określa poziom, w którym jest ustawiony przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="30509-103">Specifies the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="30509-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="30509-104">\<configuration></span></span>  
<span data-ttu-id="30509-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="30509-105">\<system.diagnostics></span></span>  
<span data-ttu-id="30509-106">\<Przełączniki ></span><span class="sxs-lookup"><span data-stu-id="30509-106">\<switches></span></span>  
<span data-ttu-id="30509-107">\<add></span><span class="sxs-lookup"><span data-stu-id="30509-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30509-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="30509-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30509-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="30509-109">Attributes and Elements</span></span>  
 <span data-ttu-id="30509-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="30509-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30509-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="30509-111">Attributes</span></span>  
  
|<span data-ttu-id="30509-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="30509-112">Attribute</span></span>|<span data-ttu-id="30509-113">Opis</span><span class="sxs-lookup"><span data-stu-id="30509-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30509-114">**name**</span><span class="sxs-lookup"><span data-stu-id="30509-114">**name**</span></span>|<span data-ttu-id="30509-115">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="30509-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="30509-116">Określa nazwę przełącznika.</span><span class="sxs-lookup"><span data-stu-id="30509-116">Specifies the name of the switch.</span></span> <span data-ttu-id="30509-117">Wartość tego atrybutu odpowiada parametrowi *DisplayName* , który jest przesyłany do konstruktora przełącznika.</span><span class="sxs-lookup"><span data-stu-id="30509-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="30509-118">**value**</span><span class="sxs-lookup"><span data-stu-id="30509-118">**value**</span></span>|<span data-ttu-id="30509-119">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="30509-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="30509-120">Określa poziom przełącznika.</span><span class="sxs-lookup"><span data-stu-id="30509-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30509-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="30509-121">Child Elements</span></span>  
 <span data-ttu-id="30509-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="30509-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30509-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="30509-123">Parent Elements</span></span>  
  
|<span data-ttu-id="30509-124">Element</span><span class="sxs-lookup"><span data-stu-id="30509-124">Element</span></span>|<span data-ttu-id="30509-125">Opis</span><span class="sxs-lookup"><span data-stu-id="30509-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="30509-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="30509-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="30509-127">Zawiera przełączniki śledzenia i poziom, w którym są ustawione przełączniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="30509-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="30509-128">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="30509-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30509-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="30509-129">Remarks</span></span>  
 <span data-ttu-id="30509-130">Możesz zmienić poziom przełącznika śledzenia, umieszczając go w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="30509-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="30509-131">Jeśli przełącznik jest <xref:System.Diagnostics.BooleanSwitch>, możesz go włączyć i wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="30509-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="30509-132">Jeśli przełącznik jest <xref:System.Diagnostics.TraceSwitch>, można przypisać do niego różne poziomy, aby określić typy komunikatów śledzenia lub debugowania, które są wyprowadzane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="30509-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30509-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="30509-133">Example</span></span>  
 <span data-ttu-id="30509-134">Poniższy przykład pokazuje, jak <xref:System.Diagnostics.TraceLevel> używać `Data` `General`  **\<elementu > Dodaj** , aby ustawić przełącznik śledzenia na poziomie i włączyć przełącznik logiczny śledzenia.</span><span class="sxs-lookup"><span data-stu-id="30509-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="30509-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30509-135">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="30509-136">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="30509-136">Trace and Debug Settings Schema</span></span>](index.md)
