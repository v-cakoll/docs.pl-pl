---
title: '&lt;webScriptEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c321167eb32535d7b39c3d36cdeefe5c8a218f70
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltwebscriptendpointgt"></a><span data-ttu-id="eb374-102">&lt;webScriptEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="eb374-102">&lt;webScriptEndpoint&gt;</span></span>
<span data-ttu-id="eb374-103">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) powiązania, które automatycznie dodaje [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) zachowanie.</span><span class="sxs-lookup"><span data-stu-id="eb374-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="eb374-104">Podczas pisania to usługa, która jest wywoływana z aplikacji ASP.NET AJAX, należy używać tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="eb374-104">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="eb374-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="eb374-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="eb374-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="eb374-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb374-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb374-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String"/>
    </webScriptEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb374-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="eb374-108">Attributes and Elements</span></span>  
 <span data-ttu-id="eb374-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="eb374-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb374-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="eb374-110">Attributes</span></span>  
  
|<span data-ttu-id="eb374-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="eb374-111">Attribute</span></span>|<span data-ttu-id="eb374-112">Opis</span><span class="sxs-lookup"><span data-stu-id="eb374-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eb374-113">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="eb374-113">webEndpointType</span></span>|<span data-ttu-id="eb374-114">Ciąg określający typ punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="eb374-114">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb374-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="eb374-115">Child Elements</span></span>  
 <span data-ttu-id="eb374-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="eb374-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eb374-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="eb374-117">Parent Elements</span></span>  
  
|<span data-ttu-id="eb374-118">Element</span><span class="sxs-lookup"><span data-stu-id="eb374-118">Element</span></span>|<span data-ttu-id="eb374-119">Opis</span><span class="sxs-lookup"><span data-stu-id="eb374-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb374-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="eb374-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="eb374-121">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowanych punktów końcowych z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="eb374-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eb374-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb374-122">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
