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
# <a name="security-negotiation-and-timeouts"></a>Negocjacje i limity czasu dotyczące zabezpieczeń
Podczas uwierzytelniania klientów i usług, Windows Communication Foundation (WCF) obsługuje tryb, w którym poświadczenia usługi jest negocjowane w ramach uwierzytelniania. W takich scenariuszach exchange potencjalnie wielu gałęzi występuje między klientem i usługi do propagowania poświadczenia usługi do klienta. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Właściwość określa, jak długo exchange wielu gałęzi może trwać do ukończenia. Jednak tego limitu czasu zastosowanie tylko w przypadku programu exchange w rzeczywistości więcej, pojedynczą odpowiedź żądania. W przypadkach, w którym negocjacji kończy w jednym obiegu limit czasu nie ma zastosowania.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Instrukcje: Zestaw maksymalnego przesunięcia czasowego zegara](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
