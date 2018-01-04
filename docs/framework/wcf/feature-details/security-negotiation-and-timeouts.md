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
# <a name="security-negotiation-and-timeouts"></a>Negocjacje i limity czasu dotyczące zabezpieczeń
Podczas uwierzytelniania klientów i usług, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] obsługuje tryb, w którym poświadczenia usługi jest negocjowanych w ramach uwierzytelniania. W takich scenariuszach exchange potencjalnie wieloetapowego występuje między klientem a usługa propagacji poświadczenie usługi do klienta. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Właściwość określa, jak długo exchange wieloetapowego może trwać do wykonania. Jednak tego limitu czasu tylko w przypadku programu exchange w rzeczywistości więcej który pojedynczą żądanie odpowiedź. W przypadkach, gdy negocjacji kończy w jednej Rundy limitu czasu nie ma zastosowania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [Instrukcje: ustawianie maksymalnego przesunięcia czasowego zegara](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
