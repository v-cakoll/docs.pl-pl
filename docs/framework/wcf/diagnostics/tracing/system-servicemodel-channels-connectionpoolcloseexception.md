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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0ea98388efe14ac0d18a94ec056a441096a4d7c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException
Wystąpił wyjątek podczas zamykania połączeń z tej puli połączeń.  
  
## <a name="description"></a>Opis  
 Wskazuje śledzenia poziomu ten błąd wystąpił błąd podczas zamykania pul połączeń używanych przez [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]przez funkcję puli połączeń. Jedną z możliwych przyczyn tego jest zamknięcie połączenia z puli nie powiodło się lub zestawu puli połączeń w ramach limitu czasu zamykania. Wszystkie pozostałe niezamknięty połączenia w tej puli są przerywane, gdy ten wyjątek; niezamknięty połączeń w innych pulach zostały porzucone.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i Diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
