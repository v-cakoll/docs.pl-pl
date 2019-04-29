---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: 3dd28276cd3a39497c0387f5b9d0adec23d07c37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666836"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException
Wystąpił wyjątek podczas zamykania połączenia w tej puli połączeń.  
  
## <a name="description"></a>Opis  
 Śledzenie poziomu ten błąd wskazuje, wystąpił błąd podczas zamykania pul połączeń używane przez funkcję buforowanie połączenia z programem Windows Communication Foundation (WCF) firmy. Jedną z możliwych przyczyn tego jest powiodło się zamknięcie połączenia z puli lub zbiór puli połączeń w ramach CloseTimeout. Gdy ten wyjątek jest zgłaszany, wszystkie pozostałe zamknięto połączenia w tej puli zostaną przerwane; Zamknięto połączenia w innych pulach są porzucona.  
  
## <a name="see-also"></a>Zobacz także

- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
