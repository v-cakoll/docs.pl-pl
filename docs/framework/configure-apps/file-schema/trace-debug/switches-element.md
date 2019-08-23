---
title: <switches>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
ms.openlocfilehash: 92a1c8db43579048945d76082e3ebd2862efd7ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920443"
---
# <a name="switches-element"></a><span data-ttu-id="47c11-102">\<przełącza > elementu</span><span class="sxs-lookup"><span data-stu-id="47c11-102">\<switches> Element</span></span>
<span data-ttu-id="47c11-103">Zawiera przełączniki śledzenia i poziom, w którym są ustawione przełączniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="47c11-103">Contains trace switches and the level where the trace switches are set.</span></span>  
  
 <span data-ttu-id="47c11-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="47c11-104">\<configuration></span></span>  
<span data-ttu-id="47c11-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="47c11-105">\<system.diagnostics></span></span>  
<span data-ttu-id="47c11-106">\<Przełączniki ></span><span class="sxs-lookup"><span data-stu-id="47c11-106">\<switches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47c11-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="47c11-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47c11-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="47c11-108">Attributes and Elements</span></span>  
 <span data-ttu-id="47c11-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="47c11-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47c11-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="47c11-110">Attributes</span></span>  
 <span data-ttu-id="47c11-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="47c11-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="47c11-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="47c11-112">Child Elements</span></span>  
  
|<span data-ttu-id="47c11-113">Element</span><span class="sxs-lookup"><span data-stu-id="47c11-113">Element</span></span>|<span data-ttu-id="47c11-114">Opis</span><span class="sxs-lookup"><span data-stu-id="47c11-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47c11-115">\<add></span><span class="sxs-lookup"><span data-stu-id="47c11-115">\<add></span></span>](add-element-for-switches.md)|<span data-ttu-id="47c11-116">Określa poziom, w którym jest ustawiony przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="47c11-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="47c11-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="47c11-117">Parent Elements</span></span>  
  
|<span data-ttu-id="47c11-118">Element</span><span class="sxs-lookup"><span data-stu-id="47c11-118">Element</span></span>|<span data-ttu-id="47c11-119">Opis</span><span class="sxs-lookup"><span data-stu-id="47c11-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="47c11-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="47c11-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="47c11-121">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="47c11-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47c11-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="47c11-122">Remarks</span></span>  
 <span data-ttu-id="47c11-123">Możesz zmienić poziom przełącznika śledzenia, umieszczając go w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="47c11-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="47c11-124">Jeśli przełącznik jest <xref:System.Diagnostics.BooleanSwitch>, możesz go włączyć i wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="47c11-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="47c11-125">Jeśli przełącznik jest <xref:System.Diagnostics.TraceSwitch>, można przypisać do niego różne poziomy, aby określić typy komunikatów śledzenia lub debugowania, które są wyprowadzane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="47c11-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47c11-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="47c11-126">Example</span></span>  
 <span data-ttu-id="47c11-127">Poniższy przykład pokazuje, jak <xref:System.Diagnostics.TraceLevel> używać `Data` `General`  **\<elementu Switch >** , aby ustawić przełącznik śledzenia na poziomie i włączyć przełącznik logiczny śledzenia.</span><span class="sxs-lookup"><span data-stu-id="47c11-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="47c11-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47c11-128">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="47c11-129">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="47c11-129">Trace and Debug Settings Schema</span></span>](index.md)
