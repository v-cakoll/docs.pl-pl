---
title: "Programowanie na poziomie kanału klienta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c3d9bc1819045c8261f003cbab52dd71c4da408
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="client-channel-level-programming"></a>Programowanie na poziomie kanału klienta
W tym temacie opisano sposób zapisania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji klienckiej bez użycia <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> klasy i jego skojarzony obiekt modelu.  
  
## <a name="sending-messages"></a>Wysyłanie wiadomości  
 Aby mógł wysyłać i odbierać i przetwarzać odpowiedzi, wymagane są następujące kroki:  
  
1.  Utwórz powiązanie.  
  
2.  Tworzenie fabryki kanałów.  
  
3.  Tworzenie kanału.  
  
4.  Wyślij żądanie i odpowiedź do odczytu.  
  
5.  Zamknij wszystkie obiekty kanału.  
  
#### <a name="creating-a-binding"></a>Tworzenie powiązania  
 Podobnie jak w przypadku odbierania (zobacz [programowania na poziomie kanału usługi](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), wysyłanie wiadomości rozpoczyna się przez utworzenie powiązania. Tworzy nową klasę w tym przykładzie <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> i dodaje <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> do swojej kolekcji elementów.  
  
#### <a name="building-a-channelfactory"></a>Tworzenie elementu ChannelFactory  
 Zamiast tworzyć <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, utworzymy teraz <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> przez wywołanie metody <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> w powiązaniu, gdzie parametr typu jest <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>. Odbiorniki kanałów są używane przez stronę oczekiwania dla komunikatów przychodzących, fabryk kanałów, które są używane przez strony, która inicjuje komunikację, aby utworzyć kanał. Podobnie jak odbiorniki kanałów fabryk kanałów, które należy otworzyć przed ich użyciem.  
  
#### <a name="creating-a-channel"></a>Tworzenie kanału  
 Następnie wywołaj <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> do utworzenia <xref:System.ServiceModel.Channels.IRequestChannel>. To wywołanie pobiera adres punktu końcowego, z którą chcemy, aby komunikować się za pomocą nowego kanału tworzona. Gdy mamy kanału Open nazywa się na niej umieszcza je w stanie gotowy do komunikacji. W zależności od charakteru transportu to wywołanie do otworzenia mogą inicjować połączenia z punktem końcowym docelowej lub może nic nie rób w ogóle w sieci.  
  
#### <a name="sending-a-request-and-reading-the-reply"></a>Wysyłanie żądania i odczytywanie odpowiedzi  
 Po mamy kanał otwarty możemy utworzyć wiadomości i używać metody żądania kanału do wysyłania żądania i oczekiwania na odpowiedź, aby wrócić do. Po powrocie z tej metody mamy komunikat odpowiedzi, który firma Microsoft może być odczytany Aby dowiedzieć się, została odpowiedzi punktu końcowego.  
  
#### <a name="closing-objects"></a>Zamykanie obiektów  
 Aby uniknąć przeciek zasobów, możemy zamknąć obiekty używane podczas komunikacji, gdy nie są już wymagane.  
  
 Poniższy przykładowy kod przedstawia podstawowe klienta przy użyciu fabryki kanału do wysyłania wiadomości i odczytu odpowiedzi.  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
