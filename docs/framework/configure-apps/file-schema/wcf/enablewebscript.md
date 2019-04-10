---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: b2cdd29cda7f82ce555b0f6c1a963567b41ff81b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213002"
---
# <a name="enablewebscript"></a><span data-ttu-id="88179-101">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="88179-101">\<enableWebScript></span></span>
<span data-ttu-id="88179-102">Ten element włącza zachowanie punktu końcowego, który pozwala na korzystanie z usługi z ASP.NET AJAX stron sieci web.</span><span class="sxs-lookup"><span data-stu-id="88179-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="88179-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="88179-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="88179-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="88179-104">\<behaviors></span></span>  
<span data-ttu-id="88179-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="88179-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="88179-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="88179-106">\<behavior></span></span>  
<span data-ttu-id="88179-107">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="88179-107">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88179-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="88179-108">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88179-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="88179-109">Attributes and Elements</span></span>  
 <span data-ttu-id="88179-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="88179-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88179-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="88179-111">Attributes</span></span>  
 <span data-ttu-id="88179-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="88179-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="88179-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="88179-113">Child Elements</span></span>  
 <span data-ttu-id="88179-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="88179-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="88179-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="88179-115">Parent Elements</span></span>  
  
|<span data-ttu-id="88179-116">Element</span><span class="sxs-lookup"><span data-stu-id="88179-116">Element</span></span>|<span data-ttu-id="88179-117">Opis</span><span class="sxs-lookup"><span data-stu-id="88179-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88179-118">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="88179-118">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="88179-119">Określa zestaw zachowań punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="88179-119">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88179-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88179-120">Remarks</span></span>  
 <span data-ttu-id="88179-121">To zachowanie należy używać tylko w połączeniu z oboma [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) Powiązanie standardowe lub [ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) element powiązania.</span><span class="sxs-lookup"><span data-stu-id="88179-121">This behavior should only be used in conjunction with either the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="88179-122">Aby uzyskać więcej informacji na temat tego zachowania, zobacz <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="88179-122">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88179-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88179-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="88179-124">Obsługa integracji AJAX i notacji JSON</span><span class="sxs-lookup"><span data-stu-id="88179-124">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="88179-125">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="88179-125">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
