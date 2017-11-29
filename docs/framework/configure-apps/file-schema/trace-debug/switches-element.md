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
ms.openlocfilehash: 6240f8192f2a31faeb81528e54481eb06cc04d04
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltswitchesgt-element"></a><span data-ttu-id="f5875-102">&lt;przełączniki&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="f5875-102">&lt;switches&gt; Element</span></span>
<span data-ttu-id="f5875-103">Zawiera przełączniki śledzenia i poziom, gdzie są ustawione przełączniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f5875-103">Contains trace switches and the level where the trace switches are set.</span></span>  
  
 <span data-ttu-id="f5875-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="f5875-104">\<configuration></span></span>  
<span data-ttu-id="f5875-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="f5875-105">\<system.diagnostics></span></span>  
<span data-ttu-id="f5875-106">\<przełączniki ></span><span class="sxs-lookup"><span data-stu-id="f5875-106">\<switches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5875-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5875-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5875-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f5875-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f5875-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f5875-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5875-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f5875-110">Attributes</span></span>  
 <span data-ttu-id="f5875-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="f5875-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f5875-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f5875-112">Child Elements</span></span>  
  
|<span data-ttu-id="f5875-113">Element</span><span class="sxs-lookup"><span data-stu-id="f5875-113">Element</span></span>|<span data-ttu-id="f5875-114">Opis</span><span class="sxs-lookup"><span data-stu-id="f5875-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f5875-115">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="f5875-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|<span data-ttu-id="f5875-116">Określa poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f5875-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f5875-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f5875-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f5875-118">Element</span><span class="sxs-lookup"><span data-stu-id="f5875-118">Element</span></span>|<span data-ttu-id="f5875-119">Opis</span><span class="sxs-lookup"><span data-stu-id="f5875-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f5875-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f5875-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="f5875-121">Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f5875-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5875-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5875-122">Remarks</span></span>  
 <span data-ttu-id="f5875-123">Aby zmienić poziom przełącznika śledzenia, należy umieścić go w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f5875-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="f5875-124">Jeśli przełącznik jest <xref:System.Diagnostics.BooleanSwitch>, możesz ją włączyć lub wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="f5875-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="f5875-125">Jeśli przełącznik jest <xref:System.Diagnostics.TraceSwitch>można przypisać różne poziomy, aby określić typy śledzenia i debugowania komunikatów dane wyjściowe aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f5875-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5875-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5875-126">Example</span></span>  
 <span data-ttu-id="f5875-127">Poniższy przykład przedstawia użycie  **\<przełącznika >** element, aby ustawić `General` przełącznika śledzenia do <xref:System.Diagnostics.TraceLevel> poziomu, a następnie Włącz `Data` przełącznika logiczna śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f5875-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f5875-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5875-128">See Also</span></span>  
 <xref:System.Diagnostics.Switch>  
 <xref:System.Diagnostics.TraceSwitch>  
 <xref:System.Diagnostics.BooleanSwitch>  
 [<span data-ttu-id="f5875-129">Schemat ustawień debugowania i śledzenia</span><span class="sxs-lookup"><span data-stu-id="f5875-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
