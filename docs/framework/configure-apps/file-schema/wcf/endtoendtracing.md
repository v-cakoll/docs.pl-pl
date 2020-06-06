---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 1a274f15800c6a132994a2437943c83982de9de0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855299"
---
# \<endToEndTracing>
<span data-ttu-id="88ef9-101">Element konfiguracji, który pozwala na włączenie i wyłączenie różnych aspektów śledzenia end-to-end podczas uruchamiania aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="88ef9-101">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endToEndTracing>**  
  
## <a name="syntax"></a><span data-ttu-id="88ef9-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="88ef9-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88ef9-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="88ef9-103">Attributes and Elements</span></span>  
 <span data-ttu-id="88ef9-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="88ef9-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88ef9-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="88ef9-105">Attributes</span></span>  
  
|<span data-ttu-id="88ef9-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="88ef9-106">Attribute</span></span>|<span data-ttu-id="88ef9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="88ef9-107">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="88ef9-108">Wartość logiczna określająca, czy włączone jest śledzenie aktywności.</span><span class="sxs-lookup"><span data-stu-id="88ef9-108">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="88ef9-109">Wartość logiczna określająca, czy włączone jest śledzenie przepływu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="88ef9-109">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="88ef9-110">Wartość logiczna określająca, czy propagowany atrybut jest ustawiony na wartość true.</span><span class="sxs-lookup"><span data-stu-id="88ef9-110">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88ef9-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="88ef9-111">Child Elements</span></span>  
 <span data-ttu-id="88ef9-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="88ef9-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="88ef9-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="88ef9-113">Parent Elements</span></span>  
  
|<span data-ttu-id="88ef9-114">Element</span><span class="sxs-lookup"><span data-stu-id="88ef9-114">Element</span></span>|<span data-ttu-id="88ef9-115">Opis</span><span class="sxs-lookup"><span data-stu-id="88ef9-115">Description</span></span>|  
|-------------|-----------------|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="88ef9-116">Definiuje ustawienia WCF na potrzeby inspekcji i kontroli środowiska uruchomieniowego dla administratora.</span><span class="sxs-lookup"><span data-stu-id="88ef9-116">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="88ef9-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88ef9-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="88ef9-118">Kompleksowe śledzenie</span><span class="sxs-lookup"><span data-stu-id="88ef9-118">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
