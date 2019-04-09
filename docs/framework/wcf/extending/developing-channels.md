---
title: Opracowywanie kanałów
ms.date: 03/30/2017
ms.assetid: 0513af9f-a0c2-457b-9a50-5b6bfee48513
ms.openlocfilehash: 1922f5158d72bc5bc443e92c6eabb28510dec0ae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175204"
---
# <a name="developing-channels"></a>Opracowywanie kanałów
Tworzenie kanału protokołu lub transportu, który może służyć za pomocą Windows Communication Foundation (WCF) w warstwie aplikacji wymaga wykonania kilku czynności. W tym temacie opisano kroki i kieruje użytkownika do określonych tematów, aby uzyskać więcej informacji. Aby poznać model kanału i różne typy, które są wymienione w tym temacie, zobacz [Przegląd modelu kanału](../../../../docs/framework/wcf/extending/channel-model-overview.md). Transport kompletny przykładowy kanału, [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md).  
  
## <a name="the-channel-development-task-list"></a>Lista zadań tworzenia kanału  
 Dostępne są następujące kroki, aby utworzyć kanał zdefiniowanych przez użytkownika. Wszystkie kanały musi:  
  
1.  Zdecyduj, które kanału wiadomości programu Exchange wzorców (<xref:System.ServiceModel.Channels.IOutputChannel>, <xref:System.ServiceModel.Channels.IInputChannel>, <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IRequestChannel>, lub <xref:System.ServiceModel.Channels.IReplyChannel>) Twojej <xref:System.ServiceModel.Channels.IChannelFactory> i <xref:System.ServiceModel.Channels.IChannelListener> będzie obsługiwać, a także czy obsługują sessionful zmiany tych interfejsów. Aby uzyskać więcej informacji, zobacz [Wybieranie platformy wymiany komunikatów](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md).  
  
2.  Tworzenie fabryki kanałów i odbiorników (<xref:System.ServiceModel.Channels.IChannelFactory> i <xref:System.ServiceModel.Channels.IChannelListener>) obsługujące usługi wymiany komunikatów. Aby uzyskać szczegółowe informacje na temat tworzenia fabryk, zobacz [klienta: Fabryki kanałów i kanały](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md). Aby uzyskać szczegółowe informacje o tworzeniu odbiorników, zobacz [usługi: Odbiorniki kanałów i kanały](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md).  
  
3.  Upewnij się, że wszystkie wyjątki dotyczące sieci są znormalizowane zgodnie z jedną <xref:System.TimeoutException?displayProperty=nameWithType> lub odpowiednie wywodzącej się klasy z <xref:System.ServiceModel.CommunicationException>. Aby uzyskać więcej informacji, zobacz [obsługi wyjątków i błędów](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
4.  Aby włączyć korzystanie z warstwy aplikacji, należy dodać <xref:System.ServiceModel.Channels.BindingElement> dodająca niestandardowym kanale stos kanału. Aby uzyskać więcej informacji, zobacz [Tworzenie elementu BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md).  
  
 Następujące dodatkowe kroki są wymagane do włączenia obsługi bardziej szczegółowy w warstwie aplikacji:  
  
1.  Dodaj sekcję rozszerzenia elementu powiązania do udostępnienia nowego elementu powiązania do konfiguracji systemu. Aby uzyskać więcej informacji, zobacz [Konfiguracja i Obsługa metadanych](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
2.  Dodaj rozszerzenia metadanych do komunikowania się funkcji innych punktów końcowych. Aby uzyskać więcej informacji, zobacz [Konfiguracja i Obsługa metadanych](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
3.  Dodaj powiązanie, które są wstępnie konfiguruje stosie elementów wiązania zgodnie z profilem dobrze zdefiniowane. Aby uzyskać więcej informacji, zobacz [powiązania Creating User-Defined](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
4.  Dodaj sekcję wiązania i element konfiguracji powiązania aby uwidocznić powiązania do systemu konfiguracji. Aby uzyskać więcej informacji, zobacz [Konfiguracja i Obsługa metadanych](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
## <a name="see-also"></a>Zobacz także

- [Rozszerzanie powiązań](../../../../docs/framework/wcf/extending/extending-bindings.md)
