---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 123f58ee3d77bf605db21fa0d9537b3196d56468
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919111"
---
# <a name="enablewebscript"></a><span data-ttu-id="6a0e3-101">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="6a0e3-101">\<enableWebScript></span></span>
<span data-ttu-id="6a0e3-102">Ten element włącza zachowanie punktu końcowego, który umożliwia korzystanie z usługi z ASP.NET AJAX stron sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6a0e3-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="6a0e3-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6a0e3-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="6a0e3-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="6a0e3-104">\<behaviors></span></span>  
<span data-ttu-id="6a0e3-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="6a0e3-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="6a0e3-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="6a0e3-106">\<behavior></span></span>  
<span data-ttu-id="6a0e3-107">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="6a0e3-107">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a0e3-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a0e3-108">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a0e3-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6a0e3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6a0e3-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6a0e3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a0e3-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6a0e3-111">Attributes</span></span>  
 <span data-ttu-id="6a0e3-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="6a0e3-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6a0e3-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6a0e3-113">Child Elements</span></span>  
 <span data-ttu-id="6a0e3-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="6a0e3-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6a0e3-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6a0e3-115">Parent Elements</span></span>  
  
|<span data-ttu-id="6a0e3-116">Element</span><span class="sxs-lookup"><span data-stu-id="6a0e3-116">Element</span></span>|<span data-ttu-id="6a0e3-117">Opis</span><span class="sxs-lookup"><span data-stu-id="6a0e3-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a0e3-118">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="6a0e3-118">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="6a0e3-119">Określa zestaw zachowań punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="6a0e3-119">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a0e3-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a0e3-120">Remarks</span></span>  
 <span data-ttu-id="6a0e3-121">Tego zachowania należy używać tylko w połączeniu z [ \<](webhttpbinding.md) elementem WebHttpBinding > [ \<](webmessageencoding.md) powiązanie standardowe lub webMessageEncoding > powiązania.</span><span class="sxs-lookup"><span data-stu-id="6a0e3-121">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="6a0e3-122">Aby uzyskać więcej informacji na temat tego zachowania <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>, zobacz.</span><span class="sxs-lookup"><span data-stu-id="6a0e3-122">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a0e3-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a0e3-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="6a0e3-124">Obsługa integracji AJAX i notacji JSON</span><span class="sxs-lookup"><span data-stu-id="6a0e3-124">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="6a0e3-125">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="6a0e3-125">\<webHttp></span></span>](webhttp.md)
