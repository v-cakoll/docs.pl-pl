---
title: Konfigurowanie usług
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 7718edaefbad18afa11b3e3680fac39da585a610
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="configuring-services"></a><span data-ttu-id="11257-102">Konfigurowanie usług</span><span class="sxs-lookup"><span data-stu-id="11257-102">Configuring Services</span></span>
<span data-ttu-id="11257-103">Po zaprojektowane i zaimplementowane umowy serwisowej, możesz przystąpić do konfigurowania usługi.</span><span class="sxs-lookup"><span data-stu-id="11257-103">Once you have designed and implemented your service contract, you are ready to configure your service.</span></span> <span data-ttu-id="11257-104">To pozwala definiować i dostosowywać, jak usługa jest widoczne dla klientów, łącznie z określeniem adres, gdzie można je znaleźć, transport i kodowanie wiadomości używanych do wysyłania i odbierania wiadomości oraz typ zabezpieczeń, które wymaga.</span><span class="sxs-lookup"><span data-stu-id="11257-104">This is where you define and customize how your service is exposed to clients, including specifying the address where it can be found, the transport and message encoding it uses to send and receive messages, and the type of security it requires.</span></span>  
  
 <span data-ttu-id="11257-105">Konfiguracja tutaj obejmuje wszystkich metod imperatively w kodzie, lub za pomocą pliku konfiguracji, w którym można zdefiniować i dostosować różne aspekty usług, takich jak określanie jego adresy punktów końcowych, transportów używane i jego systemów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="11257-105">Configuration as used here includes all the ways, imperatively in code or by using a configuration file, in which you can define and customize the various aspects of a service, such as specifying its endpoint addresses, the transports used, and its security schemes.</span></span> <span data-ttu-id="11257-106">W praktyce, zapisywanie konfiguracji jest poważnym należą do programowania aplikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="11257-106">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="11257-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="11257-107">In This Section</span></span>  
 [<span data-ttu-id="11257-108">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="11257-108">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 <span data-ttu-id="11257-109">Począwszy od [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF jest dostarczany z nowy model konfiguracji domyślnej, które upraszcza wymagania dotyczące konfiguracji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="11257-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="11257-110">Jeśli nie zostanie określona żadna konfiguracja usługi WCF dla określonej usługi, środowisko uruchomieniowe automatycznie konfiguruje usługi domyślne punkty końcowe, powiązania i zachowania.</span><span class="sxs-lookup"><span data-stu-id="11257-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with default endpoints, bindings, and behaviors.</span></span>  
  
 [<span data-ttu-id="11257-111">Konfigurowanie usług za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="11257-111">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 <span data-ttu-id="11257-112">Usługa Windows Communication Foundation (WCF) to można skonfigurować przy użyciu [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] technologia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="11257-112">A Windows Communication Foundation (WCF) service is configurable using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration technology.</span></span> <span data-ttu-id="11257-113">Najczęściej elementy XML są dodawane do pliku Web.config dla witryny Internet Information Services (IIS), który jest hostem usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="11257-113">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="11257-114">Elementy umożliwiają zmianę szczegóły, takie jak adresy punktów końcowych (rzeczywiste adresy używane do komunikacji z usługą) na komputerze przez komputer.</span><span class="sxs-lookup"><span data-stu-id="11257-114">The elements allow you to change details, such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span>  
  
 [<span data-ttu-id="11257-115">Powiązania</span><span class="sxs-lookup"><span data-stu-id="11257-115">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)  
 <span data-ttu-id="11257-116">Ponadto WCF zawiera kilka typowych konfiguracji dostarczane przez system w postaci powiązania, które umożliwiają szybkie wybierz najbardziej podstawowa funkcje sposobu komunikacji między klientem a usługą, na przykład transportów, zabezpieczeń i używane kodowanie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="11257-116">In addition, WCF includes several system-provided common configurations in the form of bindings that allow you to quickly select the most basic features for how a client and service communicate, such as the transports, security, and message encodings used.</span></span>  
  
 [<span data-ttu-id="11257-117">Punkty końcowe</span><span class="sxs-lookup"><span data-stu-id="11257-117">Endpoints</span></span>](../../../docs/framework/wcf/endpoints.md)  
 <span data-ttu-id="11257-118">Cała komunikacja z usługą WCF odbywa się przez *punkty końcowe* usługi.</span><span class="sxs-lookup"><span data-stu-id="11257-118">All communication with a WCF service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="11257-119">Punkty końcowe zawiera kontrakt, informacje o konfiguracji, który jest określony w powiązaniach i adresy, wskazujące, gdzie można znaleźć usługi lub gdzie można uzyskać informacji o usłudze.</span><span class="sxs-lookup"><span data-stu-id="11257-119">Endpoints contain the contract, the configuration information that is specified in the bindings, and the addresses that indicate where to find the service or where to obtain information about the service.</span></span>  
  
 [<span data-ttu-id="11257-120">Zabezpieczanie usług</span><span class="sxs-lookup"><span data-stu-id="11257-120">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 <span data-ttu-id="11257-121">Za pomocą usługi WCF i istniejące mechanizmy zabezpieczeń, można zaimplementować poufność, integralność, uwierzytelniania i autoryzacji do dowolnej usługi.</span><span class="sxs-lookup"><span data-stu-id="11257-121">Using WCF and existing security mechanisms, you can implement confidentiality, integrity, authentication, and authorization into any service.</span></span> <span data-ttu-id="11257-122">Można również przeprowadzać inspekcję dla zabezpieczeń sukcesy i niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="11257-122">You can also audit for security successes and failures.</span></span>  
  
 [<span data-ttu-id="11257-123">Tworzenie usług międzyoperacyjnych 1.1 profilu podstawowego WS-I</span><span class="sxs-lookup"><span data-stu-id="11257-123">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 <span data-ttu-id="11257-124">Wymagania dotyczące wdrażania usługi, która współdziała z usług i klientów na dowolnej platformie lub systemu operacyjnego zostały opisane w WS-I Basic Profile 1.1 specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="11257-124">The requirements for deploying a service that is interoperable with services and clients on any other platform or operating system are outlined in the WS-I Basic Profile 1.1 specification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="11257-125">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="11257-125">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="11257-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="11257-126">Related Sections</span></span>  
 [<span data-ttu-id="11257-127">Podstawowy cykl życia programowania</span><span class="sxs-lookup"><span data-stu-id="11257-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [<span data-ttu-id="11257-128">Projektowanie i implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="11257-128">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [<span data-ttu-id="11257-129">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="11257-129">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)  
  
 [<span data-ttu-id="11257-130">Kompilowanie klientów</span><span class="sxs-lookup"><span data-stu-id="11257-130">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
  
 [<span data-ttu-id="11257-131">Wprowadzenie do rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="11257-131">Introduction to Extensibility</span></span>](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [<span data-ttu-id="11257-132">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="11257-132">Administration and Diagnostics</span></span>](../../../docs/framework/wcf/diagnostics/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="11257-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11257-133">See Also</span></span>  
 [<span data-ttu-id="11257-134">Podstawy programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="11257-134">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="11257-135">Omówienie pojęć</span><span class="sxs-lookup"><span data-stu-id="11257-135">Conceptual Overview</span></span>](../../../docs/framework/wcf/conceptual-overview.md)  
 [<span data-ttu-id="11257-136">Szczegóły funkcji WCF</span><span class="sxs-lookup"><span data-stu-id="11257-136">WCF Feature Details</span></span>](../../../docs/framework/wcf/feature-details/index.md)
