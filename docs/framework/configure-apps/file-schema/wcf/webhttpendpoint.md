---
title: '&lt;webHttpEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 46691a36b62898583132b5668b06de5659926d66
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltwebhttpendpointgt"></a><span data-ttu-id="04a8b-102">&lt;webHttpEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="04a8b-102">&lt;webHttpEndpoint&gt;</span></span>
<span data-ttu-id="04a8b-103">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) powiązania, które automatycznie dodaje [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) zachowanie.</span><span class="sxs-lookup"><span data-stu-id="04a8b-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="04a8b-104">Podczas zapisywania usługi REST, należy używać tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="04a8b-104">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="04a8b-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="04a8b-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="04a8b-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="04a8b-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04a8b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="04a8b-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String" 
                        defaultOutgoingResponseFormat="Xml/Json" 
                        helpEnabled="Boolean" 
                        webEndpointType="String"/>
    </webHttpEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04a8b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="04a8b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="04a8b-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="04a8b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04a8b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="04a8b-110">Attributes</span></span>  
  
|<span data-ttu-id="04a8b-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="04a8b-111">Attribute</span></span>|<span data-ttu-id="04a8b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="04a8b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="04a8b-113">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="04a8b-113">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="04a8b-114">Wartość logiczna wskazująca, czy jest włączone automatyczne wybieranie formatu.</span><span class="sxs-lookup"><span data-stu-id="04a8b-114">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="04a8b-115">Włączenie automatycznego wyboru formatu infrastruktury analizuje `Accept` nagłówka komunikatu żądania i określa najbardziej odpowiedni format odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="04a8b-115">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="04a8b-116">Jeśli `Accept` nagłówka nie określa formatu odpowiedniego odpowiedzi, korzysta z infrastruktury `Content-Type` komunikat żądania lub domyślny format odpowiedzi operacji.</span><span class="sxs-lookup"><span data-stu-id="04a8b-116">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="04a8b-117">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="04a8b-117">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="04a8b-118">Atrybut, który określa domyślny format odpowiedzi wychodzącej.</span><span class="sxs-lookup"><span data-stu-id="04a8b-118">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="04a8b-119">Ten atrybut jest <xref:System.ServiceModel.Web.WebMessageFormat> typu</span><span class="sxs-lookup"><span data-stu-id="04a8b-119">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="04a8b-120">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="04a8b-120">helpEnabled</span></span>|<span data-ttu-id="04a8b-121">Wartość logiczna wskazująca, czy strona pomocy protokołu HTTP jest włączone dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="04a8b-121">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="04a8b-122">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="04a8b-122">webEndpointType</span></span>|<span data-ttu-id="04a8b-123">Ciąg określający typ punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="04a8b-123">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04a8b-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="04a8b-124">Child Elements</span></span>  
 <span data-ttu-id="04a8b-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="04a8b-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04a8b-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="04a8b-126">Parent Elements</span></span>  
  
|<span data-ttu-id="04a8b-127">Element</span><span class="sxs-lookup"><span data-stu-id="04a8b-127">Element</span></span>|<span data-ttu-id="04a8b-128">Opis</span><span class="sxs-lookup"><span data-stu-id="04a8b-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04a8b-129">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="04a8b-129">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="04a8b-130">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowanych punktów końcowych z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="04a8b-130">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04a8b-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="04a8b-131">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
