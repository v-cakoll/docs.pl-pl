---
title: 'Samouczek: Wprowadzenie do aplikacji Windows Communication Foundation'
description: Te samouczki zawiera wprowadzenie do tworzenia aplikacji WCF.
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: df73f953372202796cebce9d3e3f28bd617c67ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184124"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a><span data-ttu-id="9ecd4-103">Samouczek: Wprowadzenie do aplikacji Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="9ecd4-103">Tutorial: Get started with Windows Communication Foundation applications</span></span>
<span data-ttu-id="9ecd4-104">Poniższa seria samouczków przedstawia środowisko programowania Programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9ecd4-104">The following series of tutorials introduce you to the Windows Communication Foundation (WCF) programming experience.</span></span> <span data-ttu-id="9ecd4-105">Praca za pomocą tych samouczków w kolejności daje wstępne zrozumienie kroków wymaganych do tworzenia aplikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="9ecd4-105">Working through these tutorials in order will give you an introductory understanding of the steps required to create WCF applications.</span></span> <span data-ttu-id="9ecd4-106">Po zakończeniu będziesz mieć uruchomionej usługi WCF i klienta WCF, który wywołuje usługę.</span><span class="sxs-lookup"><span data-stu-id="9ecd4-106">After you finish, you'll have a running WCF service and a WCF client that calls the service.</span></span>

<span data-ttu-id="9ecd4-107">W samouczku przyjęto założenie, że używasz programu Visual Studio jako środowiska programistycznego.</span><span class="sxs-lookup"><span data-stu-id="9ecd4-107">The tutorial assumes you're using Visual Studio as the development environment.</span></span> <span data-ttu-id="9ecd4-108">Jeśli używasz innego środowiska programistycznego, zignoruj instrukcje specyficzne dla programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9ecd4-108">If you're using another development environment, ignore the Visual Studio-specific instructions.</span></span>

<span data-ttu-id="9ecd4-109">Aby uzyskać przykładowe aplikacje WCF, które można pobrać i uruchomić, zobacz [przykłady Programu Windows Communication Foundation](samples/index.md).</span><span class="sxs-lookup"><span data-stu-id="9ecd4-109">For sample WCF applications that you can download and run, see [Windows Communication Foundation samples](samples/index.md).</span></span> <span data-ttu-id="9ecd4-110">Aby zapoznać się z wprowadzeniem do próbek, zobacz [Wprowadzenie próbki](samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="9ecd4-110">For an introduction to the samples, see [Getting started sample](samples/getting-started-sample.md).</span></span>

<span data-ttu-id="9ecd4-111">Aby uzyskać bardziej szczegółowe informacje na temat tworzenia usług i klientów, zobacz [Podstawowe programowanie WCF](basic-wcf-programming.md).</span><span class="sxs-lookup"><span data-stu-id="9ecd4-111">For more in-depth information about creating services and clients, see [Basic WCF programming](basic-wcf-programming.md).</span></span>

## <a name="wcf-tutorials"></a><span data-ttu-id="9ecd4-112">Samouczki WCF</span><span class="sxs-lookup"><span data-stu-id="9ecd4-112">WCF tutorials</span></span>

<span data-ttu-id="9ecd4-113">Pierwsze trzy samouczki opisują sposób definiowania umowy serwisowej WCF, jak ją zaimplementować i jak go hostować.</span><span class="sxs-lookup"><span data-stu-id="9ecd4-113">The first three tutorials describe how to define a WCF service contract, how to implement it, and how to host it.</span></span> <span data-ttu-id="9ecd4-114">Utworzona usługa jest hostowana samodzielnie w aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="9ecd4-114">The service that you create is self-hosted within a console application.</span></span> <span data-ttu-id="9ecd4-115">Usługi można również hostować w ramach internetowych usług informacyjnych firmy Microsoft (IIS).</span><span class="sxs-lookup"><span data-stu-id="9ecd4-115">You can also host services under Microsoft Internet Information Services (IIS).</span></span> <span data-ttu-id="9ecd4-116">Aby uzyskać więcej informacji, zobacz [Jak: Hostować usługę WCF w usługach IIS](feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="9ecd4-116">For more information, see [How to: Host a WCF Service in IIS](feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span> <span data-ttu-id="9ecd4-117">Chociaż kod służy do konfigurowania usługi w samouczku, można również [skonfigurować usługi w pliku konfiguracyjnym](configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="9ecd4-117">Although you use code to configure the service in the tutorial, you can also [configure services within a configuration file](configuring-services-using-configuration-files.md).</span></span>

- [<span data-ttu-id="9ecd4-118">Samouczek: Definiowanie umowy serwisowej</span><span class="sxs-lookup"><span data-stu-id="9ecd4-118">Tutorial: Define a service contract</span></span>](how-to-define-a-wcf-service-contract.md)

    <span data-ttu-id="9ecd4-119">Tworzenie umowy WCF z interfejsem zdefiniowanym przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9ecd4-119">You create a WCF contract with a user-defined interface.</span></span> <span data-ttu-id="9ecd4-120">Ten kontrakt definiuje funkcje, które usługa udostępnia.</span><span class="sxs-lookup"><span data-stu-id="9ecd4-120">This contract defines the functionality that the service exposes.</span></span>

- [<span data-ttu-id="9ecd4-121">Samouczek: Zaimplementowanie umowy serwisowej</span><span class="sxs-lookup"><span data-stu-id="9ecd4-121">Tutorial: Implement a service contract</span></span>](how-to-implement-a-wcf-contract.md)

    <span data-ttu-id="9ecd4-122">Po zdefiniowaniu umowy należy zaimplementować ją z klasą usługi.</span><span class="sxs-lookup"><span data-stu-id="9ecd4-122">After you define a contract, you must implement it with a service class.</span></span>

- [<span data-ttu-id="9ecd4-123">Samouczek: Host i uruchom podstawową usługę</span><span class="sxs-lookup"><span data-stu-id="9ecd4-123">Tutorial: Host and run a basic service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)

    <span data-ttu-id="9ecd4-124">Skonfiguruj punkt końcowy dla usługi i hostuj usługę w aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="9ecd4-124">Configure an endpoint for the service and host the service in a console application.</span></span> <span data-ttu-id="9ecd4-125">Aby usługa stała się aktywna, należy ją skonfigurować i hostować w środowisku wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9ecd4-125">For a service to become active, you must configure it and host it within a run-time environment.</span></span> <span data-ttu-id="9ecd4-126">To środowisko wykonywania tworzy usługę i kontroluje jej kontekst i okres istnienia.</span><span class="sxs-lookup"><span data-stu-id="9ecd4-126">This run-time environment creates the service and controls its context and lifetime.</span></span>

<span data-ttu-id="9ecd4-127">Następne dwa samouczki opisują sposób tworzenia, konfigurowania i używania aplikacji klienckiej do wywoływania operacji udostępnianych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="9ecd4-127">The next two tutorials describe how to create, configure, and use a client application to call the operations the service exposes.</span></span> <span data-ttu-id="9ecd4-128">Usługi publikują metadane definiujące informacje, które aplikacja kliencka musi komunikować się z usługą.</span><span class="sxs-lookup"><span data-stu-id="9ecd4-128">Services publish metadata that define the information a client application needs to communicate with the service.</span></span> <span data-ttu-id="9ecd4-129">Visual Studio automatyzuje proces uzyskiwania dostępu do tych metadanych i używa go do konstruowania aplikacji klienckiej dla usługi.</span><span class="sxs-lookup"><span data-stu-id="9ecd4-129">Visual Studio automates the process of accessing this metadata and uses it to construct the client application for the service.</span></span> <span data-ttu-id="9ecd4-130">Jeśli zdecydujesz się nie używać programu Visual Studio, możesz użyć [narzędzia Narzędzia metadanych ServiceModel (*Svcutil.exe).*](servicemodel-metadata-utility-tool-svcutil-exe.md)</span><span class="sxs-lookup"><span data-stu-id="9ecd4-130">If you decide not to use Visual Studio, you can use the [ServiceModel Metadata Utility tool (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) instead.</span></span>

- [<span data-ttu-id="9ecd4-131">Samouczek: Tworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="9ecd4-131">Tutorial: Create a client</span></span>](how-to-create-a-wcf-client.md)

    <span data-ttu-id="9ecd4-132">Pobieranie metadanych do tworzenia serwera proxy klienta WCF z usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="9ecd4-132">Retrieve metadata for creating a WCF client proxy from a WCF service.</span></span> <span data-ttu-id="9ecd4-133">Pobierasz metadane za pomocą programu Visual Studio, aby dodać odwołanie do usługi lub można użyć narzędzia Narzędzia Metadata ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="9ecd4-133">You retrieve metadata by using Visual Studio to add a service reference or you can use the ServiceModel Metadata Utility tool.</span></span> <span data-ttu-id="9ecd4-134">Należy określić punkt końcowy, który klient używa do uzyskania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="9ecd4-134">You specify the endpoint that the client uses to access the service.</span></span>

- [<span data-ttu-id="9ecd4-135">Samouczek: Korzystanie z klienta</span><span class="sxs-lookup"><span data-stu-id="9ecd4-135">Tutorial: Use a client</span></span>](how-to-use-a-wcf-client.md)

    <span data-ttu-id="9ecd4-136">Użyj serwera proxy klienta WCF do wywołania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="9ecd4-136">Use the WCF client proxy to call the service operations.</span></span>

## <a name="reference"></a><span data-ttu-id="9ecd4-137">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="9ecd4-137">Reference</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a><span data-ttu-id="9ecd4-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ecd4-138">See also</span></span>

- [<span data-ttu-id="9ecd4-139">Omówienie pojęć</span><span class="sxs-lookup"><span data-stu-id="9ecd4-139">Conceptual overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="9ecd4-140">Przewodnik po dokumentacji</span><span class="sxs-lookup"><span data-stu-id="9ecd4-140">Guide to the documentation</span></span>](guide-to-the-documentation.md)
- [<span data-ttu-id="9ecd4-141">Co to jest Fundacja Komunikacji systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9ecd4-141">What is Windows Communication Foundation</span></span>](whats-wcf.md)
- [<span data-ttu-id="9ecd4-142">Szczegóły funkcji WCF</span><span class="sxs-lookup"><span data-stu-id="9ecd4-142">WCF feature details</span></span>](feature-details/index.md)
- [<span data-ttu-id="9ecd4-143">Podstawowy cykl programowania</span><span class="sxs-lookup"><span data-stu-id="9ecd4-143">Basic programming lifecycle</span></span>](basic-programming-lifecycle.md)
- [<span data-ttu-id="9ecd4-144">Budowanie klientów</span><span class="sxs-lookup"><span data-stu-id="9ecd4-144">Building clients</span></span>](building-clients.md)
- [<span data-ttu-id="9ecd4-145">Podstawowe programowanie WCF</span><span class="sxs-lookup"><span data-stu-id="9ecd4-145">Basic WCF programming</span></span>](basic-wcf-programming.md)
- [<span data-ttu-id="9ecd4-146">Jak: Tworzenie kontraktu dupleksowego</span><span class="sxs-lookup"><span data-stu-id="9ecd4-146">How to: Create a duplex contract</span></span>](feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="9ecd4-147">Jak: Dostęp do usług z umową dupleksową</span><span class="sxs-lookup"><span data-stu-id="9ecd4-147">How to: Access services with a duplex contract</span></span>](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="9ecd4-148">Narzędzie narzędzia Metadata Usługi ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="9ecd4-148">ServiceModel Metadata Utility tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="9ecd4-149">Jak: Pobieranie dokumentów metadanych za pomocą programu Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="9ecd4-149">How to: Use Svcutil.exe to download metadata documents</span></span>](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [<span data-ttu-id="9ecd4-150">Jak: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracyjnego</span><span class="sxs-lookup"><span data-stu-id="9ecd4-150">How to: Publish metadata for a service using a configuration file</span></span>](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="9ecd4-151">Używanie powiązań do konfigurowania usług i klientów</span><span class="sxs-lookup"><span data-stu-id="9ecd4-151">Using bindings to configure services and clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9ecd4-152">Wprowadzenie próbki</span><span class="sxs-lookup"><span data-stu-id="9ecd4-152">Getting started sample</span></span>](samples/getting-started-sample.md)
- [<span data-ttu-id="9ecd4-153">Przykłady programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="9ecd4-153">Windows Communication Foundation samples</span></span>](samples/index.md)
- [<span data-ttu-id="9ecd4-154">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="9ecd4-154">Self-Host</span></span>](samples/self-host.md)
