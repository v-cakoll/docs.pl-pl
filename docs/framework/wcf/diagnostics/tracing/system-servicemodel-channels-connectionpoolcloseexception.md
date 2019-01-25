---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: b2d49910ecbcd67beca83e2fbeabfbcafe6e1dd0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628035"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException
Wystąpił wyjątek podczas zamykania połączenia w tej puli połączeń.  
  
## <a name="description"></a>Opis  
 Śledzenie poziomu ten błąd wskazuje, wystąpił błąd podczas zamykania pul połączeń używane przez funkcję buforowanie połączenia z programem Windows Communication Foundation (WCF) firmy. Jedną z możliwych przyczyn tego jest powiodło się zamknięcie połączenia z puli lub zbiór puli połączeń w ramach CloseTimeout. Gdy ten wyjątek jest zgłaszany, wszystkie pozostałe zamknięto połączenia w tej puli zostaną przerwane; Zamknięto połączenia w innych pulach są porzucona.  
  
## <a name="see-also"></a>Zobacz także
- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
