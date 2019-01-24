---
title: '&lt;endToEndTracing&gt;'
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: c2f5e33eff4fdc6dfa85bcc10b59a7c1436cabb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519398"
---
# <a name="ltendtoendtracinggt"></a><span data-ttu-id="cf4f6-102">&lt;endToEndTracing&gt;</span><span class="sxs-lookup"><span data-stu-id="cf4f6-102">&lt;endToEndTracing&gt;</span></span>
<span data-ttu-id="cf4f6-103">Element konfiguracji, który umożliwia włączanie i wyłączanie różnych aspektów śledzenia end-to-end podczas uruchamiania aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="cf4f6-103">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="cf4f6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cf4f6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cf4f6-105">\<diagnostyczne ></span><span class="sxs-lookup"><span data-stu-id="cf4f6-105">\<diagnostic></span></span>  
<span data-ttu-id="cf4f6-106">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="cf4f6-106">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf4f6-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="cf4f6-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf4f6-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cf4f6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="cf4f6-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cf4f6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf4f6-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cf4f6-110">Attributes</span></span>  
  
|<span data-ttu-id="cf4f6-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cf4f6-111">Attribute</span></span>|<span data-ttu-id="cf4f6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="cf4f6-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="cf4f6-113">Wartość logiczna określająca, czy czynność śledzenia jest włączona.</span><span class="sxs-lookup"><span data-stu-id="cf4f6-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="cf4f6-114">Wartość logiczna określająca, czy jest włączone śledzenie przepływu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="cf4f6-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="cf4f6-115">Wartość logiczna określająca, czy propagowany atrybut jest ustawiony na wartość true.</span><span class="sxs-lookup"><span data-stu-id="cf4f6-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf4f6-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cf4f6-116">Child Elements</span></span>  
 <span data-ttu-id="cf4f6-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="cf4f6-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cf4f6-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cf4f6-118">Parent Elements</span></span>  
  
|<span data-ttu-id="cf4f6-119">Element</span><span class="sxs-lookup"><span data-stu-id="cf4f6-119">Element</span></span>|<span data-ttu-id="cf4f6-120">Opis</span><span class="sxs-lookup"><span data-stu-id="cf4f6-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf4f6-121">\<Diagnostyka ></span><span class="sxs-lookup"><span data-stu-id="cf4f6-121">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="cf4f6-122">Definiuje ustawienia WCF dla środowiska uruchomieniowego kontroli i kontroli dla administratora.</span><span class="sxs-lookup"><span data-stu-id="cf4f6-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf4f6-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf4f6-123">See also</span></span>
- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="cf4f6-124">Kompleksowe śledzenie</span><span class="sxs-lookup"><span data-stu-id="cf4f6-124">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
