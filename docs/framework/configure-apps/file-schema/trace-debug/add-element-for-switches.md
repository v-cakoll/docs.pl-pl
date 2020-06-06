---
title: <add>, element dla <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: db2de681227dfdb7420808963219b9f52381f8fe
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088963"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="1d09c-102">\<add>, element dla \<switches></span><span class="sxs-lookup"><span data-stu-id="1d09c-102">\<add> Element for \<switches></span></span>
<span data-ttu-id="1d09c-103">Określa poziom, w którym jest ustawiony przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1d09c-103">Specifies the level where a trace switch is set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="1d09c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d09c-104">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d09c-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1d09c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1d09c-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1d09c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d09c-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1d09c-107">Attributes</span></span>  
  
|<span data-ttu-id="1d09c-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1d09c-108">Attribute</span></span>|<span data-ttu-id="1d09c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1d09c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d09c-110">**Nazwij**</span><span class="sxs-lookup"><span data-stu-id="1d09c-110">**name**</span></span>|<span data-ttu-id="1d09c-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="1d09c-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="1d09c-112">Określa nazwę przełącznika.</span><span class="sxs-lookup"><span data-stu-id="1d09c-112">Specifies the name of the switch.</span></span> <span data-ttu-id="1d09c-113">Wartość tego atrybutu odpowiada parametrowi *DisplayName* , który jest przesyłany do konstruktora przełącznika.</span><span class="sxs-lookup"><span data-stu-id="1d09c-113">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="1d09c-114">**wartościami**</span><span class="sxs-lookup"><span data-stu-id="1d09c-114">**value**</span></span>|<span data-ttu-id="1d09c-115">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="1d09c-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="1d09c-116">Określa poziom przełącznika.</span><span class="sxs-lookup"><span data-stu-id="1d09c-116">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d09c-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1d09c-117">Child Elements</span></span>  
 <span data-ttu-id="1d09c-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="1d09c-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d09c-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1d09c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1d09c-120">Element</span><span class="sxs-lookup"><span data-stu-id="1d09c-120">Element</span></span>|<span data-ttu-id="1d09c-121">Opis</span><span class="sxs-lookup"><span data-stu-id="1d09c-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1d09c-122">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1d09c-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="1d09c-123">Zawiera przełączniki śledzenia i poziom, w którym są ustawione przełączniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1d09c-123">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="1d09c-124">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1d09c-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d09c-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d09c-125">Remarks</span></span>  
 <span data-ttu-id="1d09c-126">Możesz zmienić poziom przełącznika śledzenia, umieszczając go w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1d09c-126">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="1d09c-127">Jeśli przełącznik jest, możesz <xref:System.Diagnostics.BooleanSwitch> go włączyć i wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="1d09c-127">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="1d09c-128">Jeśli przełącznik jest <xref:System.Diagnostics.TraceSwitch> , można przypisać do niego różne poziomy, aby określić typy komunikatów śledzenia lub debugowania, które są wyprowadzane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="1d09c-128">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d09c-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d09c-129">Example</span></span>  
 <span data-ttu-id="1d09c-130">Poniższy przykład pokazuje, jak używać **\<add>** elementu do ustawiania `General` przełącznika śledzenia na <xref:System.Diagnostics.TraceLevel> poziomie i włączania `Data` logicznego przełącznika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1d09c-130">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1d09c-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d09c-131">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="1d09c-132">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="1d09c-132">Trace and Debug Settings Schema</span></span>](index.md)
