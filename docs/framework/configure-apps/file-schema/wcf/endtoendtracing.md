---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 266b33e9b0386d0346a86ba8bd82cc65def4f0c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180157"
---
# <a name="endtoendtracing"></a><span data-ttu-id="92f1c-101">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="92f1c-101">\<endToEndTracing></span></span>
<span data-ttu-id="92f1c-102">Element konfiguracji, który umożliwia włączanie i wyłączanie różnych aspektów śledzenia end-to-end podczas uruchamiania aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="92f1c-102">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="92f1c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="92f1c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="92f1c-104">\<diagnostyczne ></span><span class="sxs-lookup"><span data-stu-id="92f1c-104">\<diagnostic></span></span>  
<span data-ttu-id="92f1c-105">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="92f1c-105">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92f1c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="92f1c-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92f1c-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="92f1c-107">Attributes and Elements</span></span>  
 <span data-ttu-id="92f1c-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="92f1c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92f1c-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="92f1c-109">Attributes</span></span>  
  
|<span data-ttu-id="92f1c-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="92f1c-110">Attribute</span></span>|<span data-ttu-id="92f1c-111">Opis</span><span class="sxs-lookup"><span data-stu-id="92f1c-111">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="92f1c-112">Wartość logiczna określająca, czy czynność śledzenia jest włączona.</span><span class="sxs-lookup"><span data-stu-id="92f1c-112">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="92f1c-113">Wartość logiczna określająca, czy jest włączone śledzenie przepływu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="92f1c-113">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="92f1c-114">Wartość logiczna określająca, czy propagowany atrybut jest ustawiony na wartość true.</span><span class="sxs-lookup"><span data-stu-id="92f1c-114">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="92f1c-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="92f1c-115">Child Elements</span></span>  
 <span data-ttu-id="92f1c-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="92f1c-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="92f1c-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="92f1c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="92f1c-118">Element</span><span class="sxs-lookup"><span data-stu-id="92f1c-118">Element</span></span>|<span data-ttu-id="92f1c-119">Opis</span><span class="sxs-lookup"><span data-stu-id="92f1c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92f1c-120">\<Diagnostyka ></span><span class="sxs-lookup"><span data-stu-id="92f1c-120">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="92f1c-121">Definiuje ustawienia WCF dla środowiska uruchomieniowego kontroli i kontroli dla administratora.</span><span class="sxs-lookup"><span data-stu-id="92f1c-121">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92f1c-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92f1c-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="92f1c-123">Kompleksowe śledzenie</span><span class="sxs-lookup"><span data-stu-id="92f1c-123">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
