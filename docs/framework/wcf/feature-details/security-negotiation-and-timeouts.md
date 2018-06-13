---
title: Negocjacje i limity czasu dotyczące zabezpieczeń
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 508d648acf148f13076327bb312d0a0b08471ac1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497467"
---
# <a name="security-negotiation-and-timeouts"></a>Negocjacje i limity czasu dotyczące zabezpieczeń
Podczas uwierzytelniania klientów i usług, Windows Communication Foundation (WCF) obsługuje tryb, w którym poświadczenia usługi jest negocjowanych w ramach uwierzytelniania. W takich scenariuszach exchange potencjalnie wieloetapowego występuje między klientem a usługa propagacji poświadczenie usługi do klienta. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> Właściwość określa, jak długo exchange wieloetapowego może trwać do wykonania. Jednak tego limitu czasu tylko w przypadku programu exchange w rzeczywistości więcej który pojedynczą żądanie odpowiedź. W przypadkach, gdy negocjacji kończy w jednej Rundy limitu czasu nie ma zastosowania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [Instrukcje: ustawianie maksymalnego przesunięcia czasowego zegara](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
