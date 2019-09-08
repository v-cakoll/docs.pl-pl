---
title: Powiązania niestandardowe
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
ms.openlocfilehash: a4b3abfe9be25c9080a362eb4a6e4c7b070528f1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797224"
---
# <a name="custom-bindings"></a><span data-ttu-id="ca32c-102">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="ca32c-102">Custom Bindings</span></span>

<span data-ttu-id="ca32c-103">Klasy można użyć, <xref:System.ServiceModel.Channels.CustomBinding> gdy jedno z powiązań dostarczonych przez system nie spełnia wymagań usługi.</span><span class="sxs-lookup"><span data-stu-id="ca32c-103">You can use the <xref:System.ServiceModel.Channels.CustomBinding> class when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="ca32c-104">Wszystkie powiązania są zbudowane z uporządkowanego zestawu elementów powiązania.</span><span class="sxs-lookup"><span data-stu-id="ca32c-104">All bindings are constructed from an ordered set of binding elements.</span></span> <span data-ttu-id="ca32c-105">Niestandardowe powiązania mogą być kompilowane z zestawu elementów powiązania dostarczonych przez system lub mogą zawierać niestandardowe elementy powiązań zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ca32c-105">Custom bindings can be built from a set of system-provided binding elements or can include user-defined custom binding elements.</span></span> <span data-ttu-id="ca32c-106">Możesz użyć niestandardowych elementów powiązania, na przykład, aby umożliwić korzystanie z nowych transportów lub koderów w punkcie końcowym usługi.</span><span class="sxs-lookup"><span data-stu-id="ca32c-106">You can use custom binding elements, for example, to enable the use of new transports or encoders at a service endpoint.</span></span> <span data-ttu-id="ca32c-107">Aby zapoznać się z przykładami pracy, zobacz [niestandardowe powiązania przykładów](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="ca32c-107">For working examples, see [Custom Binding Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751479(v=vs.90)).</span></span> <span data-ttu-id="ca32c-108">Aby uzyskać więcej informacji, zobacz [ \<CustomBinding >](../../configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="ca32c-108">For more information, see [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>

## <a name="construction-of-a-custom-binding"></a><span data-ttu-id="ca32c-109">Konstruowanie niestandardowego powiązania</span><span class="sxs-lookup"><span data-stu-id="ca32c-109">Construction of a Custom Binding</span></span>

<span data-ttu-id="ca32c-110">Niestandardowe powiązanie jest konstruowane przy użyciu <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> konstruktora z kolekcji elementów powiązania, które są "ułożone" w określonej kolejności:</span><span class="sxs-lookup"><span data-stu-id="ca32c-110">A custom binding is constructed using the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> constructor from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="ca32c-111">U góry jest klasą opcjonalną <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> , która umożliwia przepływ transakcji.</span><span class="sxs-lookup"><span data-stu-id="ca32c-111">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> class that allows flowing transactions.</span></span>

- <span data-ttu-id="ca32c-112">Dalej jest klasą <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> opcjonalną, która dostarcza do sesji i mechanizmy porządkowania, zgodnie z definicją w specyfikacji WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="ca32c-112">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> class that provides a session and ordering mechanisms as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="ca32c-113">Sesja może przekroczyć pośredników SOAP i transportowych.</span><span class="sxs-lookup"><span data-stu-id="ca32c-113">A session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="ca32c-114">Następnie jest opcjonalną <xref:System.ServiceModel.Channels.SecurityBindingElement> klasą, która zapewnia funkcje zabezpieczeń, takie jak autoryzacja, uwierzytelnianie, ochrona i poufność.</span><span class="sxs-lookup"><span data-stu-id="ca32c-114">Next is an optional <xref:System.ServiceModel.Channels.SecurityBindingElement> class that provides security features such as authorization, authentication, protection, and confidentiality.</span></span>

- <span data-ttu-id="ca32c-115">Dalej jest klasą <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> opcjonalną, która zapewnia możliwość dwukierunkowej komunikacji dwustronnej z protokołem transportu, który nie obsługuje natywnej komunikacji dupleksowej, na przykład http.</span><span class="sxs-lookup"><span data-stu-id="ca32c-115">Next is an optional <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> class that provides the ability to have two way duplex communication with a transport protocol that does not support duplex communication natively, such as HTTP.</span></span>

- <span data-ttu-id="ca32c-116">Next to opcjonalna <xref:System.ServiceModel.Channels.OneWayBindingElement>Klasa, która zapewnia komunikację jednokierunkową.</span><span class="sxs-lookup"><span data-stu-id="ca32c-116">Next is an optional <xref:System.ServiceModel.Channels.OneWayBindingElement>) class that provides one-way communication.</span></span>

- <span data-ttu-id="ca32c-117">Następny to opcjonalny element powiązania zabezpieczeń strumienia, który może mieć jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="ca32c-117">Next is an optional stream security binding element which can be one of the following.</span></span>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="ca32c-118">Następnie jest wymagany element powiązania kodowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ca32c-118">Next is a required message encoding binding element.</span></span> <span data-ttu-id="ca32c-119">Możesz użyć własnego kodera komunikatów lub jednego z trzech powiązań kodowania komunikatów:</span><span class="sxs-lookup"><span data-stu-id="ca32c-119">You can use your own message encoder or one of the three message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

<span data-ttu-id="ca32c-120">U dołu jest wymagany element transportu.</span><span class="sxs-lookup"><span data-stu-id="ca32c-120">At the bottom is a required transport element.</span></span> <span data-ttu-id="ca32c-121">Możesz użyć własnego transportu lub jednego z następujących elementów powiązania transportowego Windows Communication Foundation (WCF) zapewnia:</span><span class="sxs-lookup"><span data-stu-id="ca32c-121">You can use your own transport or one of the following transport binding elements Windows Communication Foundation (WCF) provides:</span></span>

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>

<span data-ttu-id="ca32c-122">Poniższa tabela zawiera podsumowanie opcji dla każdej warstwy.</span><span class="sxs-lookup"><span data-stu-id="ca32c-122">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="ca32c-123">Warstwa</span><span class="sxs-lookup"><span data-stu-id="ca32c-123">Layer</span></span>|<span data-ttu-id="ca32c-124">Opcje</span><span class="sxs-lookup"><span data-stu-id="ca32c-124">Options</span></span>|<span data-ttu-id="ca32c-125">Wymagane</span><span class="sxs-lookup"><span data-stu-id="ca32c-125">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="ca32c-126">Transakcje</span><span class="sxs-lookup"><span data-stu-id="ca32c-126">Transactions</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="ca32c-127">Nie</span><span class="sxs-lookup"><span data-stu-id="ca32c-127">No</span></span>|
|<span data-ttu-id="ca32c-128">Niezawodność</span><span class="sxs-lookup"><span data-stu-id="ca32c-128">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="ca32c-129">Nie</span><span class="sxs-lookup"><span data-stu-id="ca32c-129">No</span></span>|
|<span data-ttu-id="ca32c-130">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="ca32c-130">Security</span></span>|<xref:System.ServiceModel.Channels.SecurityBindingElement>|<span data-ttu-id="ca32c-131">Nie</span><span class="sxs-lookup"><span data-stu-id="ca32c-131">No</span></span>|
|<span data-ttu-id="ca32c-132">Kodowanie</span><span class="sxs-lookup"><span data-stu-id="ca32c-132">Encoding</span></span>|<span data-ttu-id="ca32c-133">Tekst, binarny, mechanizm optymalizacji transmisji wiadomości (MTOM), niestandardowy</span><span class="sxs-lookup"><span data-stu-id="ca32c-133">Text, binary, Message Transmission Optimization Mechanism (MTOM), custom</span></span>|<span data-ttu-id="ca32c-134">Tak</span><span class="sxs-lookup"><span data-stu-id="ca32c-134">Yes</span></span>|
|<span data-ttu-id="ca32c-135">Transportu</span><span class="sxs-lookup"><span data-stu-id="ca32c-135">Transport</span></span>|<span data-ttu-id="ca32c-136">TCP, HTTP, HTTPS, nazwane potoki (znane również jako IPC), peer-to-peer (P2P), kolejkowanie komunikatów (nazywane także MSMQ), niestandardowe</span><span class="sxs-lookup"><span data-stu-id="ca32c-136">TCP, HTTP, HTTPS, named pipes (also known as IPC), Peer-to-Peer (P2P), Message Queuing (also known as MSMQ), Custom</span></span>|<span data-ttu-id="ca32c-137">Tak</span><span class="sxs-lookup"><span data-stu-id="ca32c-137">Yes</span></span>|

<span data-ttu-id="ca32c-138">Ponadto można definiować własne elementy powiązania i wstawiać je między wszystkimi wcześniej zdefiniowanymi warstwami.</span><span class="sxs-lookup"><span data-stu-id="ca32c-138">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca32c-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca32c-139">See also</span></span>

- [<span data-ttu-id="ca32c-140">Przegląd tworzenia punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="ca32c-140">Endpoint Creation Overview</span></span>](../endpoint-creation-overview.md)
- [<span data-ttu-id="ca32c-141">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="ca32c-141">Using Bindings to Configure Services and Clients</span></span>](../using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ca32c-142">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="ca32c-142">System-Provided Bindings</span></span>](../system-provided-bindings.md)
- [<span data-ttu-id="ca32c-143">Instrukcje: Dostosowywanie podanego przez system powiązania</span><span class="sxs-lookup"><span data-stu-id="ca32c-143">How to: Customize a System-Provided Binding</span></span>](how-to-customize-a-system-provided-binding.md)
- [<span data-ttu-id="ca32c-144">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ca32c-144">\<customBinding></span></span>](../../configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="ca32c-145">Powiązanie niestandardowe</span><span class="sxs-lookup"><span data-stu-id="ca32c-145">Custom Binding</span></span>](../samples/custom-binding.md)
