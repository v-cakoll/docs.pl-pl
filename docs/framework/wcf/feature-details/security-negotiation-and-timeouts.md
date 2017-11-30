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
# <a name="security-negotiation-and-timeouts"></a>Negocjacje i limity czasu dotyczące zabezpieczeń
Podczas uwierzytelniania klientów i usług, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] obsługuje tryb, w którym poświadczenia usługi jest negocjowanych w ramach uwierzytelniania. W takich scenariuszach exchange potencjalnie wieloetapowego występuje między klientem a usługa propagacji poświadczenie usługi do klienta. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Właściwość określa, jak długo exchange wieloetapowego może trwać do wykonania. Jednak tego limitu czasu tylko w przypadku programu exchange w rzeczywistości więcej który pojedynczą żądanie odpowiedź. W przypadkach, gdy negocjacji kończy w jednej Rundy limitu czasu nie ma zastosowania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [Porady: zestaw Max niedokładność zegara](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
