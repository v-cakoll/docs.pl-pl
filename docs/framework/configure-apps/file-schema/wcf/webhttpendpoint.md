---
title: '&lt;webHttpEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ee055be8c4d2e53dc22a101529e5521add9b54a4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltwebhttpendpointgt"></a><span data-ttu-id="3987f-102">&lt;webHttpEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="3987f-102">&lt;webHttpEndpoint&gt;</span></span>
<span data-ttu-id="3987f-103">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) powiązania, które automatycznie dodaje [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) zachowanie.</span><span class="sxs-lookup"><span data-stu-id="3987f-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="3987f-104">Podczas zapisywania usługi REST, należy używać tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3987f-104">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="3987f-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="3987f-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="3987f-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="3987f-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3987f-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="3987f-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3987f-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3987f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3987f-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3987f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3987f-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3987f-110">Attributes</span></span>  
  
|<span data-ttu-id="3987f-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3987f-111">Attribute</span></span>|<span data-ttu-id="3987f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3987f-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3987f-113">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="3987f-113">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="3987f-114">Wartość logiczna wskazująca, czy jest włączone automatyczne wybieranie formatu.</span><span class="sxs-lookup"><span data-stu-id="3987f-114">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="3987f-115">Włączenie automatycznego wyboru formatu infrastruktury analizuje `Accept` nagłówka komunikatu żądania i określa najbardziej odpowiedni format odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="3987f-115">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="3987f-116">Jeśli `Accept` nagłówka nie określa formatu odpowiedniego odpowiedzi, korzysta z infrastruktury `Content-Type` komunikat żądania lub domyślny format odpowiedzi operacji.</span><span class="sxs-lookup"><span data-stu-id="3987f-116">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="3987f-117">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="3987f-117">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="3987f-118">Atrybut, który określa domyślny format odpowiedzi wychodzącej.</span><span class="sxs-lookup"><span data-stu-id="3987f-118">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="3987f-119">Ten atrybut jest <xref:System.ServiceModel.Web.WebMessageFormat> typu</span><span class="sxs-lookup"><span data-stu-id="3987f-119">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="3987f-120">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="3987f-120">helpEnabled</span></span>|<span data-ttu-id="3987f-121">Wartość logiczna wskazująca, czy strona pomocy protokołu HTTP jest włączone dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3987f-121">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="3987f-122">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="3987f-122">webEndpointType</span></span>|<span data-ttu-id="3987f-123">Ciąg określający typ punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3987f-123">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3987f-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3987f-124">Child Elements</span></span>  
 <span data-ttu-id="3987f-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="3987f-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3987f-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3987f-126">Parent Elements</span></span>  
  
|<span data-ttu-id="3987f-127">Element</span><span class="sxs-lookup"><span data-stu-id="3987f-127">Element</span></span>|<span data-ttu-id="3987f-128">Opis</span><span class="sxs-lookup"><span data-stu-id="3987f-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3987f-129">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="3987f-129">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="3987f-130">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowanych punktów końcowych z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="3987f-130">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3987f-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3987f-131">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
