---
title: "Konfigurowanie usług"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0783107d22f2d64dd8ba7936ce7d2a283f6d8317
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="configuring-services"></a><span data-ttu-id="2f497-102">Konfigurowanie usług</span><span class="sxs-lookup"><span data-stu-id="2f497-102">Configuring Services</span></span>
<span data-ttu-id="2f497-103">Po zaprojektowane i zaimplementowane umowy serwisowej, możesz przystąpić do konfigurowania usługi.</span><span class="sxs-lookup"><span data-stu-id="2f497-103">Once you have designed and implemented your service contract, you are ready to configure your service.</span></span> <span data-ttu-id="2f497-104">To pozwala definiować i dostosowywać, jak usługa jest widoczne dla klientów, łącznie z określeniem adres, gdzie można je znaleźć, transport i kodowanie wiadomości używanych do wysyłania i odbierania wiadomości oraz typ zabezpieczeń, które wymaga.</span><span class="sxs-lookup"><span data-stu-id="2f497-104">This is where you define and customize how your service is exposed to clients, including specifying the address where it can be found, the transport and message encoding it uses to send and receive messages, and the type of security it requires.</span></span>  
  
 <span data-ttu-id="2f497-105">Konfiguracja tutaj obejmuje wszystkich metod imperatively w kodzie, lub za pomocą pliku konfiguracji, w którym można zdefiniować i dostosować różne aspekty usług, takich jak określanie jego adresy punktów końcowych, transportów używane i jego systemów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="2f497-105">Configuration as used here includes all the ways, imperatively in code or by using a configuration file, in which you can define and customize the various aspects of a service, such as specifying its endpoint addresses, the transports used, and its security schemes.</span></span> <span data-ttu-id="2f497-106">W praktyce, zapisywanie konfiguracji to główne programowania [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2f497-106">In practice, writing configuration is a major part of programming [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2f497-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2f497-107">In This Section</span></span>  
 [<span data-ttu-id="2f497-108">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="2f497-108">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 <span data-ttu-id="2f497-109">Począwszy od [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] jest dostarczany z nowy model konfiguracji domyślne, które upraszcza [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] wymagania dotyczące konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2f497-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] comes with a new default configuration model that simplifies [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration requirements.</span></span> <span data-ttu-id="2f497-110">Jeśli nie podano żadnego [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] konfiguracji dla określonej usługi, środowisko uruchomieniowe automatycznie konfiguruje usługi przy użyciu domyślnych punktów końcowych, powiązania i zachowania.</span><span class="sxs-lookup"><span data-stu-id="2f497-110">If you do not provide any [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration for a particular service, the runtime automatically configures your service with default endpoints, bindings, and behaviors.</span></span>  
  
 [<span data-ttu-id="2f497-111">Konfigurowanie usług za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2f497-111">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 <span data-ttu-id="2f497-112">A [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usługa jest można skonfigurować przy użyciu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] technologia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2f497-112">A [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service is configurable using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration technology.</span></span> <span data-ttu-id="2f497-113">Najczęściej, elementy XML są dodawane do pliku Web.config dla witryny Internet Information Services (IIS), który jest hostem [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="2f497-113">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="2f497-114">Elementy umożliwiają zmianę szczegóły, takie jak adresy punktów końcowych (rzeczywiste adresy używane do komunikacji z usługą) na komputerze przez komputer.</span><span class="sxs-lookup"><span data-stu-id="2f497-114">The elements allow you to change details, such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span>  
  
 [<span data-ttu-id="2f497-115">Powiązania</span><span class="sxs-lookup"><span data-stu-id="2f497-115">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)  
 <span data-ttu-id="2f497-116">Ponadto [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] obejmuje kilka typowych konfiguracji dostarczane przez system w postaci powiązania, które umożliwiają szybkie wybranie najbardziej podstawowe funkcje klienta i usługi komunikowania, takich jak transportów, zabezpieczeń i kodowanie komunikatu używane.</span><span class="sxs-lookup"><span data-stu-id="2f497-116">In addition, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] includes several system-provided common configurations in the form of bindings that allow you to quickly select the most basic features for how a client and service communicate, such as the transports, security, and message encodings used.</span></span>  
  
 [<span data-ttu-id="2f497-117">Punkty końcowe</span><span class="sxs-lookup"><span data-stu-id="2f497-117">Endpoints</span></span>](../../../docs/framework/wcf/endpoints.md)  
 <span data-ttu-id="2f497-118">Cała komunikacja z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi odbywa się przez *punkty końcowe* usługi.</span><span class="sxs-lookup"><span data-stu-id="2f497-118">All communication with a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="2f497-119">Punkty końcowe zawiera kontrakt, informacje o konfiguracji, który jest określony w powiązaniach i adresy, wskazujące, gdzie można znaleźć usługi lub gdzie można uzyskać informacji o usłudze.</span><span class="sxs-lookup"><span data-stu-id="2f497-119">Endpoints contain the contract, the configuration information that is specified in the bindings, and the addresses that indicate where to find the service or where to obtain information about the service.</span></span>  
  
 [<span data-ttu-id="2f497-120">Zabezpieczanie usług</span><span class="sxs-lookup"><span data-stu-id="2f497-120">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 <span data-ttu-id="2f497-121">Przy użyciu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] i istniejące mechanizmy zabezpieczeń, można zaimplementować poufność, integralność, uwierzytelniania i autoryzacji do dowolnej usługi.</span><span class="sxs-lookup"><span data-stu-id="2f497-121">Using [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] and existing security mechanisms, you can implement confidentiality, integrity, authentication, and authorization into any service.</span></span> <span data-ttu-id="2f497-122">Można również przeprowadzać inspekcję dla zabezpieczeń sukcesy i niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="2f497-122">You can also audit for security successes and failures.</span></span>  
  
 [<span data-ttu-id="2f497-123">Tworzenie usługi WS-I Basic Profile 1.1 usługi międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="2f497-123">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 <span data-ttu-id="2f497-124">Wymagania dotyczące wdrażania usługi, która współdziała z usług i klientów na dowolnej platformie lub systemu operacyjnego zostały opisane w WS-I Basic Profile 1.1 specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="2f497-124">The requirements for deploying a service that is interoperable with services and clients on any other platform or operating system are outlined in the WS-I Basic Profile 1.1 specification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2f497-125">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="2f497-125">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="2f497-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="2f497-126">Related Sections</span></span>  
 [<span data-ttu-id="2f497-127">Podstawowy cykl życia programowania</span><span class="sxs-lookup"><span data-stu-id="2f497-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [<span data-ttu-id="2f497-128">Projektowanie i Implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="2f497-128">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [<span data-ttu-id="2f497-129">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="2f497-129">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)  
  
 [<span data-ttu-id="2f497-130">Kompilowanie klientów</span><span class="sxs-lookup"><span data-stu-id="2f497-130">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
  
 [<span data-ttu-id="2f497-131">Wprowadzenie do rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="2f497-131">Introduction to Extensibility</span></span>](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [<span data-ttu-id="2f497-132">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="2f497-132">Administration and Diagnostics</span></span>](../../../docs/framework/wcf/diagnostics/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="2f497-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f497-133">See Also</span></span>  
 [<span data-ttu-id="2f497-134">Programowanie podstawowe usługi WCF</span><span class="sxs-lookup"><span data-stu-id="2f497-134">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="2f497-135">Omówienie pojęć</span><span class="sxs-lookup"><span data-stu-id="2f497-135">Conceptual Overview</span></span>](../../../docs/framework/wcf/conceptual-overview.md)  
 [<span data-ttu-id="2f497-136">Szczegóły funkcji WCF</span><span class="sxs-lookup"><span data-stu-id="2f497-136">WCF Feature Details</span></span>](../../../docs/framework/wcf/feature-details/index.md)
