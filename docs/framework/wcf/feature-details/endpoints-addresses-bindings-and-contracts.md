---
title: "Punkty końcowe: Adresy, powiązania i kontrakty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af82cb934570b371d332c0e08ebc9b2338d0c0d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="37b41-102">Punkty końcowe: Adresy, powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="37b41-102">Endpoints: Addresses, Bindings, and Contracts</span></span>
<span data-ttu-id="37b41-103">Cała komunikacja z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi odbywa się przez *punkty końcowe* usługi.</span><span class="sxs-lookup"><span data-stu-id="37b41-103">All communication with a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="37b41-104">Punkty końcowe zapewnić klientom dostęp do funkcji oferowanych przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="37b41-104">Endpoints provide clients access to the functionality offered by a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="37b41-105">Każdy punkt końcowy składa się z czterech właściwości:</span><span class="sxs-lookup"><span data-stu-id="37b41-105">Each endpoint consists of four properties:</span></span>  
  
-   <span data-ttu-id="37b41-106">Adres, który wskazuje, gdzie można znaleźć punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="37b41-106">An address that indicates where the endpoint can be found.</span></span>  
  
-   <span data-ttu-id="37b41-107">Wiązanie, który określa, jak klient może komunikować się z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="37b41-107">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="37b41-108">Kontrakt określa operacje dostępne.</span><span class="sxs-lookup"><span data-stu-id="37b41-108">A contract that identifies the operations available.</span></span>  
  
-   <span data-ttu-id="37b41-109">Zestaw zachowań, które określają szczegóły implementacji lokalnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="37b41-109">A set of behaviors that specify local implementation details of the endpoint.</span></span>  
  
 <span data-ttu-id="37b41-110">W tym temacie omówiono tego punktu końcowego struktury oraz wyjaśniono, jak są reprezentowane w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiektu modelu.</span><span class="sxs-lookup"><span data-stu-id="37b41-110">This topic discusses this endpoint structure and explains how it is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="37b41-111">Struktura punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="37b41-111">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="37b41-112">Każdy punkt końcowy składa się z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="37b41-112">Each endpoint consists of the following:</span></span>  
  
-   <span data-ttu-id="37b41-113">Adres: Adres unikatowo identyfikuje punkt końcowy i informuje potencjalne korzystającym z usług, w którym znajduje się.</span><span class="sxs-lookup"><span data-stu-id="37b41-113">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="37b41-114">Jest reprezentowana w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model obiektów przez <xref:System.ServiceModel.EndpointAddress> klasy.</span><span class="sxs-lookup"><span data-stu-id="37b41-114">It is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="37b41-115"><xref:System.ServiceModel.EndpointAddress> Klasa zawiera:</span><span class="sxs-lookup"><span data-stu-id="37b41-115">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>  
  
    -   <span data-ttu-id="37b41-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> właściwość, która reprezentuje adres usługi.</span><span class="sxs-lookup"><span data-stu-id="37b41-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>  
  
    -   <span data-ttu-id="37b41-117"><xref:System.ServiceModel.EndpointAddress.Identity%2A> Właściwość, która reprezentuje tożsamości zabezpieczeń usługi i kolekcję nagłówków komunikatów opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="37b41-117">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="37b41-118">Nagłówki komunikatów opcjonalne służą do zapewniania dodatkowe i bardziej szczegółowych informacji o adresach do identyfikacji użytkownika lub interakcji z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="37b41-118">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="37b41-119">[Określanie adresu punktu końcowego](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="37b41-119"> [Specifying an Endpoint Address](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
-   <span data-ttu-id="37b41-120">Powiązanie: Powiązanie określa sposób komunikowania się z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="37b41-120">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="37b41-121">Możliwości obejmują:</span><span class="sxs-lookup"><span data-stu-id="37b41-121">This includes:</span></span>  
  
    -   <span data-ttu-id="37b41-122">Protokół transportu do użycia (np. TCP lub HTTP).</span><span class="sxs-lookup"><span data-stu-id="37b41-122">The transport protocol to use (for example, TCP or HTTP).</span></span>  
  
    -   <span data-ttu-id="37b41-123">Szyfrowanie do użycia dla wiadomości (na przykład tekst lub binarny).</span><span class="sxs-lookup"><span data-stu-id="37b41-123">The encoding to use for the messages (for example, text or binary).</span></span>  
  
    -   <span data-ttu-id="37b41-124">Niezbędne wymagania dotyczące zabezpieczeń (na przykład protokołu SSL lub protokołu SOAP wiadomości zabezpieczeń).</span><span class="sxs-lookup"><span data-stu-id="37b41-124">The necessary security requirements (for example, SSL or SOAP message security).</span></span>  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="37b41-125">[Omówienie powiązań WCF](../../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="37b41-125"> [WCF Bindings Overview](../../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="37b41-126">Powiązanie jest reprezentowana w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model obiektów przez abstrakcyjna klasa podstawowa <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="37b41-126">A binding is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="37b41-127">W przypadku większości scenariuszy użytkownicy mogą używać jednego powiązania dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="37b41-127">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="37b41-128">Aby uzyskać więcej informacji, zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="37b41-128">For more information, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
-   <span data-ttu-id="37b41-129">Kontrakty: Kontrakt przedstawiono funkcje punktu końcowego udostępnia do klienta.</span><span class="sxs-lookup"><span data-stu-id="37b41-129">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="37b41-130">Kontrakt określa:</span><span class="sxs-lookup"><span data-stu-id="37b41-130">A contract specifies:</span></span>  
  
    -   <span data-ttu-id="37b41-131">Jakie operacje może zostać wywołany przez klienta.</span><span class="sxs-lookup"><span data-stu-id="37b41-131">What operations can be called by a client.</span></span>  
  
    -   <span data-ttu-id="37b41-132">Formularz wiadomości.</span><span class="sxs-lookup"><span data-stu-id="37b41-132">The form of the message.</span></span>  
  
    -   <span data-ttu-id="37b41-133">Typ parametrów wejściowych lub danych wymaganych do wywołania operacji.</span><span class="sxs-lookup"><span data-stu-id="37b41-133">The type of input parameters or data required to call the operation.</span></span>  
  
    -   <span data-ttu-id="37b41-134">Jakiego typu Przetwarzanie lub odpowiedzi wiadomości przez klienta może spodziewać się.</span><span class="sxs-lookup"><span data-stu-id="37b41-134">What type of processing or response message the client can expect.</span></span>  
  
     <span data-ttu-id="37b41-135">Aby uzyskać więcej informacji na temat definiowania kontrakt, zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="37b41-135">For more information about defining a contract, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
-   <span data-ttu-id="37b41-136">Zachowania: Aby dostosować zachowanie lokalnego punktu końcowego usługi można użyć zachowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="37b41-136">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="37b41-137">Zachowania punktu końcowego to zrobić, uczestnictwa w procesie tworzenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="37b41-137">Endpoint behaviors achieve this by participating in the process of building a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]runtime.</span></span> <span data-ttu-id="37b41-138">Przykład zachowania punktu końcowego <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> właściwość, która pozwala na określenie nasłuchiwania inny adres niż adres SOAP lub Web Services Description Language (WSDL).</span><span class="sxs-lookup"><span data-stu-id="37b41-138">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="37b41-139">[ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="37b41-139"> [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span></span>  
  
## <a name="defining-endpoints"></a><span data-ttu-id="37b41-140">Definiowanie punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="37b41-140">Defining Endpoints</span></span>  
 <span data-ttu-id="37b41-141">Można określić punktu końcowego usługi za pomocą kodu imperatively lub deklaratywnie przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="37b41-141">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="37b41-142">[Porady: Tworzenie punktu końcowego usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) i [porady: Tworzenie punktu końcowego usługi w kodzie](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="37b41-142"> [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="37b41-143">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="37b41-143">In This Section</span></span>  
 <span data-ttu-id="37b41-144">W tej sekcji opisano w celu powiązania, punktów końcowych i adresy; Pokazuje, jak skonfigurować powiązania i punktu końcowego; i przedstawiono sposób użycia `ClientVia` zachowania i `ListenUri` właściwości.</span><span class="sxs-lookup"><span data-stu-id="37b41-144">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>  
  
 [<span data-ttu-id="37b41-145">Adresy</span><span class="sxs-lookup"><span data-stu-id="37b41-145">Addresses</span></span>](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 <span data-ttu-id="37b41-146">W tym artykule opisano, jak punkty końcowe zostały rozwiązane w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="37b41-146">Describes how endpoints are addressed in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="37b41-147">Powiązania</span><span class="sxs-lookup"><span data-stu-id="37b41-147">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 <span data-ttu-id="37b41-148">Opisuje sposób powiązania są używane do określania transportu, kodowanie i szczegóły protokołu wymagane dla klientów i usług komunikować się ze sobą.</span><span class="sxs-lookup"><span data-stu-id="37b41-148">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>  
  
 [<span data-ttu-id="37b41-149">Kontrakty</span><span class="sxs-lookup"><span data-stu-id="37b41-149">Contracts</span></span>](../../../../docs/framework/wcf/feature-details/contracts.md)  
 <span data-ttu-id="37b41-150">W tym artykule opisano, jak kontrakty definiować metody usługi.</span><span class="sxs-lookup"><span data-stu-id="37b41-150">Describes how contracts define the methods of a service.</span></span>  
  
 [<span data-ttu-id="37b41-151">Instrukcje: tworzenie punktu końcowego usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="37b41-151">How to: Create a Service Endpoint in Configuration</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="37b41-152">Opisuje sposób tworzenia punktu końcowego usługi w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="37b41-152">Describes how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="37b41-153">Instrukcje: tworzenie punktu końcowego usługi w kodzie</span><span class="sxs-lookup"><span data-stu-id="37b41-153">How to: Create a Service Endpoint in Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="37b41-154">Opisuje sposób tworzenia punktu końcowego usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="37b41-154">Describes how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="37b41-155">Instrukcje: weryfikacja skompilowanego kodu usługi za pomocą programu Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="37b41-155">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 <span data-ttu-id="37b41-156">Opisuje sposób wykrywania błędów w implementacji usługi i konfiguracji bez hostingu za pomocą usługi [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="37b41-156">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37b41-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="37b41-157">See Also</span></span>  
 [<span data-ttu-id="37b41-158">Konfigurowanie usług</span><span class="sxs-lookup"><span data-stu-id="37b41-158">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="37b41-159">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="37b41-159">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
