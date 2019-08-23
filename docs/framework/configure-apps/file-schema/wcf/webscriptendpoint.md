---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: cc69029d9830fd12df5a4070f11847fadf4c60bb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940408"
---
# <a name="webscriptendpoint"></a><span data-ttu-id="d207a-101">\<webScriptEndpoint></span><span class="sxs-lookup"><span data-stu-id="d207a-101">\<webScriptEndpoint></span></span>
<span data-ttu-id="d207a-102">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym [ \<](webhttpbinding.md) powiązaniem WebHttpBinding > [ \<](enablewebscript.md) , które automatycznie dodaje zachowanie > enableWebScript.</span><span class="sxs-lookup"><span data-stu-id="d207a-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="d207a-103">Użyj tego punktu końcowego podczas pisania usługi, która jest wywoływana z aplikacji ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="d207a-103">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="d207a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d207a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d207a-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="d207a-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d207a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d207a-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d207a-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d207a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d207a-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d207a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d207a-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d207a-109">Attributes</span></span>  
  
|<span data-ttu-id="d207a-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d207a-110">Attribute</span></span>|<span data-ttu-id="d207a-111">Opis</span><span class="sxs-lookup"><span data-stu-id="d207a-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d207a-112">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="d207a-112">webEndpointType</span></span>|<span data-ttu-id="d207a-113">Ciąg określający typ punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="d207a-113">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d207a-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d207a-114">Child Elements</span></span>  
 <span data-ttu-id="d207a-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="d207a-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d207a-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d207a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d207a-117">Element</span><span class="sxs-lookup"><span data-stu-id="d207a-117">Element</span></span>|<span data-ttu-id="d207a-118">Opis</span><span class="sxs-lookup"><span data-stu-id="d207a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d207a-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="d207a-119">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="d207a-120">Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).</span><span class="sxs-lookup"><span data-stu-id="d207a-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d207a-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d207a-121">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
