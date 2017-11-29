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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6d847f267a0e88a16195273197876a00dd07f0df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltwebscriptendpointgt"></a><span data-ttu-id="2e73b-102">&lt;webScriptEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="2e73b-102">&lt;webScriptEndpoint&gt;</span></span>
<span data-ttu-id="2e73b-103">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) powiązania, które automatycznie dodaje [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) zachowanie.</span><span class="sxs-lookup"><span data-stu-id="2e73b-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="2e73b-104">Podczas pisania to usługa, która jest wywoływana z aplikacji ASP.NET AJAX, należy używać tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="2e73b-104">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="2e73b-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2e73b-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="2e73b-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="2e73b-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e73b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e73b-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String"/>
    </webScriptEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e73b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2e73b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2e73b-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2e73b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e73b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2e73b-110">Attributes</span></span>  
  
|<span data-ttu-id="2e73b-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2e73b-111">Attribute</span></span>|<span data-ttu-id="2e73b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="2e73b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2e73b-113">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="2e73b-113">webEndpointType</span></span>|<span data-ttu-id="2e73b-114">Ciąg określający typ punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="2e73b-114">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2e73b-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2e73b-115">Child Elements</span></span>  
 <span data-ttu-id="2e73b-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="2e73b-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2e73b-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2e73b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2e73b-118">Element</span><span class="sxs-lookup"><span data-stu-id="2e73b-118">Element</span></span>|<span data-ttu-id="2e73b-119">Opis</span><span class="sxs-lookup"><span data-stu-id="2e73b-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2e73b-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="2e73b-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="2e73b-121">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowanych punktów końcowych z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="2e73b-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e73b-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e73b-122">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
