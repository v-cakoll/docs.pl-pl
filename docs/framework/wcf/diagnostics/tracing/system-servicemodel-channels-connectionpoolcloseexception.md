---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c7a134a60656c6ee237203b69e1bce40656f13d2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException
Wystąpił wyjątek podczas zamykania połączeń z tej puli połączeń.  
  
## <a name="description"></a>Opis  
 Wskazuje śledzenia poziomu ten błąd wystąpił błąd podczas zamykania pul połączeń używanych przez [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]przez funkcję puli połączeń. Jedną z możliwych przyczyn tego jest zamknięcie połączenia z puli nie powiodło się lub zestawu puli połączeń w ramach limitu czasu zamykania. Wszystkie pozostałe niezamknięty połączenia w tej puli są przerywane, gdy ten wyjątek; niezamknięty połączeń w innych pulach zostały porzucone.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
