---
title: '&lt;enableWebScript&gt;'
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 1115b598776ca7d28698815974e06f3de57be598
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600105"
---
# <a name="ltenablewebscriptgt"></a><span data-ttu-id="4dd76-102">&lt;enableWebScript&gt;</span><span class="sxs-lookup"><span data-stu-id="4dd76-102">&lt;enableWebScript&gt;</span></span>
<span data-ttu-id="4dd76-103">Ten element włącza zachowanie punktu końcowego, który pozwala na korzystanie z usługi z ASP.NET AJAX stron sieci web.</span><span class="sxs-lookup"><span data-stu-id="4dd76-103">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="4dd76-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4dd76-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4dd76-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="4dd76-105">\<behaviors></span></span>  
<span data-ttu-id="4dd76-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="4dd76-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="4dd76-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="4dd76-107">\<behavior></span></span>  
<span data-ttu-id="4dd76-108">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="4dd76-108">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dd76-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="4dd76-109">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4dd76-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4dd76-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4dd76-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4dd76-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4dd76-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4dd76-112">Attributes</span></span>  
 <span data-ttu-id="4dd76-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="4dd76-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4dd76-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4dd76-114">Child Elements</span></span>  
 <span data-ttu-id="4dd76-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="4dd76-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4dd76-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4dd76-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4dd76-117">Element</span><span class="sxs-lookup"><span data-stu-id="4dd76-117">Element</span></span>|<span data-ttu-id="4dd76-118">Opis</span><span class="sxs-lookup"><span data-stu-id="4dd76-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4dd76-119">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="4dd76-119">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="4dd76-120">Określa zestaw zachowań punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="4dd76-120">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4dd76-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4dd76-121">Remarks</span></span>  
 <span data-ttu-id="4dd76-122">To zachowanie należy używać tylko w połączeniu z oboma [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) Powiązanie standardowe lub [ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) element powiązania.</span><span class="sxs-lookup"><span data-stu-id="4dd76-122">This behavior should only be used in conjunction with either the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="4dd76-123">Aby uzyskać więcej informacji na temat tego zachowania, zobacz <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="4dd76-123">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dd76-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4dd76-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="4dd76-125">Obsługa integracji AJAX i notacji JSON</span><span class="sxs-lookup"><span data-stu-id="4dd76-125">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="4dd76-126">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="4dd76-126">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
