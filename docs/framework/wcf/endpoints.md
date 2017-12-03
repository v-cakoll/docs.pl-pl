---
title: "Punkty końcowe WCF (Windows Communication Foundation)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a1771f5c69442ea4e95925339c28204663f78eb2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="2e963-102">Punkty końcowe WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="2e963-102">Windows Communication Foundation Endpoints</span></span>
<span data-ttu-id="2e963-103">Cała komunikacja z [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usługi odbywa się przez *punkty końcowe* usługi.</span><span class="sxs-lookup"><span data-stu-id="2e963-103">All communication with a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="2e963-104">Punkty końcowe zapewnić klientom dostęp do funkcji [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] oferty usługi.</span><span class="sxs-lookup"><span data-stu-id="2e963-104">Endpoints provide clients access to the functionality that a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service offers.</span></span>  
  
 <span data-ttu-id="2e963-105">Aby uzyskać ogólne informacje o sposobie tworzenia punktu końcowego, zobacz [Przegląd tworzenia punktów końcowych](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2e963-105">For an overview about how to create an endpoint, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="2e963-106">Każdy punkt końcowy zawiera:</span><span class="sxs-lookup"><span data-stu-id="2e963-106">Each endpoint contains:</span></span>  
  
-   <span data-ttu-id="2e963-107">Adres, który wskazuje, gdzie można znaleźć punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="2e963-107">An address that indicates where to find the endpoint.</span></span>  
  
-   <span data-ttu-id="2e963-108">Wiązanie, który określa, jak klient może komunikować się z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="2e963-108">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="2e963-109">Kontrakt, który identyfikuje dostępne metody.</span><span class="sxs-lookup"><span data-stu-id="2e963-109">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="2e963-110">Opisy o sposobie określania tych poszczególnych części punktu końcowego, zobacz:</span><span class="sxs-lookup"><span data-stu-id="2e963-110">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
-   [<span data-ttu-id="2e963-111">Określanie adresu punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="2e963-111">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
  
-   [<span data-ttu-id="2e963-112">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="2e963-112">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
  
-   [<span data-ttu-id="2e963-113">Projektowanie i Implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="2e963-113">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="2e963-114">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2e963-114">In This Section</span></span>  
 [<span data-ttu-id="2e963-115">Przegląd tworzenia punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="2e963-115">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 <span data-ttu-id="2e963-116">Opisuje strukturę punktu końcowego, a także przedstawiono sposób definiowania punkt końcowy w konfiguracji i w kodzie, jak używać domyślnych punktów końcowych, powiązania i zachowania dostarczonym w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2e963-116">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="2e963-117">Określanie adresu punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="2e963-117">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 <span data-ttu-id="2e963-118">W tym artykule opisano sposób komunikacji z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi odbywa się przez punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="2e963-118">Describes how communication with a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="2e963-119">Porady: Tworzenie punktu końcowego usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2e963-119">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="2e963-120">Pokazuje, jak utworzyć punkt końcowy usługi w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2e963-120">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="2e963-121">Porady: Tworzenie punktu końcowego usługi w kodzie</span><span class="sxs-lookup"><span data-stu-id="2e963-121">How to: Create a Service Endpoint in Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="2e963-122">Pokazuje, jak utworzyć punkt końcowy usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2e963-122">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="2e963-123">Publikowanie punktów końcowych metadanych</span><span class="sxs-lookup"><span data-stu-id="2e963-123">Publishing Metadata Endpoints</span></span>](../../../docs/framework/wcf/publishing-metadata-endpoints.md)  
 <span data-ttu-id="2e963-124">Pokazuje, jak publikować metadane publikując punkty końcowe metadanych w konfiguracji i w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2e963-124">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2e963-125">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="2e963-125">Reference</span></span>  
 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="2e963-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="2e963-126">Related Sections</span></span>  
 [<span data-ttu-id="2e963-127">Podstawowy cykl życia programowania</span><span class="sxs-lookup"><span data-stu-id="2e963-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)
