---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 6b23728451a051f21ad3863b9a29e6290c3c837a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919011"
---
# <a name="endtoendtracing"></a><span data-ttu-id="f6c0e-101">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="f6c0e-101">\<endToEndTracing></span></span>
<span data-ttu-id="f6c0e-102">Element konfiguracji, który pozwala na włączenie i wyłączenie różnych aspektów śledzenia end-to-end podczas uruchamiania aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="f6c0e-102">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="f6c0e-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f6c0e-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="f6c0e-104">\<> diagnostyki</span><span class="sxs-lookup"><span data-stu-id="f6c0e-104">\<diagnostic></span></span>  
<span data-ttu-id="f6c0e-105">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="f6c0e-105">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6c0e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6c0e-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6c0e-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f6c0e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f6c0e-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f6c0e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6c0e-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f6c0e-109">Attributes</span></span>  
  
|<span data-ttu-id="f6c0e-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f6c0e-110">Attribute</span></span>|<span data-ttu-id="f6c0e-111">Opis</span><span class="sxs-lookup"><span data-stu-id="f6c0e-111">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="f6c0e-112">Wartość logiczna określająca, czy włączone jest śledzenie aktywności.</span><span class="sxs-lookup"><span data-stu-id="f6c0e-112">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="f6c0e-113">Wartość logiczna określająca, czy włączone jest śledzenie przepływu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f6c0e-113">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="f6c0e-114">Wartość logiczna określająca, czy propagowany atrybut jest ustawiony na wartość true.</span><span class="sxs-lookup"><span data-stu-id="f6c0e-114">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6c0e-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f6c0e-115">Child Elements</span></span>  
 <span data-ttu-id="f6c0e-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="f6c0e-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6c0e-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f6c0e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f6c0e-118">Element</span><span class="sxs-lookup"><span data-stu-id="f6c0e-118">Element</span></span>|<span data-ttu-id="f6c0e-119">Opis</span><span class="sxs-lookup"><span data-stu-id="f6c0e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6c0e-120">\<> diagnostyki</span><span class="sxs-lookup"><span data-stu-id="f6c0e-120">\<diagnostics></span></span>](diagnostics.md)|<span data-ttu-id="f6c0e-121">Definiuje ustawienia WCF na potrzeby inspekcji i kontroli środowiska uruchomieniowego dla administratora.</span><span class="sxs-lookup"><span data-stu-id="f6c0e-121">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f6c0e-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6c0e-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="f6c0e-123">Kompleksowe śledzenie</span><span class="sxs-lookup"><span data-stu-id="f6c0e-123">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
