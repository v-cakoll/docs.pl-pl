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
ms.openlocfilehash: 6c0b13ee48ed729d89f4b4b506e3608abe7e82b5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="e5a17-102">Punkty końcowe: Adresy, powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="e5a17-102">Endpoints: Addresses, Bindings, and Contracts</span></span>
<span data-ttu-id="e5a17-103">Cała komunikacja z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi odbywa się przez *punkty końcowe* usługi.</span><span class="sxs-lookup"><span data-stu-id="e5a17-103">All communication with a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="e5a17-104">Punkty końcowe zapewnić klientom dostęp do funkcji oferowanych przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="e5a17-104">Endpoints provide clients access to the functionality offered by a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="e5a17-105">Każdy punkt końcowy składa się z czterech właściwości:</span><span class="sxs-lookup"><span data-stu-id="e5a17-105">Each endpoint consists of four properties:</span></span>  
  
-   <span data-ttu-id="e5a17-106">Adres, który wskazuje, gdzie można znaleźć punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e5a17-106">An address that indicates where the endpoint can be found.</span></span>  
  
-   <span data-ttu-id="e5a17-107">Wiązanie, który określa, jak klient może komunikować się z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="e5a17-107">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="e5a17-108">Kontrakt określa operacje dostępne.</span><span class="sxs-lookup"><span data-stu-id="e5a17-108">A contract that identifies the operations available.</span></span>  
  
-   <span data-ttu-id="e5a17-109">Zestaw zachowań, które określają szczegóły implementacji lokalnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e5a17-109">A set of behaviors that specify local implementation details of the endpoint.</span></span>  
  
 <span data-ttu-id="e5a17-110">W tym temacie omówiono tego punktu końcowego struktury oraz wyjaśniono, jak są reprezentowane w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiektu modelu.</span><span class="sxs-lookup"><span data-stu-id="e5a17-110">This topic discusses this endpoint structure and explains how it is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="e5a17-111">Struktura punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="e5a17-111">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="e5a17-112">Każdy punkt końcowy składa się z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="e5a17-112">Each endpoint consists of the following:</span></span>  
  
-   <span data-ttu-id="e5a17-113">Adres: Adres unikatowo identyfikuje punkt końcowy i informuje potencjalne korzystającym z usług, w którym znajduje się.</span><span class="sxs-lookup"><span data-stu-id="e5a17-113">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="e5a17-114">Jest reprezentowana w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model obiektów przez <xref:System.ServiceModel.EndpointAddress> klasy.</span><span class="sxs-lookup"><span data-stu-id="e5a17-114">It is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="e5a17-115"><xref:System.ServiceModel.EndpointAddress> Klasa zawiera:</span><span class="sxs-lookup"><span data-stu-id="e5a17-115">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>  
  
    -   <span data-ttu-id="e5a17-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> właściwość, która reprezentuje adres usługi.</span><span class="sxs-lookup"><span data-stu-id="e5a17-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>  
  
    -   <span data-ttu-id="e5a17-117"><xref:System.ServiceModel.EndpointAddress.Identity%2A> Właściwość, która reprezentuje tożsamości zabezpieczeń usługi i kolekcję nagłówków komunikatów opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e5a17-117">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="e5a17-118">Nagłówki komunikatów opcjonalne służą do zapewniania dodatkowe i bardziej szczegółowych informacji o adresach do identyfikacji użytkownika lub interakcji z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="e5a17-118">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="e5a17-119">[Określanie adresu punktu końcowego](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="e5a17-119"> [Specifying an Endpoint Address](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
-   <span data-ttu-id="e5a17-120">Powiązanie: Powiązanie określa sposób komunikowania się z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="e5a17-120">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="e5a17-121">Możliwości obejmują:</span><span class="sxs-lookup"><span data-stu-id="e5a17-121">This includes:</span></span>  
  
    -   <span data-ttu-id="e5a17-122">Protokół transportu do użycia (np. TCP lub HTTP).</span><span class="sxs-lookup"><span data-stu-id="e5a17-122">The transport protocol to use (for example, TCP or HTTP).</span></span>  
  
    -   <span data-ttu-id="e5a17-123">Szyfrowanie do użycia dla wiadomości (na przykład tekst lub binarny).</span><span class="sxs-lookup"><span data-stu-id="e5a17-123">The encoding to use for the messages (for example, text or binary).</span></span>  
  
    -   <span data-ttu-id="e5a17-124">Niezbędne wymagania dotyczące zabezpieczeń (na przykład protokołu SSL lub protokołu SOAP wiadomości zabezpieczeń).</span><span class="sxs-lookup"><span data-stu-id="e5a17-124">The necessary security requirements (for example, SSL or SOAP message security).</span></span>  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="e5a17-125">[Omówienie powiązań WCF](../../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e5a17-125"> [WCF Bindings Overview](../../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="e5a17-126">Powiązanie jest reprezentowana w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model obiektów przez abstrakcyjna klasa podstawowa <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="e5a17-126">A binding is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="e5a17-127">W przypadku większości scenariuszy użytkownicy mogą używać jednego powiązania dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="e5a17-127">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="e5a17-128">Aby uzyskać więcej informacji, zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="e5a17-128">For more information, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
-   <span data-ttu-id="e5a17-129">Kontrakty: Kontrakt przedstawiono funkcje punktu końcowego udostępnia do klienta.</span><span class="sxs-lookup"><span data-stu-id="e5a17-129">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="e5a17-130">Kontrakt określa:</span><span class="sxs-lookup"><span data-stu-id="e5a17-130">A contract specifies:</span></span>  
  
    -   <span data-ttu-id="e5a17-131">Jakie operacje może zostać wywołany przez klienta.</span><span class="sxs-lookup"><span data-stu-id="e5a17-131">What operations can be called by a client.</span></span>  
  
    -   <span data-ttu-id="e5a17-132">Formularz wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e5a17-132">The form of the message.</span></span>  
  
    -   <span data-ttu-id="e5a17-133">Typ parametrów wejściowych lub danych wymaganych do wywołania operacji.</span><span class="sxs-lookup"><span data-stu-id="e5a17-133">The type of input parameters or data required to call the operation.</span></span>  
  
    -   <span data-ttu-id="e5a17-134">Jakiego typu Przetwarzanie lub odpowiedzi wiadomości przez klienta może spodziewać się.</span><span class="sxs-lookup"><span data-stu-id="e5a17-134">What type of processing or response message the client can expect.</span></span>  
  
     <span data-ttu-id="e5a17-135">Aby uzyskać więcej informacji na temat definiowania kontrakt, zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="e5a17-135">For more information about defining a contract, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
-   <span data-ttu-id="e5a17-136">Zachowania: Aby dostosować zachowanie lokalnego punktu końcowego usługi można użyć zachowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e5a17-136">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="e5a17-137">Zachowania punktu końcowego to zrobić, uczestnictwa w procesie tworzenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="e5a17-137">Endpoint behaviors achieve this by participating in the process of building a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]runtime.</span></span> <span data-ttu-id="e5a17-138">Przykład zachowania punktu końcowego <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> właściwość, która pozwala na określenie nasłuchiwania inny adres niż adres SOAP lub Web Services Description Language (WSDL).</span><span class="sxs-lookup"><span data-stu-id="e5a17-138">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="e5a17-139">[ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="e5a17-139"> [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span></span>  
  
## <a name="defining-endpoints"></a><span data-ttu-id="e5a17-140">Definiowanie punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="e5a17-140">Defining Endpoints</span></span>  
 <span data-ttu-id="e5a17-141">Można określić punktu końcowego usługi za pomocą kodu imperatively lub deklaratywnie przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e5a17-141">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="e5a17-142">[Porady: Tworzenie punktu końcowego usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) i [porady: Tworzenie punktu końcowego usługi w kodzie](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="e5a17-142"> [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5a17-143">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e5a17-143">In This Section</span></span>  
 <span data-ttu-id="e5a17-144">W tej sekcji opisano w celu powiązania, punktów końcowych i adresy; Pokazuje, jak skonfigurować powiązania i punktu końcowego; i przedstawiono sposób użycia `ClientVia` zachowania i `ListenUri` właściwości.</span><span class="sxs-lookup"><span data-stu-id="e5a17-144">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>  
  
 [<span data-ttu-id="e5a17-145">Adresy</span><span class="sxs-lookup"><span data-stu-id="e5a17-145">Addresses</span></span>](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 <span data-ttu-id="e5a17-146">W tym artykule opisano, jak punkty końcowe zostały rozwiązane w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5a17-146">Describes how endpoints are addressed in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="e5a17-147">Powiązania</span><span class="sxs-lookup"><span data-stu-id="e5a17-147">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 <span data-ttu-id="e5a17-148">Opisuje sposób powiązania są używane do określania transportu, kodowanie i szczegóły protokołu wymagane dla klientów i usług komunikować się ze sobą.</span><span class="sxs-lookup"><span data-stu-id="e5a17-148">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>  
  
 [<span data-ttu-id="e5a17-149">Kontrakty</span><span class="sxs-lookup"><span data-stu-id="e5a17-149">Contracts</span></span>](../../../../docs/framework/wcf/feature-details/contracts.md)  
 <span data-ttu-id="e5a17-150">W tym artykule opisano, jak kontrakty definiować metody usługi.</span><span class="sxs-lookup"><span data-stu-id="e5a17-150">Describes how contracts define the methods of a service.</span></span>  
  
 [<span data-ttu-id="e5a17-151">Porady: Tworzenie punktu końcowego usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e5a17-151">How to: Create a Service Endpoint in Configuration</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="e5a17-152">Opisuje sposób tworzenia punktu końcowego usługi w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e5a17-152">Describes how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="e5a17-153">Porady: Tworzenie punktu końcowego usługi w kodzie</span><span class="sxs-lookup"><span data-stu-id="e5a17-153">How to: Create a Service Endpoint in Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="e5a17-154">Opisuje sposób tworzenia punktu końcowego usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e5a17-154">Describes how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="e5a17-155">Porady: Weryfikacja skompilowanego kodu usługi za pomocą programu Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="e5a17-155">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 <span data-ttu-id="e5a17-156">Opisuje sposób wykrywania błędów w implementacji usługi i konfiguracji bez hostingu za pomocą usługi [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e5a17-156">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5a17-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5a17-157">See Also</span></span>  
 [<span data-ttu-id="e5a17-158">Konfigurowanie usług</span><span class="sxs-lookup"><span data-stu-id="e5a17-158">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="e5a17-159">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="e5a17-159">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
