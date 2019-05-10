---
title: Tworzenie elementu BindingElement
ms.date: 03/30/2017
ms.assetid: 01a35307-a41f-4ef6-a3db-322af40afc99
ms.openlocfilehash: 0c08494315f43f35f60d70abf643f596a013c302
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587343"
---
# <a name="creating-a-bindingelement"></a>Tworzenie elementu BindingElement
Powiązania i elementy powiązań (obiekty, które rozszerzają <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>odpowiednio) to miejsce, gdzie model aplikacji Windows Communication Foundation (WCF) skojarzony z fabryki kanałów i odbiorników kanału. Bez powiązania, za pomocą niestandardowych kanałów wymaga programowania na poziomie kanału zgodnie z opisem w [programowania na poziomie kanału usługi](../../../../docs/framework/wcf/extending/service-channel-level-programming.md) i [programowania na poziomie kanału klienta](../../../../docs/framework/wcf/extending/client-channel-level-programming.md). W tym temacie omówiono wymagania minimalne, aby umożliwić używanie Twojego kanału w usłudze WCF, rozwoju <xref:System.ServiceModel.Channels.BindingElement> dla kanału i Zezwalaj na używanie aplikacji, zgodnie z opisem w kroku 4 [kanały rozwijających się](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="overview"></a>Omówienie  
 Tworzenie <xref:System.ServiceModel.Channels.BindingElement> dla kanału temu deweloperzy mogą używać go w aplikacji WCF. <xref:System.ServiceModel.Channels.BindingElement> obiekty mogą być używane z <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> klasy, aby połączyć aplikację WCF do Twojego kanału bez konieczności informacje o typie dokładne swojego kanału.  
  
 Raz <xref:System.ServiceModel.Channels.BindingElement> został utworzony, aby umożliwić więcej funkcji, wykonując pozostałe kroki tworzenia kanału opisanego w zależności od wymagań dotyczących [kanały rozwijających się](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="adding-a-binding-element"></a>Dodawanie elementu powiązania  
 Aby zaimplementować niestandardowy <xref:System.ServiceModel.Channels.BindingElement>, napisać klasę, która dziedziczy po elemencie <xref:System.ServiceModel.Channels.BindingElement>. Na przykład, jeśli masz `ChunkingChannel` , dzielenie dużych komunikatów na fragmenty oraz łączenie ich z drugiej, można użyć tego kanału wszystkie powiązania, implementując <xref:System.ServiceModel.Channels.BindingElement> i konfigurowanie powiązania z niego korzystać. W pozostałej części tego tematu używa `ChunkingChannel` jako przykład ilustrujący wymagania dotyczące wdrażania elementu powiązania.  
  
 A `ChunkingBindingElement` jest odpowiedzialny za tworzenie `ChunkingChannelFactory` i `ChunkingChannelListener`. Zastępuje ona <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelFactory%2A> i <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelListener%2A> implementacji i sprawdza, czy ma parametr typu <xref:System.ServiceModel.Channels.IDuplexSessionChannel> (w naszym przykładzie jest to jedyna kształtu kanału obsługiwane przez `ChunkingChannel`) i inne elementy powiązania powiązanie obsługuje to kształtu kanału.  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> najpierw sprawdza, czy żądanego kształtu kanału mogą być wbudowane, a następnie pobiera listę akcji komunikat na być podzielony. Następnie tworzy nową `ChunkingChannelFactory`, podając mu wewnętrzna fabryka kanałów. (W przypadku tworzenia elementu powiązania transportu tego elementu jest ostatnim blokiem w stosie powiązania i dlatego należy utworzyć odbiornik kanału lub fabryki kanałów)  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> zawiera podobne implementację tworzenia `ChunkingChannelListener` i przekazanie do niej odbiornik kanału wewnętrznego.  
  
 Innym przykładem przy użyciu kanał transportu [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) przykład zawiera następujące zastąpienie.  
  
 W tym przykładzie jest element powiązania `UdpTransportBindingElement`, która jest pochodną <xref:System.ServiceModel.Channels.TransportBindingElement>. Zastępuje ona następujące metody umożliwiające tworzenie fabryk skojarzone z kanału.  
  
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
  
 Zawiera również członków do klonowania `BindingElement` i zwracanie tym schemacie (soap.udp).  
  
#### <a name="protocol-binding-elements"></a>Elementy powiązania protokołu  
 Nowe elementy powiązania można zastąpić lub rozszerzyć elementy powiązania dołączone, dodawanie nowego transportu, kodowania lub protokołów wyższego poziomu. Aby utworzyć nowy Element powiązania protokołu, start, rozszerzając <xref:System.ServiceModel.Channels.BindingElement> klasy. Jako minimum, następnie należy zaimplementować <xref:System.ServiceModel.Channels.BindingElement.Clone%2A?displayProperty=nameWithType> i zaimplementować `ChannelProtectionRequirements` przy użyciu <xref:System.ServiceModel.Channels.IChannel.GetProperty%2A?displayProperty=nameWithType>. Spowoduje to zwrócenie <xref:System.ServiceModel.Security.ChannelProtectionRequirements> dla tego elementu powiązania.  Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Security.ChannelProtectionRequirements>.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> powinien zostać zwrócony świeżą kopię tego elementu powiązania. Najlepszym rozwiązaniem jest firma Microsoft zaleca tego elementu powiązania autorów Implementowanie <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> za pomocą konstruktora kopiującego, który wywołuje konstruktor Kopiuj podstawowej, następnie klony dodatkowe pola w tej klasie.  
  
#### <a name="transport-binding-elements"></a>Elementy powiązania transportu  
 Aby utworzyć nowy Element powiązania transportu, rozszerzyć <xref:System.ServiceModel.Channels.TransportBindingElement> interfejsu. Jako minimum, następnie należy zaimplementować <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> metody i <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A?displayProperty=nameWithType> właściwości.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> — Powinna zwrócić świeżą kopię tego elementu powiązania.  Najlepszym rozwiązaniem zaleca się, że autorzy Element powiązania wdrożyć klonu za pomocą konstruktora kopiującego, który wywołuje konstruktor Kopiuj podstawowy, a następnie klony dodatkowe pola w tej klasie.  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> — <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> Uzyskać właściwość zwraca schemat identyfikatora URI protokołu transportowego reprezentowanego przez element powiązania. Na przykład <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> i <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType> zwracać "http" i "net.tcp" z odpowiednich <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> właściwości.  
  
#### <a name="encoding-binding-elements"></a>Kodowanie elementów wiązania  
 Do tworzenia nowych kodowanie powiązań elementów, należy uruchomić, rozszerzając <xref:System.ServiceModel.Channels.BindingElement> klasy i wdrażanie <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType> klasy. Jako minimum, następnie należy zaimplementować <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A?displayProperty=nameWithType> metod i <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A?displayProperty=nameWithType> właściwości.  
  
- <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>. Zwraca świeżą kopię tego elementu powiązania. Najlepszym rozwiązaniem jest firma Microsoft zaleca tego elementu powiązania autorów Implementowanie <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> za pomocą konstruktora kopiującego, który wywołuje konstruktor Kopiuj podstawowej, następnie klony dodatkowe pola w tej klasie.  
  
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A>. Zwraca <xref:System.ServiceModel.Channels.MessageEncoderFactory>, zapewniającą dojścia do rzeczywista klasa implementuje koder nowych i który powinny rozszerzać <xref:System.ServiceModel.Channels.MessageEncoder>. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Channels.MessageEncoderFactory> i <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A>. Zwraca <xref:System.ServiceModel.Channels.MessageVersion> używane w tym kodowania, która reprezentuje wersje protokołu SOAP i WS-Addressing w użyciu.  
  
 Aby uzyskać pełną listę opcjonalnych metod i właściwości zdefiniowanych przez użytkownika elementy powiązania kodowania, zobacz <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 Aby uzyskać więcej informacji na temat tworzenia nowego elementu powiązania, zobacz [powiązania Creating User-Defined](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
 Po utworzeniu elementu powiązania kanału, wróć do [kanały rozwijających się](../../../../docs/framework/wcf/extending/developing-channels.md) tematu, aby zobaczyć, czy chcesz dodać obsługę pliku konfiguracji usługi elementu powiązania, jeśli i jak dodać obsługę publikowania metadanych, i czy i w jaki sposób do utworzenia powiązania zdefiniowane przez użytkownika, który używa usługi elementu powiązania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.BindingElement>
- [Opracowywanie kanałów](../../../../docs/framework/wcf/extending/developing-channels.md)
- [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
