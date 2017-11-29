---
title: '&lt;enableWebScript&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cfb6981947b457d5fdad59e96bdcd6937b9abd02
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltenablewebscriptgt"></a><span data-ttu-id="d3e94-102">&lt;enableWebScript&gt;</span><span class="sxs-lookup"><span data-stu-id="d3e94-102">&lt;enableWebScript&gt;</span></span>
<span data-ttu-id="d3e94-103">Ten element włącza zachowanie punktu końcowego, który pozwala na korzystanie z usługi z ASP.NET AJAX stron sieci web.</span><span class="sxs-lookup"><span data-stu-id="d3e94-103">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="d3e94-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d3e94-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d3e94-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="d3e94-105">\<behaviors></span></span>  
<span data-ttu-id="d3e94-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d3e94-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="d3e94-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="d3e94-107">\<behavior></span></span>  
<span data-ttu-id="d3e94-108">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="d3e94-108">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3e94-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3e94-109">Syntax</span></span>  
  
```xml  
<enableWebScript />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3e94-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d3e94-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d3e94-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d3e94-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3e94-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d3e94-112">Attributes</span></span>  
 <span data-ttu-id="d3e94-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="d3e94-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d3e94-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d3e94-114">Child Elements</span></span>  
 <span data-ttu-id="d3e94-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="d3e94-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3e94-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d3e94-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d3e94-117">Element</span><span class="sxs-lookup"><span data-stu-id="d3e94-117">Element</span></span>|<span data-ttu-id="d3e94-118">Opis</span><span class="sxs-lookup"><span data-stu-id="d3e94-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3e94-119">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="d3e94-119">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d3e94-120">Określa zestaw zachowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="d3e94-120">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3e94-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d3e94-121">Remarks</span></span>  
 <span data-ttu-id="d3e94-122">To zachowanie należy używać tylko w połączeniu z albo [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) Powiązanie standardowe, lub [ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="d3e94-122">This behavior should only be used in conjunction with either the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="d3e94-123">Aby uzyskać więcej informacji dotyczących tego zachowania, zobacz <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="d3e94-123">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e94-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3e94-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>  
 [<span data-ttu-id="d3e94-125">Integracji AJAX i obsługi JSON</span><span class="sxs-lookup"><span data-stu-id="d3e94-125">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="d3e94-126">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="d3e94-126">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
