---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.date: 03/30/2017
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
ms.openlocfilehash: 93afa0b495e20c02c58ac1fa75c31715eaa0e8dc
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596093"
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a>System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
Szybkość odbierania komunikatów przychodzących jest zbyt wysoka.  
  
## <a name="description"></a>Opis  
 Ten ślad występuje podczas próby przetworzenia komunikatów przychodzących. Nie można przesłać komunikatu do określonego sąsiada, ponieważ został przekroczony limit przydziału ustawiony dla tego sąsiada. Dzieje się tak, gdy nieodpowiadający sąsiad nie może wyczyścić zaległości komunikatów oczekujących dla tego sąsiada.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Zmniejsz szybkość, z jaką komunikaty są wysyłane w obrębie siatki.  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](using-tracing-to-troubleshoot-your-application.md)
- [Administracja i Diagnostyka](../index.md)
