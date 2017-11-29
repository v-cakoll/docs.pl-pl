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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f3cde90bf5e9c57ff54378eaaf970aec219871a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
