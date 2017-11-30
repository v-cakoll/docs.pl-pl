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
ms.openlocfilehash: b4d0b2953a91040c37afe88d9499fd4be1970f31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="e8383-102">Negocjacje i limity czasu dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="e8383-102">Security Negotiation and Timeouts</span></span>
<span data-ttu-id="e8383-103">Podczas uwierzytelniania klientów i usług, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] obsługuje tryb, w którym poświadczenia usługi jest negocjowanych w ramach uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="e8383-103">When clients and services authenticate, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="e8383-104">W takich scenariuszach exchange potencjalnie wieloetapowego występuje między klientem a usługa propagacji poświadczenie usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="e8383-104">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="e8383-105"><xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Właściwość określa, jak długo exchange wieloetapowego może trwać do wykonania.</span><span class="sxs-lookup"><span data-stu-id="e8383-105">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="e8383-106">Jednak tego limitu czasu tylko w przypadku programu exchange w rzeczywistości więcej który pojedynczą żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="e8383-106">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="e8383-107">W przypadkach, gdy negocjacji kończy w jednej Rundy limitu czasu nie ma zastosowania.</span><span class="sxs-lookup"><span data-stu-id="e8383-107">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8383-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8383-108">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [<span data-ttu-id="e8383-109">Porady: zestaw Max niedokładność zegara</span><span class="sxs-lookup"><span data-stu-id="e8383-109">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
