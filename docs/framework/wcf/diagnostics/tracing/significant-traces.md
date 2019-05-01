---
title: Ważne ślady
ms.date: 03/30/2017
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
ms.openlocfilehash: c230c65b4d3fd45c4905d4ae5f4cbbf90e10faad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784964"
---
# <a name="significant-traces"></a>Ważne ślady
W tym temacie przedstawiono niektóre z najważniejszych danych śledzenia emitowane przez Windows Communication Foundation (WCF).  
  
## <a name="significant-traces"></a>Ważne ślady  
  
|Śledzenia|Opis|  
|-----------|-----------------|  
|Śledzenie dziennika komunikatów|Śledzenia jest emitowane po wiadomości WCF jest rejestrowane przez rejestrowanie komunikatów funkcji podczas `System.ServiceModel.MessageLogging` źródła śledzenia jest włączona. Kliknięcie tego śledzenia wyświetla komunikat. Istnieją cztery punkty rejestrowania można skonfigurować wiadomości: `ServiceLevelSendRequest`, `TransportSend`, `TransportReceive`, `ServiceLevelReceiveRequest`, również wskazane przez atrybut źródło komunikatu w śladzie dziennik komunikatów.|  
|Odebrano komunikat śledzenia|Ta śledzenia jest emitowane po odebraniu wiadomości WCF, jeśli `System.ServiceModel` źródła śledzenia jest włączona na poziomie pełne lub informacji. Ślad jest strzałką korelacji wiadomości w widoku wykresu aktywności.|  
|Śledzenie komunikatów wysyłanych|Ślad jest emitowane po wysłaniu wiadomości WCF, jeśli `System.ServiceModel` źródła śledzenia jest włączona na poziomie pełne lub informacji. Ślad jest strzałką korelacji wiadomości w widoku wykresu aktywności.|  
|Get ChannelEndpointElement|Ta śledzenia jest emitowane w konstrukcji fabryki kanałów, na poziomie informacji. Zapewnia ona opis punktu końcowego klient rozmawia (adresów zdalnych, powiązanie, Nazwa kontraktu).|  
|Uzyskiwanie elementu ServiceElement|Ta śledzenia jest emitowane w konstrukcji hosta usługi na poziomie informacji. Zawiera on opis kontraktu usługi i powiązania.|  
|Utworzenie połączenia SocketConnection|Ta śledzenia jest emitowane w pierwszej akcji przetwarzania wykonywane przez klienta i działania bajtów przyjęcie w usłudze. Zapewnia lokalnych i zdalnych adresów IP. Jest on emitowane na poziomie informacji.|
