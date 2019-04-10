---
title: Programowanie na poziomie kanału klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
ms.openlocfilehash: ea56c99d7d122dd20fc217f8ecb2937bcf81bec3
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324136"
---
# <a name="client-channel-level-programming"></a>Programowanie na poziomie kanału klienta
W tym temacie opisano sposób pisania aplikacji klienckiej Windows Communication Foundation (WCF) bez użycia <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> klasy i jego skojarzonego obiektu modelu.  
  
## <a name="sending-messages"></a>Wysyłanie wiadomości  
 Gotowość wysyłać i odbierać i przetwarzać odpowiedzi, wymagane są następujące kroki:  
  
1. Tworzenie powiązania.  
  
2. Tworzenie fabryki kanałów.  
  
3. Utwórz kanał.  
  
4. Wyślij żądanie i odpowiedź do odczytu.  
  
5. Zamknij wszystkie obiekty kanału.  
  
#### <a name="creating-a-binding"></a>Tworzenie powiązania  
 Podobnie jak w przypadku odbieranego (zobacz [programowania na poziomie kanału usługi](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), wysyłanie komunikatów rozpoczyna się przez utworzenie powiązania. W tym przykładzie tworzy nowy <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> i dodaje <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> do swojej kolekcji elementów.  
  
#### <a name="building-a-channelfactory"></a>Tworzenie elementu ChannelFactory  
 Zamiast tworzyć <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, tym razem możemy utworzyć <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> przez wywołanie metody <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> w powiązaniu, gdzie parametr typu jest <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>. Odbiorniki kanałów są używane przez stronę, która czeka na komunikaty przychodzące, fabryki kanałów są używane przez strony, która inicjuje komunikację, próba utworzenia kanału. Podobnie jak odbiorniki kanałów fabryki kanałów najpierw należy otworzyć zanim będzie można ich użyć.  
  
#### <a name="creating-a-channel"></a>Tworzenie kanału  
 Następnie wywołaj <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> utworzyć <xref:System.ServiceModel.Channels.IRequestChannel>. To wywołanie pobiera adres punktu końcowego za pomocą którego chcemy, aby komunikować się za pomocą nowego kanału tworzona. Gdy będziemy już mieć kanał, nazywamy otwórz go, aby umieścić ją w stanie gotowy do komunikacji. W zależności od charakteru transportu tego wywołania do otworzenia może zainicjować połączenia z punktem końcowym docelowego lub mogą nic w ogóle w sieci.  
  
#### <a name="sending-a-request-and-reading-the-reply"></a>Wysyłanie żądania i odpowiedzi do czytania  
 Gdy będziemy już mieć otwarty kanał, firma Microsoft Utwórz wiadomość, a następnie wysłać żądanie i oczekiwania na odpowiedź, aby wrócić do tego za pomocą metody żądania tego kanału. Gdy metoda zwróci wartość, mamy komunikat odpowiedzi, który firma Microsoft może odczytać, aby dowiedzieć się, jaka była odpowiedzi punktu końcowego.  
  
#### <a name="closing-objects"></a>Zamykanie obiektów  
 Aby uniknąć wyciek zasobów, możemy zamknąć obiekty używane podczas komunikacji, gdy nie są już wymagane.  
  
 Poniższy przykład kodu pokazuje podstawowe klienta za pomocą fabryki kanałów, aby wysłać wiadomość i odczytać odpowiedzi.  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
