---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 1a274f15800c6a132994a2437943c83982de9de0
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855299"
---
# <a name="endtoendtracing"></a><span data-ttu-id="f9c78-101">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="f9c78-101">\<endToEndTracing></span></span>
<span data-ttu-id="f9c78-102">Element konfiguracji, który pozwala na włączenie i wyłączenie różnych aspektów śledzenia end-to-end podczas uruchamiania aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="f9c78-102">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
<span data-ttu-id="f9c78-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f9c78-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f9c78-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f9c78-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f9c78-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> diagnostyki**](diagnostics.md)</span><span class="sxs-lookup"><span data-stu-id="f9c78-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)</span></span>\
<span data-ttu-id="f9c78-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<endToEndTracing >**</span><span class="sxs-lookup"><span data-stu-id="f9c78-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endToEndTracing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9c78-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9c78-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9c78-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f9c78-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f9c78-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f9c78-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9c78-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f9c78-110">Attributes</span></span>  
  
|<span data-ttu-id="f9c78-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f9c78-111">Attribute</span></span>|<span data-ttu-id="f9c78-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f9c78-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="f9c78-113">Wartość logiczna określająca, czy włączone jest śledzenie aktywności.</span><span class="sxs-lookup"><span data-stu-id="f9c78-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="f9c78-114">Wartość logiczna określająca, czy włączone jest śledzenie przepływu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f9c78-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="f9c78-115">Wartość logiczna określająca, czy propagowany atrybut jest ustawiony na wartość true.</span><span class="sxs-lookup"><span data-stu-id="f9c78-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9c78-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f9c78-116">Child Elements</span></span>  
 <span data-ttu-id="f9c78-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="f9c78-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9c78-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f9c78-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f9c78-119">Element</span><span class="sxs-lookup"><span data-stu-id="f9c78-119">Element</span></span>|<span data-ttu-id="f9c78-120">Opis</span><span class="sxs-lookup"><span data-stu-id="f9c78-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9c78-121">\<> diagnostyki</span><span class="sxs-lookup"><span data-stu-id="f9c78-121">\<diagnostics></span></span>](diagnostics.md)|<span data-ttu-id="f9c78-122">Definiuje ustawienia WCF na potrzeby inspekcji i kontroli środowiska uruchomieniowego dla administratora.</span><span class="sxs-lookup"><span data-stu-id="f9c78-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9c78-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9c78-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="f9c78-124">Kompleksowe śledzenie</span><span class="sxs-lookup"><span data-stu-id="f9c78-124">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
