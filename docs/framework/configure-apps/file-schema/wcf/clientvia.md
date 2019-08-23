---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: b12a882d942555a24c145b243d2cea764ba106b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919504"
---
# <a name="clientvia"></a><span data-ttu-id="c2367-101">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="c2367-101">\<clientVia></span></span>
<span data-ttu-id="c2367-102">Określa identyfikator URI, dla którego należy utworzyć kanał transportu.</span><span class="sxs-lookup"><span data-stu-id="c2367-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="c2367-103">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="c2367-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="c2367-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c2367-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c2367-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="c2367-105">\<behaviors></span></span>  
<span data-ttu-id="c2367-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="c2367-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="c2367-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="c2367-107">\<behavior></span></span>  
<span data-ttu-id="c2367-108">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="c2367-108">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2367-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2367-109">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2367-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c2367-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c2367-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c2367-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2367-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c2367-112">Attributes</span></span>  
  
|<span data-ttu-id="c2367-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c2367-113">Attribute</span></span>|<span data-ttu-id="c2367-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c2367-114">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="c2367-115">Ciąg określający identyfikator URI, który wskazuje trasę, którą powinien wykonać komunikat.</span><span class="sxs-lookup"><span data-stu-id="c2367-115">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2367-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c2367-116">Child Elements</span></span>  
 <span data-ttu-id="c2367-117">Brak</span><span class="sxs-lookup"><span data-stu-id="c2367-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c2367-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c2367-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c2367-119">Element</span><span class="sxs-lookup"><span data-stu-id="c2367-119">Element</span></span>|<span data-ttu-id="c2367-120">Opis</span><span class="sxs-lookup"><span data-stu-id="c2367-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2367-121">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="c2367-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c2367-122">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c2367-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2367-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2367-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
