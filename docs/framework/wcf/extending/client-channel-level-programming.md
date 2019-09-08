---
title: Programowanie na poziomie kanału klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
ms.openlocfilehash: 4f24c558b1d5303b2417416beb14555539f498ea
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797268"
---
# <a name="client-channel-level-programming"></a>Programowanie na poziomie kanału klienta
W tym temacie opisano sposób pisania aplikacji klienckiej programu Windows Communication Foundation (WCF) bez użycia <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> klasy i skojarzonego z nią modelu obiektów.  
  
## <a name="sending-messages"></a>Wysyłanie komunikatów  
 Aby można było wysyłać wiadomości i odbierać i przetwarzać odpowiedzi, wymagane są następujące kroki:  
  
1. Utwórz powiązanie.  
  
2. Kompiluj fabrykę kanałów.  
  
3. Utwórz kanał.  
  
4. Wyślij żądanie i przeczytaj odpowiedź.  
  
5. Zamknij wszystkie obiekty kanału.  
  
#### <a name="creating-a-binding"></a>Tworzenie powiązania  
 Podobnie jak w przypadku odbioru (zobacz [Programowanie na poziomie kanału usługi](service-channel-level-programming.md)), wysyłanie komunikatów zaczyna się od utworzenia powiązania. Ten przykład tworzy nowe <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> dodaje do kolekcji elementów.  
  
#### <a name="building-a-channelfactory"></a>Kompilowanie elementu ChannelFactory  
 Zamiast tworzenia <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, ten czas <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> tworzymy, wywołując <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> na powiązanie, gdzie parametr typu jest <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>. Gdy Odbiorniki kanałów są używane po stronie, które czekają na komunikaty przychodzące, fabryki kanałów są używane przez stronę, która inicjuje komunikację w celu utworzenia kanału. Podobnie jak w przypadku odbiorników kanału należy najpierw otworzyć fabryki kanałów przed ich użyciem.  
  
#### <a name="creating-a-channel"></a>Tworzenie kanału  
 Następnie wywołajmy <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> , aby <xref:System.ServiceModel.Channels.IRequestChannel>utworzyć. To wywołanie Pobiera adres punktu końcowego, z którym chcemy się komunikować przy użyciu nowego tworzonego kanału. Gdy będziemy korzystać z kanału, dzwonimy na niego, aby przygotować go w stanie gotowym do komunikacji. W zależności od rodzaju transportu to wywołanie do otwarcia może inicjować połączenie z docelowym punktem końcowym lub w ogóle nie ma nic w sieci.  
  
#### <a name="sending-a-request-and-reading-the-reply"></a>Wysyłanie żądania i odczytywanie odpowiedzi  
 Po otwarciu kanału można utworzyć komunikat i użyć metody żądania kanału, aby wysłać żądanie i poczekać na powrót odpowiedzi. Po powrocie tej metody mamy komunikat odpowiedzi, który możemy przeczytać, aby dowiedzieć się, co to jest odpowiedź punktu końcowego.  
  
#### <a name="closing-objects"></a>Zamykanie obiektów  
 Aby uniknąć przecieków zasobów, należy zamknąć obiekty używane w komunikacji, gdy nie są już wymagane.  
  
 Poniższy przykład kodu pokazuje klienta podstawowego przy użyciu fabryki kanałów do wysyłania wiadomości i odczytywania odpowiedzi.  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
