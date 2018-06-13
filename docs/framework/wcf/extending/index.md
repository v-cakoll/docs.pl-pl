---
title: Rozszerzanie architektury WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
ms.openlocfilehash: 24ad74f04a3ac31d0b0d0d87f0d74f88c0521f50
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803708"
---
# <a name="extending-wcf"></a><span data-ttu-id="2bc55-102">Rozszerzanie architektury WCF</span><span class="sxs-lookup"><span data-stu-id="2bc55-102">Extending WCF</span></span>
<span data-ttu-id="2bc55-103">Windows Communication Foundation (WCF) służy do modyfikowania i rozszerzania składników dokładnie określić czas wykonywania, a rozszerzenie aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="2bc55-103">Windows Communication Foundation (WCF) allows you to modify and extend run time components to precisely control and extend service-based applications.</span></span> <span data-ttu-id="2bc55-104">Przejdź w tematach w tej sekcji szczegółowo o architekturze rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="2bc55-104">The topics in this section go in depth about the extensibility architecture.</span></span> <span data-ttu-id="2bc55-105">Aby uzyskać więcej informacji na temat podstawy programowania, zobacz [podstawowe programowania WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).</span><span class="sxs-lookup"><span data-stu-id="2bc55-105">For more information about basic programming, see [Basic WCF Programming](../../../../docs/framework/wcf/basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2bc55-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2bc55-106">In This Section</span></span>  
 [<span data-ttu-id="2bc55-107">Rozszerzanie elementu ServiceHost i warstwy modelu usług</span><span class="sxs-lookup"><span data-stu-id="2bc55-107">Extending ServiceHost and the Service Model Layer</span></span>](../../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)  
 <span data-ttu-id="2bc55-108">Warstwy modelu usług jest odpowiedzialny za ściąganie wiadomości przychodzących poza podstawowej kanały, tłumaczenia je do wywołania metody w kodzie aplikacji i wysłaniem wyniki z powrotem do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="2bc55-108">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span>  <span data-ttu-id="2bc55-109">Rozszerzenia modelu usługi zmodyfikować, lub zaimplementuj wykonywania lub zachowanie komunikacji i funkcje dotyczące funkcji dyspozytora, niestandardowe zachowania, wiadomości i przechwytywaniu parametru i innych funkcji rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="2bc55-109">Service model extensions modify or implement execution or communication behavior and features involving dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
 [<span data-ttu-id="2bc55-110">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="2bc55-110">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 <span data-ttu-id="2bc55-111">Powiązania są obiekty, które opisują szczegóły komunikacji wymagane do połączenia z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="2bc55-111">Bindings are objects that describe the communication details required to connect to an endpoint.</span></span> <span data-ttu-id="2bc55-112">Powiązania niestandardowe lub rozszerzenia powiązania implementowania niestandardowych komunikacji wymagane do obsługi funkcji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2bc55-112">Binding extensions or custom bindings implement custom communication functionality required to support application features.</span></span>  
  
 [<span data-ttu-id="2bc55-113">Rozszerzanie warstwy kanału</span><span class="sxs-lookup"><span data-stu-id="2bc55-113">Extending the Channel Layer</span></span>](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)  
 <span data-ttu-id="2bc55-114">Warstwie kanału znajduje się poniżej warstwy modelu usług i jest odpowiedzialny za wymiana wiadomości między klientami i usługami.</span><span class="sxs-lookup"><span data-stu-id="2bc55-114">The channel layer sits beneath the service model layer and is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="2bc55-115">Rozszerzenia kanału można zaimplementować nowych funkcji protokołu, takie jak zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="2bc55-115">Channel extensions can implement new protocol functionality, such as security.</span></span> <span data-ttu-id="2bc55-116">Rozszerzenia kanał transportu również funkcje, takie jak wdrażanie nowego transportu sieciowego do przenoszenia wiadomości SOAP.</span><span class="sxs-lookup"><span data-stu-id="2bc55-116">Channel extensions also transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
 [<span data-ttu-id="2bc55-117">Rozszerzanie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="2bc55-117">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
 <span data-ttu-id="2bc55-118">Zabezpieczenia w programie WCF składa się z przesunięcia zabezpieczeń (integralność, poufność i uwierzytelnianie), kontrola dostępu (autoryzacja) i inspekcji.</span><span class="sxs-lookup"><span data-stu-id="2bc55-118">Security in WCF consists of transfer security (integrity, confidentiality, and authentication), access control (authorization) and auditing.</span></span> <span data-ttu-id="2bc55-119">Znaleziono klas w `IdentityModel` przestrzeni nazw są używane przez usługi WCF do kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="2bc55-119">The classes found in the `IdentityModel` namespace are used by WCF for access control.</span></span> <span data-ttu-id="2bc55-120">Omówienie architektury zabezpieczeń służy do tworzenia niestandardowych oświadczenia, aby pomieścić systemów kontroli dostępu niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="2bc55-120">Understanding the security architecture allows you to create custom claim types to accommodate custom access control systems.</span></span>  
  
 [<span data-ttu-id="2bc55-121">Rozszerzanie systemu metadanych</span><span class="sxs-lookup"><span data-stu-id="2bc55-121">Extending the Metadata System</span></span>](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)  
 <span data-ttu-id="2bc55-122">System metadanych WCF jest grupą klasy i interfejsy, które reprezentują metadane wymagane do wdrożenia aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="2bc55-122">The WCF metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="2bc55-123">Modyfikowanie lub rozszerzyć klasy lub wdrożenia i skonfigurować interfejsów, aby wyeksportować i zaimportować niestandardowy metadane, takie jak rozszerzenia usługi sieci Web Services Description Language (WSDL) lub niestandardowych asercji WS PolicyAttachments.</span><span class="sxs-lookup"><span data-stu-id="2bc55-123">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
 [<span data-ttu-id="2bc55-124">Rozszerzanie koderów i serializatorów</span><span class="sxs-lookup"><span data-stu-id="2bc55-124">Extending Encoders and Serializers</span></span>](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
 <span data-ttu-id="2bc55-125">Koderów i serializatorów tłumaczenie danych z jednego formularza.</span><span class="sxs-lookup"><span data-stu-id="2bc55-125">Encoders and serializers translate data from one form to another.</span></span> <span data-ttu-id="2bc55-126">Tematy w tej sekcji omówiono sposób rozszerzyć klasy dostarczony, aby spełnić te wymagania.</span><span class="sxs-lookup"><span data-stu-id="2bc55-126">The topics in this section discuss how to extend the supplied classes to meet special requirements.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2bc55-127">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="2bc55-127">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a><span data-ttu-id="2bc55-128">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="2bc55-128">Related Sections</span></span>  
 [<span data-ttu-id="2bc55-129">Podstawy programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="2bc55-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="2bc55-130">Szczegóły funkcji WCF</span><span class="sxs-lookup"><span data-stu-id="2bc55-130">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="2bc55-131">Wskazówki i najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="2bc55-131">Guidelines and Best Practices</span></span>](../../../../docs/framework/wcf/guidelines-and-best-practices.md)
