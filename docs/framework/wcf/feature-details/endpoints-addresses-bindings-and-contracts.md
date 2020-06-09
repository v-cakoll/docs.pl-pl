---
title: 'Punkty końcowe: Adresy, powiązania i kontrakty'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 3ac7f0b165b99a1ed3702628958f7d4c7702f5b1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593519"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="62e9e-102">Punkty końcowe: Adresy, powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="62e9e-102">Endpoints: Addresses, Bindings, and Contracts</span></span>

<span data-ttu-id="62e9e-103">Cała komunikacja z usługą Windows Communication Foundation (WCF) odbywa się za pomocą *punktów końcowych* usługi.</span><span class="sxs-lookup"><span data-stu-id="62e9e-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="62e9e-104">Punkty końcowe zapewniają klientom dostęp do funkcji oferowanych przez usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="62e9e-104">Endpoints provide clients access to the functionality offered by a WCF service.</span></span>

<span data-ttu-id="62e9e-105">Każdy punkt końcowy zawiera cztery właściwości:</span><span class="sxs-lookup"><span data-stu-id="62e9e-105">Each endpoint consists of four properties:</span></span>

- <span data-ttu-id="62e9e-106">Adres wskazujący, gdzie można znaleźć punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="62e9e-106">An address that indicates where the endpoint can be found.</span></span>

- <span data-ttu-id="62e9e-107">Powiązanie określające, w jaki sposób klient może komunikować się z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="62e9e-107">A binding that specifies how a client can communicate with the endpoint.</span></span>

- <span data-ttu-id="62e9e-108">Kontrakt, który identyfikuje dostępne operacje.</span><span class="sxs-lookup"><span data-stu-id="62e9e-108">A contract that identifies the operations available.</span></span>

- <span data-ttu-id="62e9e-109">Zestaw zachowań określających szczegóły implementacji lokalnej punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="62e9e-109">A set of behaviors that specify local implementation details of the endpoint.</span></span>

<span data-ttu-id="62e9e-110">W tym temacie omówiono tę strukturę punktu końcowego i wyjaśniono, jak jest reprezentowana w modelu obiektów WCF.</span><span class="sxs-lookup"><span data-stu-id="62e9e-110">This topic discusses this endpoint structure and explains how it is represented in the WCF object model.</span></span>

## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="62e9e-111">Struktura punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="62e9e-111">The Structure of an Endpoint</span></span>

<span data-ttu-id="62e9e-112">Każdy punkt końcowy składa się z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="62e9e-112">Each endpoint consists of the following:</span></span>

- <span data-ttu-id="62e9e-113">Address: adres jednoznacznie identyfikuje punkt końcowy i informuje potencjalnych klientów usługi o tym, gdzie się znajdują.</span><span class="sxs-lookup"><span data-stu-id="62e9e-113">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="62e9e-114">Jest reprezentowana w modelu obiektów WCF przez <xref:System.ServiceModel.EndpointAddress> klasę.</span><span class="sxs-lookup"><span data-stu-id="62e9e-114">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="62e9e-115"><xref:System.ServiceModel.EndpointAddress>Klasa zawiera:</span><span class="sxs-lookup"><span data-stu-id="62e9e-115">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>

  - <span data-ttu-id="62e9e-116"><xref:System.ServiceModel.EndpointAddress.Uri%2A>Właściwość, która reprezentuje adres usługi.</span><span class="sxs-lookup"><span data-stu-id="62e9e-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>

  - <span data-ttu-id="62e9e-117"><xref:System.ServiceModel.EndpointAddress.Identity%2A>Właściwość, która reprezentuje tożsamość zabezpieczeń usługi i kolekcję opcjonalnych nagłówków komunikatów.</span><span class="sxs-lookup"><span data-stu-id="62e9e-117">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="62e9e-118">Opcjonalne nagłówki wiadomości są używane do udostępniania dodatkowych i bardziej szczegółowych informacji o adresach w celu identyfikowania punktu końcowego lub korzystania z niego.</span><span class="sxs-lookup"><span data-stu-id="62e9e-118">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>

  <span data-ttu-id="62e9e-119">Aby uzyskać więcej informacji, zobacz [Określanie adresu punktu końcowego](../specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="62e9e-119">For more information, see [Specifying an Endpoint Address](../specifying-an-endpoint-address.md).</span></span>

- <span data-ttu-id="62e9e-120">Powiązanie: powiązanie określa sposób komunikacji z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="62e9e-120">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="62e9e-121">Obejmuje to:</span><span class="sxs-lookup"><span data-stu-id="62e9e-121">This includes:</span></span>

  - <span data-ttu-id="62e9e-122">Protokół transportowy do użycia (na przykład TCP lub HTTP).</span><span class="sxs-lookup"><span data-stu-id="62e9e-122">The transport protocol to use (for example, TCP or HTTP).</span></span>

  - <span data-ttu-id="62e9e-123">Kodowanie, które ma być używane dla wiadomości (na przykład tekst lub binarny).</span><span class="sxs-lookup"><span data-stu-id="62e9e-123">The encoding to use for the messages (for example, text or binary).</span></span>

  - <span data-ttu-id="62e9e-124">Niezbędne wymagania dotyczące zabezpieczeń (na przykład zabezpieczenia protokołu SSL lub protokołu SOAP).</span><span class="sxs-lookup"><span data-stu-id="62e9e-124">The necessary security requirements (for example, SSL or SOAP message security).</span></span>

  <span data-ttu-id="62e9e-125">Aby uzyskać więcej informacji, zobacz temat [powiązania WCF — Omówienie](../bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="62e9e-125">For more information, see [WCF Bindings Overview](../bindings-overview.md).</span></span> <span data-ttu-id="62e9e-126">Powiązanie jest reprezentowane w modelu obiektów WCF przez abstrakcyjną klasę bazową <xref:System.ServiceModel.Channels.Binding> .</span><span class="sxs-lookup"><span data-stu-id="62e9e-126">A binding is represented in the WCF object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="62e9e-127">W przypadku większości scenariuszy użytkownicy mogą korzystać z jednego z powiązań dostarczonych przez system.</span><span class="sxs-lookup"><span data-stu-id="62e9e-127">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="62e9e-128">Aby uzyskać więcej informacji, zobacz [powiązania dostarczone przez system](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="62e9e-128">For more information, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

- <span data-ttu-id="62e9e-129">Kontrakty: kontrakt zawiera informacje o funkcjach, które punkt końcowy uwidoczni dla klienta.</span><span class="sxs-lookup"><span data-stu-id="62e9e-129">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="62e9e-130">Kontrakt określa:</span><span class="sxs-lookup"><span data-stu-id="62e9e-130">A contract specifies:</span></span>

  - <span data-ttu-id="62e9e-131">Jakie operacje mogą być wywoływane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="62e9e-131">What operations can be called by a client.</span></span>

  - <span data-ttu-id="62e9e-132">Formularz wiadomości.</span><span class="sxs-lookup"><span data-stu-id="62e9e-132">The form of the message.</span></span>

  - <span data-ttu-id="62e9e-133">Typ parametrów wejściowych lub danych wymaganych do wywołania operacji.</span><span class="sxs-lookup"><span data-stu-id="62e9e-133">The type of input parameters or data required to call the operation.</span></span>

  - <span data-ttu-id="62e9e-134">Jakiego typu komunikaty o przetwarzaniu lub odpowiedzi mogą oczekiwać klient.</span><span class="sxs-lookup"><span data-stu-id="62e9e-134">What type of processing or response message the client can expect.</span></span>

  <span data-ttu-id="62e9e-135">Aby uzyskać więcej informacji na temat definiowania kontraktu, zobacz [Projektowanie kontraktów usług](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="62e9e-135">For more information about defining a contract, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>

- <span data-ttu-id="62e9e-136">Zachowania: można użyć zachowań punktów końcowych, aby dostosować lokalne zachowanie punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="62e9e-136">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="62e9e-137">Zachowania punktów końcowych osiągają ten udział w procesie tworzenia środowiska uruchomieniowego WCF.</span><span class="sxs-lookup"><span data-stu-id="62e9e-137">Endpoint behaviors achieve this by participating in the process of building a WCF runtime.</span></span> <span data-ttu-id="62e9e-138">Przykładem zachowania punktu końcowego jest <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> Właściwość, która umożliwia określenie innego adresu nasłuchiwania niż adres SOAP lub Web Services Description Language (WSDL).</span><span class="sxs-lookup"><span data-stu-id="62e9e-138">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> <span data-ttu-id="62e9e-139">Aby uzyskać więcej informacji, zobacz [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="62e9e-139">For more information, see [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).</span></span>

## <a name="defining-endpoints"></a><span data-ttu-id="62e9e-140">Definiowanie punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="62e9e-140">Defining Endpoints</span></span>

<span data-ttu-id="62e9e-141">Punkt końcowy usługi można określić za pomocą kodu lub deklaratywnie za pośrednictwem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="62e9e-141">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="62e9e-142">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie punktu końcowego usługi w konfiguracji](how-to-create-a-service-endpoint-in-configuration.md) i [instrukcje: Tworzenie punktu końcowego usługi w kodzie](how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="62e9e-142">For more information, see [How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="62e9e-143">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="62e9e-143">In This Section</span></span>

<span data-ttu-id="62e9e-144">W tej sekcji wyjaśniono cel powiązań, punktów końcowych i adresów; pokazuje, jak skonfigurować powiązanie i punkt końcowy; i pokazuje, jak używać `ClientVia` zachowań i `ListenUri` właściwości.</span><span class="sxs-lookup"><span data-stu-id="62e9e-144">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>

<span data-ttu-id="62e9e-145">[Adres](endpoint-addresses.md)</span><span class="sxs-lookup"><span data-stu-id="62e9e-145">[Addresses](endpoint-addresses.md)</span></span>\
<span data-ttu-id="62e9e-146">Opisuje, w jaki sposób punkty końcowe są rozkierowane na platformie WCF.</span><span class="sxs-lookup"><span data-stu-id="62e9e-146">Describes how endpoints are addressed in WCF.</span></span>

<span data-ttu-id="62e9e-147">[Powiązań](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="62e9e-147">[Bindings](bindings.md)</span></span>\
<span data-ttu-id="62e9e-148">Opisuje, w jaki sposób powiązania są używane do określania informacji o transportach, kodowaniu i protokole wymaganych przez klientów i usługi do komunikowania się ze sobą.</span><span class="sxs-lookup"><span data-stu-id="62e9e-148">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>

<span data-ttu-id="62e9e-149">[Kontraktacj](contracts.md)</span><span class="sxs-lookup"><span data-stu-id="62e9e-149">[Contracts](contracts.md)</span></span>\
<span data-ttu-id="62e9e-150">Opisuje, jak kontrakty definiują metody usługi.</span><span class="sxs-lookup"><span data-stu-id="62e9e-150">Describes how contracts define the methods of a service.</span></span>

<span data-ttu-id="62e9e-151">[Instrukcje: Tworzenie punktu końcowego usługi w konfiguracji](how-to-create-a-service-endpoint-in-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="62e9e-151">[How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md)</span></span>\
<span data-ttu-id="62e9e-152">Opisuje sposób tworzenia punktu końcowego usługi w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="62e9e-152">Describes how to create a service endpoint in configuration.</span></span>

<span data-ttu-id="62e9e-153">[Instrukcje: Tworzenie punktu końcowego usługi w kodzie](how-to-create-a-service-endpoint-in-code.md)</span><span class="sxs-lookup"><span data-stu-id="62e9e-153">[How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md)</span></span>\
<span data-ttu-id="62e9e-154">Opisuje sposób tworzenia punktu końcowego usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="62e9e-154">Describes how to create a service endpoint in code.</span></span>

<span data-ttu-id="62e9e-155">[Instrukcje: użycie programu Svcutil. exe do zweryfikowania skompilowanego kodu usługi](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span><span class="sxs-lookup"><span data-stu-id="62e9e-155">[How to: Use Svcutil.exe to Validate Compiled Service Code](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span></span>\
<span data-ttu-id="62e9e-156">Opisuje sposób wykrywania błędów w implementacjach i konfiguracjach usług bez udostępniania usługi przy użyciu [Narzędzia do obsługi metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="62e9e-156">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="62e9e-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62e9e-157">See also</span></span>

- [<span data-ttu-id="62e9e-158">Konfigurowanie usług</span><span class="sxs-lookup"><span data-stu-id="62e9e-158">Configuring Services</span></span>](../configuring-services.md)
- [<span data-ttu-id="62e9e-159">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="62e9e-159">Extending Bindings</span></span>](../extending/extending-bindings.md)
