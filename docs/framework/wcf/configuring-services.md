---
title: Konfigurowanie usług WCF
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 81727adbf985986a71cc9f9e2d42a1de0cb1fd76
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59156510"
---
# <a name="configuring-wcf-services"></a><span data-ttu-id="8e834-102">Konfigurowanie usług WCF</span><span class="sxs-lookup"><span data-stu-id="8e834-102">Configuring WCF services</span></span>

<span data-ttu-id="8e834-103">Po zaprojektowane i zaimplementowane umowy serwisowej można przystąpić do konfigurowania usługi.</span><span class="sxs-lookup"><span data-stu-id="8e834-103">Once you have designed and implemented your service contract, you are ready to configure your service.</span></span> <span data-ttu-id="8e834-104">Jest to, gdzie zdefiniujesz i dostosujesz, jak usługa jest narażony na klientów, łącznie z określeniem adresu, gdzie można je znaleźć, transport i kodowanie komunikatu, używanych do wysyłania i odbierania komunikatów i typ zabezpieczeń wymagane przez nią.</span><span class="sxs-lookup"><span data-stu-id="8e834-104">This is where you define and customize how your service is exposed to clients, including specifying the address where it can be found, the transport and message encoding it uses to send and receive messages, and the type of security it requires.</span></span>  
  
 <span data-ttu-id="8e834-105">Konfiguracja tutaj obejmuje wszystkie sposoby obowiązkowo w kodzie lub za pomocą pliku konfiguracji, można zdefiniować i dostosować różnych aspektów usługi, takich jak określanie jego adresy punktów końcowych, transportów używane i jej programów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="8e834-105">Configuration as used here includes all the ways, imperatively in code or by using a configuration file, in which you can define and customize the various aspects of a service, such as specifying its endpoint addresses, the transports used, and its security schemes.</span></span> <span data-ttu-id="8e834-106">W praktyce Zapisywanie konfiguracji jest poważnym należą do programowania aplikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="8e834-106">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8e834-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="8e834-107">In This Section</span></span>  
 [<span data-ttu-id="8e834-108">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="8e834-108">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 <span data-ttu-id="8e834-109">Począwszy od [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF, który jest dostarczany z nowy model konfiguracji domyślnej, który upraszcza wymagania dotyczące konfiguracji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="8e834-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="8e834-110">Jeśli nie podano żadnej konfiguracji programu WCF dla określonej usługi, środowisko uruchomieniowe automatycznie konfiguruje usługi przy użyciu domyślnych punktów końcowych, powiązania i zachowania.</span><span class="sxs-lookup"><span data-stu-id="8e834-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with default endpoints, bindings, and behaviors.</span></span>  
  
 [<span data-ttu-id="8e834-111">Konfigurowanie usług za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8e834-111">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 <span data-ttu-id="8e834-112">Usługa Windows Communication Foundation (WCF) jest, można skonfigurować przy użyciu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] technologia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8e834-112">A Windows Communication Foundation (WCF) service is configurable using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration technology.</span></span> <span data-ttu-id="8e834-113">Najczęściej XML elementy są dodawane do pliku Web.config dla witryny usług Internet Information Services (IIS), który hostuje usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="8e834-113">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="8e834-114">Elementy umożliwiają zmianę szczegóły, takie jak adresy punktów końcowych (rzeczywista adresy, używane do komunikacji z usługą) na podstawie maszyny według komputera.</span><span class="sxs-lookup"><span data-stu-id="8e834-114">The elements allow you to change details, such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span>  
  
 [<span data-ttu-id="8e834-115">Powiązania</span><span class="sxs-lookup"><span data-stu-id="8e834-115">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)  
 <span data-ttu-id="8e834-116">Ponadto WCF zawiera kilka typowych konfiguracji dostarczane przez system w postaci powiązania, które umożliwiają szybko wybrać najbardziej podstawowe funkcje dla sposób komunikacji klientów i usług, takich jak transportu, zabezpieczeń i używać kodowania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="8e834-116">In addition, WCF includes several system-provided common configurations in the form of bindings that allow you to quickly select the most basic features for how a client and service communicate, such as the transports, security, and message encodings used.</span></span>  
  
 [<span data-ttu-id="8e834-117">Punkty końcowe</span><span class="sxs-lookup"><span data-stu-id="8e834-117">Endpoints</span></span>](../../../docs/framework/wcf/endpoints.md)  
 <span data-ttu-id="8e834-118">Cała komunikacja z usługą WCF odbywa się przez *punktów końcowych* usługi.</span><span class="sxs-lookup"><span data-stu-id="8e834-118">All communication with a WCF service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="8e834-119">Punkty końcowe zawierać umowy, informacje o konfiguracji, który jest określony w powiązaniach i adresy, które wskazują, gdzie można znaleźć usługi lub gdzie można uzyskać informacji na temat usługi.</span><span class="sxs-lookup"><span data-stu-id="8e834-119">Endpoints contain the contract, the configuration information that is specified in the bindings, and the addresses that indicate where to find the service or where to obtain information about the service.</span></span>  
  
 [<span data-ttu-id="8e834-120">Zabezpieczanie usług</span><span class="sxs-lookup"><span data-stu-id="8e834-120">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 <span data-ttu-id="8e834-121">Przy użyciu usługi WCF i istniejące mechanizmy zabezpieczeń, można zaimplementować poufność, integralność, uwierzytelniania i autoryzacji do każdej usługi.</span><span class="sxs-lookup"><span data-stu-id="8e834-121">Using WCF and existing security mechanisms, you can implement confidentiality, integrity, authentication, and authorization into any service.</span></span> <span data-ttu-id="8e834-122">Można również przeprowadzać inspekcję zabezpieczeń sukcesów i niepowodzeń.</span><span class="sxs-lookup"><span data-stu-id="8e834-122">You can also audit for security successes and failures.</span></span>  
  
 [<span data-ttu-id="8e834-123">Tworzenie usług międzyoperacyjnych 1.1 profilu podstawowego WS-I</span><span class="sxs-lookup"><span data-stu-id="8e834-123">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 <span data-ttu-id="8e834-124">Wymagania dotyczące wdrażania usługi, która współdziała z usług i klientów na dowolnej platformie lub systemu operacyjnego zostały opisane w WS-I Basic Profile 1.1 specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="8e834-124">The requirements for deploying a service that is interoperable with services and clients on any other platform or operating system are outlined in the WS-I Basic Profile 1.1 specification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8e834-125">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="8e834-125">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="8e834-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="8e834-126">Related Sections</span></span>  
 [<span data-ttu-id="8e834-127">Podstawowy cykl życia programowania</span><span class="sxs-lookup"><span data-stu-id="8e834-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [<span data-ttu-id="8e834-128">Projektowanie i implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="8e834-128">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [<span data-ttu-id="8e834-129">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="8e834-129">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)  
  
 [<span data-ttu-id="8e834-130">Kompilowanie klientów</span><span class="sxs-lookup"><span data-stu-id="8e834-130">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
  
 [<span data-ttu-id="8e834-131">Wprowadzenie do rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="8e834-131">Introduction to Extensibility</span></span>](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [<span data-ttu-id="8e834-132">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="8e834-132">Administration and Diagnostics</span></span>](../../../docs/framework/wcf/diagnostics/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="8e834-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e834-133">See also</span></span>

- [<span data-ttu-id="8e834-134">Podstawy programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="8e834-134">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)
- [<span data-ttu-id="8e834-135">Omówienie pojęć</span><span class="sxs-lookup"><span data-stu-id="8e834-135">Conceptual Overview</span></span>](../../../docs/framework/wcf/conceptual-overview.md)
- [<span data-ttu-id="8e834-136">Szczegóły funkcji WCF</span><span class="sxs-lookup"><span data-stu-id="8e834-136">WCF Feature Details</span></span>](../../../docs/framework/wcf/feature-details/index.md)
