---
title: Tworzenie elementu BindingElement
ms.date: 03/30/2017
ms.assetid: 01a35307-a41f-4ef6-a3db-322af40afc99
ms.openlocfilehash: 96924e97ad3fcc121ef7b28125301060d8448514
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="creating-a-bindingelement"></a>Tworzenie elementu BindingElement
Powiązania i elementy powiązań (obiekty, które rozszerzają <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>odpowiednio) są na miejscu, gdzie jest skojarzony z fabryk kanałów i odbiorników kanału modelu aplikacji Windows Communication Foundation (WCF). Bez powiązania, za pomocą niestandardowych kanałów wymaga programowania na poziomie kanału zgodnie z opisem w [programowania na poziomie kanału usługi](../../../../docs/framework/wcf/extending/service-channel-level-programming.md) i [programowania na poziomie kanału klienta](../../../../docs/framework/wcf/extending/client-channel-level-programming.md). W tym temacie omówiono wymagania minimalne, aby włączyć za pomocą kanału w programie WCF, rozwoju <xref:System.ServiceModel.Channels.BindingElement> kanału i Włącz użycie z aplikacji, zgodnie z opisem w kroku 4 [kanały rozwijających się](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="overview"></a>Omówienie  
 Tworzenie <xref:System.ServiceModel.Channels.BindingElement> dla kanału umożliwia deweloperom używany w aplikacji WCF. <xref:System.ServiceModel.Channels.BindingElement> obiekty mogą być używane z <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> klasy łączenie aplikacji WCF do kanału bez konieczności informacje dokładny typ kanału.  
  
 Raz <xref:System.ServiceModel.Channels.BindingElement> został utworzony, można włączyć więcej funkcji, wykonując pozostałe kroki tworzenia kanału opisanego w zależności od wymagań [kanały rozwijających się](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="adding-a-binding-element"></a>Dodawanie elementu powiązania  
 Aby wdrożyć niestandardowy <xref:System.ServiceModel.Channels.BindingElement>, zapisać klasy, która dziedziczy <xref:System.ServiceModel.Channels.BindingElement>. Na przykład, jeśli masz `ChunkingChannel` czy podzielić duże wiadomości na fragmenty i ponownie połączyć je z drugiej, możesz użyć tego kanału w powiązania zaimplementowanie <xref:System.ServiceModel.Channels.BindingElement> i konfigurowanie powiązania z niego korzystać. W pozostałej części tego tematu używa `ChunkingChannel` jako przykład w celu zademonstrowania wymagania dotyczące wdrażania elementu powiązania.  
  
 A `ChunkingBindingElement` odpowiedzialną za tworzenie `ChunkingChannelFactory` i `ChunkingChannelListener`. Zastępuje on <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelFactory%2A> i <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelListener%2A> implementacji i sprawdza, czy parametr typu jest <xref:System.ServiceModel.Channels.IDuplexSessionChannel> (w naszym przykładzie jest to tylko kształtu kanału obsługiwane przez `ChunkingChannel`) i inne elementy powiązania powiązanie obsługuje to kształtu kanału.  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> najpierw sprawdza, czy mogą być wbudowane żądanego kształtu kanału, a następnie pobiera listę komunikatów akcje fragmentarycznego można. Następnie tworzy nowy `ChunkingChannelFactory`, przekazanie jej wewnętrzna fabryka kanałów. (Jeśli tworzysz element powiązania transportu tego elementu jest ostatnim w stosie powiązania i dlatego należy utworzyć odbiornik kanału lub fabryki kanałów.)  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> implementacją podobne do tworzenia `ChunkingChannelListener` i przekazanie jej przez odbiornik kanału wewnętrzny.  
  
 Innym przykładem za pomocą kanał transportu [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) przykład zawiera następujące zastąpienia.  
  
 W przykładzie jest element powiązania `UdpTransportBindingElement`, która jest pochodną <xref:System.ServiceModel.Channels.TransportBindingElement>. Zastępuje on następujące metody umożliwiające tworzenie fabryki skojarzony z kanałem.  
  
```  
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
            return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
            return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 Zawiera także członków do klonowania `BindingElement` i zwracanie naszych schematu (soap.udp).  
  
#### <a name="protocol-binding-elements"></a>Elementy powiązania protokołu  
 Nowe elementy powiązania można zastąpić lub rozszerzyć elementy powiązania dołączone, dodawanie nowych transportów, kodowania i protokoły wyższego poziomu. Aby utworzyć nowy Element powiązania protokołu, Rozpocznij od rozszerzanie <xref:System.ServiceModel.Channels.BindingElement> klasy. Co najmniej, następnie należy zaimplementować <xref:System.ServiceModel.Channels.BindingElement.Clone%2A?displayProperty=nameWithType> i wdrożenie `ChannelProtectionRequirements` przy użyciu <xref:System.ServiceModel.Channels.IChannel.GetProperty%2A?displayProperty=nameWithType>. To polecenie zwróci <xref:System.ServiceModel.Security.ChannelProtectionRequirements> dla tego elementu powiązania.  Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Security.ChannelProtectionRequirements>.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> powinien zwrócić świeżą kopię tego elementu powiązania. Najlepszym rozwiązaniem, zaleca się wdrożenie autorów elementu powiązania <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> przy użyciu konstruktora kopiującego, który wywołuje Konstruktor kopiujący podstawowej, następnie klonów dodatkowe pola w tej klasie.  
  
#### <a name="transport-binding-elements"></a>Elementy powiązania transportu  
 Aby utworzyć nowy Element powiązania transportu, rozszerzanie <xref:System.ServiceModel.Channels.TransportBindingElement> interfejsu. Co najmniej, następnie należy zaimplementować <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> — metoda i <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A?displayProperty=nameWithType> właściwości.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> — Powinna zwrócić świeżą kopię tego elementu powiązania.  Najlepszym rozwiązaniem zaleca się, że autorów elementu powiązania wdrożyć klonu i konstruktora kopiującego, który wywołuje Konstruktor kopiujący podstawowej, a następnie klonów dodatkowe pola w tej klasie.  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> — <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> Pobierz właściwość zwraca schemat identyfikatora URI reprezentowany przez element powiązania protokołu transportu. Na przykład <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType> zwrócić "http" i "net.tcp" z odpowiednich <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> właściwości.  
  
#### <a name="encoding-binding-elements"></a>Kodowanie elementów wiązania  
 Do tworzenia nowych kodowanie powiązania elementów, Rozpocznij od rozszerzanie <xref:System.ServiceModel.Channels.BindingElement> klasy i wdrażanie <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType> klasy. Co najmniej, następnie należy zaimplementować <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A?displayProperty=nameWithType> metod i <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A?displayProperty=nameWithType> właściwości.  
  
-   <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>. Zwraca nową kopię tego elementu powiązania. Najlepszym rozwiązaniem, zaleca się wdrożenie autorów elementu powiązania <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> przy użyciu konstruktora kopiującego, który wywołuje Konstruktor kopiujący podstawowej, następnie klonów dodatkowe pola w tej klasie.  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A>. Zwraca <xref:System.ServiceModel.Channels.MessageEncoderFactory>, zapewniające dojścia do rzeczywistego klasa implementuje kodera nowy i który powinien być rozszerzany <xref:System.ServiceModel.Channels.MessageEncoder>. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Channels.MessageEncoderFactory> i <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A>. Zwraca <xref:System.ServiceModel.Channels.MessageVersion> używane kodowanie, który reprezentuje wersje protokołu SOAP i WS-Addressing w użyciu.  
  
 Pełna lista opcjonalny metody i właściwości zdefiniowane przez użytkownika elementy powiązania kodowania, zobacz <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 Aby uzyskać więcej informacji na temat tworzenia nowego elementu powiązania, zobacz [powiązania Creating User-Defined](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
 Po utworzeniu elementu powiązania dla kanału, wróć do [rozwijających się kanałów](../../../../docs/framework/wcf/extending/developing-channels.md) tematu, aby zobaczyć Określa, czy chcesz dodać obsługę pliku konfiguracji do danego elementu powiązania, jeśli i dodawania obsługi Publikowanie metadanych, i czy i jak do utworzenia powiązania zdefiniowane przez użytkownika, który używa programu elementu powiązania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [Opracowywanie kanałów](../../../../docs/framework/wcf/extending/developing-channels.md)  
 [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
