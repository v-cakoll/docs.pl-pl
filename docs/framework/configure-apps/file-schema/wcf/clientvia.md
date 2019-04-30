---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: b8864760c1700cd785922b922346204d194f56cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673631"
---
# <a name="clientvia"></a><span data-ttu-id="9df9e-101">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="9df9e-101">\<clientVia></span></span>
<span data-ttu-id="9df9e-102">Określa identyfikator URI, dla którego należy utworzyć kanał transportu.</span><span class="sxs-lookup"><span data-stu-id="9df9e-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="9df9e-103">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="9df9e-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="9df9e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9df9e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9df9e-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="9df9e-105">\<behaviors></span></span>  
<span data-ttu-id="9df9e-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="9df9e-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="9df9e-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="9df9e-107">\<behavior></span></span>  
<span data-ttu-id="9df9e-108">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="9df9e-108">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9df9e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="9df9e-109">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9df9e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9df9e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9df9e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9df9e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9df9e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9df9e-112">Attributes</span></span>  
  
|<span data-ttu-id="9df9e-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9df9e-113">Attribute</span></span>|<span data-ttu-id="9df9e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9df9e-114">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="9df9e-115">Ciąg, który określa identyfikator URI wskazujący trasę wyznaczoną dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9df9e-115">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9df9e-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9df9e-116">Child Elements</span></span>  
 <span data-ttu-id="9df9e-117">Brak</span><span class="sxs-lookup"><span data-stu-id="9df9e-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9df9e-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9df9e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9df9e-119">Element</span><span class="sxs-lookup"><span data-stu-id="9df9e-119">Element</span></span>|<span data-ttu-id="9df9e-120">Opis</span><span class="sxs-lookup"><span data-stu-id="9df9e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9df9e-121">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="9df9e-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="9df9e-122">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="9df9e-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9df9e-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9df9e-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
