---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.date: 03/30/2017
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
ms.openlocfilehash: f79f5703c621951029f3e7f6a36a3d0ebeca58a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a>System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
Nie można odebrać wiadomości kanałem HTTP.  
  
## <a name="description"></a>Opis  
 Ślad może być wysyłany jako ostrzeżenia lub błędu. W obu przypadkach dane śledzenia są emitowane po zgodne odbiornik nie został znaleziony dla przychodzącego żądania HTTP i żądania HTTP są usuwane. Może się to zdarzyć, ponieważ zlecenie HTTP żądania nie został rozpoznany przez dowolnego odbiornik HTTP lub ponieważ odbiornik nie nasłuchuje na adresie żądania był przeznaczony dla. Śledzenie jest emitowany jako ostrzeżenia w przypadku hostowania samoobsługowego i jako błąd, kiedy usługa znajduje się w usługach IIS.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
