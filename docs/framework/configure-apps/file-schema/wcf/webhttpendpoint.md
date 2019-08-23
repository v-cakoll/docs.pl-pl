---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 866be522cb1c64142227a8d6a1a8f88551ca9105
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940471"
---
# <a name="webhttpendpoint"></a><span data-ttu-id="1c0f4-101">\<webHttpEndpoint></span><span class="sxs-lookup"><span data-stu-id="1c0f4-101">\<webHttpEndpoint></span></span>
<span data-ttu-id="1c0f4-102">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym [ \<](webhttpbinding.md) powiązaniem WebHttpBinding > [ \<](webhttp.md) , które automatycznie dodaje zachowanie > sieci Webhttp.</span><span class="sxs-lookup"><span data-stu-id="1c0f4-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="1c0f4-103">Użyj tego punktu końcowego podczas pisania usługi REST.</span><span class="sxs-lookup"><span data-stu-id="1c0f4-103">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="1c0f4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1c0f4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1c0f4-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="1c0f4-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c0f4-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c0f4-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c0f4-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1c0f4-107">Attributes and Elements</span></span>  
 <span data-ttu-id="1c0f4-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1c0f4-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c0f4-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1c0f4-109">Attributes</span></span>  
  
|<span data-ttu-id="1c0f4-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1c0f4-110">Attribute</span></span>|<span data-ttu-id="1c0f4-111">Opis</span><span class="sxs-lookup"><span data-stu-id="1c0f4-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1c0f4-112">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="1c0f4-112">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="1c0f4-113">Wartość logiczna wskazująca, czy jest włączone automatyczne Wybieranie formatu.</span><span class="sxs-lookup"><span data-stu-id="1c0f4-113">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="1c0f4-114">Po włączeniu automatycznego wybierania formatu infrastruktura analizuje `Accept` nagłówek komunikatu żądania i określa najbardziej odpowiedni format odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1c0f4-114">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="1c0f4-115">Jeśli w `Accept` nagłówku nie określono odpowiedniego formatu odpowiedzi, infrastruktura `Content-Type` używa komunikatu żądania lub domyślnego formatu odpowiedzi operacji.</span><span class="sxs-lookup"><span data-stu-id="1c0f4-115">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="1c0f4-116">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="1c0f4-116">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="1c0f4-117">Atrybut, który określa domyślny format odpowiedzi wychodzącej.</span><span class="sxs-lookup"><span data-stu-id="1c0f4-117">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="1c0f4-118">Ten atrybut jest <xref:System.ServiceModel.Web.WebMessageFormat> typu</span><span class="sxs-lookup"><span data-stu-id="1c0f4-118">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="1c0f4-119">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="1c0f4-119">helpEnabled</span></span>|<span data-ttu-id="1c0f4-120">Wartość logiczna wskazująca, czy strona pomocy protokołu HTTP jest włączona dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="1c0f4-120">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="1c0f4-121">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="1c0f4-121">webEndpointType</span></span>|<span data-ttu-id="1c0f4-122">Ciąg określający typ punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="1c0f4-122">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c0f4-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1c0f4-123">Child Elements</span></span>  
 <span data-ttu-id="1c0f4-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="1c0f4-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1c0f4-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1c0f4-125">Parent Elements</span></span>  
  
|<span data-ttu-id="1c0f4-126">Element</span><span class="sxs-lookup"><span data-stu-id="1c0f4-126">Element</span></span>|<span data-ttu-id="1c0f4-127">Opis</span><span class="sxs-lookup"><span data-stu-id="1c0f4-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c0f4-128">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="1c0f4-128">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="1c0f4-129">Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).</span><span class="sxs-lookup"><span data-stu-id="1c0f4-129">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c0f4-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c0f4-130">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
