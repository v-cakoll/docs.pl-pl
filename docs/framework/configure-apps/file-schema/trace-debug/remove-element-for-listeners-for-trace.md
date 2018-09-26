---
title: '&lt;Usuń&gt; elementu &lt;odbiorników&gt; dla &lt;śledzenia&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 54fd529c571c8e8cf43c5dabe2398ae4a6cf4f11
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47230985"
---
# <a name="ltremovegt-element-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="6d423-102">&lt;Usuń&gt; elementu &lt;odbiorników&gt; dla &lt;śledzenia&gt;</span><span class="sxs-lookup"><span data-stu-id="6d423-102">&lt;remove&gt; Element for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="6d423-103">Usuwa odbiornik z **odbiorników** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6d423-103">Removes a listener from the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="6d423-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="6d423-104">\<configuration></span></span>  
<span data-ttu-id="6d423-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="6d423-105">\<system.diagnostics></span></span>  
<span data-ttu-id="6d423-106">\<śledzenia ></span><span class="sxs-lookup"><span data-stu-id="6d423-106">\<trace></span></span>  
<span data-ttu-id="6d423-107">\<odbiorniki ></span><span class="sxs-lookup"><span data-stu-id="6d423-107">\<listeners></span></span>  
<span data-ttu-id="6d423-108">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="6d423-108">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d423-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d423-109">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d423-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6d423-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6d423-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6d423-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d423-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6d423-112">Attributes</span></span>  
  
|<span data-ttu-id="6d423-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6d423-113">Attribute</span></span>|<span data-ttu-id="6d423-114">Opis</span><span class="sxs-lookup"><span data-stu-id="6d423-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6d423-115">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="6d423-115">**name**</span></span>|<span data-ttu-id="6d423-116">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="6d423-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="6d423-117">Nazwa odbiornika do usunięcia z **odbiorników** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6d423-117">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d423-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6d423-118">Child Elements</span></span>  
 <span data-ttu-id="6d423-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="6d423-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6d423-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6d423-120">Parent Elements</span></span>  
  
|<span data-ttu-id="6d423-121">Element</span><span class="sxs-lookup"><span data-stu-id="6d423-121">Element</span></span>|<span data-ttu-id="6d423-122">Opis</span><span class="sxs-lookup"><span data-stu-id="6d423-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6d423-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6d423-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="6d423-124">Określa odbiornik, który zbiera, magazynów i przekazuje komunikaty.</span><span class="sxs-lookup"><span data-stu-id="6d423-124">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="6d423-125">Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="6d423-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6d423-126">Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="6d423-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="6d423-127">Konfiguruje usługę śledzenia programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6d423-127">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d423-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d423-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d423-129">Usuwanie <xref:System.Diagnostics.DefaultTraceListener> z `Listeners` kolekcji zmienia zachowanie <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, i <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="6d423-129">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="6d423-130">Wywoływanie `Assert` lub `Fail` metoda zwykle nie powoduje wyświetlanie okna komunikatu, ale nie zostanie wyświetlone okno komunikatu, jeśli <xref:System.Diagnostics.DefaultTraceListener> nie znajduje się w `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6d423-130">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d423-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="6d423-131">Example</span></span>  
 <span data-ttu-id="6d423-132">Poniższy przykład pokazuje, jak usunąć odbiornik śledzenia domyślnego z śledzenia **odbiorników** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6d423-132">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6d423-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d423-133">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 [<span data-ttu-id="6d423-134">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="6d423-134">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
