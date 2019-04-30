---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.date: 03/30/2017
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
ms.openlocfilehash: b848963caff706ff8a886c1e358ad6688e9611c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666693"
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a>System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
Nie może odebrać komunikatu za pośrednictwem kanału protokołu HTTP.  
  
## <a name="description"></a>Opis  
 Ślad może być emitowana jako ostrzeżenia lub błędu. W obu przypadkach śledzenia jest emitowane, gdy nie znaleziono niezgodny odbiornik dla przychodzących żądań HTTP i odrzucenia żądania HTTP. Może się to zdarzyć, ponieważ czasownik HTTP żądania nie został rozpoznany przez dowolnego odbiornika protokołu HTTP lub ponieważ brak odbiornika prowadził nasłuchiwanie na adresie żądania był przeznaczony dla. Śledzenia jest emitowane ostrzeżenie w przypadku Self-Hosted, jak i błąd, gdy usługa jest hostowana w usługach IIS.  
  
## <a name="see-also"></a>Zobacz także

- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
