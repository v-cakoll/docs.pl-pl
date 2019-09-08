---
title: Tworzenie elementu BindingElement
ms.date: 03/30/2017
ms.assetid: 01a35307-a41f-4ef6-a3db-322af40afc99
ms.openlocfilehash: 4b760f9373e64e153bd5a21469eb7a503283d35c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795823"
---
# <a name="creating-a-bindingelement"></a>Tworzenie elementu BindingElement
Powiązania i elementy powiązania (obiekty, które <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType> rozszerzają i <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>odpowiednio) to miejsce, w którym model aplikacji Windows Communication Foundation (WCF) jest skojarzony z fabrykami kanałów i odbiornikami kanałów. Bez powiązań używanie niestandardowych kanałów wymaga programowania na poziomie kanału, zgodnie z opisem w [programowaniu na poziomie kanału usług](service-channel-level-programming.md) i [programowaniem na poziomie kanału klienta](client-channel-level-programming.md). W tym temacie omówiono minimalny wymóg włączania korzystania z kanału w programie WCF, opracowywanie <xref:System.ServiceModel.Channels.BindingElement> dla kanału i możliwość używania z aplikacji zgodnie z opisem w sekcji Krok 4. [Tworzenie kanałów](developing-channels.md).  
  
## <a name="overview"></a>Omówienie  
 <xref:System.ServiceModel.Channels.BindingElement> Utworzenie dla kanału pozwala deweloperom korzystać z niego w aplikacji WCF. <xref:System.ServiceModel.Channels.BindingElement>obiekty mogą być używane z <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> klasy do łączenia aplikacji WCF z kanałem bez konieczności dokładnego typu informacji o kanale.  
  
 Po utworzeniu <xref:System.ServiceModel.Channels.BindingElement> programu można włączyć więcej funkcji, w zależności od wymagań, postępując zgodnie z opisanymi w temacie [Tworzenie kanałów](developing-channels.md).  
  
## <a name="adding-a-binding-element"></a>Dodawanie elementu powiązania  
 Aby zaimplementować niestandardowy <xref:System.ServiceModel.Channels.BindingElement>, należy napisać klasę, która dziedziczy z <xref:System.ServiceModel.Channels.BindingElement>. Na przykład, jeśli opracowano `ChunkingChannel` , że program może podzielić duże wiadomości na fragmenty i ponownie umieścić je na drugim końcu, można użyć tego kanału w dowolnym powiązaniu, <xref:System.ServiceModel.Channels.BindingElement> implementując a i konfigurując powiązanie do jego używania. Pozostała część tego tematu używa `ChunkingChannel` jako przykładu, aby przedstawić wymagania dotyczące implementowania elementu powiązania.  
  
 Jest odpowiedzialny za `ChunkingChannelFactory` tworzenie i `ChunkingChannelListener`. `ChunkingBindingElement` Zastępuje <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelFactory%2A> i <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelListener%2A> implementacje i sprawdza, czy parametr typu jest <xref:System.ServiceModel.Channels.IDuplexSessionChannel> (w naszym przykładzie `ChunkingChannel`jest to jedyny kształt kanału obsługiwany przez) i czy inne elementy powiązania w powiązaniu obsługują tę kształt kanału.  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A>najpierw sprawdza, czy żądany kształt kanału można skompilować, a następnie pobiera listę akcji komunikatów, które mają zostać rozbudowane. Następnie tworzy nową `ChunkingChannelFactory`, przekazując ją do wewnętrznej fabryki kanałów. (Jeśli tworzysz element powiązania transportowego, ten element jest ostatnim z nich w stosie powiązań i dlatego musi utworzyć odbiornik kanału lub fabrykę kanałów).  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A>ma podobną implementację do `ChunkingChannelListener` tworzenia i przekazywania do niego wewnętrznego odbiornika kanału.  
  
 Innym przykładem jest użycie kanału [transportowego: Przykład](../samples/transport-udp.md) UDP zapewnia następujące przesłonięcie.  
  
 W przykładzie element Binding ma wartość `UdpTransportBindingElement`, która pochodzi od. <xref:System.ServiceModel.Channels.TransportBindingElement> Zastępuje on następujące metody tworzenia fabryk skojarzonych z kanałem.  
  
```csharp  
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 Zawiera również elementy członkowskie do klonowania `BindingElement` i zwracania naszego schematu (SOAP. UDP).  
  
#### <a name="protocol-binding-elements"></a>Elementy powiązania protokołów  
 Nowe elementy powiązania mogą zastąpić lub rozszerzyć dowolne z zawartych elementów powiązania, dodawanie nowych transportów, kodowań lub protokołów wyższego poziomu. Aby utworzyć nowy element powiązania protokołu, Zacznij od rozszerzenia <xref:System.ServiceModel.Channels.BindingElement> klasy. Najpierw należy wdrożyć <xref:System.ServiceModel.Channels.BindingElement.Clone%2A?displayProperty=nameWithType> i `ChannelProtectionRequirements` zaimplementować polecenie using <xref:System.ServiceModel.Channels.IChannel.GetProperty%2A?displayProperty=nameWithType>. Zwraca wartość <xref:System.ServiceModel.Security.ChannelProtectionRequirements> dla tego elementu powiązania.  Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Security.ChannelProtectionRequirements>.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>powinna zwracać świeżą kopię tego elementu powiązania. Najlepszym rozwiązaniem jest, że zaleca się, aby elementy tworzące <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> powiązania autorów zaimplementowali przy użyciu konstruktora kopiującego, który wywołuje podstawowy Konstruktor kopiujący, a następnie klonuje wszelkie dodatkowe pola w tej klasie.  
  
#### <a name="transport-binding-elements"></a>Elementy powiązania transportu  
 Aby utworzyć nowy element powiązania transportu, należy rozszerzać <xref:System.ServiceModel.Channels.TransportBindingElement> interfejs. Najpierw należy zaimplementować <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> metodę <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A?displayProperty=nameWithType> i właściwość.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>— Powinna zwrócić świeżą kopię tego elementu powiązania.  Najlepszym rozwiązaniem jest zalecanie, aby elementy tworzące powiązania autorów implementują klon według konstruktora kopiującego, który wywołuje podstawowy Konstruktor kopiujący, a następnie klonuje wszelkie dodatkowe pola w tej klasie.  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A>— Właściwość <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> Get zwraca schemat identyfikatora URI dla protokołu transportowego reprezentowanego przez element powiązania. Na przykład, <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType> i zwraca "http" i "net. TCP" z odpowiednich <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> właściwości.  
  
#### <a name="encoding-binding-elements"></a>Kodowanie elementów powiązania  
 Aby utworzyć nowe elementy powiązania kodowania, Zacznij od rozszerzenia <xref:System.ServiceModel.Channels.BindingElement> klasy i <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType> implementującej klasę. Najpierw należy zaimplementować <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A?displayProperty=nameWithType> metody i <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A?displayProperty=nameWithType> właściwość.  
  
- <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>. Zwraca świeżą kopię tego elementu powiązania. Najlepszym rozwiązaniem jest, że zaleca się, aby elementy tworzące <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> powiązania autorów zaimplementowali przy użyciu konstruktora kopiującego, który wywołuje podstawowy Konstruktor kopiujący, a następnie klonuje wszelkie dodatkowe pola w tej klasie.  
  
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A>. Zwraca obiekt <xref:System.ServiceModel.Channels.MessageEncoderFactory>, który dostarcza dojście do rzeczywistej klasy implementującej nowy koder i który <xref:System.ServiceModel.Channels.MessageEncoder>powinien zostać rozbudowany. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Channels.MessageEncoderFactory> i <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A>. <xref:System.ServiceModel.Channels.MessageVersion> Zwraca użyte w tym kodowaniu kodowanie, które reprezentuje wersje protokołu SOAP i WS-Addressing w użyciu.  
  
 Aby zapoznać się z pełną listą opcjonalnych metod i właściwości dla elementów powiązania kodowania zdefiniowanych przez <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>użytkownika, zobacz.  
  
 Aby uzyskać więcej informacji na temat tworzenia nowego elementu powiązania, zobacz [Tworzenie powiązań zdefiniowanych przez użytkownika](creating-user-defined-bindings.md).  
  
 Po utworzeniu elementu powiązania dla kanału Wróć do tematu [Opracowywanie kanałów](developing-channels.md) , aby sprawdzić, czy chcesz dodać obsługę plików konfiguracji do elementu powiązania, jeśli i jak dodać obsługę publikacji metadanych, oraz określić, czy i jak należy Utwórz powiązanie zdefiniowane przez użytkownika, które używa elementu wiązania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.BindingElement>
- [Opracowywanie kanałów](developing-channels.md)
- [Transportu UDP](../samples/transport-udp.md)
