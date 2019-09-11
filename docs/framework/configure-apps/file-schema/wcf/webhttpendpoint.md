---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 8d4f55fd5b51ea77839b7fdbb930e937f5700417
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854797"
---
# <a name="webhttpendpoint"></a><span data-ttu-id="464fe-101">\<webHttpEndpoint></span><span class="sxs-lookup"><span data-stu-id="464fe-101">\<webHttpEndpoint></span></span>
<span data-ttu-id="464fe-102">Ten element konfiguracji definiuje standardowy punkt końcowy ze [ \<](webhttp.md) stałym [ \<powiązaniem WebHttpBinding >](webhttpbinding.md) , które automatycznie dodaje zachowanie > sieci Webhttp.</span><span class="sxs-lookup"><span data-stu-id="464fe-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="464fe-103">Użyj tego punktu końcowego podczas pisania usługi REST.</span><span class="sxs-lookup"><span data-stu-id="464fe-103">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="464fe-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="464fe-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="464fe-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="464fe-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="464fe-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="464fe-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="464fe-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webHttpEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="464fe-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="464fe-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="464fe-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="464fe-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="464fe-109">Attributes and Elements</span></span>  
 <span data-ttu-id="464fe-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="464fe-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="464fe-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="464fe-111">Attributes</span></span>  
  
|<span data-ttu-id="464fe-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="464fe-112">Attribute</span></span>|<span data-ttu-id="464fe-113">Opis</span><span class="sxs-lookup"><span data-stu-id="464fe-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="464fe-114">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="464fe-114">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="464fe-115">Wartość logiczna wskazująca, czy jest włączone automatyczne Wybieranie formatu.</span><span class="sxs-lookup"><span data-stu-id="464fe-115">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="464fe-116">Po włączeniu automatycznego wybierania formatu infrastruktura analizuje `Accept` nagłówek komunikatu żądania i określa najbardziej odpowiedni format odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="464fe-116">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="464fe-117">Jeśli w `Accept` nagłówku nie określono odpowiedniego formatu odpowiedzi, infrastruktura `Content-Type` używa komunikatu żądania lub domyślnego formatu odpowiedzi operacji.</span><span class="sxs-lookup"><span data-stu-id="464fe-117">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="464fe-118">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="464fe-118">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="464fe-119">Atrybut, który określa domyślny format odpowiedzi wychodzącej.</span><span class="sxs-lookup"><span data-stu-id="464fe-119">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="464fe-120">Ten atrybut jest <xref:System.ServiceModel.Web.WebMessageFormat> typu</span><span class="sxs-lookup"><span data-stu-id="464fe-120">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="464fe-121">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="464fe-121">helpEnabled</span></span>|<span data-ttu-id="464fe-122">Wartość logiczna wskazująca, czy strona pomocy protokołu HTTP jest włączona dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="464fe-122">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="464fe-123">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="464fe-123">webEndpointType</span></span>|<span data-ttu-id="464fe-124">Ciąg określający typ punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="464fe-124">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="464fe-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="464fe-125">Child Elements</span></span>  
 <span data-ttu-id="464fe-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="464fe-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="464fe-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="464fe-127">Parent Elements</span></span>  
  
|<span data-ttu-id="464fe-128">Element</span><span class="sxs-lookup"><span data-stu-id="464fe-128">Element</span></span>|<span data-ttu-id="464fe-129">Opis</span><span class="sxs-lookup"><span data-stu-id="464fe-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="464fe-130">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="464fe-130">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="464fe-131">Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).</span><span class="sxs-lookup"><span data-stu-id="464fe-131">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="464fe-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="464fe-132">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
