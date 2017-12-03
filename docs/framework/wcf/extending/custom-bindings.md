---
title: "Powiązania niestandardowe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45945fb07f7d1807674453296f7c5e62c829a401
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="custom-bindings"></a><span data-ttu-id="ff360-102">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="ff360-102">Custom Bindings</span></span>
<span data-ttu-id="ff360-103">Można użyć <xref:System.ServiceModel.Channels.CustomBinding> klasy, jeśli jedno z powiązań dostarczane przez system nie spełnia wymagania dotyczące usługi.</span><span class="sxs-lookup"><span data-stu-id="ff360-103">You can use the <xref:System.ServiceModel.Channels.CustomBinding> class when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="ff360-104">Wszystkie powiązania są tworzone na podstawie uporządkowany zestaw elementów wiązania.</span><span class="sxs-lookup"><span data-stu-id="ff360-104">All bindings are constructed from an ordered set of binding elements.</span></span> <span data-ttu-id="ff360-105">Powiązania niestandardowe mogą być zbudowane z zestawu elementów powiązania dostarczane przez system, lub mogą zawierać elementy zdefiniowane przez użytkownika niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="ff360-105">Custom bindings can be built from a set of system-provided binding elements or can include user-defined custom binding elements.</span></span> <span data-ttu-id="ff360-106">Elementy wiązania niestandardowego, na przykład umożliwia korzystanie z nowego transportu lub koderów na punkt końcowy usługi.</span><span class="sxs-lookup"><span data-stu-id="ff360-106">You can use custom binding elements, for example, to enable the use of new transports or encoders at a service endpoint.</span></span> <span data-ttu-id="ff360-107">Przykłady pracy można znaleźć [przykłady powiązań niestandardowych](http://msdn.microsoft.com/en-us/657e8143-beb0-472d-9cfe-ed1a19c2ab08).</span><span class="sxs-lookup"><span data-stu-id="ff360-107">For working examples, see [Custom Binding Samples](http://msdn.microsoft.com/en-us/657e8143-beb0-472d-9cfe-ed1a19c2ab08).</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="ff360-108">[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="ff360-108"> [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
## <a name="construction-of-a-custom-binding"></a><span data-ttu-id="ff360-109">Konstrukcja wiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="ff360-109">Construction of a Custom Binding</span></span>  
 <span data-ttu-id="ff360-110">Wiązanie niestandardowe jest tworzony przy użyciu <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> konstruktora z kolekcji elementów, które są "skumulowany" w określonej kolejności wiązania:</span><span class="sxs-lookup"><span data-stu-id="ff360-110">A custom binding is constructed using the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> constructor from a collection of binding elements that are "stacked" in a specific order:</span></span>  
  
-   <span data-ttu-id="ff360-111">U góry to opcjonalna <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> klasy, która umożliwia przepływu transakcji.</span><span class="sxs-lookup"><span data-stu-id="ff360-111">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> class that allows flowing transactions.</span></span>  
  
-   <span data-ttu-id="ff360-112">Następnie to opcjonalna <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> klasy, która udostępnia sesję i kolejności mechanizmów zgodnie z definicją w specyfikacji WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="ff360-112">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> class that provides a session and ordering mechanisms as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="ff360-113">Sesja może krzyżowe pośredników SOAP i transportu.</span><span class="sxs-lookup"><span data-stu-id="ff360-113">A session can cross SOAP and transport intermediaries.</span></span>  
  
-   <span data-ttu-id="ff360-114">Następnie to opcjonalna <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy, która udostępnia funkcje zabezpieczeń, takich jak autoryzacja, uwierzytelnianie, ochrony i poufności.</span><span class="sxs-lookup"><span data-stu-id="ff360-114">Next is an optional <xref:System.ServiceModel.Channels.SecurityBindingElement> class that provides security features such as authorization, authentication, protection, and confidentiality.</span></span>  
  
-   <span data-ttu-id="ff360-115">Następnie to opcjonalna <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> klasy, która pozwala na dwóch sposób dupleksu komunikacji za pomocą protokołu transport, który nie obsługuje komunikację dupleksową natywnie, takich jak HTTP.</span><span class="sxs-lookup"><span data-stu-id="ff360-115">Next is an optional <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> class that provides the ability to have two way duplex communication with a transport protocol that does not support duplex communication natively, such as HTTP.</span></span>  
  
-   <span data-ttu-id="ff360-116">Następnie to opcjonalna <xref:System.ServiceModel.Channels.OneWayBindingElement>) klasy, która zapewnia komunikację jednokierunkowe.</span><span class="sxs-lookup"><span data-stu-id="ff360-116">Next is an optional <xref:System.ServiceModel.Channels.OneWayBindingElement>) class that provides one-way communication.</span></span>  
  
-   <span data-ttu-id="ff360-117">Następnie jest opcjonalny strumienia elementu powiązania zabezpieczeń, które może być jedną z następujących czynności.</span><span class="sxs-lookup"><span data-stu-id="ff360-117">Next is an optional stream security binding element which can be one of the following.</span></span>  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   <span data-ttu-id="ff360-118">Obok jest element powiązania kodowania komunikatu wymagane.</span><span class="sxs-lookup"><span data-stu-id="ff360-118">Next is a required message encoding binding element.</span></span> <span data-ttu-id="ff360-119">Można użyć kodera wiadomości lub jeden z trzech powiązania kodowania wiadomości:</span><span class="sxs-lookup"><span data-stu-id="ff360-119">You can use your own message encoder or one of the three message encoding bindings:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
 <span data-ttu-id="ff360-120">W dolnej części jest element wymagany transportu.</span><span class="sxs-lookup"><span data-stu-id="ff360-120">At the bottom is a required transport element.</span></span> <span data-ttu-id="ff360-121">Można użyć własnych transportu lub jeden z następujących elementów powiązania transportu [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zawiera:</span><span class="sxs-lookup"><span data-stu-id="ff360-121">You can use your own transport or one of the following transport binding elements [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] provides:</span></span>  
  
-   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
-   <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
 <span data-ttu-id="ff360-122">W poniższej tabeli przedstawiono opcje dla każdej warstwy.</span><span class="sxs-lookup"><span data-stu-id="ff360-122">The following table summarizes the options for each layer.</span></span>  
  
|<span data-ttu-id="ff360-123">Warstwy</span><span class="sxs-lookup"><span data-stu-id="ff360-123">Layer</span></span>|<span data-ttu-id="ff360-124">Opcje</span><span class="sxs-lookup"><span data-stu-id="ff360-124">Options</span></span>|<span data-ttu-id="ff360-125">Wymagane</span><span class="sxs-lookup"><span data-stu-id="ff360-125">Required</span></span>|  
|-----------|-------------|--------------|  
|<span data-ttu-id="ff360-126">Transakcje</span><span class="sxs-lookup"><span data-stu-id="ff360-126">Transactions</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="ff360-127">Nie</span><span class="sxs-lookup"><span data-stu-id="ff360-127">No</span></span>|  
|<span data-ttu-id="ff360-128">Niezawodność</span><span class="sxs-lookup"><span data-stu-id="ff360-128">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="ff360-129">Nie</span><span class="sxs-lookup"><span data-stu-id="ff360-129">No</span></span>|  
|<span data-ttu-id="ff360-130">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="ff360-130">Security</span></span>|<xref:System.ServiceModel.Channels.SecurityBindingElement>|<span data-ttu-id="ff360-131">Nie</span><span class="sxs-lookup"><span data-stu-id="ff360-131">No</span></span>|  
|<span data-ttu-id="ff360-132">Kodowanie</span><span class="sxs-lookup"><span data-stu-id="ff360-132">Encoding</span></span>|<span data-ttu-id="ff360-133">Tekst, niestandardowe binary, komunikat transmisji optymalizacji mechanizmu (MTOM)</span><span class="sxs-lookup"><span data-stu-id="ff360-133">Text, binary, Message Transmission Optimization Mechanism (MTOM), custom</span></span>|<span data-ttu-id="ff360-134">Tak</span><span class="sxs-lookup"><span data-stu-id="ff360-134">Yes</span></span>|  
|<span data-ttu-id="ff360-135">Transportu</span><span class="sxs-lookup"><span data-stu-id="ff360-135">Transport</span></span>|<span data-ttu-id="ff360-136">TCP, HTTP i HTTPS, nazwane potoki (znanej także jako IPC) między równorzędnych (P2P), Usługa kolejkowania komunikatów (MSMQ), niestandardowe</span><span class="sxs-lookup"><span data-stu-id="ff360-136">TCP, HTTP, HTTPS, named pipes (also known as IPC), Peer-to-Peer (P2P), Message Queuing (also known as MSMQ), Custom</span></span>|<span data-ttu-id="ff360-137">Tak</span><span class="sxs-lookup"><span data-stu-id="ff360-137">Yes</span></span>|  
  
 <span data-ttu-id="ff360-138">Ponadto można definiować własne elementy powiązania i wstawione między dowolnymi z poprzednim zdefiniowane warstwy.</span><span class="sxs-lookup"><span data-stu-id="ff360-138">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff360-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff360-139">See Also</span></span>  
 [<span data-ttu-id="ff360-140">Przegląd tworzenia punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="ff360-140">Endpoint Creation Overview</span></span>](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [<span data-ttu-id="ff360-141">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="ff360-141">Using Bindings to Configure Services and Clients</span></span>](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="ff360-142">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="ff360-142">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [<span data-ttu-id="ff360-143">Porady: dostosowywanie powiązania dostarczane przez System</span><span class="sxs-lookup"><span data-stu-id="ff360-143">How to: Customize a System-Provided Binding</span></span>](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)  
 [<span data-ttu-id="ff360-144">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="ff360-144">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="ff360-145">Wiązanie niestandardowe</span><span class="sxs-lookup"><span data-stu-id="ff360-145">Custom Binding</span></span>](../../../../docs/framework/wcf/samples/custom-binding.md)
