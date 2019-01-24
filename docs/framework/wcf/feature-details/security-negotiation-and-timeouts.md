---
title: Negocjacje i limity czasu dotyczące zabezpieczeń
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: 38dce9bd6587850a5e3327600bb8bc13c48b93e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592617"
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="9a1f9-102">Negocjacje i limity czasu dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="9a1f9-102">Security Negotiation and Timeouts</span></span>
<span data-ttu-id="9a1f9-103">Podczas uwierzytelniania klientów i usług, Windows Communication Foundation (WCF) obsługuje tryb, w którym poświadczenia usługi jest negocjowane w ramach uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="9a1f9-103">When clients and services authenticate, Windows Communication Foundation (WCF) supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="9a1f9-104">W takich scenariuszach exchange potencjalnie wielu gałęzi występuje między klientem i usługi do propagowania poświadczenia usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="9a1f9-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="9a1f9-105"><xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Właściwość określa, jak długo exchange wielu gałęzi może trwać do ukończenia.</span><span class="sxs-lookup"><span data-stu-id="9a1f9-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="9a1f9-106">Jednak tego limitu czasu zastosowanie tylko w przypadku programu exchange w rzeczywistości więcej, pojedynczą odpowiedź żądania.</span><span class="sxs-lookup"><span data-stu-id="9a1f9-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="9a1f9-107">W przypadkach, w którym negocjacji kończy w jednym obiegu limit czasu nie ma zastosowania.</span><span class="sxs-lookup"><span data-stu-id="9a1f9-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a1f9-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a1f9-108">See also</span></span>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="9a1f9-109">Instrukcje: Zestaw maksymalnego przesunięcia czasowego zegara</span><span class="sxs-lookup"><span data-stu-id="9a1f9-109">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
