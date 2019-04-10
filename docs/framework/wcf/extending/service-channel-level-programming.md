---
title: Programowanie na poziomie kanału usługi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8d8dcd85-0a05-4c44-8861-4a0b3b90cca9
ms.openlocfilehash: be5c73e2ac9fcc45d136280c869148326cd91315
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329133"
---
# <a name="service-channel-level-programming"></a>Programowanie na poziomie kanału usługi
W tym temacie opisano sposób pisania aplikacji usługi Windows Communication Foundation (WCF) bez użycia <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> i jego skojarzonego obiektu modelu.  
  
## <a name="receiving-messages"></a>Odbieranie komunikatów  
 Będzie gotowa do odbierania i przetwarzania wiadomości, wymagane są następujące kroki:  
  
1. Tworzenie powiązania.  
  
2. Tworzenie odbiornika kanałów.  
  
3. Otwórz odbiornika kanałów.  
  
4. Żądania odczytu i wysyłać odpowiedzi.  
  
5. Zamknij wszystkie obiekty kanału.  
  
#### <a name="creating-a-binding"></a>Tworzenie powiązania  
 Pierwszym etapem nasłuchiwać i odbierać wiadomości jest utworzenie powiązania. Usługi WCF jest dostarczany z kilku wbudowanych lub dostarczane przez system powiązań, które mogą być używane bezpośrednio przez utworzenie wystąpienia jednego z nich. Ponadto można również utworzyć własne powiązania niestandardowego przez utworzenie wystąpienia klasy CustomBinding, która jest wykonuje kod w ofercie 1.  
  
 Poniższy przykładowy kod tworzy wystąpienie <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> i dodaje <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> do swojej kolekcji elementów, który jest kolekcją elementów, które są używane do tworzenia stosu kanału wiązania. W tym przykładzie ponieważ kolekcja elementów zawiera tylko <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, wynikowy stos kanał ma kanał transportu HTTP.  
  
#### <a name="building-a-channellistener"></a>Tworzenie ChannelListener  
 Po utworzeniu powiązanie nazywamy <xref:System.ServiceModel.Channels.Binding.BuildChannelListener%2A?displayProperty=nameWithType> do tworzenia odbiornika kanałów, w której parametr typu jest kształtu kanału do utworzenia. W tym przykładzie używamy <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> ponieważ chcemy nasłuchiwać komunikatów przychodzących w wymiany komunikatów typu żądanie/odpowiedź.  
  
 <xref:System.ServiceModel.Channels.IReplyChannel> jest używany do odbierania żądań wiadomości i ponownie wysyłanie komunikatów odpowiedzi. Wywoływanie <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A?displayProperty=nameWithType> zwraca <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>, które mogą służyć do odbierania komunikatów żądań i przesyła z powrotem komunikat odpowiedzi.  
  
 Podczas tworzenia odbiornika, przekazujemy adresu sieciowego, na którym nasłuchuje on, w tym przypadku `http://localhost:8080/channelapp`. Ogólnie rzecz biorąc każdy kanał transportowy obsługuje co najmniej prawdopodobnie kilka schematów adresów, na przykład transportu HTTP obsługuje schematy http i https.  
  
 Możemy również przekazać pusty <xref:System.ServiceModel.Channels.BindingParameterCollection?displayProperty=nameWithType> podczas tworzenia odbiornika. Parametr wiązania to mechanizm, aby przekazać parametry, które kontrolują, jak powinny zostać skompilowane odbiornika. W naszym przykładzie nie używamy tych parametrów, dzięki czemu możemy przekazać pustą kolekcję.  
  
#### <a name="listening-for-incoming-messages"></a>Nasłuchiwanie przychodzących wiadomości  
 Następnie wywołaj <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> na odbiornik i rozpoczęcia akceptowanie kanałów. Zachowanie <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType> zależy od tego, czy transport jest ukierunkowane na połączenia lub bez połączenia. Dla transportu z nawiązaniem połączenia <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> blokuje, aż nowego żądania połączenia są obciążone tym momencie zwraca nowy kanał, który reprezentuje tego nowego połączenia. Dla mniej połączenia transportu, takich jak HTTP <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> zwraca bezpośrednio z jednego i kanału, który tworzy odbiornika transportu.  
  
 W tym przykładzie odbiornik zwraca kanału, który implementuje <xref:System.ServiceModel.Channels.IReplyChannel>. Do odbierania komunikatów na ten kanał, firma Microsoft pierwsze wywołanie <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> na nim zostać umieszczone w stanie gotowy do komunikacji. Następnie wywołaj <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> które bloków, dopóki nadejścia wiadomości.  
  
#### <a name="reading-the-request-and-sending-a-reply"></a>Żądania odczytu i wysyłania odpowiedzi  
 Gdy <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> zwraca <xref:System.ServiceModel.Channels.RequestContext>, uzyskujemy odebranej wiadomości przy użyciu jego <xref:System.ServiceModel.Channels.RequestContext.RequestMessage%2A> właściwości. Możemy zapisać zawartości komunikatu akcji i treści, (który przyjęto założenie, że jest to ciąg).  
  
 Aby wysłać odpowiedź, utworzymy nowy komunikat odpowiedzi w tym przypadku ponownie przekazując dane ciągu, że firma Microsoft została odebrana w żądaniu. Następnie wywołaj <xref:System.ServiceModel.Channels.RequestContext.Reply%2A> do wysłania komunikatu odpowiedzi.  
  
#### <a name="closing-objects"></a>Zamykanie obiektów  
 Aby uniknąć wyciek zasobów, jest bardzo ważne, aby zamknąć obiekty używane podczas komunikacji, gdy nie są już wymagane. W tym przykładzie firma Microsoft Zamknij komunikat żądania, kontekst żądania, kanału i odbiornika.  
  
 Poniższy przykład kodu pokazuje podstawowe usługi, w której odbiornik kanału odbiera tylko jeden komunikat. Rzeczywista Usługa przechowuje akceptowanie kanałów i odbieranie wiadomości, dopóki nie kończy działanie usługi.  
  
 [!code-csharp[ChannelProgrammingBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/serviceprogram.cs#1)]
 [!code-vb[ChannelProgrammingBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/serviceprogram.vb#1)]
