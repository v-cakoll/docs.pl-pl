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
ms.openlocfilehash: 15cc9680d7a20341eb5d1d1df302c1e034e70e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153233"
---
# <a name="switches-element"></a><span data-ttu-id="3b90c-102">\<przełączniki> Element</span><span class="sxs-lookup"><span data-stu-id="3b90c-102">\<switches> Element</span></span>
<span data-ttu-id="3b90c-103">Zawiera przełączniki śledzenia i poziom, na którym są ustawione przełączniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3b90c-103">Contains trace switches and the level where the trace switches are set.</span></span>  

<span data-ttu-id="3b90c-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3b90c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3b90c-105">&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="3b90c-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="3b90c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<przełączniki>**</span><span class="sxs-lookup"><span data-stu-id="3b90c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3b90c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="3b90c-107">Syntax</span></span>  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b90c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3b90c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3b90c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3b90c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b90c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3b90c-110">Attributes</span></span>  
 <span data-ttu-id="3b90c-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="3b90c-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3b90c-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3b90c-112">Child Elements</span></span>  
  
|<span data-ttu-id="3b90c-113">Element</span><span class="sxs-lookup"><span data-stu-id="3b90c-113">Element</span></span>|<span data-ttu-id="3b90c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="3b90c-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3b90c-115">\<dodaj></span><span class="sxs-lookup"><span data-stu-id="3b90c-115">\<add></span></span>](add-element-for-switches.md)|<span data-ttu-id="3b90c-116">Określa poziom, na którym ustawiony jest przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3b90c-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3b90c-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3b90c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3b90c-118">Element</span><span class="sxs-lookup"><span data-stu-id="3b90c-118">Element</span></span>|<span data-ttu-id="3b90c-119">Opis</span><span class="sxs-lookup"><span data-stu-id="3b90c-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3b90c-120">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3b90c-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="3b90c-121">Określa odbiorniki śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, na którym ustawiony jest przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3b90c-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b90c-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3b90c-122">Remarks</span></span>  
 <span data-ttu-id="3b90c-123">Można zmienić poziom przełącznika śledzenia, umieszczając go w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="3b90c-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="3b90c-124">Jeśli przełącznik jest <xref:System.Diagnostics.BooleanSwitch>, można go włączyć i wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="3b90c-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="3b90c-125">Jeśli przełącznik jest <xref:System.Diagnostics.TraceSwitch>, można przypisać różne poziomy do niego, aby określić typy śledzenia lub debugowania komunikatów danych wyjściowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3b90c-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b90c-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b90c-126">Example</span></span>  
 <span data-ttu-id="3b90c-127">W poniższym przykładzie pokazano, jak użyć \*\* \<switch>\*\* element, aby ustawić `Data` przełącznik `General` śledzenia do <xref:System.Diagnostics.TraceLevel> poziomu i włączyć przełącznik śledzenia logicznego.</span><span class="sxs-lookup"><span data-stu-id="3b90c-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3b90c-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b90c-128">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="3b90c-129">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="3b90c-129">Trace and Debug Settings Schema</span></span>](index.md)
