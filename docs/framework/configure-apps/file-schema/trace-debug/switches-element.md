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
ms.openlocfilehash: 44f5c918f19f84daf827ad4e8f3b6bfbc3e9f439
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196531"
---
# <a name="switches-element"></a><span data-ttu-id="9d438-102">\<przełączniki > Element</span><span class="sxs-lookup"><span data-stu-id="9d438-102">\<switches> Element</span></span>
<span data-ttu-id="9d438-103">Zawiera przełączniki śledzenia i poziomu, gdzie są ustawione przełączniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9d438-103">Contains trace switches and the level where the trace switches are set.</span></span>  
  
 <span data-ttu-id="9d438-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="9d438-104">\<configuration></span></span>  
<span data-ttu-id="9d438-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="9d438-105">\<system.diagnostics></span></span>  
<span data-ttu-id="9d438-106">\<przełączniki ></span><span class="sxs-lookup"><span data-stu-id="9d438-106">\<switches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d438-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d438-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d438-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9d438-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9d438-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9d438-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d438-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9d438-110">Attributes</span></span>  
 <span data-ttu-id="9d438-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="9d438-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9d438-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9d438-112">Child Elements</span></span>  
  
|<span data-ttu-id="9d438-113">Element</span><span class="sxs-lookup"><span data-stu-id="9d438-113">Element</span></span>|<span data-ttu-id="9d438-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9d438-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d438-115">\<add></span><span class="sxs-lookup"><span data-stu-id="9d438-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|<span data-ttu-id="9d438-116">Określa poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9d438-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d438-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9d438-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9d438-118">Element</span><span class="sxs-lookup"><span data-stu-id="9d438-118">Element</span></span>|<span data-ttu-id="9d438-119">Opis</span><span class="sxs-lookup"><span data-stu-id="9d438-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9d438-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9d438-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="9d438-121">Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9d438-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d438-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d438-122">Remarks</span></span>  
 <span data-ttu-id="9d438-123">Aby zmienić poziom o przełącznikiem śledzenia, należy umieścić go w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9d438-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="9d438-124">Jeśli przełącznik <xref:System.Diagnostics.BooleanSwitch>, możesz je włączyć lub wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="9d438-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="9d438-125">Jeśli przełącznik <xref:System.Diagnostics.TraceSwitch>można przypisać różne poziomy, aby określić typy śledzenia i debugowania komunikaty wyjściowe aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9d438-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d438-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="9d438-126">Example</span></span>  
 <span data-ttu-id="9d438-127">Poniższy przykład pokazuje, jak używać  **\<przełącznika >** element, aby ustawić `General` przełącznikiem śledzenia do <xref:System.Diagnostics.TraceLevel> poziomu i włączyć `Data` przełącznikiem logiczna śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9d438-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9d438-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d438-128">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="9d438-129">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="9d438-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
