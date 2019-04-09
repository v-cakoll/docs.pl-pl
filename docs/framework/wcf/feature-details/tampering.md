---
title: Manipulowanie
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: 7a4265c30a6713f9557de2b3d1e99c87b7dd3e58
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107890"
---
# <a name="tampering"></a><span data-ttu-id="e6b75-102">Manipulowanie</span><span class="sxs-lookup"><span data-stu-id="e6b75-102">Tampering</span></span>
<span data-ttu-id="e6b75-103">*Manipulowanie* polega na zmianę wiadomości lub dostarczania wiadomości i przy użyciu zmienionego komunikatu w celu innym niż co zostało przeznaczone.</span><span class="sxs-lookup"><span data-stu-id="e6b75-103">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="e6b75-104">Nie można wyłączyć usługi WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="e6b75-104">Do Not Disable WS-Addressing</span></span>  
 <span data-ttu-id="e6b75-105">Specyfikacja WS-Addressing zawiera nagłówki adresów dla każdej wiadomości, dzięki czemu adresat wiadomości sprawdzić nadawcy wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e6b75-105">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="e6b75-106">Tę funkcję można wyłączyć, ustawiając <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> właściwość <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="e6b75-106">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="e6b75-107">Gdy tryb zabezpieczeń jest ustawiony na komunikat i WS-Addressing jest wyłączona, osoba atakująca może wykonać żądania z klienta i wysyłać je do innej usługi, a druga usługa nie ma możliwości wykrywania, czy wiadomość pochodzi z oryginalnego klienta.</span><span class="sxs-lookup"><span data-stu-id="e6b75-107">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="e6b75-108">W efekcie pierwszej usługi poudawać się klienta w przypadku drugiej usługi.</span><span class="sxs-lookup"><span data-stu-id="e6b75-108">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="e6b75-109">Aby temu zaradzić, nigdy nie ustawiono <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> właściwości <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>i należy unikać użycia <xref:System.ServiceModel.Channels.MessageVersion>, takie jak statyczne <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> właściwość, która ustawia <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> właściwość <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="e6b75-109">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6b75-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6b75-110">See also</span></span>

- [<span data-ttu-id="e6b75-111">Zagadnienia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="e6b75-111">Security Considerations</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [<span data-ttu-id="e6b75-112">Ujawnianie informacji</span><span class="sxs-lookup"><span data-stu-id="e6b75-112">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [<span data-ttu-id="e6b75-113">Podniesienie uprawnień</span><span class="sxs-lookup"><span data-stu-id="e6b75-113">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [<span data-ttu-id="e6b75-114">Odmowa usługi</span><span class="sxs-lookup"><span data-stu-id="e6b75-114">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [<span data-ttu-id="e6b75-115">Nieobsługiwane scenariusze</span><span class="sxs-lookup"><span data-stu-id="e6b75-115">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
- [<span data-ttu-id="e6b75-116">Ataki oparte na metodzie powtórzeń</span><span class="sxs-lookup"><span data-stu-id="e6b75-116">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
