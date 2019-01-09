---
title: '&lt;webHttp&gt;'
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 9ba54dc1744751efe4efad04f829cccce1244e0d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145682"
---
# <a name="ltwebhttpgt"></a><span data-ttu-id="e89f8-102">&lt;webHttp&gt;</span><span class="sxs-lookup"><span data-stu-id="e89f8-102">&lt;webHttp&gt;</span></span>
<span data-ttu-id="e89f8-103">Ten element Określa <xref:System.ServiceModel.Description.WebHttpBehavior> w punkcie końcowym za pośrednictwem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e89f8-103">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="e89f8-104">To zachowanie, gdy jest używana w połączeniu z [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) Powiązanie standardowe, umożliwia modelu programowania w sieci Web dla usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e89f8-104">This behavior, when used in conjunction with the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="e89f8-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e89f8-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="e89f8-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="e89f8-106">\<behaviors></span></span>  
<span data-ttu-id="e89f8-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="e89f8-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="e89f8-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="e89f8-108">\<behavior></span></span>  
<span data-ttu-id="e89f8-109">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="e89f8-109">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e89f8-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="e89f8-110">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e89f8-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e89f8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e89f8-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e89f8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e89f8-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e89f8-113">Attributes</span></span>  
  
|<span data-ttu-id="e89f8-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e89f8-114">Attribute</span></span>|<span data-ttu-id="e89f8-115">Opis</span><span class="sxs-lookup"><span data-stu-id="e89f8-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e89f8-116">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="e89f8-116">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="e89f8-117">Jeśli ta właściwość jest równa `true`, infrastruktura WCF Określa format najlepszy do użycia.</span><span class="sxs-lookup"><span data-stu-id="e89f8-117">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="e89f8-118">Automatyczne wybieranie formatu jest domyślnie wyłączona dla zapewnienia zgodności.</span><span class="sxs-lookup"><span data-stu-id="e89f8-118">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="e89f8-119">Można włączyć automatyczne wybieranie formatu programowo lub za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e89f8-119">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="e89f8-120">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="e89f8-120">defaultBodyStyle</span></span>|<span data-ttu-id="e89f8-121">Określa domyślny styl treści zwróconych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e89f8-121">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="e89f8-122">Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Web.WebMessageBodyStyle> i [WCF Web HTTP formatowanie](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="e89f8-122">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="e89f8-123">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="e89f8-123">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="e89f8-124">Określa domyślny format odpowiedzi wychodzących dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e89f8-124">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="e89f8-125">Aby uzyskać więcej informacji, zobacz [WCF Web HTTP formatowanie](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="e89f8-125">For more information, see [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="e89f8-126">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="e89f8-126">faultExceptionEnabled</span></span>|<span data-ttu-id="e89f8-127">Pobiera lub ustawia flagę określającą, czy wyjątek FaultException podczas wystąpił wewnętrzny błąd serwera (kod stanu HTTP: 500) występuje.</span><span class="sxs-lookup"><span data-stu-id="e89f8-127">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="e89f8-128">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="e89f8-128">helpEnabled</span></span>|<span data-ttu-id="e89f8-129">Pobiera lub ustawia wartość określającą, czy strona pomocy jest włączona.</span><span class="sxs-lookup"><span data-stu-id="e89f8-129">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e89f8-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e89f8-130">Child Elements</span></span>  
 <span data-ttu-id="e89f8-131">Brak.</span><span class="sxs-lookup"><span data-stu-id="e89f8-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e89f8-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e89f8-132">Parent Elements</span></span>  
  
|<span data-ttu-id="e89f8-133">Element</span><span class="sxs-lookup"><span data-stu-id="e89f8-133">Element</span></span>|<span data-ttu-id="e89f8-134">Opis</span><span class="sxs-lookup"><span data-stu-id="e89f8-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e89f8-135">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="e89f8-135">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="e89f8-136">Określa zestaw zachowań punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e89f8-136">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e89f8-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e89f8-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebHttpElement>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [<span data-ttu-id="e89f8-138">Obsługa integracji AJAX i notacji JSON</span><span class="sxs-lookup"><span data-stu-id="e89f8-138">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="e89f8-139">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e89f8-139">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
