---
title: '&lt;endToEndTracing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb187302000291fd6b540b562ed7aebf1db7add2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltendtoendtracinggt"></a><span data-ttu-id="b7cc9-102">&lt;endToEndTracing&gt;</span><span class="sxs-lookup"><span data-stu-id="b7cc9-102">&lt;endToEndTracing&gt;</span></span>
<span data-ttu-id="b7cc9-103">Element konfiguracji, który umożliwia włączanie i wyłączanie różnych aspektów śledzenia end-to-end podczas uruchamiania aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="b7cc9-103">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="b7cc9-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b7cc9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b7cc9-105">\<diagnostycznych ></span><span class="sxs-lookup"><span data-stu-id="b7cc9-105">\<diagnostic></span></span>  
<span data-ttu-id="b7cc9-106">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="b7cc9-106">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7cc9-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="b7cc9-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7cc9-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b7cc9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b7cc9-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b7cc9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7cc9-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b7cc9-110">Attributes</span></span>  
  
|<span data-ttu-id="b7cc9-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b7cc9-111">Attribute</span></span>|<span data-ttu-id="b7cc9-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b7cc9-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="b7cc9-113">Wartość logiczna określająca, czy czynność śledzenia jest włączona.</span><span class="sxs-lookup"><span data-stu-id="b7cc9-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="b7cc9-114">Wartość logiczna określająca, czy jest włączone śledzenie przepływu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b7cc9-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="b7cc9-115">Wartość logiczna określająca, czy propagowany atrybut jest ustawiony na wartość true.</span><span class="sxs-lookup"><span data-stu-id="b7cc9-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7cc9-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b7cc9-116">Child Elements</span></span>  
 <span data-ttu-id="b7cc9-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="b7cc9-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b7cc9-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b7cc9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b7cc9-119">Element</span><span class="sxs-lookup"><span data-stu-id="b7cc9-119">Element</span></span>|<span data-ttu-id="b7cc9-120">Opis</span><span class="sxs-lookup"><span data-stu-id="b7cc9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7cc9-121">\<Diagnostyka ></span><span class="sxs-lookup"><span data-stu-id="b7cc9-121">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="b7cc9-122">Definiuje ustawienia WCF dla środowiska uruchomieniowego inspekcji i kontroli administratora.</span><span class="sxs-lookup"><span data-stu-id="b7cc9-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7cc9-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7cc9-123">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>  
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>  
 [<span data-ttu-id="b7cc9-124">Śledzenia end-to-End</span><span class="sxs-lookup"><span data-stu-id="b7cc9-124">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
