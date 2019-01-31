---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 063dbee71a91e098e26026ea78c74642115c7955
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266666"
---
# <a name="clientvia"></a><span data-ttu-id="78090-101">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="78090-101">\<clientVia></span></span>
<span data-ttu-id="78090-102">Określa identyfikator URI, dla którego należy utworzyć kanał transportu.</span><span class="sxs-lookup"><span data-stu-id="78090-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="78090-103">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="78090-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="78090-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="78090-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="78090-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="78090-105">\<behaviors></span></span>  
<span data-ttu-id="78090-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="78090-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="78090-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="78090-107">\<behavior></span></span>  
<span data-ttu-id="78090-108">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="78090-108">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78090-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="78090-109">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78090-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="78090-110">Attributes and Elements</span></span>  
 <span data-ttu-id="78090-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="78090-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78090-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="78090-112">Attributes</span></span>  
  
|<span data-ttu-id="78090-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="78090-113">Attribute</span></span>|<span data-ttu-id="78090-114">Opis</span><span class="sxs-lookup"><span data-stu-id="78090-114">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="78090-115">Ciąg, który określa identyfikator URI wskazujący trasę wyznaczoną dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="78090-115">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78090-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="78090-116">Child Elements</span></span>  
 <span data-ttu-id="78090-117">Brak</span><span class="sxs-lookup"><span data-stu-id="78090-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="78090-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="78090-118">Parent Elements</span></span>  
  
|<span data-ttu-id="78090-119">Element</span><span class="sxs-lookup"><span data-stu-id="78090-119">Element</span></span>|<span data-ttu-id="78090-120">Opis</span><span class="sxs-lookup"><span data-stu-id="78090-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78090-121">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="78090-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="78090-122">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="78090-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="78090-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78090-123">See also</span></span>
- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
