---
title: Negocjacje i limity czasu dotyczące zabezpieczeń
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: a02c9d7b42eadf9a5ce9af8022fe292d6c23249c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180651"
---
# <a name="security-negotiation-and-timeouts"></a>Negocjacje i limity czasu dotyczące zabezpieczeń
Podczas uwierzytelniania klientów i usług, Windows Communication Foundation (WCF) obsługuje tryb, w którym poświadczenia usługi jest negocjowane w ramach uwierzytelniania. W takich scenariuszach exchange potencjalnie wielu gałęzi występuje między klientem i usługi do propagowania poświadczenia usługi do klienta. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Właściwość określa, jak długo exchange wielu gałęzi może trwać do ukończenia. Jednak tego limitu czasu zastosowanie tylko w przypadku programu exchange w rzeczywistości więcej, pojedynczą odpowiedź żądania. W przypadkach, w którym negocjacji kończy w jednym obiegu limit czasu nie ma zastosowania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Instrukcje: Zestaw maksymalnego przesunięcia czasowego zegara](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
