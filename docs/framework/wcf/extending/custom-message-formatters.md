---
title: Niestandardowe elementy formatujące komunikaty
ms.date: 03/30/2017
ms.assetid: c07435f3-5214-4791-8961-2c2b61306d71
ms.openlocfilehash: af1596c65fc87a68bc3dc2ab5ab2d82133e0fed4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196245"
---
# <a name="custom-message-formatters"></a>Niestandardowe elementy formatujące komunikaty
Zawartość komunikatu jest często w formacie XML, który zwykle nie jest to wygodne format dla aplikacji. Aplikacje manipulowania obiektami, pobierania i ustawiania ich właściwości. Windows Communication Foundation (WCF) używa *kontraktu danych* przekonwertować <xref:System.ServiceModel.Channels.Message> obiektu do obiektu może z łatwością obsłużyć przez aplikację. Procesy te są nazywane serializacji i deserializacji. Należy pamiętać, że tych samych warunkach są używane do opisywania serializacji i deserializacji, wykonywane przez warstwy transportowej do i z formatu o komunikacji sieciowej komunikat, który jest procesem niepowiązanych.  
  
 Możesz użyć programu formatującego niestandardowy komunikat, jeśli musisz wdrożyć wyspecjalizowane konwersji między komunikatów i obiekty, które nie można wykonać za pomocą kontraktu danych. W tym celu modyfikowania i rozszerzania zachowanie wykonania operacji konkretnej umowy, na kliencie lub usługi.  
  
## <a name="custom-message-formatters-on-the-client"></a>Niestandardowe elementy formatujące komunikaty na komputerze klienckim  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Interfejs definiuje metody, które są używane w celu kontroli konwersji wiadomości do obiektów i obiektów do wiadomości dla aplikacji klienckich.  
  
 Musisz zaimplementować ten interfejs. Najpierw Zastąp <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> metodę deserializacji komunikatu. Ta metoda jest wywoływana po otrzymaniu wiadomości przychodzących, ale przed jest wysyłany do operacji klienta.  
  
 Następnie zastąp <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> metody do serializacji obiektu. Ta metoda jest wywoływana przed wysłaniem wiadomości wychodzących.  
  
 Aby wstawić niestandardowego elementu formatującego do aplikacji usługi, należy przypisać <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> obiekt <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> właściwości przy użyciu operacji zachowanie. Aby uzyskać informacje na temat działania, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="custom-message-formatters-on-the-service"></a>Niestandardowe elementy formatujące komunikaty w usłudze  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> Interfejs definiuje metody, które konwertują <xref:System.ServiceModel.Channels.Message> obiektu do parametrów operacji i parametrów w <xref:System.ServiceModel.Channels.Message> obiektu w aplikacji usługi.  
  
 Musisz zaimplementować ten interfejs. Najpierw Zastąp <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> metodę deserializacji komunikatu. Ta metoda jest wywoływana po otrzymaniu wiadomości przychodzących, ale przed jest wysyłany do operacji klienta.  
  
 Następnie zastąp <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> metody do serializacji obiektu. Ta metoda jest wywoływana przed wysłaniem wiadomości wychodzących.  
  
 Aby wstawić niestandardowego elementu formatującego do aplikacji usługi, należy przypisać <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> obiekt <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> właściwości przy użyciu operacji zachowanie. Aby uzyskać informacje na temat działania, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>
- [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
