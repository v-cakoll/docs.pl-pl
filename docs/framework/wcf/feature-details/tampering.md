---
title: Manipulowanie
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 96ab38de1fb2a932fefd4e37cbfab3d9bfbea616
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="tampering"></a><span data-ttu-id="39d81-102">Manipulowanie</span><span class="sxs-lookup"><span data-stu-id="39d81-102">Tampering</span></span>
<span data-ttu-id="39d81-103">*Manipulowanie* jest czynnością, zmienianie lub dostarczenia komunikatów wiadomości i za pomocą zmieniony komunikatu do celów innych niż to, co zostało przeznaczone.</span><span class="sxs-lookup"><span data-stu-id="39d81-103">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="39d81-104">Nie można wyłączyć usługi WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="39d81-104">Do Not Disable WS-Addressing</span></span>  
 <span data-ttu-id="39d81-105">Specyfikacja WS-Addressing zawiera nagłówki adresów dla każdej wiadomości, dzięki czemu adresat wiadomości sprawdzić nadawcy wiadomości.</span><span class="sxs-lookup"><span data-stu-id="39d81-105">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="39d81-106">Tę funkcję można wyłączyć, ustawiając <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> właściwości <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="39d81-106">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="39d81-107">Gdy tryb zabezpieczeń jest ustawiony na komunikat i WS-Addressing jest wyłączona, osoba atakująca może wykonać żądania z klienta i wysyłania go do innej usługi, a drugi usługi nie ma możliwości ustalenia, czy komunikat pochodzi z oryginalnego klienta.</span><span class="sxs-lookup"><span data-stu-id="39d81-107">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="39d81-108">W efekcie pierwszej usługi mogą podawać się klienta po rozmowie z drugiego usługi.</span><span class="sxs-lookup"><span data-stu-id="39d81-108">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="39d81-109">Aby temu zaradzić, nigdy nie ustawiono <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> właściwości <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>i unikaj używania <xref:System.ServiceModel.Channels.MessageVersion>, takich jak statycznych <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> właściwość, która ustawia <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> właściwości <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="39d81-109">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39d81-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="39d81-110">See Also</span></span>  
 [<span data-ttu-id="39d81-111">Zagadnienia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="39d81-111">Security Considerations</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [<span data-ttu-id="39d81-112">Ujawnienie informacji</span><span class="sxs-lookup"><span data-stu-id="39d81-112">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [<span data-ttu-id="39d81-113">Podniesienie uprawnień</span><span class="sxs-lookup"><span data-stu-id="39d81-113">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [<span data-ttu-id="39d81-114">Odmowa usługi</span><span class="sxs-lookup"><span data-stu-id="39d81-114">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [<span data-ttu-id="39d81-115">Nieobsługiwane scenariusze</span><span class="sxs-lookup"><span data-stu-id="39d81-115">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 [<span data-ttu-id="39d81-116">Ataki</span><span class="sxs-lookup"><span data-stu-id="39d81-116">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
