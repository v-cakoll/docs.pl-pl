---
title: Konfigurowanie usług WCF
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 4fcf01c9f65f2b1bd11462a6f7d61b3551f37b86
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320653"
---
# <a name="configuring-wcf-services"></a><span data-ttu-id="6fe0a-102">Konfigurowanie usług WCF</span><span class="sxs-lookup"><span data-stu-id="6fe0a-102">Configuring WCF services</span></span>

<span data-ttu-id="6fe0a-103">Po zaprojektowaniu i wdrożeniu kontraktu usługi możesz przystąpić do konfigurowania usługi.</span><span class="sxs-lookup"><span data-stu-id="6fe0a-103">Once you have designed and implemented your service contract, you are ready to configure your service.</span></span> <span data-ttu-id="6fe0a-104">Jest to miejsce, w którym można definiować i dostosowywać sposób, w jaki usługa jest narażona na komputery klienckie, w tym określenie adresu, pod którym można je znaleźć, używanego do wysyłania i odbierania komunikatów oraz typu bezpieczeństwa, którego wymaga.</span><span class="sxs-lookup"><span data-stu-id="6fe0a-104">This is where you define and customize how your service is exposed to clients, including specifying the address where it can be found, the transport and message encoding it uses to send and receive messages, and the type of security it requires.</span></span>  
  
 <span data-ttu-id="6fe0a-105">Konfiguracja użyta w tym miejscu obejmuje wszystkie metody, w sposób niezależny w kodzie lub przy użyciu pliku konfiguracji, w którym można definiować i dostosowywać różne aspekty usługi, takie jak określanie adresów punktów końcowych, używanych transportów i ich schematów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6fe0a-105">Configuration as used here includes all the ways, imperatively in code or by using a configuration file, in which you can define and customize the various aspects of a service, such as specifying its endpoint addresses, the transports used, and its security schemes.</span></span> <span data-ttu-id="6fe0a-106">W tym przypadku Zapisywanie konfiguracji jest główną częścią programowania aplikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="6fe0a-106">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6fe0a-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6fe0a-107">In This Section</span></span>  
 [<span data-ttu-id="6fe0a-108">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="6fe0a-108">Simplified Configuration</span></span>](simplified-configuration.md)  
 <span data-ttu-id="6fe0a-109">Począwszy od [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF jest dostarczany z nowym domyślnym modelem konfiguracji, który upraszcza wymagania dotyczące konfiguracji programu WCF.</span><span class="sxs-lookup"><span data-stu-id="6fe0a-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="6fe0a-110">Jeśli nie podasz żadnej konfiguracji WCF dla określonej usługi, środowisko uruchomieniowe automatycznie skonfiguruje usługę przy użyciu domyślnych punktów końcowych, powiązań i zachowań.</span><span class="sxs-lookup"><span data-stu-id="6fe0a-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with default endpoints, bindings, and behaviors.</span></span>  
  
 [<span data-ttu-id="6fe0a-111">Konfigurowanie usług za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6fe0a-111">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
 <span data-ttu-id="6fe0a-112">Usługa Windows Communication Foundation (WCF) można skonfigurować przy użyciu technologii konfiguracji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6fe0a-112">A Windows Communication Foundation (WCF) service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="6fe0a-113">Najczęściej elementy XML są dodawane do pliku Web. config dla witryny Internet Information Services (IIS), która hostuje usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="6fe0a-113">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="6fe0a-114">Elementy umożliwiają zmianę szczegółów, takich jak adresy punktów końcowych (rzeczywiste adresy używane do komunikowania się z usługą) na poszczególnych komputerach.</span><span class="sxs-lookup"><span data-stu-id="6fe0a-114">The elements allow you to change details, such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span>  
  
 [<span data-ttu-id="6fe0a-115">Powiązania</span><span class="sxs-lookup"><span data-stu-id="6fe0a-115">Bindings</span></span>](bindings.md)  
 <span data-ttu-id="6fe0a-116">Ponadto program WCF zawiera kilka typowych konfiguracji dostarczonych przez system w formie powiązań, które umożliwiają szybkie wybieranie najbardziej podstawowych funkcji komunikacji klienta i usługi, takich jak transporty, zabezpieczenia i używane kodowanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6fe0a-116">In addition, WCF includes several system-provided common configurations in the form of bindings that allow you to quickly select the most basic features for how a client and service communicate, such as the transports, security, and message encodings used.</span></span>  
  
 [<span data-ttu-id="6fe0a-117">Punkty końcowe</span><span class="sxs-lookup"><span data-stu-id="6fe0a-117">Endpoints</span></span>](endpoints.md)  
 <span data-ttu-id="6fe0a-118">Cała komunikacja z usługą WCF odbywa się za pomocą *punktów końcowych* usługi.</span><span class="sxs-lookup"><span data-stu-id="6fe0a-118">All communication with a WCF service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="6fe0a-119">Punkty końcowe zawierają kontrakt, informacje o konfiguracji określone w powiązaniach oraz adresy wskazujące, gdzie znaleźć usługę lub gdzie mają zostać uzyskane informacje o usłudze.</span><span class="sxs-lookup"><span data-stu-id="6fe0a-119">Endpoints contain the contract, the configuration information that is specified in the bindings, and the addresses that indicate where to find the service or where to obtain information about the service.</span></span>  
  
 [<span data-ttu-id="6fe0a-120">Zabezpieczanie usług</span><span class="sxs-lookup"><span data-stu-id="6fe0a-120">Securing Services</span></span>](securing-services.md)  
 <span data-ttu-id="6fe0a-121">Korzystając z programu WCF i istniejących mechanizmów zabezpieczeń, można zaimplementować poufność, integralność, uwierzytelnianie i autoryzację w dowolnej usłudze.</span><span class="sxs-lookup"><span data-stu-id="6fe0a-121">Using WCF and existing security mechanisms, you can implement confidentiality, integrity, authentication, and authorization into any service.</span></span> <span data-ttu-id="6fe0a-122">Możesz także przeprowadzić inspekcję pod kątem sukcesów i niepowodzeń zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6fe0a-122">You can also audit for security successes and failures.</span></span>  
  
 [<span data-ttu-id="6fe0a-123">Tworzenie usług międzyoperacyjnych 1.1 profilu podstawowego WS-I</span><span class="sxs-lookup"><span data-stu-id="6fe0a-123">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>](./creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 <span data-ttu-id="6fe0a-124">Wymagania dotyczące wdrażania usługi, która jest współdziałania z usługami i klientami na dowolnej innej platformie lub systemie operacyjnym, opisano w specyfikacji WS-I Basic Profile 1,1.</span><span class="sxs-lookup"><span data-stu-id="6fe0a-124">The requirements for deploying a service that is interoperable with services and clients on any other platform or operating system are outlined in the WS-I Basic Profile 1.1 specification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6fe0a-125">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="6fe0a-125">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="6fe0a-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="6fe0a-126">Related Sections</span></span>  
 [<span data-ttu-id="6fe0a-127">Podstawowy cykl życia programowania</span><span class="sxs-lookup"><span data-stu-id="6fe0a-127">Basic Programming Lifecycle</span></span>](basic-programming-lifecycle.md)  
  
 [<span data-ttu-id="6fe0a-128">Projektowanie i implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="6fe0a-128">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)  
  
 [<span data-ttu-id="6fe0a-129">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="6fe0a-129">Hosting Services</span></span>](hosting-services.md)  
  
 [<span data-ttu-id="6fe0a-130">Kompilowanie klientów</span><span class="sxs-lookup"><span data-stu-id="6fe0a-130">Building Clients</span></span>](building-clients.md)  
  
 [<span data-ttu-id="6fe0a-131">Wprowadzenie do rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="6fe0a-131">Introduction to Extensibility</span></span>](introduction-to-extensibility.md)  
  
 [<span data-ttu-id="6fe0a-132">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="6fe0a-132">Administration and Diagnostics</span></span>](./diagnostics/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="6fe0a-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6fe0a-133">See also</span></span>

- [<span data-ttu-id="6fe0a-134">Podstawy programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="6fe0a-134">Basic WCF Programming</span></span>](basic-wcf-programming.md)
- [<span data-ttu-id="6fe0a-135">Omówienie pojęć</span><span class="sxs-lookup"><span data-stu-id="6fe0a-135">Conceptual Overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="6fe0a-136">Szczegóły funkcji WCF</span><span class="sxs-lookup"><span data-stu-id="6fe0a-136">WCF Feature Details</span></span>](./feature-details/index.md)
