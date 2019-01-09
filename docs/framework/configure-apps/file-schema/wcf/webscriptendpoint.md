---
title: '&lt;webScriptEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: beb17d4ccc39bcca30e97d4f0df47c797cde6216
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148776"
---
# <a name="ltwebscriptendpointgt"></a><span data-ttu-id="9c7c0-102">&lt;webScriptEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="9c7c0-102">&lt;webScriptEndpoint&gt;</span></span>
<span data-ttu-id="9c7c0-103">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) powiązania, który automatycznie dodaje [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) zachowanie.</span><span class="sxs-lookup"><span data-stu-id="9c7c0-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="9c7c0-104">Używanie tego punktu końcowego, gdy tworzysz usługę, która jest wywoływana z poziomu aplikacji ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="9c7c0-104">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="9c7c0-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9c7c0-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="9c7c0-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="9c7c0-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c7c0-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c7c0-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c7c0-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9c7c0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9c7c0-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9c7c0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c7c0-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9c7c0-110">Attributes</span></span>  
  
|<span data-ttu-id="9c7c0-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9c7c0-111">Attribute</span></span>|<span data-ttu-id="9c7c0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9c7c0-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9c7c0-113">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="9c7c0-113">webEndpointType</span></span>|<span data-ttu-id="9c7c0-114">Ciąg, który określa typ punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="9c7c0-114">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c7c0-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9c7c0-115">Child Elements</span></span>  
 <span data-ttu-id="9c7c0-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="9c7c0-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9c7c0-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9c7c0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9c7c0-118">Element</span><span class="sxs-lookup"><span data-stu-id="9c7c0-118">Element</span></span>|<span data-ttu-id="9c7c0-119">Opis</span><span class="sxs-lookup"><span data-stu-id="9c7c0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c7c0-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="9c7c0-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="9c7c0-121">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="9c7c0-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c7c0-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c7c0-122">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
