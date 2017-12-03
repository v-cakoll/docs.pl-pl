---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1bbad8d743ff64aea923e7fbf62871e495253aea
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a>System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
Nie można odebrać wiadomości kanałem HTTP.  
  
## <a name="description"></a>Opis  
 Ślad może być wysyłany jako ostrzeżenia lub błędu. W obu przypadkach dane śledzenia są emitowane po zgodne odbiornik nie został znaleziony dla przychodzącego żądania HTTP i żądania HTTP są usuwane. Może się to zdarzyć, ponieważ zlecenie HTTP żądania nie został rozpoznany przez dowolnego odbiornik HTTP lub ponieważ odbiornik nie nasłuchuje na adresie żądania był przeznaczony dla. Śledzenie jest emitowany jako ostrzeżenia w przypadku hostowania samoobsługowego i jako błąd, kiedy usługa znajduje się w usługach IIS.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i Diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
