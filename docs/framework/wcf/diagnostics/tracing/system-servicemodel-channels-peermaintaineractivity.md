---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: ea4c8110a8f820e0c6204fbd22b3d5b747709fba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59126038"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a>System.ServiceModel.Channels.PeerMaintainerActivity
Moduł PeerMaintainer wykonuje określoną operację (szczegóły zawartych w treści komunikatu śledzenia).  
  
## <a name="description"></a>Opis  
 Ślad występuje podczas wykonywania różnych operacji PeerMaintainer.  
  
 PeerMaintainer jest składnikiem wewnętrznego węzeł równorzędny. Co minutę lub co 32 komunikaty odbierane, wysyła wiadomość LinkUtility dla swoich sąsiadów ze statystykami o ile komunikaty są wymieniane i ile są przydatne (innych niż duplikatów, untampered). Dzięki temu można ustalić określonego sąsiada łącze narzędzia. Co około pięciu minut, Element utrzymujący sprawdza kondycję sąsiada połączeń. Jeśli liczba połączeń sąsiada przekracza kwotę idealne, Element utrzymujący oczyszcza off najmniej przydatne połączeń. Jeśli nie ma wystarczającej liczby połączeń, Element utrzymujący uzyskuje nowe połączenia.  
  
## <a name="see-also"></a>Zobacz także

- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
