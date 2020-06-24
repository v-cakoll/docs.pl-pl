---
title: 'Punkty końcowe: Adresy, powiązania i kontrakty'
description: Dowiedz się, jak cała komunikacja z usługą WCF odbywa się za pomocą punktów końcowych usługi, które zapewniają klientom dostęp do funkcji oferowanych przez usługę.
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: ce0874bfed716716b6fd1801b35a4266095cd752
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247315"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="9b986-103">Punkty końcowe: Adresy, powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="9b986-103">Endpoints: Addresses, Bindings, and Contracts</span></span>

<span data-ttu-id="9b986-104">Cała komunikacja z usługą Windows Communication Foundation (WCF) odbywa się za pomocą *punktów końcowych* usługi.</span><span class="sxs-lookup"><span data-stu-id="9b986-104">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="9b986-105">Punkty końcowe zapewniają klientom dostęp do funkcji oferowanych przez usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="9b986-105">Endpoints provide clients access to the functionality offered by a WCF service.</span></span>

<span data-ttu-id="9b986-106">Każdy punkt końcowy zawiera cztery właściwości:</span><span class="sxs-lookup"><span data-stu-id="9b986-106">Each endpoint consists of four properties:</span></span>

- <span data-ttu-id="9b986-107">Adres wskazujący, gdzie można znaleźć punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="9b986-107">An address that indicates where the endpoint can be found.</span></span>

- <span data-ttu-id="9b986-108">Powiązanie określające, w jaki sposób klient może komunikować się z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="9b986-108">A binding that specifies how a client can communicate with the endpoint.</span></span>

- <span data-ttu-id="9b986-109">Kontrakt, który identyfikuje dostępne operacje.</span><span class="sxs-lookup"><span data-stu-id="9b986-109">A contract that identifies the operations available.</span></span>

- <span data-ttu-id="9b986-110">Zestaw zachowań określających szczegóły implementacji lokalnej punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="9b986-110">A set of behaviors that specify local implementation details of the endpoint.</span></span>

<span data-ttu-id="9b986-111">W tym temacie omówiono tę strukturę punktu końcowego i wyjaśniono, jak jest reprezentowana w modelu obiektów WCF.</span><span class="sxs-lookup"><span data-stu-id="9b986-111">This topic discusses this endpoint structure and explains how it is represented in the WCF object model.</span></span>

## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="9b986-112">Struktura punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="9b986-112">The Structure of an Endpoint</span></span>

<span data-ttu-id="9b986-113">Każdy punkt końcowy składa się z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="9b986-113">Each endpoint consists of the following:</span></span>

- <span data-ttu-id="9b986-114">Address: adres jednoznacznie identyfikuje punkt końcowy i informuje potencjalnych klientów usługi o tym, gdzie się znajdują.</span><span class="sxs-lookup"><span data-stu-id="9b986-114">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="9b986-115">Jest reprezentowana w modelu obiektów WCF przez <xref:System.ServiceModel.EndpointAddress> klasę.</span><span class="sxs-lookup"><span data-stu-id="9b986-115">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="9b986-116"><xref:System.ServiceModel.EndpointAddress>Klasa zawiera:</span><span class="sxs-lookup"><span data-stu-id="9b986-116">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>

  - <span data-ttu-id="9b986-117"><xref:System.ServiceModel.EndpointAddress.Uri%2A>Właściwość, która reprezentuje adres usługi.</span><span class="sxs-lookup"><span data-stu-id="9b986-117">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>

  - <span data-ttu-id="9b986-118"><xref:System.ServiceModel.EndpointAddress.Identity%2A>Właściwość, która reprezentuje tożsamość zabezpieczeń usługi i kolekcję opcjonalnych nagłówków komunikatów.</span><span class="sxs-lookup"><span data-stu-id="9b986-118">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="9b986-119">Opcjonalne nagłówki wiadomości są używane do udostępniania dodatkowych i bardziej szczegółowych informacji o adresach w celu identyfikowania punktu końcowego lub korzystania z niego.</span><span class="sxs-lookup"><span data-stu-id="9b986-119">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>

  <span data-ttu-id="9b986-120">Aby uzyskać więcej informacji, zobacz [Określanie adresu punktu końcowego](../specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="9b986-120">For more information, see [Specifying an Endpoint Address](../specifying-an-endpoint-address.md).</span></span>

- <span data-ttu-id="9b986-121">Powiązanie: powiązanie określa sposób komunikacji z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="9b986-121">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="9b986-122">Obejmuje to:</span><span class="sxs-lookup"><span data-stu-id="9b986-122">This includes:</span></span>

  - <span data-ttu-id="9b986-123">Protokół transportowy do użycia (na przykład TCP lub HTTP).</span><span class="sxs-lookup"><span data-stu-id="9b986-123">The transport protocol to use (for example, TCP or HTTP).</span></span>

  - <span data-ttu-id="9b986-124">Kodowanie, które ma być używane dla wiadomości (na przykład tekst lub binarny).</span><span class="sxs-lookup"><span data-stu-id="9b986-124">The encoding to use for the messages (for example, text or binary).</span></span>

  - <span data-ttu-id="9b986-125">Niezbędne wymagania dotyczące zabezpieczeń (na przykład zabezpieczenia protokołu SSL lub protokołu SOAP).</span><span class="sxs-lookup"><span data-stu-id="9b986-125">The necessary security requirements (for example, SSL or SOAP message security).</span></span>

  <span data-ttu-id="9b986-126">Aby uzyskać więcej informacji, zobacz temat [powiązania WCF — Omówienie](../bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9b986-126">For more information, see [WCF Bindings Overview](../bindings-overview.md).</span></span> <span data-ttu-id="9b986-127">Powiązanie jest reprezentowane w modelu obiektów WCF przez abstrakcyjną klasę bazową <xref:System.ServiceModel.Channels.Binding> .</span><span class="sxs-lookup"><span data-stu-id="9b986-127">A binding is represented in the WCF object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="9b986-128">W przypadku większości scenariuszy użytkownicy mogą korzystać z jednego z powiązań dostarczonych przez system.</span><span class="sxs-lookup"><span data-stu-id="9b986-128">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="9b986-129">Aby uzyskać więcej informacji, zobacz [powiązania dostarczone przez system](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="9b986-129">For more information, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

- <span data-ttu-id="9b986-130">Kontrakty: kontrakt zawiera informacje o funkcjach, które punkt końcowy uwidoczni dla klienta.</span><span class="sxs-lookup"><span data-stu-id="9b986-130">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="9b986-131">Kontrakt określa:</span><span class="sxs-lookup"><span data-stu-id="9b986-131">A contract specifies:</span></span>

  - <span data-ttu-id="9b986-132">Jakie operacje mogą być wywoływane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="9b986-132">What operations can be called by a client.</span></span>

  - <span data-ttu-id="9b986-133">Formularz wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9b986-133">The form of the message.</span></span>

  - <span data-ttu-id="9b986-134">Typ parametrów wejściowych lub danych wymaganych do wywołania operacji.</span><span class="sxs-lookup"><span data-stu-id="9b986-134">The type of input parameters or data required to call the operation.</span></span>

  - <span data-ttu-id="9b986-135">Jakiego typu komunikaty o przetwarzaniu lub odpowiedzi mogą oczekiwać klient.</span><span class="sxs-lookup"><span data-stu-id="9b986-135">What type of processing or response message the client can expect.</span></span>

  <span data-ttu-id="9b986-136">Aby uzyskać więcej informacji na temat definiowania kontraktu, zobacz [Projektowanie kontraktów usług](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="9b986-136">For more information about defining a contract, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>

- <span data-ttu-id="9b986-137">Zachowania: można użyć zachowań punktów końcowych, aby dostosować lokalne zachowanie punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="9b986-137">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="9b986-138">Zachowania punktów końcowych osiągają ten udział w procesie tworzenia środowiska uruchomieniowego WCF.</span><span class="sxs-lookup"><span data-stu-id="9b986-138">Endpoint behaviors achieve this by participating in the process of building a WCF runtime.</span></span> <span data-ttu-id="9b986-139">Przykładem zachowania punktu końcowego jest <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> Właściwość, która umożliwia określenie innego adresu nasłuchiwania niż adres SOAP lub Web Services Description Language (WSDL).</span><span class="sxs-lookup"><span data-stu-id="9b986-139">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> <span data-ttu-id="9b986-140">Aby uzyskać więcej informacji, zobacz [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="9b986-140">For more information, see [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).</span></span>

## <a name="defining-endpoints"></a><span data-ttu-id="9b986-141">Definiowanie punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="9b986-141">Defining Endpoints</span></span>

<span data-ttu-id="9b986-142">Punkt końcowy usługi można określić za pomocą kodu lub deklaratywnie za pośrednictwem konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9b986-142">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="9b986-143">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie punktu końcowego usługi w konfiguracji](how-to-create-a-service-endpoint-in-configuration.md) i [instrukcje: Tworzenie punktu końcowego usługi w kodzie](how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="9b986-143">For more information, see [How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="9b986-144">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9b986-144">In This Section</span></span>

<span data-ttu-id="9b986-145">W tej sekcji wyjaśniono cel powiązań, punktów końcowych i adresów; pokazuje, jak skonfigurować powiązanie i punkt końcowy; i pokazuje, jak używać `ClientVia` zachowań i `ListenUri` właściwości.</span><span class="sxs-lookup"><span data-stu-id="9b986-145">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>

<span data-ttu-id="9b986-146">[Adres](endpoint-addresses.md)</span><span class="sxs-lookup"><span data-stu-id="9b986-146">[Addresses](endpoint-addresses.md)</span></span>\
<span data-ttu-id="9b986-147">Opisuje, w jaki sposób punkty końcowe są rozkierowane na platformie WCF.</span><span class="sxs-lookup"><span data-stu-id="9b986-147">Describes how endpoints are addressed in WCF.</span></span>

<span data-ttu-id="9b986-148">[Powiązań](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="9b986-148">[Bindings](bindings.md)</span></span>\
<span data-ttu-id="9b986-149">Opisuje, w jaki sposób powiązania są używane do określania informacji o transportach, kodowaniu i protokole wymaganych przez klientów i usługi do komunikowania się ze sobą.</span><span class="sxs-lookup"><span data-stu-id="9b986-149">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>

<span data-ttu-id="9b986-150">[Kontraktacj](contracts.md)</span><span class="sxs-lookup"><span data-stu-id="9b986-150">[Contracts](contracts.md)</span></span>\
<span data-ttu-id="9b986-151">Opisuje, jak kontrakty definiują metody usługi.</span><span class="sxs-lookup"><span data-stu-id="9b986-151">Describes how contracts define the methods of a service.</span></span>

<span data-ttu-id="9b986-152">[Instrukcje: Tworzenie punktu końcowego usługi w konfiguracji](how-to-create-a-service-endpoint-in-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="9b986-152">[How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md)</span></span>\
<span data-ttu-id="9b986-153">Opisuje sposób tworzenia punktu końcowego usługi w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9b986-153">Describes how to create a service endpoint in configuration.</span></span>

<span data-ttu-id="9b986-154">[Instrukcje: Tworzenie punktu końcowego usługi w kodzie](how-to-create-a-service-endpoint-in-code.md)</span><span class="sxs-lookup"><span data-stu-id="9b986-154">[How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md)</span></span>\
<span data-ttu-id="9b986-155">Opisuje sposób tworzenia punktu końcowego usługi w kodzie.</span><span class="sxs-lookup"><span data-stu-id="9b986-155">Describes how to create a service endpoint in code.</span></span>

<span data-ttu-id="9b986-156">[Instrukcje: użycie Svcutil.exe do zweryfikowania skompilowanego kodu usługi](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span><span class="sxs-lookup"><span data-stu-id="9b986-156">[How to: Use Svcutil.exe to Validate Compiled Service Code](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span></span>\
<span data-ttu-id="9b986-157">Opisuje, jak wykrywać błędy w implementacjach i konfiguracjach usług bez obsługi usługi przy użyciu [Narzędzia do przesyłania metadanych modelu ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9b986-157">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9b986-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b986-158">See also</span></span>

- [<span data-ttu-id="9b986-159">Konfigurowanie usług</span><span class="sxs-lookup"><span data-stu-id="9b986-159">Configuring Services</span></span>](../configuring-services.md)
- [<span data-ttu-id="9b986-160">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="9b986-160">Extending Bindings</span></span>](../extending/extending-bindings.md)
