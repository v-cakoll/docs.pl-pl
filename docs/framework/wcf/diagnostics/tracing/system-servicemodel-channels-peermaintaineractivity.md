---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71bcb16b89934f7f04cfd7d2f3c4b0ef3009dd78
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a>System.ServiceModel.Channels.PeerMaintainerActivity
Moduł PeerMaintainer wykonuje określonej operacji (szczegółowe informacje zawarte w treści wiadomości śledzenia).  
  
## <a name="description"></a>Opis  
 Ślad występuje w ciągu różne operacje PeerMaintainer.  
  
 PeerMaintainer jest to wewnętrzny składnik węzeł równorzędny. Co minutę lub co 32 komunikatów odebranych, wysyła wiadomość LinkUtility z jej sąsiadami dane statystyczne o ile komunikatów są wymieniane i ile są przydatne (z systemem innym niż — duplikatów, untampered). Dzięki temu można ustalić określonego sąsiada łącze narzędzia. Co około pięciu minut, Element utrzymujący sprawdza stan sąsiedniego połączenia. Jeśli liczba połączeń sąsiada przekracza wielkość idealne, Element utrzymujący oczyszcza poza przydatne najmniej połączeń. Jeśli nie ma wystarczającej liczby połączeń, Element utrzymujący uzyskuje nowe połączenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i Diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
