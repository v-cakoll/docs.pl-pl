---
title: Manipulowanie
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: e618ab369a46d403aa8db26c4b472e2be3634785
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600714"
---
# <a name="tampering"></a><span data-ttu-id="687a4-102">Manipulowanie</span><span class="sxs-lookup"><span data-stu-id="687a4-102">Tampering</span></span>
<span data-ttu-id="687a4-103">*Manipulowanie* to czynność polegająca na zmianie wiadomości lub dostarczeniu wiadomości, a także przy użyciu zmienionego komunikatu do celów innych niż to, do czego została zaprojektowana.</span><span class="sxs-lookup"><span data-stu-id="687a4-103">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="687a4-104">Nie należy wyłączać usługi WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="687a4-104">Do Not Disable WS-Addressing</span></span>  
 <span data-ttu-id="687a4-105">Specyfikacja WS-Addressing zawiera nagłówki adresów dla każdego komunikatu, umożliwiając odbiorcom komunikatu zweryfikowanie nadawcy wiadomości.</span><span class="sxs-lookup"><span data-stu-id="687a4-105">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="687a4-106">Tę funkcję można wyłączyć, ustawiając <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> Właściwość na <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="687a4-106">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="687a4-107">Gdy tryb zabezpieczeń jest ustawiony na komunikat, a Usługa WS-Addressing jest wyłączona, osoba atakująca może wykonać żądanie od klienta i wysłać ją do innej usługi, a druga usługa nie ma możliwości wykrycia, że wiadomość pochodzi od oryginalnego klienta.</span><span class="sxs-lookup"><span data-stu-id="687a4-107">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="687a4-108">W efekcie pierwsza usługa może poudawać, że jest klientem podczas rozmowy z drugą usługą.</span><span class="sxs-lookup"><span data-stu-id="687a4-108">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="687a4-109">Aby rozwiązać ten problem, nigdy nie ustawiaj <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> właściwości na <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> i Unikaj używania <xref:System.ServiceModel.Channels.MessageVersion> , takich jak właściwość statyczna <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> , która ustawia <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> Właściwość na <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="687a4-109">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="687a4-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="687a4-110">See also</span></span>

- [<span data-ttu-id="687a4-111">Zagadnienia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="687a4-111">Security Considerations</span></span>](security-considerations-in-wcf.md)
- [<span data-ttu-id="687a4-112">Ujawnianie informacji</span><span class="sxs-lookup"><span data-stu-id="687a4-112">Information Disclosure</span></span>](information-disclosure.md)
- [<span data-ttu-id="687a4-113">Podniesienie uprawnień</span><span class="sxs-lookup"><span data-stu-id="687a4-113">Elevation of Privilege</span></span>](elevation-of-privilege.md)
- [<span data-ttu-id="687a4-114">Odmowa usługi</span><span class="sxs-lookup"><span data-stu-id="687a4-114">Denial of Service</span></span>](denial-of-service.md)
- [<span data-ttu-id="687a4-115">Nieobsługiwane scenariusze</span><span class="sxs-lookup"><span data-stu-id="687a4-115">Unsupported Scenarios</span></span>](unsupported-scenarios.md)
- [<span data-ttu-id="687a4-116">Ataki oparte na metodzie powtórzeń</span><span class="sxs-lookup"><span data-stu-id="687a4-116">Replay Attacks</span></span>](replay-attacks.md)
