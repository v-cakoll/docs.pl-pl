---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: 3ce6b3021f47708c222c3ec5a88d474d17106748
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500996"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a>System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
Szybkość odbierania przychodzących komunikatów jest zbyt wysoka.  
  
## <a name="description"></a>Opis  
 Ślad występuje podczas próby przetworzenia przychodzących komunikatów. Nie można przesłać dalej wiadomość do określonych sąsiada, ponieważ przekroczono limit przydziału, ustaw dla tej sąsiada. Dzieje się tak, gdy sąsiada nie odpowiada nie powiedzie się wyczyścić zaległości komunikatów oczekujących dla tego sąsiada.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Zmniejsz szybkość jaką komunikaty są wysyłane w obrębie siatki.  
  
## <a name="see-also"></a>Zobacz także
- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
