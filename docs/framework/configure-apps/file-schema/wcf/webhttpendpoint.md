---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 8d4f55fd5b51ea77839b7fdbb930e937f5700417
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854797"
---
# \<webHttpEndpoint>
<span data-ttu-id="3d275-101">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym [\<webHttpBinding>](webhttpbinding.md) powiązaniem, które automatycznie dodaje [\<webHttp>](webhttp.md) zachowanie.</span><span class="sxs-lookup"><span data-stu-id="3d275-101">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="3d275-102">Użyj tego punktu końcowego podczas pisania usługi REST.</span><span class="sxs-lookup"><span data-stu-id="3d275-102">Use this endpoint when writing a REST service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="3d275-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d275-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d275-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3d275-104">Attributes and Elements</span></span>  
 <span data-ttu-id="3d275-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3d275-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d275-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3d275-106">Attributes</span></span>  
  
|<span data-ttu-id="3d275-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3d275-107">Attribute</span></span>|<span data-ttu-id="3d275-108">Opis</span><span class="sxs-lookup"><span data-stu-id="3d275-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3d275-109">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="3d275-109">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="3d275-110">Wartość logiczna wskazująca, czy jest włączone automatyczne Wybieranie formatu.</span><span class="sxs-lookup"><span data-stu-id="3d275-110">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="3d275-111">Po włączeniu automatycznego wybierania formatu infrastruktura analizuje `Accept` nagłówek komunikatu żądania i określa najbardziej odpowiedni format odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="3d275-111">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="3d275-112">Jeśli w `Accept` nagłówku nie określono odpowiedniego formatu odpowiedzi, infrastruktura używa `Content-Type` komunikatu żądania lub domyślnego formatu odpowiedzi operacji.</span><span class="sxs-lookup"><span data-stu-id="3d275-112">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="3d275-113">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="3d275-113">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="3d275-114">Atrybut, który określa domyślny format odpowiedzi wychodzącej.</span><span class="sxs-lookup"><span data-stu-id="3d275-114">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="3d275-115">Ten atrybut jest <xref:System.ServiceModel.Web.WebMessageFormat> typu</span><span class="sxs-lookup"><span data-stu-id="3d275-115">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="3d275-116">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="3d275-116">helpEnabled</span></span>|<span data-ttu-id="3d275-117">Wartość logiczna wskazująca, czy strona pomocy protokołu HTTP jest włączona dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3d275-117">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="3d275-118">WebEndpointType</span><span class="sxs-lookup"><span data-stu-id="3d275-118">webEndpointType</span></span>|<span data-ttu-id="3d275-119">Ciąg określający typ punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3d275-119">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d275-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3d275-120">Child Elements</span></span>  
 <span data-ttu-id="3d275-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="3d275-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3d275-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3d275-122">Parent Elements</span></span>  
  
|<span data-ttu-id="3d275-123">Element</span><span class="sxs-lookup"><span data-stu-id="3d275-123">Element</span></span>|<span data-ttu-id="3d275-124">Opis</span><span class="sxs-lookup"><span data-stu-id="3d275-124">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="3d275-125">Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).</span><span class="sxs-lookup"><span data-stu-id="3d275-125">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3d275-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d275-126">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
