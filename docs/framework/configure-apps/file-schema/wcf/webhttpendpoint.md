---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 9b4dd3a61a9b5ad1b35cce4025a50ac4220fd77e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256437"
---
# <a name="webhttpendpoint"></a><span data-ttu-id="38626-101">\<webHttpEndpoint></span><span class="sxs-lookup"><span data-stu-id="38626-101">\<webHttpEndpoint></span></span>
<span data-ttu-id="38626-102">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) powiązania, który automatycznie dodaje [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) zachowanie.</span><span class="sxs-lookup"><span data-stu-id="38626-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="38626-103">Używanie tego punktu końcowego podczas pisania usługi REST.</span><span class="sxs-lookup"><span data-stu-id="38626-103">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="38626-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="38626-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="38626-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="38626-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38626-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="38626-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String"
                        defaultOutgoingResponseFormat="Xml/Json"
                        helpEnabled="Boolean"
                        webEndpointType="String" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38626-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="38626-107">Attributes and Elements</span></span>  
 <span data-ttu-id="38626-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="38626-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38626-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="38626-109">Attributes</span></span>  
  
|<span data-ttu-id="38626-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="38626-110">Attribute</span></span>|<span data-ttu-id="38626-111">Opis</span><span class="sxs-lookup"><span data-stu-id="38626-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38626-112">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="38626-112">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="38626-113">Wartość logiczna wskazująca, czy jest włączone automatyczne wybieranie formatu.</span><span class="sxs-lookup"><span data-stu-id="38626-113">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="38626-114">Po włączeniu automatyczne wybieranie formatu infrastruktury analizuje `Accept` nagłówka komunikatu żądania i określa najbardziej odpowiedni format odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="38626-114">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="38626-115">Jeśli `Accept` nagłówka nie określa format odpowiedniej odpowiedzi, korzysta z infrastruktury `Content-Type` komunikatu żądania lub domyślny format odpowiedzi operacji.</span><span class="sxs-lookup"><span data-stu-id="38626-115">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="38626-116">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="38626-116">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="38626-117">Atrybut, który określa domyślny format odpowiedzi wychodzącej.</span><span class="sxs-lookup"><span data-stu-id="38626-117">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="38626-118">Ten atrybut jest <xref:System.ServiceModel.Web.WebMessageFormat> typu</span><span class="sxs-lookup"><span data-stu-id="38626-118">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="38626-119">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="38626-119">helpEnabled</span></span>|<span data-ttu-id="38626-120">Wartość logiczna wskazująca, czy strona pomocy protokołu HTTP jest włączona dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="38626-120">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="38626-121">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="38626-121">webEndpointType</span></span>|<span data-ttu-id="38626-122">Ciąg, który określa typ punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="38626-122">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38626-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="38626-123">Child Elements</span></span>  
 <span data-ttu-id="38626-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="38626-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38626-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="38626-125">Parent Elements</span></span>  
  
|<span data-ttu-id="38626-126">Element</span><span class="sxs-lookup"><span data-stu-id="38626-126">Element</span></span>|<span data-ttu-id="38626-127">Opis</span><span class="sxs-lookup"><span data-stu-id="38626-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38626-128">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="38626-128">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="38626-129">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="38626-129">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38626-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38626-130">See also</span></span>
- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
