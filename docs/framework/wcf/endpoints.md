---
title: Punkty końcowe WCF (Windows Communication Foundation)
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
ms.openlocfilehash: f11a8198d38a01fe27a84a3e613e1ff066c25b9d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319910"
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="e0bbd-102">Punkty końcowe WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="e0bbd-102">Windows Communication Foundation Endpoints</span></span>
<span data-ttu-id="e0bbd-103">Cała komunikacja z usługą Windows Communication Foundation (WCF) odbywa się za pomocą *punktów końcowych* usługi.</span><span class="sxs-lookup"><span data-stu-id="e0bbd-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="e0bbd-104">Punkty końcowe zapewniają klientom dostęp do funkcji oferowanych przez usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="e0bbd-104">Endpoints provide clients access to the functionality that a WCF service offers.</span></span>  
  
 <span data-ttu-id="e0bbd-105">Aby dowiedzieć się, jak utworzyć punkt końcowy, zobacz [Omówienie tworzenia punktów końcowych](endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e0bbd-105">For an overview about how to create an endpoint, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="e0bbd-106">Każdy punkt końcowy zawiera:</span><span class="sxs-lookup"><span data-stu-id="e0bbd-106">Each endpoint contains:</span></span>  
  
- <span data-ttu-id="e0bbd-107">Adres wskazujący, gdzie znaleźć punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="e0bbd-107">An address that indicates where to find the endpoint.</span></span>  
  
- <span data-ttu-id="e0bbd-108">Powiązanie określające, w jaki sposób klient może komunikować się z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="e0bbd-108">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
- <span data-ttu-id="e0bbd-109">Kontrakt, który identyfikuje dostępne metody.</span><span class="sxs-lookup"><span data-stu-id="e0bbd-109">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="e0bbd-110">Opis sposobu określania poszczególnych części punktu końcowego można znaleźć w temacie:</span><span class="sxs-lookup"><span data-stu-id="e0bbd-110">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
- [<span data-ttu-id="e0bbd-111">Określanie adresu punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="e0bbd-111">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)  
  
- [<span data-ttu-id="e0bbd-112">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="e0bbd-112">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)  
  
- [<span data-ttu-id="e0bbd-113">Projektowanie i implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="e0bbd-113">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="e0bbd-114">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e0bbd-114">In This Section</span></span>  
 [<span data-ttu-id="e0bbd-115">Przegląd tworzenia punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="e0bbd-115">Endpoint Creation Overview</span></span>](endpoint-creation-overview.md)  
 <span data-ttu-id="e0bbd-116">Opisuje strukturę punktu końcowego oraz instrukcje definiowania punktu końcowego w konfiguracji i w kodzie, jak również używania domyślnych punktów końcowych, powiązań i zachowań zapewnianych przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="e0bbd-116">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="e0bbd-117">Określanie adresu punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="e0bbd-117">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)  
 <span data-ttu-id="e0bbd-118">Opisuje sposób komunikacji z usługą WCF odbywa się za pomocą punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="e0bbd-118">Describes how communication with a WCF service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="e0bbd-119">Instrukcje: tworzenie punktu końcowego usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e0bbd-119">How to: Create a Service Endpoint in Configuration</span></span>](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="e0bbd-120">Pokazuje, jak utworzyć punkt końcowy usługi w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e0bbd-120">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="e0bbd-121">Instrukcje: tworzenie punktu końcowego usługi w kodzie</span><span class="sxs-lookup"><span data-stu-id="e0bbd-121">How to: Create a Service Endpoint in Code</span></span>](./feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="e0bbd-122">Pokazuje, jak utworzyć punkt końcowy usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e0bbd-122">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="e0bbd-123">Publikowanie punktów końcowych metadanych</span><span class="sxs-lookup"><span data-stu-id="e0bbd-123">Publishing Metadata Endpoints</span></span>](publishing-metadata-endpoints.md)  
 <span data-ttu-id="e0bbd-124">Demonstruje sposób publikowania metadanych przez Publikowanie punktów końcowych metadanych w konfiguracji i w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e0bbd-124">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e0bbd-125">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="e0bbd-125">Reference</span></span>  
 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="e0bbd-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="e0bbd-126">Related Sections</span></span>  
 [<span data-ttu-id="e0bbd-127">Podstawowy cykl życia programowania</span><span class="sxs-lookup"><span data-stu-id="e0bbd-127">Basic Programming Lifecycle</span></span>](basic-programming-lifecycle.md)
