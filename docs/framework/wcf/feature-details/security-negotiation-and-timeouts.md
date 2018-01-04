---
title: "Negocjacje i limity czasu dotyczące zabezpieczeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 6fbee18d31cb1774300c14587b0f7d973a4996ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="90778-102">Negocjacje i limity czasu dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="90778-102">Security Negotiation and Timeouts</span></span>
<span data-ttu-id="90778-103">Podczas uwierzytelniania klientów i usług, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] obsługuje tryb, w którym poświadczenia usługi jest negocjowanych w ramach uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="90778-103">When clients and services authenticate, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="90778-104">W takich scenariuszach exchange potencjalnie wieloetapowego występuje między klientem a usługa propagacji poświadczenie usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="90778-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="90778-105"><xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Właściwość określa, jak długo exchange wieloetapowego może trwać do wykonania.</span><span class="sxs-lookup"><span data-stu-id="90778-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="90778-106">Jednak tego limitu czasu tylko w przypadku programu exchange w rzeczywistości więcej który pojedynczą żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="90778-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="90778-107">W przypadkach, gdy negocjacji kończy w jednej Rundy limitu czasu nie ma zastosowania.</span><span class="sxs-lookup"><span data-stu-id="90778-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90778-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90778-108">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [<span data-ttu-id="90778-109">Instrukcje: ustawianie maksymalnego przesunięcia czasowego zegara</span><span class="sxs-lookup"><span data-stu-id="90778-109">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
