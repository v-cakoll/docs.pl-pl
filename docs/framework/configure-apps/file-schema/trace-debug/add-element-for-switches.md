---
title: '&lt;Dodaj&gt; elementu &lt;przełączników&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e0dc425327f6577606e1205a23fdaffcc39f6e01
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-element-for-ltswitchesgt"></a><span data-ttu-id="4021e-102">&lt;Dodaj&gt; elementu &lt;przełączników&gt;</span><span class="sxs-lookup"><span data-stu-id="4021e-102">&lt;add&gt; Element for &lt;switches&gt;</span></span>
<span data-ttu-id="4021e-103">Określa poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4021e-103">Specifies the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="4021e-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="4021e-104">\<configuration></span></span>  
<span data-ttu-id="4021e-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="4021e-105">\<system.diagnostics></span></span>  
<span data-ttu-id="4021e-106">\<przełączniki ></span><span class="sxs-lookup"><span data-stu-id="4021e-106">\<switches></span></span>  
<span data-ttu-id="4021e-107">\<add></span><span class="sxs-lookup"><span data-stu-id="4021e-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4021e-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="4021e-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4021e-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4021e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4021e-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4021e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4021e-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4021e-111">Attributes</span></span>  
  
|<span data-ttu-id="4021e-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4021e-112">Attribute</span></span>|<span data-ttu-id="4021e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="4021e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4021e-114">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="4021e-114">**name**</span></span>|<span data-ttu-id="4021e-115">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="4021e-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="4021e-116">Określa nazwę tego przełącznika.</span><span class="sxs-lookup"><span data-stu-id="4021e-116">Specifies the name of the switch.</span></span> <span data-ttu-id="4021e-117">Wartość tego atrybutu odpowiada *displayName* parametr przekazany do konstruktora przełącznika.</span><span class="sxs-lookup"><span data-stu-id="4021e-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="4021e-118">**value**</span><span class="sxs-lookup"><span data-stu-id="4021e-118">**value**</span></span>|<span data-ttu-id="4021e-119">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="4021e-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="4021e-120">Określa poziom przełącznika.</span><span class="sxs-lookup"><span data-stu-id="4021e-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4021e-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4021e-121">Child Elements</span></span>  
 <span data-ttu-id="4021e-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="4021e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4021e-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4021e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4021e-124">Element</span><span class="sxs-lookup"><span data-stu-id="4021e-124">Element</span></span>|<span data-ttu-id="4021e-125">Opis</span><span class="sxs-lookup"><span data-stu-id="4021e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4021e-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4021e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="4021e-127">Zawiera przełączniki śledzenia i poziom, gdzie są ustawione przełączniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4021e-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4021e-128">Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4021e-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4021e-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4021e-129">Remarks</span></span>  
 <span data-ttu-id="4021e-130">Aby zmienić poziom przełącznika śledzenia, należy umieścić go w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4021e-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="4021e-131">Jeśli przełącznik jest <xref:System.Diagnostics.BooleanSwitch>, możesz ją włączyć lub wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="4021e-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="4021e-132">Jeśli przełącznik jest <xref:System.Diagnostics.TraceSwitch>można przypisać różne poziomy, aby określić typy śledzenia i debugowania komunikatów dane wyjściowe aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4021e-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4021e-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="4021e-133">Example</span></span>  
 <span data-ttu-id="4021e-134">Poniższy przykład przedstawia użycie  **\<Dodaj >** element, aby ustawić `General` przełącznika śledzenia do <xref:System.Diagnostics.TraceLevel> poziomu, a następnie Włącz `Data` przełącznika logiczna śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4021e-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4021e-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4021e-135">See Also</span></span>  
 <xref:System.Diagnostics.Switch>  
 <xref:System.Diagnostics.TraceSwitch>  
 <xref:System.Diagnostics.BooleanSwitch>  
 [<span data-ttu-id="4021e-136">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="4021e-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
