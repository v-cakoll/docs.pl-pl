---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: 0a312d192546655dc327667c00f4f2bbc0c15fdb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602053"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException
Wystąpił wyjątek podczas zamykania połączeń z tej puli połączeń.  
  
## <a name="description"></a>Opis  
 Ten ślad poziomu błędu wskazuje, że wystąpił błąd podczas zamykania pul połączeń używanych przez funkcję puli połączeń Windows Communication Foundation (WCF). Jedną z możliwych przyczyn jest to nieudane zamknięcie połączenia w puli lub zestaw połączeń w puli w ramach CloseTimeout. Gdy ten wyjątek jest zgłaszany, wszystkie pozostałe niezamknięte połączenia w tej puli są przerywane; niezamknięte połączenia w innych pulach są porzucane.  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](using-tracing-to-troubleshoot-your-application.md)
- [Administracja i Diagnostyka](../index.md)
