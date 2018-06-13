---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: a7f353b00796c845f5686ca2926bbe7effe09e3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33480587"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a>System.ServiceModel.Channels.PeerMaintainerActivity
Moduł PeerMaintainer wykonuje określonej operacji (szczegółowe informacje zawarte w treści wiadomości śledzenia).  
  
## <a name="description"></a>Opis  
 Ślad występuje w ciągu różne operacje PeerMaintainer.  
  
 PeerMaintainer jest to wewnętrzny składnik węzeł równorzędny. Co minutę lub co 32 komunikatów odebranych, wysyła wiadomość LinkUtility z jej sąsiadami dane statystyczne o ile komunikatów są wymieniane i ile są przydatne (z systemem innym niż — duplikatów, untampered). Dzięki temu można ustalić określonego sąsiada łącze narzędzia. Co około pięciu minut, Element utrzymujący sprawdza stan sąsiedniego połączenia. Jeśli liczba połączeń sąsiada przekracza wielkość idealne, Element utrzymujący oczyszcza poza przydatne najmniej połączeń. Jeśli nie ma wystarczającej liczby połączeń, Element utrzymujący uzyskuje nowe połączenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
