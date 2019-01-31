---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: 3d95624c82388ed6219fc567dd2d3c17bedad7a1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255292"
---
# <a name="webscriptendpoint"></a><span data-ttu-id="95333-101">\<webScriptEndpoint></span><span class="sxs-lookup"><span data-stu-id="95333-101">\<webScriptEndpoint></span></span>
<span data-ttu-id="95333-102">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) powiązania, który automatycznie dodaje [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) zachowanie.</span><span class="sxs-lookup"><span data-stu-id="95333-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="95333-103">Używanie tego punktu końcowego, gdy tworzysz usługę, która jest wywoływana z poziomu aplikacji ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="95333-103">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="95333-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="95333-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="95333-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="95333-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95333-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="95333-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95333-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="95333-107">Attributes and Elements</span></span>  
 <span data-ttu-id="95333-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="95333-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95333-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="95333-109">Attributes</span></span>  
  
|<span data-ttu-id="95333-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="95333-110">Attribute</span></span>|<span data-ttu-id="95333-111">Opis</span><span class="sxs-lookup"><span data-stu-id="95333-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="95333-112">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="95333-112">webEndpointType</span></span>|<span data-ttu-id="95333-113">Ciąg, który określa typ punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="95333-113">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95333-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="95333-114">Child Elements</span></span>  
 <span data-ttu-id="95333-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="95333-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="95333-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="95333-116">Parent Elements</span></span>  
  
|<span data-ttu-id="95333-117">Element</span><span class="sxs-lookup"><span data-stu-id="95333-117">Element</span></span>|<span data-ttu-id="95333-118">Opis</span><span class="sxs-lookup"><span data-stu-id="95333-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95333-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="95333-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="95333-120">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="95333-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="95333-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95333-121">See also</span></span>
- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
