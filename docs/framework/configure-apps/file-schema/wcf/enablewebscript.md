---
title: '&lt;enableWebScript&gt;'
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: b14923c1b9a80bcd1c47db0e4fad6a6224b95329
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751899"
---
# <a name="ltenablewebscriptgt"></a><span data-ttu-id="cb21f-102">&lt;enableWebScript&gt;</span><span class="sxs-lookup"><span data-stu-id="cb21f-102">&lt;enableWebScript&gt;</span></span>
<span data-ttu-id="cb21f-103">Ten element włącza zachowanie punktu końcowego, który pozwala na korzystanie z usługi z ASP.NET AJAX stron sieci web.</span><span class="sxs-lookup"><span data-stu-id="cb21f-103">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="cb21f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cb21f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cb21f-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="cb21f-105">\<behaviors></span></span>  
<span data-ttu-id="cb21f-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="cb21f-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="cb21f-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="cb21f-107">\<behavior></span></span>  
<span data-ttu-id="cb21f-108">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="cb21f-108">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb21f-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb21f-109">Syntax</span></span>  
  
```xml  
<enableWebScript />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb21f-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cb21f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cb21f-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cb21f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb21f-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cb21f-112">Attributes</span></span>  
 <span data-ttu-id="cb21f-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="cb21f-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cb21f-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cb21f-114">Child Elements</span></span>  
 <span data-ttu-id="cb21f-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="cb21f-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb21f-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cb21f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="cb21f-117">Element</span><span class="sxs-lookup"><span data-stu-id="cb21f-117">Element</span></span>|<span data-ttu-id="cb21f-118">Opis</span><span class="sxs-lookup"><span data-stu-id="cb21f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb21f-119">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="cb21f-119">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="cb21f-120">Określa zestaw zachowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="cb21f-120">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb21f-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb21f-121">Remarks</span></span>  
 <span data-ttu-id="cb21f-122">To zachowanie należy używać tylko w połączeniu z albo [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) Powiązanie standardowe, lub [ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="cb21f-122">This behavior should only be used in conjunction with either the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="cb21f-123">Aby uzyskać więcej informacji dotyczących tego zachowania, zobacz <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="cb21f-123">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb21f-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb21f-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>  
 [<span data-ttu-id="cb21f-125">Obsługa integracji AJAX i notacji JSON</span><span class="sxs-lookup"><span data-stu-id="cb21f-125">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="cb21f-126">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="cb21f-126">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
