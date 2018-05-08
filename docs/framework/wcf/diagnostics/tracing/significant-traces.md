---
title: Ważne ślady
ms.date: 03/30/2017
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
ms.openlocfilehash: 2dc5010874285ba14dae625fcbf92740eb1707b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="significant-traces"></a>Ważne ślady
W tym temacie wymieniono niektóre główne śledzenia emitowane przez Windows Communication Foundation (WCF).  
  
## <a name="significant-traces"></a>Ważne ślady  
  
|śledzenia|Opis|  
|-----------|-----------------|  
|Komunikat dziennika śledzenia|Śledzenie jest emitowany podczas [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] jest rejestrowany przez rejestrowanie komunikatów funkcji podczas `System.ServiceModel.MessageLogging` źródła śledzenia jest włączona. Kliknięcie tego śledzenia powoduje wyświetlenie komunikatu. Istnieją cztery punkty można skonfigurować rejestrowanie wiadomości: `ServiceLevelSendRequest`, `TransportSend`, `TransportReceive`, `ServiceLevelReceiveRequest`, również wskazane przez atrybut źródła wiadomości w wiadomości dziennika śledzenia.|  
|Odebrano komunikat śledzenia|Ślad jest emitowany podczas [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] wiadomość zostanie odebrana, jeśli `System.ServiceModel` źródła śledzenia jest włączona na poziomie pełne lub informacji. Ślad jest niezbędne wyświetlić strzałkę korelacji wiadomości w widoku wykresu działań.|  
|Wysłano wiadomość śledzenia|Ślad jest emitowany podczas [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] jest wysyłany komunikat, jeśli `System.ServiceModel` źródła śledzenia jest włączona na poziomie pełne lub informacji. Ślad jest niezbędne wyświetlić strzałkę korelacji wiadomości w widoku wykresu działań.|  
|Uzyskiwanie elementu ChannelEndpointElement|Ślad są emitowane w konstrukcji fabryki kanałów, na poziomie informacji. Zapewnia ona rozmawia opis punktu końcowego klienta (adresu zdalnego, powiązanie, Nazwa kontraktu).|  
|Uzyskiwanie elementu ServiceElement|Ślad są emitowane w konstrukcji hosta usługi, na poziomie informacji. Zawiera on opis kontraktu usługi i powiązania.|  
|Utwórz połączenie SocketConnection poprzez|Ślad są emitowane w pierwszej procesu akcji wykonywanych przez klienta i działanie Receive bajtów w usłudze. Zapewnia lokalnych i zdalnych adresów IP. Jest on wyemitowany na poziomie informacji.|
