---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 795e61b9054d2ea9276970988018c50099bcbe17
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129652"
---
# <a name="webhttp"></a><span data-ttu-id="022ae-101">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="022ae-101">\<webHttp></span></span>
<span data-ttu-id="022ae-102">Ten element Określa <xref:System.ServiceModel.Description.WebHttpBehavior> w punkcie końcowym za pośrednictwem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="022ae-102">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="022ae-103">To zachowanie, gdy jest używana w połączeniu z [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) Powiązanie standardowe, umożliwia modelu programowania w sieci Web dla usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="022ae-103">This behavior, when used in conjunction with the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="022ae-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="022ae-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="022ae-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="022ae-105">\<behaviors></span></span>  
<span data-ttu-id="022ae-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="022ae-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="022ae-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="022ae-107">\<behavior></span></span>  
<span data-ttu-id="022ae-108">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="022ae-108">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="022ae-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="022ae-109">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="022ae-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="022ae-110">Attributes and Elements</span></span>  
 <span data-ttu-id="022ae-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="022ae-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="022ae-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="022ae-112">Attributes</span></span>  
  
|<span data-ttu-id="022ae-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="022ae-113">Attribute</span></span>|<span data-ttu-id="022ae-114">Opis</span><span class="sxs-lookup"><span data-stu-id="022ae-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="022ae-115">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="022ae-115">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="022ae-116">Jeśli ta właściwość jest równa `true`, infrastruktura WCF Określa format najlepszy do użycia.</span><span class="sxs-lookup"><span data-stu-id="022ae-116">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="022ae-117">Automatyczne wybieranie formatu jest domyślnie wyłączona dla zapewnienia zgodności.</span><span class="sxs-lookup"><span data-stu-id="022ae-117">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="022ae-118">Można włączyć automatyczne wybieranie formatu programowo lub za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="022ae-118">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="022ae-119">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="022ae-119">defaultBodyStyle</span></span>|<span data-ttu-id="022ae-120">Określa domyślny styl treści zwróconych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="022ae-120">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="022ae-121">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Web.WebMessageBodyStyle> i [WCF Web HTTP formatowanie](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="022ae-121">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="022ae-122">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="022ae-122">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="022ae-123">Określa domyślny format odpowiedzi wychodzących dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="022ae-123">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="022ae-124">Aby uzyskać więcej informacji, zobacz [WCF Web HTTP formatowanie](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="022ae-124">For more information, see [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="022ae-125">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="022ae-125">faultExceptionEnabled</span></span>|<span data-ttu-id="022ae-126">Pobiera lub ustawia flagę określającą, czy wyjątek FaultException podczas wystąpił wewnętrzny błąd serwera (kod stanu HTTP: 500) występuje.</span><span class="sxs-lookup"><span data-stu-id="022ae-126">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="022ae-127">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="022ae-127">helpEnabled</span></span>|<span data-ttu-id="022ae-128">Pobiera lub ustawia wartość określającą, czy strona pomocy jest włączona.</span><span class="sxs-lookup"><span data-stu-id="022ae-128">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="022ae-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="022ae-129">Child Elements</span></span>  
 <span data-ttu-id="022ae-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="022ae-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="022ae-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="022ae-131">Parent Elements</span></span>  
  
|<span data-ttu-id="022ae-132">Element</span><span class="sxs-lookup"><span data-stu-id="022ae-132">Element</span></span>|<span data-ttu-id="022ae-133">Opis</span><span class="sxs-lookup"><span data-stu-id="022ae-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="022ae-134">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="022ae-134">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="022ae-135">Określa zestaw zachowań punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="022ae-135">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="022ae-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="022ae-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="022ae-137">Obsługa integracji AJAX i notacji JSON</span><span class="sxs-lookup"><span data-stu-id="022ae-137">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="022ae-138">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="022ae-138">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
