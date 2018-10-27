---
title: Negocjacje i limity czasu dotyczące zabezpieczeń
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: dfabdb05c7658e3cf9eb5b325597360bbc0bb588
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50037801"
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="cd2d5-102">Negocjacje i limity czasu dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="cd2d5-102">Security Negotiation and Timeouts</span></span>
<span data-ttu-id="cd2d5-103">Podczas uwierzytelniania klientów i usług, Windows Communication Foundation (WCF) obsługuje tryb, w którym poświadczenia usługi jest negocjowane w ramach uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="cd2d5-103">When clients and services authenticate, Windows Communication Foundation (WCF) supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="cd2d5-104">W takich scenariuszach exchange potencjalnie wielu gałęzi występuje między klientem i usługi do propagowania poświadczenia usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="cd2d5-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="cd2d5-105"><xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Właściwość określa, jak długo exchange wielu gałęzi może trwać do ukończenia.</span><span class="sxs-lookup"><span data-stu-id="cd2d5-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="cd2d5-106">Jednak tego limitu czasu zastosowanie tylko w przypadku programu exchange w rzeczywistości więcej, pojedynczą odpowiedź żądania.</span><span class="sxs-lookup"><span data-stu-id="cd2d5-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="cd2d5-107">W przypadkach, w którym negocjacji kończy w jednym obiegu limit czasu nie ma zastosowania.</span><span class="sxs-lookup"><span data-stu-id="cd2d5-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd2d5-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd2d5-108">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [<span data-ttu-id="cd2d5-109">Instrukcje: ustawianie maksymalnego przesunięcia czasowego zegara</span><span class="sxs-lookup"><span data-stu-id="cd2d5-109">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
