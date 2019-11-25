---
title: Element <remove> dla <listeners> <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: f06973ec30d5061e4a200d6bf7e68adcf6302018
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088835"
---
# <a name="remove-element-for-listeners-for-trace"></a><span data-ttu-id="9392c-102">\<usunąć elementu > dla odbiorników \<> \<śledzenia ></span><span class="sxs-lookup"><span data-stu-id="9392c-102">\<remove> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="9392c-103">Usuwa odbiornik z kolekcji **odbiorników** .</span><span class="sxs-lookup"><span data-stu-id="9392c-103">Removes a listener from the **Listeners** collection.</span></span>  

<span data-ttu-id="9392c-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="9392c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9392c-105">&nbsp;&nbsp;[ **\<system. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="9392c-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="9392c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Trace**](trace-element.md) ></span><span class="sxs-lookup"><span data-stu-id="9392c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="9392c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**odbiorników**](listeners-element-for-trace.md) ></span><span class="sxs-lookup"><span data-stu-id="9392c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="9392c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<usuń >**</span><span class="sxs-lookup"><span data-stu-id="9392c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9392c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="9392c-109">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9392c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9392c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9392c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9392c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9392c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9392c-112">Attributes</span></span>  
  
|<span data-ttu-id="9392c-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9392c-113">Attribute</span></span>|<span data-ttu-id="9392c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9392c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9392c-115">**Nazwij**</span><span class="sxs-lookup"><span data-stu-id="9392c-115">**name**</span></span>|<span data-ttu-id="9392c-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="9392c-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="9392c-117">Nazwa odbiornika, który ma zostać usunięty z kolekcji **odbiorników** .</span><span class="sxs-lookup"><span data-stu-id="9392c-117">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9392c-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9392c-118">Child Elements</span></span>  
 <span data-ttu-id="9392c-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="9392c-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9392c-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9392c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9392c-121">Element</span><span class="sxs-lookup"><span data-stu-id="9392c-121">Element</span></span>|<span data-ttu-id="9392c-122">Opis</span><span class="sxs-lookup"><span data-stu-id="9392c-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9392c-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9392c-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="9392c-124">Określa odbiornik, który zbiera, przechowuje i kieruje komunikaty.</span><span class="sxs-lookup"><span data-stu-id="9392c-124">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="9392c-125">Odbiorniki kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="9392c-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="9392c-126">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9392c-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="9392c-127">Konfiguruje usługę śledzenia ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9392c-127">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9392c-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9392c-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9392c-129">Usunięcie <xref:System.Diagnostics.DefaultTraceListener> z kolekcji `Listeners` zmienia zachowanie <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>i <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> metod.</span><span class="sxs-lookup"><span data-stu-id="9392c-129">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="9392c-130">Wywołanie metody `Assert` lub `Fail` zwykle powoduje wyświetlenie okna komunikatu, ale okno komunikatu nie jest wyświetlane, jeśli <xref:System.Diagnostics.DefaultTraceListener> nie znajduje się w kolekcji `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="9392c-130">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9392c-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="9392c-131">Example</span></span>  
 <span data-ttu-id="9392c-132">Poniższy przykład pokazuje, jak usunąć domyślny odbiornik śledzenia z kolekcji **detektorów** śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9392c-132">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <remove name="Default" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9392c-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9392c-133">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="9392c-134">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="9392c-134">Trace and Debug Settings Schema</span></span>](index.md)
