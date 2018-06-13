---
title: '&lt;przełączniki&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 60a18ae8d89d6be69b2c10c07064f123d3f9c0f8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745151"
---
# <a name="ltswitchesgt-element"></a><span data-ttu-id="4ce13-102">&lt;przełączniki&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="4ce13-102">&lt;switches&gt; Element</span></span>
<span data-ttu-id="4ce13-103">Zawiera przełączniki śledzenia i poziom, gdzie są ustawione przełączniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4ce13-103">Contains trace switches and the level where the trace switches are set.</span></span>  
  
 <span data-ttu-id="4ce13-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="4ce13-104">\<configuration></span></span>  
<span data-ttu-id="4ce13-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="4ce13-105">\<system.diagnostics></span></span>  
<span data-ttu-id="4ce13-106">\<przełączniki ></span><span class="sxs-lookup"><span data-stu-id="4ce13-106">\<switches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ce13-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ce13-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ce13-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4ce13-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4ce13-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4ce13-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ce13-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4ce13-110">Attributes</span></span>  
 <span data-ttu-id="4ce13-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="4ce13-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4ce13-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4ce13-112">Child Elements</span></span>  
  
|<span data-ttu-id="4ce13-113">Element</span><span class="sxs-lookup"><span data-stu-id="4ce13-113">Element</span></span>|<span data-ttu-id="4ce13-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4ce13-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ce13-115">\<add></span><span class="sxs-lookup"><span data-stu-id="4ce13-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|<span data-ttu-id="4ce13-116">Określa poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4ce13-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4ce13-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4ce13-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4ce13-118">Element</span><span class="sxs-lookup"><span data-stu-id="4ce13-118">Element</span></span>|<span data-ttu-id="4ce13-119">Opis</span><span class="sxs-lookup"><span data-stu-id="4ce13-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4ce13-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4ce13-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="4ce13-121">Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4ce13-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ce13-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ce13-122">Remarks</span></span>  
 <span data-ttu-id="4ce13-123">Aby zmienić poziom przełącznika śledzenia, należy umieścić go w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4ce13-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="4ce13-124">Jeśli przełącznik jest <xref:System.Diagnostics.BooleanSwitch>, możesz ją włączyć lub wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="4ce13-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="4ce13-125">Jeśli przełącznik jest <xref:System.Diagnostics.TraceSwitch>można przypisać różne poziomy, aby określić typy śledzenia i debugowania komunikatów dane wyjściowe aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4ce13-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ce13-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ce13-126">Example</span></span>  
 <span data-ttu-id="4ce13-127">Poniższy przykład przedstawia użycie  **\<przełącznika >** element, aby ustawić `General` przełącznika śledzenia do <xref:System.Diagnostics.TraceLevel> poziomu, a następnie Włącz `Data` przełącznika logiczna śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4ce13-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4ce13-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ce13-128">See Also</span></span>  
 <xref:System.Diagnostics.Switch>  
 <xref:System.Diagnostics.TraceSwitch>  
 <xref:System.Diagnostics.BooleanSwitch>  
 [<span data-ttu-id="4ce13-129">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="4ce13-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
