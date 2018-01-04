---
title: "&lt;przełączniki&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 64cf3ba9e5529c4a46b2d5365931a47ad2ab211a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltswitchesgt-element"></a><span data-ttu-id="3e8ae-102">&lt;przełączniki&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="3e8ae-102">&lt;switches&gt; Element</span></span>
<span data-ttu-id="3e8ae-103">Zawiera przełączniki śledzenia i poziom, gdzie są ustawione przełączniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-103">Contains trace switches and the level where the trace switches are set.</span></span>  
  
 <span data-ttu-id="3e8ae-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="3e8ae-104">\<configuration></span></span>  
<span data-ttu-id="3e8ae-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="3e8ae-105">\<system.diagnostics></span></span>  
<span data-ttu-id="3e8ae-106">\<przełączniki ></span><span class="sxs-lookup"><span data-stu-id="3e8ae-106">\<switches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e8ae-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e8ae-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e8ae-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3e8ae-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3e8ae-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e8ae-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3e8ae-110">Attributes</span></span>  
 <span data-ttu-id="3e8ae-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3e8ae-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3e8ae-112">Child Elements</span></span>  
  
|<span data-ttu-id="3e8ae-113">Element</span><span class="sxs-lookup"><span data-stu-id="3e8ae-113">Element</span></span>|<span data-ttu-id="3e8ae-114">Opis</span><span class="sxs-lookup"><span data-stu-id="3e8ae-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e8ae-115">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="3e8ae-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|<span data-ttu-id="3e8ae-116">Określa poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3e8ae-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3e8ae-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3e8ae-118">Element</span><span class="sxs-lookup"><span data-stu-id="3e8ae-118">Element</span></span>|<span data-ttu-id="3e8ae-119">Opis</span><span class="sxs-lookup"><span data-stu-id="3e8ae-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3e8ae-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="3e8ae-121">Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e8ae-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e8ae-122">Remarks</span></span>  
 <span data-ttu-id="3e8ae-123">Aby zmienić poziom przełącznika śledzenia, należy umieścić go w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="3e8ae-124">Jeśli przełącznik jest <xref:System.Diagnostics.BooleanSwitch>, możesz ją włączyć lub wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="3e8ae-125">Jeśli przełącznik jest <xref:System.Diagnostics.TraceSwitch>można przypisać różne poziomy, aby określić typy śledzenia i debugowania komunikatów dane wyjściowe aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e8ae-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e8ae-126">Example</span></span>  
 <span data-ttu-id="3e8ae-127">Poniższy przykład przedstawia użycie  **\<przełącznika >** element, aby ustawić `General` przełącznika śledzenia do <xref:System.Diagnostics.TraceLevel> poziomu, a następnie Włącz `Data` przełącznika logiczna śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3e8ae-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e8ae-128">See Also</span></span>  
 <xref:System.Diagnostics.Switch>  
 <xref:System.Diagnostics.TraceSwitch>  
 <xref:System.Diagnostics.BooleanSwitch>  
 [<span data-ttu-id="3e8ae-129">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="3e8ae-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
