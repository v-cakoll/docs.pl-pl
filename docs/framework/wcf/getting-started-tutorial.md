---
title: 'Samouczek: Rozpoczynanie pracy z aplikacjami Windows Communication Foundation'
description: W tych samouczkach przedstawiono wprowadzenie do tworzenia aplikacji WCF.
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: d4613edefeb8db2c0d1e11e925f8ac41329efb0d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929548"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a><span data-ttu-id="e3aa1-103">Samouczek: Rozpoczynanie pracy z aplikacjami Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="e3aa1-103">Tutorial: Get started with Windows Communication Foundation applications</span></span>
<span data-ttu-id="e3aa1-104">Poniższą sekwencję samouczki zawierają wprowadzenie do Windows Communication Foundation (WCF) środowisko programowania.</span><span class="sxs-lookup"><span data-stu-id="e3aa1-104">The following series of tutorials introduce you to the Windows Communication Foundation (WCF) programming experience.</span></span> <span data-ttu-id="e3aa1-105">Pracy przy użyciu tych samouczków, w kolejności zapewni wprowadzające zrozumienia czynności wymagane do tworzenia aplikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="e3aa1-105">Working through these tutorials in order will give you an introductory understanding of the steps required to create WCF applications.</span></span> <span data-ttu-id="e3aa1-106">Po zakończeniu będziesz mieć uruchomioną usługę WCF i klienta WCF, który wywołuje usługę.</span><span class="sxs-lookup"><span data-stu-id="e3aa1-106">After you finish, you'll have a running WCF service and a WCF client that calls the service.</span></span> 

<span data-ttu-id="e3aa1-107">W samouczku przyjęto założenie, że używasz programu Visual Studio jako środowisko projektowe.</span><span class="sxs-lookup"><span data-stu-id="e3aa1-107">The tutorial assumes you're using Visual Studio as the development environment.</span></span> <span data-ttu-id="e3aa1-108">Jeśli używasz innego środowiska deweloperskiego, zignorować instrukcje dotyczące programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e3aa1-108">If you're using another development environment, ignore the Visual Studio-specific instructions.</span></span> 

<span data-ttu-id="e3aa1-109">Dla przykładowych aplikacji WCF, które można pobierać i uruchamiać, zobacz [przykładów Windows Communication Foundation](samples/index.md).</span><span class="sxs-lookup"><span data-stu-id="e3aa1-109">For sample WCF applications that you can download and run, see [Windows Communication Foundation samples](samples/index.md).</span></span> <span data-ttu-id="e3aa1-110">Wprowadzenie do przykładów, zobacz [przykładowe wprowadzające](samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e3aa1-110">For an introduction to the samples, see [Getting started sample](samples/getting-started-sample.md).</span></span>

<span data-ttu-id="e3aa1-111">Aby uzyskać bardziej szczegółowe informacje o sposobie tworzenia usług i klientów, zobacz [programowanie WCF podstawowe](basic-wcf-programming.md).</span><span class="sxs-lookup"><span data-stu-id="e3aa1-111">For more in-depth information about creating services and clients, see [Basic WCF programming](basic-wcf-programming.md).</span></span>

## <a name="wcf-tutorials"></a><span data-ttu-id="e3aa1-112">Samouczki programu WCF</span><span class="sxs-lookup"><span data-stu-id="e3aa1-112">WCF tutorials</span></span>

<span data-ttu-id="e3aa1-113">Pierwszych trzech samouczków opisano, jak definiowanie kontraktu usługi WCF, sposobie jego implementowania i sposobu hostowania go.</span><span class="sxs-lookup"><span data-stu-id="e3aa1-113">The first three tutorials describe how to define a WCF service contract, how to implement it, and how to host it.</span></span> <span data-ttu-id="e3aa1-114">Usługa tworzona jest samodzielnie hostowany w aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="e3aa1-114">The service that you create is self-hosted within a console application.</span></span> <span data-ttu-id="e3aa1-115">You can also host services under Microsoft Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="e3aa1-115">You can also host services under Microsoft Internet Information Services (IIS).</span></span> <span data-ttu-id="e3aa1-116">Aby uzyskać więcej informacji, zobacz [jak: Hostowanie usługi WCF w programie IIS](feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="e3aa1-116">For more information, see [How to: Host a WCF Service in IIS](feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span> <span data-ttu-id="e3aa1-117">Mimo że kod jest używane do konfigurowania usługi w tym samouczku, można również [skonfigurować usługi w pliku konfiguracji](configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="e3aa1-117">Although you use code to configure the service in the tutorial, you can also [configure services within a configuration file](configuring-services-using-configuration-files.md).</span></span> 

- [<span data-ttu-id="e3aa1-118">Samouczek: Definiowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="e3aa1-118">Tutorial: Define a service contract</span></span>](how-to-define-a-wcf-service-contract.md)

    <span data-ttu-id="e3aa1-119">Możesz utworzyć kontraktu usługi WCF z interfejsem użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e3aa1-119">You create a WCF contract with a user-defined interface.</span></span> <span data-ttu-id="e3aa1-120">Ten kontrakt definiuje funkcje, które uwidacznia usługa.</span><span class="sxs-lookup"><span data-stu-id="e3aa1-120">This contract defines the functionality that the service exposes.</span></span>

- [<span data-ttu-id="e3aa1-121">Samouczek: Implementowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="e3aa1-121">Tutorial: Implement a service contract</span></span>](how-to-implement-a-wcf-contract.md)

    <span data-ttu-id="e3aa1-122">Po zdefiniowaniu kontrakt, należy zaimplementować go za pomocą klasy usługi.</span><span class="sxs-lookup"><span data-stu-id="e3aa1-122">After you define a contract, you must implement it with a service class.</span></span>

- [<span data-ttu-id="e3aa1-123">Samouczek: Hostowanie i uruchamianie podstawowej usługi</span><span class="sxs-lookup"><span data-stu-id="e3aa1-123">Tutorial: Host and run a basic service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)

    <span data-ttu-id="e3aa1-124">Skonfiguruj punkt końcowy usługi i Hostuj usługi w aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="e3aa1-124">Configure an endpoint for the service and host the service in a console application.</span></span> <span data-ttu-id="e3aa1-125">Dla usługi stanie się aktywna można ją skonfigurować, a następnie Hostuj go w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="e3aa1-125">For a service to become active, you must configure it and host it within a run-time environment.</span></span> <span data-ttu-id="e3aa1-126">To środowisko wykonawczej tworzy usługi i kontroluje jego kontekstu i okresu istnienia.</span><span class="sxs-lookup"><span data-stu-id="e3aa1-126">This run-time environment creates the service and controls its context and lifetime.</span></span>

<span data-ttu-id="e3aa1-127">W dwóch następnych samouczków opisano, jak tworzyć, konfigurować i przedstawia użycie aplikacji klienckiej, wywoływania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="e3aa1-127">The next two tutorials describe how to create, configure, and use a client application to call the operations the service exposes.</span></span> <span data-ttu-id="e3aa1-128">Usługi publikowania metadanych, który definiuje informacje, które aplikacja kliencka musi komunikować się z usługą.</span><span class="sxs-lookup"><span data-stu-id="e3aa1-128">Services publish metadata that define the information a client application needs to communicate with the service.</span></span> <span data-ttu-id="e3aa1-129">Visual Studio automatyzuje proces uzyskiwania dostępu do metadanych i używa ich do utworzenia aplikacji klienckiej dla usługi.</span><span class="sxs-lookup"><span data-stu-id="e3aa1-129">Visual Studio automates the process of accessing this metadata and uses it to construct the client application for the service.</span></span> <span data-ttu-id="e3aa1-130">Jeśli zdecydujesz się nie należy używać programu Visual Studio, możesz użyć [narzędzia narzędzie metadanych elementu ServiceModel (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="e3aa1-130">If you decide not to use Visual Studio, you can use the [ServiceModel Metadata Utility tool (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) instead.</span></span>

- [<span data-ttu-id="e3aa1-131">Samouczek: Tworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="e3aa1-131">Tutorial: Create a client</span></span>](how-to-create-a-wcf-client.md)

    <span data-ttu-id="e3aa1-132">Pobieranie metadanych tworzenia serwer proxy klienta WCF z usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="e3aa1-132">Retrieve metadata for creating a WCF client proxy from a WCF service.</span></span> <span data-ttu-id="e3aa1-133">Pobieranie metadanych przy użyciu programu Visual Studio, aby dodać odwołanie do usługi lub narzędzia narzędzie metadanych elementu ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="e3aa1-133">You retrieve metadata by using Visual Studio to add a service reference or you can use the ServiceModel Metadata Utility tool.</span></span> <span data-ttu-id="e3aa1-134">Należy określić punkt końcowy, który klient używa w celu uzyskania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="e3aa1-134">You specify the endpoint that the client uses to access the service.</span></span>

- [<span data-ttu-id="e3aa1-135">Samouczek: Używanie klienta</span><span class="sxs-lookup"><span data-stu-id="e3aa1-135">Tutorial: Use a client</span></span>](how-to-use-a-wcf-client.md)

    <span data-ttu-id="e3aa1-136">Serwer proxy klienta WCF umożliwia wywoływanie operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="e3aa1-136">Use the WCF client proxy to call the service operations.</span></span>

## <a name="reference"></a><span data-ttu-id="e3aa1-137">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="e3aa1-137">Reference</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a><span data-ttu-id="e3aa1-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3aa1-138">See also</span></span>

- [<span data-ttu-id="e3aa1-139">Omówienie pojęć</span><span class="sxs-lookup"><span data-stu-id="e3aa1-139">Conceptual overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="e3aa1-140">Przewodnik po dokumentacji</span><span class="sxs-lookup"><span data-stu-id="e3aa1-140">Guide to the documentation</span></span>](guide-to-the-documentation.md)
- [<span data-ttu-id="e3aa1-141">Co to jest Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="e3aa1-141">What is Windows Communication Foundation</span></span>](whats-wcf.md)
- [<span data-ttu-id="e3aa1-142">Szczegóły funkcji WCF</span><span class="sxs-lookup"><span data-stu-id="e3aa1-142">WCF feature details</span></span>](feature-details/index.md)
- [<span data-ttu-id="e3aa1-143">Podstawowy cykl życia programowania</span><span class="sxs-lookup"><span data-stu-id="e3aa1-143">Basic programming lifecycle</span></span>](basic-programming-lifecycle.md)
- [<span data-ttu-id="e3aa1-144">Kompilowanie klientów</span><span class="sxs-lookup"><span data-stu-id="e3aa1-144">Building clients</span></span>](building-clients.md)
- [<span data-ttu-id="e3aa1-145">Podstawy programowania programu WCF</span><span class="sxs-lookup"><span data-stu-id="e3aa1-145">Basic WCF programming</span></span>](basic-wcf-programming.md)
- [<span data-ttu-id="e3aa1-146">Instrukcje: Tworzenie kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="e3aa1-146">How to: Create a duplex contract</span></span>](feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="e3aa1-147">Instrukcje: Dostęp do usług za pomocą kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="e3aa1-147">How to: Access services with a duplex contract</span></span>](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="e3aa1-148">Narzędzie narzędzie metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="e3aa1-148">ServiceModel Metadata Utility tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="e3aa1-149">Instrukcje: Używanie Svcutil.exe do pobierania dokumentów metadanych</span><span class="sxs-lookup"><span data-stu-id="e3aa1-149">How to: Use Svcutil.exe to download metadata documents</span></span>](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [<span data-ttu-id="e3aa1-150">Instrukcje: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e3aa1-150">How to: Publish metadata for a service using a configuration file</span></span>](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="e3aa1-151">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="e3aa1-151">Using bindings to configure services and clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e3aa1-152">Wprowadzenie — przykład</span><span class="sxs-lookup"><span data-stu-id="e3aa1-152">Getting started sample</span></span>](samples/getting-started-sample.md)
- [<span data-ttu-id="e3aa1-153">Przykłady Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="e3aa1-153">Windows Communication Foundation samples</span></span>](samples/index.md)
- [<span data-ttu-id="e3aa1-154">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="e3aa1-154">Self-Host</span></span>](samples/self-host.md)
