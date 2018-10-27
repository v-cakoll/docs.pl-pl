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
# <a name="security-negotiation-and-timeouts"></a>Negocjacje i limity czasu dotyczące zabezpieczeń
Podczas uwierzytelniania klientów i usług, Windows Communication Foundation (WCF) obsługuje tryb, w którym poświadczenia usługi jest negocjowane w ramach uwierzytelniania. W takich scenariuszach exchange potencjalnie wielu gałęzi występuje między klientem i usługi do propagowania poświadczenia usługi do klienta. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Właściwość określa, jak długo exchange wielu gałęzi może trwać do ukończenia. Jednak tego limitu czasu zastosowanie tylko w przypadku programu exchange w rzeczywistości więcej, pojedynczą odpowiedź żądania. W przypadkach, w którym negocjacji kończy w jednym obiegu limit czasu nie ma zastosowania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [Instrukcje: ustawianie maksymalnego przesunięcia czasowego zegara](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
