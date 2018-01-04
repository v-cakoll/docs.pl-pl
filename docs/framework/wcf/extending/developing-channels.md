---
title: "Opracowywanie kanałów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0513af9f-a0c2-457b-9a50-5b6bfee48513
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 42c89ae71078a3ddfbe7e85273a6f62879781c80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="developing-channels"></a>Opracowywanie kanałów
Aby opracować protokołu lub transportu kanału, który może być używany z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] warstwy aplikacji wymaga podjęcia kilku czynności. W tym temacie opisano te kroki i kieruje użytkownika do określonych tematów, aby uzyskać więcej informacji. Aby poznać model kanału i różne typy, które są wymienione w tym temacie, zobacz [Przegląd modelu kanału](../../../../docs/framework/wcf/extending/channel-model-overview.md). Przykładowy kanał transportu pełną, [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md).  
  
## <a name="the-channel-development-task-list"></a>Lista zadań rozwoju kanału  
 Dostępne są następujące kroki, aby utworzyć kanał zdefiniowane przez użytkownika. Wszystkie kanały muszą:  
  
1.  Decyzji, które kanał wzorce wymiany wiadomości (<xref:System.ServiceModel.Channels.IOutputChannel>, <xref:System.ServiceModel.Channels.IInputChannel>, <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IRequestChannel>, lub <xref:System.ServiceModel.Channels.IReplyChannel>) z <xref:System.ServiceModel.Channels.IChannelFactory> i <xref:System.ServiceModel.Channels.IChannelListener> będzie obsługiwać, a także czy obsługują sessionful zmiany tych interfejsów. Aby uzyskać więcej informacji, zobacz [Wybieranie platformy wymiany komunikatów](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md).  
  
2.  Tworzenie fabryki kanału i odbiornika (<xref:System.ServiceModel.Channels.IChannelFactory> i <xref:System.ServiceModel.Channels.IChannelListener>) obsługujących Twoje wymiany komunikatów. Aby uzyskać więcej informacji o tworzeniu fabryki, zobacz [klienta: fabryk kanałów i kanały](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md). Aby uzyskać więcej informacji o tworzeniu odbiorników, zobacz [Usługa: odbiorniki kanałów i kanały](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md).  
  
3.  Upewnij się, że wszelkie wyjątki dotyczące sieci są normalized jednej <xref:System.TimeoutException?displayProperty=nameWithType> lub odpowiedniej klasy pochodne <xref:System.ServiceModel.CommunicationException>. Aby uzyskać więcej informacji, zobacz [obsługi wyjątków i błędów](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
4.  Aby włączyć korzystanie z warstwy aplikacji, należy dodać <xref:System.ServiceModel.Channels.BindingElement> dodaje niestandardowym kanale stos kanału. Aby uzyskać więcej informacji, zobacz [Tworzenie elementu BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md).  
  
 Dodatkowe kroki są wymagane do włączenia obsługi bardziej szczegółowy w warstwie aplikacji:  
  
1.  Dodaj sekcję rozszerzenia elementu powiązania do udostępnienia element powiązania do konfiguracji systemu. Aby uzyskać więcej informacji, zobacz [Konfiguracja i Obsługa metadanych](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
2.  Dodawanie rozszerzeń metadanych do komunikowania się funkcji do innych punktów końcowych. Aby uzyskać więcej informacji, zobacz [Konfiguracja i Obsługa metadanych](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
3.  Dodaj powiązanie, które wstępnie konfiguruje stos elementy wiązania zgodnie z dobrze zdefiniowanego profilu. Aby uzyskać więcej informacji, zobacz [powiązania Creating User-Defined](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
4.  Dodaj powiązanie sekcji i elementu konfiguracji powiązania do udostępnienia powiązania system konfiguracji. Aby uzyskać więcej informacji, zobacz [Konfiguracja i Obsługa metadanych](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie powiązań](../../../../docs/framework/wcf/extending/extending-bindings.md)
