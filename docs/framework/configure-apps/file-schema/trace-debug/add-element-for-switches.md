---
title: <add>, element dla <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: d7500620aed1165ff365fee8529230ba252dbc4b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673813"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="f1287-102">\<Dodaj >, Element dla \<przełączników ></span><span class="sxs-lookup"><span data-stu-id="f1287-102">\<add> Element for \<switches></span></span>
<span data-ttu-id="f1287-103">Określa poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f1287-103">Specifies the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="f1287-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="f1287-104">\<configuration></span></span>  
<span data-ttu-id="f1287-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="f1287-105">\<system.diagnostics></span></span>  
<span data-ttu-id="f1287-106">\<przełączniki ></span><span class="sxs-lookup"><span data-stu-id="f1287-106">\<switches></span></span>  
<span data-ttu-id="f1287-107">\<add></span><span class="sxs-lookup"><span data-stu-id="f1287-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1287-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1287-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1287-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f1287-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f1287-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f1287-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1287-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f1287-111">Attributes</span></span>  
  
|<span data-ttu-id="f1287-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f1287-112">Attribute</span></span>|<span data-ttu-id="f1287-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f1287-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f1287-114">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="f1287-114">**name**</span></span>|<span data-ttu-id="f1287-115">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="f1287-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="f1287-116">Określa nazwę przełącznika.</span><span class="sxs-lookup"><span data-stu-id="f1287-116">Specifies the name of the switch.</span></span> <span data-ttu-id="f1287-117">Wartość tego atrybutu odnosi się do *displayName* parametr, który jest przekazywany do konstruktora przełącznika.</span><span class="sxs-lookup"><span data-stu-id="f1287-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="f1287-118">**value**</span><span class="sxs-lookup"><span data-stu-id="f1287-118">**value**</span></span>|<span data-ttu-id="f1287-119">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="f1287-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="f1287-120">Określa poziom przełącznika.</span><span class="sxs-lookup"><span data-stu-id="f1287-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1287-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f1287-121">Child Elements</span></span>  
 <span data-ttu-id="f1287-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="f1287-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f1287-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f1287-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f1287-124">Element</span><span class="sxs-lookup"><span data-stu-id="f1287-124">Element</span></span>|<span data-ttu-id="f1287-125">Opis</span><span class="sxs-lookup"><span data-stu-id="f1287-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f1287-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f1287-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="f1287-127">Zawiera przełączniki śledzenia i poziomu, gdzie są ustawione przełączniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f1287-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="f1287-128">Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f1287-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1287-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f1287-129">Remarks</span></span>  
 <span data-ttu-id="f1287-130">Aby zmienić poziom o przełącznikiem śledzenia, należy umieścić go w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f1287-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="f1287-131">Jeśli przełącznik <xref:System.Diagnostics.BooleanSwitch>, możesz je włączyć lub wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="f1287-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="f1287-132">Jeśli przełącznik <xref:System.Diagnostics.TraceSwitch>można przypisać różne poziomy, aby określić typy śledzenia i debugowania komunikaty wyjściowe aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f1287-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1287-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="f1287-133">Example</span></span>  
 <span data-ttu-id="f1287-134">Poniższy przykład pokazuje, jak używać  **\<Dodaj >** element, aby ustawić `General` przełącznikiem śledzenia do <xref:System.Diagnostics.TraceLevel> poziomu i włączyć `Data` przełącznikiem logiczna śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f1287-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f1287-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1287-135">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="f1287-136">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="f1287-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
