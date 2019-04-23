---
title: 'Punkty końcowe: adresy, wiązania i kontrakty'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 3e78e7cf0c5acde53d7ee23294fd52134414e860
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207529"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="9d768-102">Punkty końcowe: adresy, wiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="9d768-102">Endpoints: Addresses, Bindings, and Contracts</span></span>
<span data-ttu-id="9d768-103">Cała komunikacja z usługą Windows Communication Foundation (WCF) odbywa się przez *punktów końcowych* usługi.</span><span class="sxs-lookup"><span data-stu-id="9d768-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="9d768-104">Punkty końcowe zapewnić klientom dostęp do funkcji oferowanych przez usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="9d768-104">Endpoints provide clients access to the functionality offered by a WCF service.</span></span>  
  
 <span data-ttu-id="9d768-105">Każdy punkt końcowy składa się z czterech właściwości:</span><span class="sxs-lookup"><span data-stu-id="9d768-105">Each endpoint consists of four properties:</span></span>  
  
-   <span data-ttu-id="9d768-106">Adres, który wskazuje, gdzie można znaleźć punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="9d768-106">An address that indicates where the endpoint can be found.</span></span>  
  
-   <span data-ttu-id="9d768-107">Wiązanie, który określa, jak klient może komunikować się z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="9d768-107">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="9d768-108">Kontrakt określa operacje dostępne.</span><span class="sxs-lookup"><span data-stu-id="9d768-108">A contract that identifies the operations available.</span></span>  
  
-   <span data-ttu-id="9d768-109">Zestaw zachowań, które określają szczegółów implementacji lokalnego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="9d768-109">A set of behaviors that specify local implementation details of the endpoint.</span></span>  
  
 <span data-ttu-id="9d768-110">W tym temacie omówiono tej struktury punktu końcowego i wyjaśniono, jak jest reprezentowana w modelu obiektu programu WCF.</span><span class="sxs-lookup"><span data-stu-id="9d768-110">This topic discusses this endpoint structure and explains how it is represented in the WCF object model.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="9d768-111">Struktura punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="9d768-111">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="9d768-112">Każdy punkt końcowy składa się z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="9d768-112">Each endpoint consists of the following:</span></span>  
  
-   <span data-ttu-id="9d768-113">Adres: Adres jednoznacznie identyfikuje punkt końcowy i informuje o potencjalnych klientów usługi, w którym znajduje się.</span><span class="sxs-lookup"><span data-stu-id="9d768-113">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="9d768-114">Jest reprezentowana w modelu obiektu programu WCF za <xref:System.ServiceModel.EndpointAddress> klasy.</span><span class="sxs-lookup"><span data-stu-id="9d768-114">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="9d768-115"><xref:System.ServiceModel.EndpointAddress> Klasa zawiera:</span><span class="sxs-lookup"><span data-stu-id="9d768-115">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>  
  
    -   <span data-ttu-id="9d768-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> właściwość, która reprezentuje adres usługi.</span><span class="sxs-lookup"><span data-stu-id="9d768-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>  
  
    -   <span data-ttu-id="9d768-117"><xref:System.ServiceModel.EndpointAddress.Identity%2A> Właściwość, która reprezentuje kolekcję nagłówków opcjonalną wiadomość, jak i tożsamości zabezpieczeń usługi.</span><span class="sxs-lookup"><span data-stu-id="9d768-117">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="9d768-118">Nagłówki wiadomości opcjonalne są używane do zapewnienia dodatkowych i bardziej szczegółowe informacje dotyczące adresowania, aby zidentyfikować lub nawiązać kontakt z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="9d768-118">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>  
  
     <span data-ttu-id="9d768-119">Aby uzyskać więcej informacji, zobacz [Określanie adresu punktu końcowego](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="9d768-119">For more information, see [Specifying an Endpoint Address](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
-   <span data-ttu-id="9d768-120">Powiązanie: Powiązanie Określa, jak komunikować się z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="9d768-120">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="9d768-121">Możliwości obejmują:</span><span class="sxs-lookup"><span data-stu-id="9d768-121">This includes:</span></span>  
  
    -   <span data-ttu-id="9d768-122">Protokół transportu do użycia (na przykład, TCP lub HTTP).</span><span class="sxs-lookup"><span data-stu-id="9d768-122">The transport protocol to use (for example, TCP or HTTP).</span></span>  
  
    -   <span data-ttu-id="9d768-123">Szyfrowanie do użycia dla wiadomości (na przykład tekst lub dane binarne).</span><span class="sxs-lookup"><span data-stu-id="9d768-123">The encoding to use for the messages (for example, text or binary).</span></span>  
  
    -   <span data-ttu-id="9d768-124">Niezbędne wymagania w zakresie zabezpieczeń (na przykład protokołu SSL lub protokołu SOAP wiadomości zabezpieczeń).</span><span class="sxs-lookup"><span data-stu-id="9d768-124">The necessary security requirements (for example, SSL or SOAP message security).</span></span>  
  
     <span data-ttu-id="9d768-125">Aby uzyskać więcej informacji, zobacz [omówienie powiązań WCF](../../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9d768-125">For more information, see [WCF Bindings Overview](../../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="9d768-126">Powiązanie jest reprezentowana w modelu obiektu programu WCF przez abstrakcyjna klasa bazowa <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="9d768-126">A binding is represented in the WCF object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="9d768-127">W przypadku większości scenariuszy użytkownicy mogą użyć jednego z powiązań dostarczanych przez system.</span><span class="sxs-lookup"><span data-stu-id="9d768-127">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="9d768-128">Aby uzyskać więcej informacji, zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="9d768-128">For more information, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
-   <span data-ttu-id="9d768-129">Zamówień: Kontrakt opisano, jakie funkcje uwidacznia punkt końcowy, do klienta.</span><span class="sxs-lookup"><span data-stu-id="9d768-129">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="9d768-130">Kontrakt określa:</span><span class="sxs-lookup"><span data-stu-id="9d768-130">A contract specifies:</span></span>  
  
    -   <span data-ttu-id="9d768-131">Jakie operacje mogą być wywoływane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="9d768-131">What operations can be called by a client.</span></span>  
  
    -   <span data-ttu-id="9d768-132">Formularz wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9d768-132">The form of the message.</span></span>  
  
    -   <span data-ttu-id="9d768-133">Typ parametry wejściowe i dane wymagane do wywołania operacji.</span><span class="sxs-lookup"><span data-stu-id="9d768-133">The type of input parameters or data required to call the operation.</span></span>  
  
    -   <span data-ttu-id="9d768-134">Jakiego typu Przetwarzanie lub odpowiedzi wiadomości klienta można się spodziewać.</span><span class="sxs-lookup"><span data-stu-id="9d768-134">What type of processing or response message the client can expect.</span></span>  
  
     <span data-ttu-id="9d768-135">Aby uzyskać więcej informacji na temat definiowania kontrakt zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="9d768-135">For more information about defining a contract, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
-   <span data-ttu-id="9d768-136">Zachowania: Aby dostosować zachowanie lokalny punkt końcowy usługi, można użyć zachowań punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="9d768-136">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="9d768-137">Zachowań punktu końcowego to osiągnąć przez uczestnictwem w procesie tworzenia WCFruntime.</span><span class="sxs-lookup"><span data-stu-id="9d768-137">Endpoint behaviors achieve this by participating in the process of building a WCFruntime.</span></span> <span data-ttu-id="9d768-138">Na przykład zachowanie punktu końcowego <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> właściwość, która pozwala na określenie na adres nasłuchiwania inny niż adres protokołu SOAP lub Web Services Description Language (WSDL).</span><span class="sxs-lookup"><span data-stu-id="9d768-138">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> <span data-ttu-id="9d768-139">Aby uzyskać więcej informacji, zobacz [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="9d768-139">For more information, see [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span></span>  
  
## <a name="defining-endpoints"></a><span data-ttu-id="9d768-140">Definiowanie punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="9d768-140">Defining Endpoints</span></span>  
 <span data-ttu-id="9d768-141">Można określić punktu końcowego usługi obowiązkowo za pomocą kodu lub w sposób deklaratywny przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9d768-141">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="9d768-142">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie punktu końcowego usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) i [jak: Tworzenie punktu końcowego usługi w kodzie](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="9d768-142">For more information, see [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9d768-143">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9d768-143">In This Section</span></span>  
 <span data-ttu-id="9d768-144">Ta sekcja zawiera wyjaśnienie przeznaczenia powiązania, punktów końcowych oraz adresy; Pokazuje, jak skonfigurować powiązania i punktu końcowego; i pokazuje sposób użycia `ClientVia` zachowanie i `ListenUri` właściwości.</span><span class="sxs-lookup"><span data-stu-id="9d768-144">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>  
  
 [<span data-ttu-id="9d768-145">Adresy</span><span class="sxs-lookup"><span data-stu-id="9d768-145">Addresses</span></span>](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 <span data-ttu-id="9d768-146">W tym artykule opisano, jak punkty końcowe zostały rozwiązane w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="9d768-146">Describes how endpoints are addressed in WCF.</span></span>  
  
 [<span data-ttu-id="9d768-147">Powiązania</span><span class="sxs-lookup"><span data-stu-id="9d768-147">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 <span data-ttu-id="9d768-148">W tym artykule opisano, jak powiązań są używane do określania, transport, kodowanie i szczegóły protokołu wymagane dla klientów i usług komunikować się ze sobą.</span><span class="sxs-lookup"><span data-stu-id="9d768-148">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>  
  
 [<span data-ttu-id="9d768-149">Kontrakty</span><span class="sxs-lookup"><span data-stu-id="9d768-149">Contracts</span></span>](../../../../docs/framework/wcf/feature-details/contracts.md)  
 <span data-ttu-id="9d768-150">W tym artykule opisano, jak kontrakty definiować metody usługi.</span><span class="sxs-lookup"><span data-stu-id="9d768-150">Describes how contracts define the methods of a service.</span></span>  
  
 [<span data-ttu-id="9d768-151">Instrukcje: Tworzenie punktu końcowego usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9d768-151">How to: Create a Service Endpoint in Configuration</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="9d768-152">W tym artykule opisano, jak utworzyć punkt końcowy usługi w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9d768-152">Describes how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="9d768-153">Instrukcje: Tworzenie punktu końcowego usługi w kodzie</span><span class="sxs-lookup"><span data-stu-id="9d768-153">How to: Create a Service Endpoint in Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="9d768-154">W tym artykule opisano, jak utworzyć punkt końcowy usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="9d768-154">Describes how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="9d768-155">Instrukcje: Weryfikacja skompilowanego kodu usługi za pomocą programu Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="9d768-155">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 <span data-ttu-id="9d768-156">W tym artykule opisano sposób wykrywania błędów w implementacji usługi i konfiguracji bez hostingu za pomocą usługi [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9d768-156">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d768-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d768-157">See also</span></span>

- [<span data-ttu-id="9d768-158">Konfigurowanie usług</span><span class="sxs-lookup"><span data-stu-id="9d768-158">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)
- [<span data-ttu-id="9d768-159">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="9d768-159">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
