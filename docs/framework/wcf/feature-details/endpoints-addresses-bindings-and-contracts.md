---
title: 'Punkty końcowe: Adresy, powiązania i kontrakty'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 0909d1d10ab8932f27f7ca6cba6207d57fa4f4cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493751"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="b10a7-102">Punkty końcowe: Adresy, powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="b10a7-102">Endpoints: Addresses, Bindings, and Contracts</span></span>
<span data-ttu-id="b10a7-103">Cała komunikacja z usługą Windows Communication Foundation (WCF) odbywa się przez *punkty końcowe* usługi.</span><span class="sxs-lookup"><span data-stu-id="b10a7-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="b10a7-104">Punkty końcowe zapewnić klientom dostęp do funkcji oferowanych przez usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="b10a7-104">Endpoints provide clients access to the functionality offered by a WCF service.</span></span>  
  
 <span data-ttu-id="b10a7-105">Każdy punkt końcowy składa się z czterech właściwości:</span><span class="sxs-lookup"><span data-stu-id="b10a7-105">Each endpoint consists of four properties:</span></span>  
  
-   <span data-ttu-id="b10a7-106">Adres, który wskazuje, gdzie można znaleźć punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b10a7-106">An address that indicates where the endpoint can be found.</span></span>  
  
-   <span data-ttu-id="b10a7-107">Wiązanie, który określa, jak klient może komunikować się z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="b10a7-107">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="b10a7-108">Kontrakt określa operacje dostępne.</span><span class="sxs-lookup"><span data-stu-id="b10a7-108">A contract that identifies the operations available.</span></span>  
  
-   <span data-ttu-id="b10a7-109">Zestaw zachowań, które określają szczegóły implementacji lokalnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b10a7-109">A set of behaviors that specify local implementation details of the endpoint.</span></span>  
  
 <span data-ttu-id="b10a7-110">W tym temacie tej struktury punktu końcowego i opisano, jak są reprezentowane w modelu obiektów programu WCF.</span><span class="sxs-lookup"><span data-stu-id="b10a7-110">This topic discusses this endpoint structure and explains how it is represented in the WCF object model.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="b10a7-111">Struktura punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="b10a7-111">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="b10a7-112">Każdy punkt końcowy składa się z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="b10a7-112">Each endpoint consists of the following:</span></span>  
  
-   <span data-ttu-id="b10a7-113">Adres: Adres unikatowo identyfikuje punkt końcowy i informuje potencjalne korzystającym z usług, w którym znajduje się.</span><span class="sxs-lookup"><span data-stu-id="b10a7-113">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="b10a7-114">Jest reprezentowana w modelu obiektów programu WCF przez <xref:System.ServiceModel.EndpointAddress> klasy.</span><span class="sxs-lookup"><span data-stu-id="b10a7-114">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="b10a7-115"><xref:System.ServiceModel.EndpointAddress> Klasa zawiera:</span><span class="sxs-lookup"><span data-stu-id="b10a7-115">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>  
  
    -   <span data-ttu-id="b10a7-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> właściwość, która reprezentuje adres usługi.</span><span class="sxs-lookup"><span data-stu-id="b10a7-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>  
  
    -   <span data-ttu-id="b10a7-117"><xref:System.ServiceModel.EndpointAddress.Identity%2A> Właściwość, która reprezentuje tożsamości zabezpieczeń usługi i kolekcję nagłówków komunikatów opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="b10a7-117">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="b10a7-118">Nagłówki komunikatów opcjonalne służą do zapewniania dodatkowe i bardziej szczegółowych informacji o adresach do identyfikacji użytkownika lub interakcji z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="b10a7-118">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>  
  
     <span data-ttu-id="b10a7-119">Aby uzyskać więcej informacji, zobacz [Określanie adresu punktu końcowego](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="b10a7-119">For more information, see [Specifying an Endpoint Address](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
-   <span data-ttu-id="b10a7-120">Powiązanie: Powiązanie określa sposób komunikowania się z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="b10a7-120">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="b10a7-121">Możliwości obejmują:</span><span class="sxs-lookup"><span data-stu-id="b10a7-121">This includes:</span></span>  
  
    -   <span data-ttu-id="b10a7-122">Protokół transportu do użycia (np. TCP lub HTTP).</span><span class="sxs-lookup"><span data-stu-id="b10a7-122">The transport protocol to use (for example, TCP or HTTP).</span></span>  
  
    -   <span data-ttu-id="b10a7-123">Szyfrowanie do użycia dla wiadomości (na przykład tekst lub binarny).</span><span class="sxs-lookup"><span data-stu-id="b10a7-123">The encoding to use for the messages (for example, text or binary).</span></span>  
  
    -   <span data-ttu-id="b10a7-124">Niezbędne wymagania dotyczące zabezpieczeń (na przykład protokołu SSL lub protokołu SOAP wiadomości zabezpieczeń).</span><span class="sxs-lookup"><span data-stu-id="b10a7-124">The necessary security requirements (for example, SSL or SOAP message security).</span></span>  
  
     <span data-ttu-id="b10a7-125">Aby uzyskać więcej informacji, zobacz [omówienie powiązań WCF](../../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b10a7-125">For more information, see [WCF Bindings Overview](../../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="b10a7-126">Powiązanie jest reprezentowana w modelu obiektów programu WCF przez abstrakcyjna klasa podstawowa <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="b10a7-126">A binding is represented in the WCF object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="b10a7-127">W przypadku większości scenariuszy użytkownicy mogą używać jednego powiązania dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="b10a7-127">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="b10a7-128">Aby uzyskać więcej informacji, zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="b10a7-128">For more information, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
-   <span data-ttu-id="b10a7-129">Kontrakty: Kontrakt przedstawiono funkcje punktu końcowego udostępnia do klienta.</span><span class="sxs-lookup"><span data-stu-id="b10a7-129">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="b10a7-130">Kontrakt określa:</span><span class="sxs-lookup"><span data-stu-id="b10a7-130">A contract specifies:</span></span>  
  
    -   <span data-ttu-id="b10a7-131">Jakie operacje może zostać wywołany przez klienta.</span><span class="sxs-lookup"><span data-stu-id="b10a7-131">What operations can be called by a client.</span></span>  
  
    -   <span data-ttu-id="b10a7-132">Formularz wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b10a7-132">The form of the message.</span></span>  
  
    -   <span data-ttu-id="b10a7-133">Typ parametrów wejściowych lub danych wymaganych do wywołania operacji.</span><span class="sxs-lookup"><span data-stu-id="b10a7-133">The type of input parameters or data required to call the operation.</span></span>  
  
    -   <span data-ttu-id="b10a7-134">Jakiego typu Przetwarzanie lub odpowiedzi wiadomości przez klienta może spodziewać się.</span><span class="sxs-lookup"><span data-stu-id="b10a7-134">What type of processing or response message the client can expect.</span></span>  
  
     <span data-ttu-id="b10a7-135">Aby uzyskać więcej informacji na temat definiowania kontrakt, zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="b10a7-135">For more information about defining a contract, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
-   <span data-ttu-id="b10a7-136">Zachowania: Aby dostosować zachowanie lokalnego punktu końcowego usługi można użyć zachowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b10a7-136">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="b10a7-137">Zachowania punktu końcowego można to osiągnąć przez uczestnictwa w procesie tworzenia WCFruntime.</span><span class="sxs-lookup"><span data-stu-id="b10a7-137">Endpoint behaviors achieve this by participating in the process of building a WCFruntime.</span></span> <span data-ttu-id="b10a7-138">Przykład zachowania punktu końcowego <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> właściwość, która pozwala na określenie nasłuchiwania inny adres niż adres SOAP lub Web Services Description Language (WSDL).</span><span class="sxs-lookup"><span data-stu-id="b10a7-138">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> <span data-ttu-id="b10a7-139">Aby uzyskać więcej informacji, zobacz [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="b10a7-139">For more information, see [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span></span>  
  
## <a name="defining-endpoints"></a><span data-ttu-id="b10a7-140">Definiowanie punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="b10a7-140">Defining Endpoints</span></span>  
 <span data-ttu-id="b10a7-141">Można określić punktu końcowego usługi za pomocą kodu imperatively lub deklaratywnie przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b10a7-141">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="b10a7-142">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie punktu końcowego usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) i [porady: Tworzenie punktu końcowego usługi w kodzie](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="b10a7-142">For more information, see [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b10a7-143">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b10a7-143">In This Section</span></span>  
 <span data-ttu-id="b10a7-144">W tej sekcji opisano w celu powiązania, punktów końcowych i adresy; Pokazuje, jak skonfigurować powiązania i punktu końcowego; i przedstawiono sposób użycia `ClientVia` zachowania i `ListenUri` właściwości.</span><span class="sxs-lookup"><span data-stu-id="b10a7-144">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>  
  
 [<span data-ttu-id="b10a7-145">Adresy</span><span class="sxs-lookup"><span data-stu-id="b10a7-145">Addresses</span></span>](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 <span data-ttu-id="b10a7-146">W tym artykule opisano, jak punkty końcowe są opisane w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="b10a7-146">Describes how endpoints are addressed in WCF.</span></span>  
  
 [<span data-ttu-id="b10a7-147">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b10a7-147">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 <span data-ttu-id="b10a7-148">Opisuje sposób powiązania są używane do określania transportu, kodowanie i szczegóły protokołu wymagane dla klientów i usług komunikować się ze sobą.</span><span class="sxs-lookup"><span data-stu-id="b10a7-148">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>  
  
 [<span data-ttu-id="b10a7-149">Kontrakty</span><span class="sxs-lookup"><span data-stu-id="b10a7-149">Contracts</span></span>](../../../../docs/framework/wcf/feature-details/contracts.md)  
 <span data-ttu-id="b10a7-150">W tym artykule opisano, jak kontrakty definiować metody usługi.</span><span class="sxs-lookup"><span data-stu-id="b10a7-150">Describes how contracts define the methods of a service.</span></span>  
  
 [<span data-ttu-id="b10a7-151">Instrukcje: tworzenie punktu końcowego usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b10a7-151">How to: Create a Service Endpoint in Configuration</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="b10a7-152">Opisuje sposób tworzenia punktu końcowego usługi w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b10a7-152">Describes how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="b10a7-153">Instrukcje: tworzenie punktu końcowego usługi w kodzie</span><span class="sxs-lookup"><span data-stu-id="b10a7-153">How to: Create a Service Endpoint in Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="b10a7-154">Opisuje sposób tworzenia punktu końcowego usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b10a7-154">Describes how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="b10a7-155">Instrukcje: weryfikacja skompilowanego kodu usługi za pomocą programu Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="b10a7-155">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 <span data-ttu-id="b10a7-156">Opisuje sposób wykrywania błędów w implementacji usługi i konfiguracji bez hostingu za pomocą usługi [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b10a7-156">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b10a7-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b10a7-157">See Also</span></span>  
 [<span data-ttu-id="b10a7-158">Konfigurowanie usług</span><span class="sxs-lookup"><span data-stu-id="b10a7-158">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="b10a7-159">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="b10a7-159">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
