---
title: <remove>Element dla <listeners> elementu<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: 0c5c9efb8a22d26ea5d4467f9628af5935d6dbad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920474"
---
# <a name="remove-element-for-listeners-for-trace"></a><span data-ttu-id="39618-102">\<Usuń element > dla \<odbiorników \<> śledzenia ></span><span class="sxs-lookup"><span data-stu-id="39618-102">\<remove> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="39618-103">Usuwa odbiornik z kolekcji **odbiorników** .</span><span class="sxs-lookup"><span data-stu-id="39618-103">Removes a listener from the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="39618-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="39618-104">\<configuration></span></span>  
<span data-ttu-id="39618-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="39618-105">\<system.diagnostics></span></span>  
<span data-ttu-id="39618-106">\<> śledzenia</span><span class="sxs-lookup"><span data-stu-id="39618-106">\<trace></span></span>  
<span data-ttu-id="39618-107">\<> odbiorników</span><span class="sxs-lookup"><span data-stu-id="39618-107">\<listeners></span></span>  
<span data-ttu-id="39618-108">\<remove></span><span class="sxs-lookup"><span data-stu-id="39618-108">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39618-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="39618-109">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39618-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="39618-110">Attributes and Elements</span></span>  
 <span data-ttu-id="39618-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="39618-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39618-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="39618-112">Attributes</span></span>  
  
|<span data-ttu-id="39618-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="39618-113">Attribute</span></span>|<span data-ttu-id="39618-114">Opis</span><span class="sxs-lookup"><span data-stu-id="39618-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39618-115">**name**</span><span class="sxs-lookup"><span data-stu-id="39618-115">**name**</span></span>|<span data-ttu-id="39618-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="39618-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="39618-117">Nazwa odbiornika, który ma zostać usunięty z kolekcji **odbiorników** .</span><span class="sxs-lookup"><span data-stu-id="39618-117">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39618-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="39618-118">Child Elements</span></span>  
 <span data-ttu-id="39618-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="39618-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39618-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="39618-120">Parent Elements</span></span>  
  
|<span data-ttu-id="39618-121">Element</span><span class="sxs-lookup"><span data-stu-id="39618-121">Element</span></span>|<span data-ttu-id="39618-122">Opis</span><span class="sxs-lookup"><span data-stu-id="39618-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="39618-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="39618-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="39618-124">Określa odbiornik, który zbiera, przechowuje i kieruje komunikaty.</span><span class="sxs-lookup"><span data-stu-id="39618-124">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="39618-125">Odbiorniki kierują dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="39618-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="39618-126">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="39618-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="39618-127">Konfiguruje usługę śledzenia ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="39618-127">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39618-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39618-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39618-129"><xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>Usunięcie <xref:System.Diagnostics.DefaultTraceListener> <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>z kolekcji powoduje zmianę zachowania metod,, i<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> . `Listeners`</span><span class="sxs-lookup"><span data-stu-id="39618-129">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="39618-130">Wywołanie metody `Fail` <xref:System.Diagnostics.DefaultTraceListener> lub zwykle powoduje wyświetlenie okna komunikatu, ale okno komunikatu nie jest wyświetlane, jeśli nie znajduje się w `Listeners` kolekcji. `Assert`</span><span class="sxs-lookup"><span data-stu-id="39618-130">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39618-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="39618-131">Example</span></span>  
 <span data-ttu-id="39618-132">Poniższy przykład pokazuje, jak usunąć domyślny odbiornik śledzenia z kolekcji detektorów śledzenia .</span><span class="sxs-lookup"><span data-stu-id="39618-132">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="39618-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39618-133">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="39618-134">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="39618-134">Trace and Debug Settings Schema</span></span>](index.md)
