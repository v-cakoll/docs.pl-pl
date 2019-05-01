---
title: Punkty końcowe WCF (Windows Communication Foundation)
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
ms.openlocfilehash: b55abe937701f8708643efa2ea4cb62514b3521b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923191"
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="f7d5a-102">Punkty końcowe WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="f7d5a-102">Windows Communication Foundation Endpoints</span></span>
<span data-ttu-id="f7d5a-103">Cała komunikacja z usługą Windows Communication Foundation (WCF) odbywa się przez *punktów końcowych* usługi.</span><span class="sxs-lookup"><span data-stu-id="f7d5a-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="f7d5a-104">Punkty końcowe zapewnić klientom dostęp do funkcji, która oferuje usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="f7d5a-104">Endpoints provide clients access to the functionality that a WCF service offers.</span></span>  
  
 <span data-ttu-id="f7d5a-105">Omówienie sposobu tworzenia punktu końcowego, zobacz [Przegląd tworzenia punktów końcowych](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f7d5a-105">For an overview about how to create an endpoint, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="f7d5a-106">Każdy punkt końcowy zawiera:</span><span class="sxs-lookup"><span data-stu-id="f7d5a-106">Each endpoint contains:</span></span>  
  
- <span data-ttu-id="f7d5a-107">Adres, który wskazuje, gdzie można znaleźć punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f7d5a-107">An address that indicates where to find the endpoint.</span></span>  
  
- <span data-ttu-id="f7d5a-108">Wiązanie, który określa, jak klient może komunikować się z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="f7d5a-108">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
- <span data-ttu-id="f7d5a-109">Kontrakt, który identyfikuje dostępne metody.</span><span class="sxs-lookup"><span data-stu-id="f7d5a-109">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="f7d5a-110">Opisy dotyczące sposobu określania tych poszczególnych części punktu końcowego, zobacz:</span><span class="sxs-lookup"><span data-stu-id="f7d5a-110">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
- [<span data-ttu-id="f7d5a-111">Określanie adresu punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="f7d5a-111">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
  
- [<span data-ttu-id="f7d5a-112">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="f7d5a-112">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
  
- [<span data-ttu-id="f7d5a-113">Projektowanie i implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="f7d5a-113">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="f7d5a-114">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="f7d5a-114">In This Section</span></span>  
 [<span data-ttu-id="f7d5a-115">Przegląd tworzenia punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="f7d5a-115">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 <span data-ttu-id="f7d5a-116">Opisuje strukturę punktu końcowego, a także omówiono, jak zdefiniować punkt końcowy w konfiguracji i w kodzie, jak używać domyślnych punktów końcowych, powiązania i zachowania dostarczane przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="f7d5a-116">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="f7d5a-117">Określanie adresu punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="f7d5a-117">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 <span data-ttu-id="f7d5a-118">W tym artykule opisano, jak za pomocą usługi WCF odbywa się za pośrednictwem punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="f7d5a-118">Describes how communication with a WCF service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="f7d5a-119">Instrukcje: Tworzenie punktu końcowego usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f7d5a-119">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="f7d5a-120">Pokazuje, jak utworzyć punkt końcowy usługi w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f7d5a-120">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="f7d5a-121">Instrukcje: Tworzenie punktu końcowego usługi w kodzie</span><span class="sxs-lookup"><span data-stu-id="f7d5a-121">How to: Create a Service Endpoint in Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="f7d5a-122">Pokazuje, jak utworzyć punkt końcowy usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f7d5a-122">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="f7d5a-123">Publikowanie punktów końcowych metadanych</span><span class="sxs-lookup"><span data-stu-id="f7d5a-123">Publishing Metadata Endpoints</span></span>](../../../docs/framework/wcf/publishing-metadata-endpoints.md)  
 <span data-ttu-id="f7d5a-124">Pokazuje, jak publikowanie metadanych przez publikowanie punktów końcowych metadanych w konfiguracji i w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f7d5a-124">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f7d5a-125">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="f7d5a-125">Reference</span></span>  
 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="f7d5a-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="f7d5a-126">Related Sections</span></span>  
 [<span data-ttu-id="f7d5a-127">Podstawowy cykl życia programowania</span><span class="sxs-lookup"><span data-stu-id="f7d5a-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)
