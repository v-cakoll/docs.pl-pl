---
title: Negocjacje i limity czasu dotyczące zabezpieczeń
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: 1b5fb15b4ea00ba33b741c96bcb423aefe9890fa
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601000"
---
# <a name="security-negotiation-and-timeouts"></a>Negocjacje i limity czasu dotyczące zabezpieczeń
Po uwierzytelnieniu klientów i usług Windows Communication Foundation (WCF) obsługuje tryb, w którym poświadczenia usługi są negocjowane w ramach uwierzytelniania. W takich scenariuszach potencjalnie wymiana wieloetapowa odbywa się między klientem a usługą w celu propagowania poświadczeń usługi do klienta programu. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A>Właściwość określa, jak długo można wykonać wymianę Wieloetapową. Jednak ten limit czasu ma zastosowanie tylko wtedy, gdy program Exchange rzeczywiście pobiera więcej z pojedynczej odpowiedzi na żądanie. W przypadkach, gdy negocjowanie kończy się pojedynczym rejsem, limit czasu nie ma zastosowania.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Instrukcje: ustawianie maksymalnego przesunięcia czasowego zegara](how-to-set-a-max-clock-skew.md)
