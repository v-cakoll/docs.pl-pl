---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d3919e48925eeb0d197c23da582836dec5bf6438
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a>System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
Szybkość odbierania przychodzących komunikatów jest zbyt duży.  
  
## <a name="description"></a>Opis  
 Ślad występuje podczas próby przetworzenia wiadomości przychodzących. Nie można przesłać dalej wiadomości do określonych sąsiada, ponieważ przekroczono limit przydziału określony dla tego sąsiada. Dzieje się tak w przypadku niepowodzenia wyczyść zaległości komunikatów oczekujących dla tego sąsiada sąsiada nie odpowiada.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Zmniejsz szybkość, z jaką komunikaty wewnątrz siatki.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i Diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
