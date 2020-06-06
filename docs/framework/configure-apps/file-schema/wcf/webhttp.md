---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 00644d248e6fb85d7cf712620e6ac74405e6b0c3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399165"
---
# \<webHttp>
<span data-ttu-id="7c25f-101">Ten element określa <xref:System.ServiceModel.Description.WebHttpBehavior> punkt końcowy za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7c25f-101">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="7c25f-102">Takie zachowanie, które jest używane w połączeniu ze [\<webHttpBinding>](webhttpbinding.md) standardowym powiązaniem, umożliwia model programowania sieci Web dla usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7c25f-102">This behavior, when used in conjunction with the [\<webHttpBinding>](webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttp>**  
  
## <a name="syntax"></a><span data-ttu-id="7c25f-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c25f-103">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c25f-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7c25f-104">Attributes and Elements</span></span>  
 <span data-ttu-id="7c25f-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7c25f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c25f-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7c25f-106">Attributes</span></span>  
  
|<span data-ttu-id="7c25f-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7c25f-107">Attribute</span></span>|<span data-ttu-id="7c25f-108">Opis</span><span class="sxs-lookup"><span data-stu-id="7c25f-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c25f-109">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="7c25f-109">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="7c25f-110">Jeśli ta właściwość jest ustawiona na `true` , Infrastruktura WCF określa najlepszy format do użycia.</span><span class="sxs-lookup"><span data-stu-id="7c25f-110">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="7c25f-111">Automatyczne wybieranie formatu jest domyślnie wyłączone w celu zapewnienia zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="7c25f-111">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="7c25f-112">Automatyczne wybieranie formatu można włączyć programowo lub za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7c25f-112">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="7c25f-113">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="7c25f-113">defaultBodyStyle</span></span>|<span data-ttu-id="7c25f-114">Określa domyślny styl treści zwróconych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="7c25f-114">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="7c25f-115">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Web.WebMessageBodyStyle> i [Formatowanie http sieci Web](../../../wcf/feature-details/wcf-web-http-formatting.md)w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="7c25f-115">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="7c25f-116">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="7c25f-116">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="7c25f-117">Określa domyślny format odpowiedzi wychodzącej dla komunikatów.</span><span class="sxs-lookup"><span data-stu-id="7c25f-117">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="7c25f-118">Aby uzyskać więcej informacji, zobacz temat [Formatowanie http sieci Web](../../../wcf/feature-details/wcf-web-http-formatting.md)w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="7c25f-118">For more information, see [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="7c25f-119">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="7c25f-119">faultExceptionEnabled</span></span>|<span data-ttu-id="7c25f-120">Pobiera lub ustawia flagę określającą, czy wyjątek FaultException występuje w przypadku wewnętrznego błędu serwera (kod stanu HTTP: 500).</span><span class="sxs-lookup"><span data-stu-id="7c25f-120">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="7c25f-121">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="7c25f-121">helpEnabled</span></span>|<span data-ttu-id="7c25f-122">Pobiera lub ustawia wartość określającą, czy strona pomocy jest włączona.</span><span class="sxs-lookup"><span data-stu-id="7c25f-122">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c25f-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7c25f-123">Child Elements</span></span>  
 <span data-ttu-id="7c25f-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="7c25f-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c25f-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7c25f-125">Parent Elements</span></span>  
  
|<span data-ttu-id="7c25f-126">Element</span><span class="sxs-lookup"><span data-stu-id="7c25f-126">Element</span></span>|<span data-ttu-id="7c25f-127">Opis</span><span class="sxs-lookup"><span data-stu-id="7c25f-127">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="7c25f-128">Określa zestaw zachowań punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="7c25f-128">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c25f-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c25f-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="7c25f-130">Obsługa integracji AJAX i notacji JSON</span><span class="sxs-lookup"><span data-stu-id="7c25f-130">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](webhttpbinding.md)
