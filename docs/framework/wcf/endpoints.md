---
title: "Punkty końcowe WCF (Windows Communication Foundation)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0725c4f4275853cce958072a57d7f6ca4059e8cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="239de-102">Punkty końcowe WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="239de-102">Windows Communication Foundation Endpoints</span></span>
<span data-ttu-id="239de-103">Cała komunikacja z [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usługi odbywa się przez *punkty końcowe* usługi.</span><span class="sxs-lookup"><span data-stu-id="239de-103">All communication with a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="239de-104">Punkty końcowe zapewnić klientom dostęp do funkcji [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] oferty usługi.</span><span class="sxs-lookup"><span data-stu-id="239de-104">Endpoints provide clients access to the functionality that a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service offers.</span></span>  
  
 <span data-ttu-id="239de-105">Aby uzyskać ogólne informacje o sposobie tworzenia punktu końcowego, zobacz [Przegląd tworzenia punktów końcowych](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="239de-105">For an overview about how to create an endpoint, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="239de-106">Każdy punkt końcowy zawiera:</span><span class="sxs-lookup"><span data-stu-id="239de-106">Each endpoint contains:</span></span>  
  
-   <span data-ttu-id="239de-107">Adres, który wskazuje, gdzie można znaleźć punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="239de-107">An address that indicates where to find the endpoint.</span></span>  
  
-   <span data-ttu-id="239de-108">Wiązanie, który określa, jak klient może komunikować się z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="239de-108">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="239de-109">Kontrakt, który identyfikuje dostępne metody.</span><span class="sxs-lookup"><span data-stu-id="239de-109">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="239de-110">Opisy o sposobie określania tych poszczególnych części punktu końcowego, zobacz:</span><span class="sxs-lookup"><span data-stu-id="239de-110">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
-   [<span data-ttu-id="239de-111">Określanie adresu punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="239de-111">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
  
-   [<span data-ttu-id="239de-112">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="239de-112">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
  
-   [<span data-ttu-id="239de-113">Projektowanie i implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="239de-113">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="239de-114">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="239de-114">In This Section</span></span>  
 [<span data-ttu-id="239de-115">Przegląd tworzenia punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="239de-115">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 <span data-ttu-id="239de-116">Opisuje strukturę punktu końcowego, a także przedstawiono sposób definiowania punkt końcowy w konfiguracji i w kodzie, jak używać domyślnych punktów końcowych, powiązania i zachowania dostarczonym w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="239de-116">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="239de-117">Określanie adresu punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="239de-117">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 <span data-ttu-id="239de-118">W tym artykule opisano sposób komunikacji z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi odbywa się przez punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="239de-118">Describes how communication with a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="239de-119">Instrukcje: tworzenie punktu końcowego usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="239de-119">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="239de-120">Pokazuje, jak utworzyć punkt końcowy usługi w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="239de-120">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="239de-121">Instrukcje: tworzenie punktu końcowego usługi w kodzie</span><span class="sxs-lookup"><span data-stu-id="239de-121">How to: Create a Service Endpoint in Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="239de-122">Pokazuje, jak utworzyć punkt końcowy usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="239de-122">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="239de-123">Publikowanie punktów końcowych metadanych</span><span class="sxs-lookup"><span data-stu-id="239de-123">Publishing Metadata Endpoints</span></span>](../../../docs/framework/wcf/publishing-metadata-endpoints.md)  
 <span data-ttu-id="239de-124">Pokazuje, jak publikować metadane publikując punkty końcowe metadanych w konfiguracji i w kodzie.</span><span class="sxs-lookup"><span data-stu-id="239de-124">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="239de-125">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="239de-125">Reference</span></span>  
 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="239de-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="239de-126">Related Sections</span></span>  
 [<span data-ttu-id="239de-127">Podstawowy cykl życia programowania</span><span class="sxs-lookup"><span data-stu-id="239de-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)
