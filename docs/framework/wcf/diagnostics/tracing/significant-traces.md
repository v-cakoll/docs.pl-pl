---
title: "Ważne ślady"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6641fe633585caf6cbf068a804430f9171e5ece0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="significant-traces"></a>Ważne ślady
W tym temacie wymieniono niektóre główne śledzenia emitowane przez [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  
  
## <a name="significant-traces"></a>Ważne ślady  
  
|śledzenia|Opis|  
|-----------|-----------------|  
|Komunikat dziennika śledzenia|Śledzenie jest emitowany podczas [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] jest rejestrowany przez rejestrowanie komunikatów funkcji podczas `System.ServiceModel.MessageLogging` źródła śledzenia jest włączona. Kliknięcie tego śledzenia powoduje wyświetlenie komunikatu. Istnieją cztery punkty można skonfigurować rejestrowanie wiadomości: `ServiceLevelSendRequest`, `TransportSend`, `TransportReceive`, `ServiceLevelReceiveRequest`, również wskazane przez atrybut źródła wiadomości w wiadomości dziennika śledzenia.|  
|Odebrano komunikat śledzenia|Ślad jest emitowany podczas [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] wiadomość zostanie odebrana, jeśli `System.ServiceModel` źródła śledzenia jest włączona na poziomie pełne lub informacji. Ślad jest niezbędne wyświetlić strzałkę korelacji wiadomości w widoku wykresu działań.|  
|Wysłano wiadomość śledzenia|Ślad jest emitowany podczas [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] jest wysyłany komunikat, jeśli `System.ServiceModel` źródła śledzenia jest włączona na poziomie pełne lub informacji. Ślad jest niezbędne wyświetlić strzałkę korelacji wiadomości w widoku wykresu działań.|  
|Uzyskiwanie elementu ChannelEndpointElement|Ślad są emitowane w konstrukcji fabryki kanałów, na poziomie informacji. Zapewnia ona rozmawia opis punktu końcowego klienta (adresu zdalnego, powiązanie, Nazwa kontraktu).|  
|Uzyskiwanie elementu ServiceElement|Ślad są emitowane w konstrukcji hosta usługi, na poziomie informacji. Zawiera on opis kontraktu usługi i powiązania.|  
|Utwórz połączenie SocketConnection poprzez|Ślad są emitowane w pierwszej procesu akcji wykonywanych przez klienta i działanie Receive bajtów w usłudze. Zapewnia lokalnych i zdalnych adresów IP. Jest on wyemitowany na poziomie informacji.|
