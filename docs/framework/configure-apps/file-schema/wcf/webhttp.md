---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 366def5d0f4cc82b0ff0a5127701b0b5a6adb6a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940504"
---
# <a name="webhttp"></a><span data-ttu-id="86850-101">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="86850-101">\<webHttp></span></span>
<span data-ttu-id="86850-102">Ten element określa <xref:System.ServiceModel.Description.WebHttpBehavior> punkt końcowy za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="86850-102">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="86850-103">Takie zachowanie, gdy jest [ \<](webhttpbinding.md) używane w połączeniu z standardowym powiązaniem WebHttpBinding >, włącza model programowania sieci Web dla usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="86850-103">This behavior, when used in conjunction with the [\<webHttpBinding>](webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="86850-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="86850-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="86850-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="86850-105">\<behaviors></span></span>  
<span data-ttu-id="86850-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="86850-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="86850-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="86850-107">\<behavior></span></span>  
<span data-ttu-id="86850-108">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="86850-108">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86850-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="86850-109">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86850-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="86850-110">Attributes and Elements</span></span>  
 <span data-ttu-id="86850-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="86850-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86850-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="86850-112">Attributes</span></span>  
  
|<span data-ttu-id="86850-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="86850-113">Attribute</span></span>|<span data-ttu-id="86850-114">Opis</span><span class="sxs-lookup"><span data-stu-id="86850-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86850-115">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="86850-115">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="86850-116">Jeśli ta właściwość jest ustawiona na `true`, Infrastruktura WCF określa najlepszy format do użycia.</span><span class="sxs-lookup"><span data-stu-id="86850-116">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="86850-117">Automatyczne wybieranie formatu jest domyślnie wyłączone w celu zapewnienia zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="86850-117">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="86850-118">Automatyczne wybieranie formatu można włączyć programowo lub za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="86850-118">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="86850-119">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="86850-119">defaultBodyStyle</span></span>|<span data-ttu-id="86850-120">Określa domyślny styl treści zwróconych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="86850-120">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="86850-121">Aby uzyskać więcej informacji, <xref:System.ServiceModel.Web.WebMessageBodyStyle> Zobacz i [Formatowanie http sieci Web](../../../wcf/feature-details/wcf-web-http-formatting.md)w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="86850-121">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="86850-122">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="86850-122">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="86850-123">Określa domyślny format odpowiedzi wychodzącej dla komunikatów.</span><span class="sxs-lookup"><span data-stu-id="86850-123">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="86850-124">Aby uzyskać więcej informacji, zobacz temat [Formatowanie http sieci Web](../../../wcf/feature-details/wcf-web-http-formatting.md)w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="86850-124">For more information, see [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="86850-125">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="86850-125">faultExceptionEnabled</span></span>|<span data-ttu-id="86850-126">Pobiera lub ustawia flagę określającą, czy element FaultException jest generowany w przypadku wewnętrznego błędu serwera (kod stanu HTTP: 500) występuje.</span><span class="sxs-lookup"><span data-stu-id="86850-126">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="86850-127">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="86850-127">helpEnabled</span></span>|<span data-ttu-id="86850-128">Pobiera lub ustawia wartość określającą, czy strona pomocy jest włączona.</span><span class="sxs-lookup"><span data-stu-id="86850-128">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86850-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="86850-129">Child Elements</span></span>  
 <span data-ttu-id="86850-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="86850-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86850-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="86850-131">Parent Elements</span></span>  
  
|<span data-ttu-id="86850-132">Element</span><span class="sxs-lookup"><span data-stu-id="86850-132">Element</span></span>|<span data-ttu-id="86850-133">Opis</span><span class="sxs-lookup"><span data-stu-id="86850-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86850-134">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="86850-134">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="86850-135">Określa zestaw zachowań punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="86850-135">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86850-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86850-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="86850-137">Obsługa integracji AJAX i notacji JSON</span><span class="sxs-lookup"><span data-stu-id="86850-137">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="86850-138">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="86850-138">\<webHttpBinding></span></span>](webhttpbinding.md)
