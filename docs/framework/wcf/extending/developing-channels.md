---
title: Opracowywanie kanałów
ms.date: 03/30/2017
ms.assetid: 0513af9f-a0c2-457b-9a50-5b6bfee48513
ms.openlocfilehash: 8d0ecb9ea473b78dfc648a1087ae2261406f2b4f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795788"
---
# <a name="developing-channels"></a>Opracowywanie kanałów
W celu opracowania protokołu lub kanału transportowego, który może być używany z warstwą aplikacji Windows Communication Foundation (WCF), wymagane jest wykonanie kilku kroków. W tym temacie opisano kroki i punkty, w których można uzyskać więcej informacji. Aby zrozumieć model kanału i różne typy, które są opisane w tym temacie, zobacz [Omówienie modelu kanału](channel-model-overview.md). Aby uzyskać pełny przykład kanału transportowego [, zobacz Transport: UDP](../samples/transport-udp.md).  
  
## <a name="the-channel-development-task-list"></a>Lista zadań opracowywania kanału  
 Poniżej przedstawiono procedurę tworzenia kanału zdefiniowanego przez użytkownika. Wszystkie kanały muszą:  
  
1. Decydowanie o tym, które z nich są<xref:System.ServiceModel.Channels.IOutputChannel>wzorcem wymiany <xref:System.ServiceModel.Channels.IRequestChannel>komunikatów w <xref:System.ServiceModel.Channels.IReplyChannel>kanale <xref:System.ServiceModel.Channels.IChannelFactory> ( <xref:System.ServiceModel.Channels.IChannelListener> , <xref:System.ServiceModel.Channels.IInputChannel>, <xref:System.ServiceModel.Channels.IDuplexChannel>, lub), a także o tym, czy będzie on obsługiwał sesję różnice tych interfejsów. Aby uzyskać szczegółowe informacje, zobacz [Wybieranie wzorca komunikatów Exchange](choosing-a-message-exchange-pattern.md).  
  
2. Utwórz fabrykę i odbiornik kanałów (<xref:System.ServiceModel.Channels.IChannelFactory> i <xref:System.ServiceModel.Channels.IChannelListener>), które obsługują wzorzec wymiany komunikatów. Aby uzyskać szczegółowe informacje na temat tworzenia fabryk [, zobacz klient: Fabryki kanałów i kanały](client-channel-factories-and-channels.md). Aby uzyskać szczegółowe informacje na temat tworzenia [odbiorników, zobacz Usługa: Odbiorniki kanałów i](service-channel-listeners-and-channels.md)kanały.  
  
3. Upewnij się, że wszystkie wyjątki specyficzne dla sieci są znormalizowane do <xref:System.TimeoutException?displayProperty=nameWithType> albo do odpowiedniej <xref:System.ServiceModel.CommunicationException>klasy pochodnej. Aby uzyskać szczegółowe informacje, zobacz temat [Obsługa wyjątków i błędów](handling-exceptions-and-faults.md).  
  
4. Aby umożliwić użycie z warstwy aplikacji, Dodaj dodanie <xref:System.ServiceModel.Channels.BindingElement> kanału niestandardowego do stosu kanału. Aby uzyskać więcej informacji, zobacz [Tworzenie BindingElement](creating-a-bindingelement.md).  
  
 Następujące dodatkowe kroki są wymagane, aby zapewnić pełniejszą obsługę w warstwie aplikacji:  
  
1. Dodaj sekcję rozszerzenie elementu powiązania, aby udostępnić nowy element powiązania do systemu konfiguracji. Aby uzyskać więcej informacji, zobacz temat [Obsługa konfiguracji i metadanych](configuration-and-metadata-support.md).  
  
2. Dodaj rozszerzenia metadanych, aby komunikować możliwości z innymi punktami końcowymi. Aby uzyskać więcej informacji, zobacz temat [Obsługa konfiguracji i metadanych](configuration-and-metadata-support.md).  
  
3. Dodaj powiązanie, które wstępnie konfiguruje stos elementów powiązania zgodnie z dobrze zdefiniowanym profilem. Aby uzyskać więcej informacji, zobacz [Tworzenie powiązań zdefiniowanych przez użytkownika](creating-user-defined-bindings.md).  
  
4. Dodaj sekcję powiązania i element konfiguracji powiązania, aby uwidocznić powiązanie z systemem konfiguracji. Aby uzyskać więcej informacji, zobacz temat [Obsługa konfiguracji i metadanych](configuration-and-metadata-support.md).  
  
## <a name="see-also"></a>Zobacz także

- [Rozszerzanie powiązań](extending-bindings.md)
