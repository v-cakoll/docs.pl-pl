---
title: Przegląd modelu kanału
ms.date: 03/30/2017
helpviewer_keywords:
- channel model [WCF]
ms.assetid: 07a81e11-3911-4632-90d2-cca99825b5bd
ms.openlocfilehash: 362a7392d9dbaedb1942280a6c3b6c8f2139afe5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795888"
---
# <a name="channel-model-overview"></a>Przegląd modelu kanału
Stos kanału Windows Communication Foundation (WCF) to stos komunikacji warstwowej z co najmniej jednym kanałem, który przetwarza komunikaty. W dolnej części stosu jest kanał transportu, który jest odpowiedzialny za dostosowanie stosu kanału do podstawowego transportu (na przykład TCP, HTTP, SMTP i inne typy transportu). Kanały zapewniają model programowania niskiego poziomu służący do wysyłania i otrzymywania wiadomości. Ten model programowania opiera się na kilku interfejsach i innych typach wspólnie znanych jako model kanału WCF. W tym temacie omówiono kształty kanałów, konstruowanie odbiornika podstawowego kanału (w usłudze) i fabryki kanałów (na kliencie).  
  
## <a name="channel-stack"></a>Stos kanałów  
 Punkty końcowe WCF komunikują się ze światem przy użyciu stosu komunikacji o nazwie stos kanału. Na poniższym diagramie porównano stos kanału z innymi stosami komunikacji, na przykład TCP/IP.  
  
 ![Model kanału](./media/wcfc-channelstackhighlevelc.gif "wcfc_ChannelStackHighLevelc")  
  
 Najpierw podobieństwa: W obu przypadkach każda warstwa stosu zapewnia pewne streszczenie świata poniżej tej warstwy i uwidacznia Ten abstrakcję tylko w warstwie bezpośrednio nad nią. Każda warstwa używa abstrakcji tylko warstwy bezpośrednio poniżej. Ponadto w obu przypadkach, gdy dwa stosy komunikują się, każda warstwa komunikuje się z odpowiednią warstwą w innym stosie, na przykład warstwa IP komunikuje się z warstwą IP i warstwą TCP z warstwą TCP itd.  
  
 Teraz różnice: Stos protokołu TCP został zaprojektowany tak, aby zapewnić abstrakcję sieci fizycznej, stos kanału został zaprojektowany tak, aby zapewnić abstrakcję nie tylko sposobu dostarczania wiadomości, czyli transport, ale również inne funkcje, takie jak to, co znajduje się w komunikacie lub co Protokół jest używany do komunikacji, w tym transportu, ale znacznie więcej niż ten. Na przykład element powiązania niezawodnej sesji jest częścią stosu kanału, ale nie jest niższy niż transport lub sam transport. Takie streszczenie jest osiągane przez wymaganie, aby dolny kanał w stosie przystosował podstawowy protokół transportu do architektury stosu kanału, a następnie opierał się na kanałach w dalszej części stosu w celu zapewnienia funkcji komunikacji, takich jak niezawodność gwarancje i zabezpieczenia.  
  
 Komunikaty przepływają przez stos komunikacji <xref:System.ServiceModel.Channels.Message> jako obiekty. Jak pokazano na rysunku powyżej, dolny kanał nosi nazwę kanału transportowego. Jest to kanał odpowiedzialny za wysyłanie i otrzymywanie komunikatów do i z innych stron. Obejmuje to odpowiedzialność za transformowanie <xref:System.ServiceModel.Channels.Message> obiektu do i z formatu używanego do komunikowania się z innymi stronami. Nad kanałem transportu może istnieć dowolna liczba kanałów protokołów, które są odpowiedzialne za dostarczanie funkcji komunikacji, takiej jak gwarancje niezawodnego dostarczania. Kanały protokołu działają na komunikatach przepływających przez nich w postaci <xref:System.ServiceModel.Channels.Message> obiektu. Zwykle Przekształć komunikat, na przykład przez dodanie nagłówków lub zaszyfrowanie treści lub wysłanie i odebranie własnych komunikatów kontroli protokołu, na przykład potwierdzenia odbioru.  
  
## <a name="channel-shapes"></a>Kształty kanału  
 Każdy kanał implementuje jeden lub więcej interfejsów znanych jako interfejsy kształtu kanału lub kształty kanałów. Te kształty kanałów zapewniają metody ukierunkowane na komunikację, takie jak wysyłanie i odbieranie lub żądanie, i odpowiadają za to, aby kanał został zaimplementowany, oraz użytkownika wywołań kanału. Na podstawie kształtu kanału jest <xref:System.ServiceModel.Channels.IChannel> interfejs, który `GetProperty` \<zapewnia metodę T >, która jest mechanizmem warstwowym, aby uzyskać dostęp do dowolnych funkcji udostępnianych przez kanały w stosie. Pięć kształtów kanałów, które <xref:System.ServiceModel.Channels.IChannel> są rozbudowane:  
  
- <xref:System.ServiceModel.Channels.IInputChannel>  
  
- <xref:System.ServiceModel.Channels.IOutputChannel>  
  
- <xref:System.ServiceModel.Channels.IRequestChannel>  
  
- <xref:System.ServiceModel.Channels.IReplyChannel>  
  
- <xref:System.ServiceModel.Channels.IDuplexChannel>  
  
 Dodatkowo każdy z tych kształtów ma odpowiednik, który rozciąga <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> się na obsługę sesji. Są to:  
  
- <xref:System.ServiceModel.Channels.IInputSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IOutputSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IRequestSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IReplySessionChannel>  
  
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel>  
  
 Kształty kanałów są desenie po niektórych podstawowych wzorcach wymiany komunikatów obsługiwanych przez istniejące protokoły transportowe. Na przykład komunikacja <xref:System.ServiceModel.Channels.IInputChannel> jednokierunkowa odpowiada / <xref:System.ServiceModel.Channels.IOutputChannel> pary, żądanie-odpowiedź odpowiada <xref:System.ServiceModel.Channels.IReplyChannel> <xref:System.ServiceModel.Channels.IRequestChannel> / par i dwukierunkowej komunikacji dupleksowej odnosi się do <xref:System.ServiceModel.Channels.IDuplexChannel> (który rozszerza oba <xref:System.ServiceModel.Channels.IInputChannel> i <xref:System.ServiceModel.Channels.IOutputChannel>).  
  
## <a name="programming-with-the-channel-stack"></a>Programowanie przy użyciu stosu kanału  
 Stosy kanałów są zwykle tworzone przy użyciu wzorca fabryki, gdzie powiązanie tworzy stos kanałów. Na stronie wysyłanie powiązanie służy do kompilowania <xref:System.ServiceModel.ChannelFactory>, który z kolei kompiluje stos kanału i zwraca odwołanie do górnego kanału w stosie. Następnie aplikacja może używać tego kanału do wysyłania komunikatów. Aby uzyskać więcej informacji, zobacz [Programowanie na poziomie kanału klienta](client-channel-level-programming.md).  
  
 Na stronie odbierania powiązanie służy do kompilowania <xref:System.ServiceModel.Channels.IChannelListener>, który nasłuchuje komunikatów przychodzących. <xref:System.ServiceModel.Channels.IChannelListener> Dostarcza komunikaty do aplikacji nasłuchiwania przez utworzenie stosów kanałów i przekazanie odwołania aplikacji do górnego kanału. Aplikacja używa tego kanału do odbierania wiadomości przychodzących. Aby uzyskać więcej informacji, zobacz [Programowanie na poziomie kanału usługi](service-channel-level-programming.md).  
  
## <a name="the-channel-object-model"></a>Model obiektu kanału  
 Model obiektów kanału jest podstawowym zestawem interfejsów wymaganych do implementowania kanałów, odbiorników kanałów i fabryk kanałów. Istnieją także pewne klasy bazowe, które mogą pomóc w implementacji niestandardowej.  
  
 Odbiorniki kanałów są odpowiedzialne za nasłuchiwanie wiadomości przychodzących, a następnie dostarczanie ich do warstwy powyżej za pośrednictwem kanałów utworzonych przez odbiornik kanału.  
  
 Fabryki kanałów są odpowiedzialne za tworzenie kanałów, które są używane do wysyłania komunikatów i zamykania wszystkich kanałów utworzonych podczas zamykania fabryki kanałów.  
  
 <xref:System.ServiceModel.ICommunicationObject>jest podstawowym interfejsem, który definiuje podstawowy komputer stanu, który implementuje wszystkie obiekty komunikacji. <xref:System.ServiceModel.Channels.CommunicationObject>zapewnia implementację tego interfejsu podstawowego, z którego mogą pochodzić inne klasy kanału zamiast ponownego implementowania interfejsu. Nie jest to jednak wymagane: kanał niestandardowy można zaimplementować <xref:System.ServiceModel.ICommunicationObject> bezpośrednio i nie dziedziczy z. <xref:System.ServiceModel.Channels.CommunicationObject> Żadna z klas na rysunku 3 nie jest uważana za część modelu kanału; są one pomocnikami dostępnymi dla niestandardowych realizatorów kanałów, którzy chcą tworzyć kanały.  
  
 ![Model kanału](./media/wcfc-wcfcchannelsigure3omumtreec.gif "wcfc_WCFCChannelsigure3OMUMTreec")  
  
 W poniższych tematach opisano model obiektów kanału oraz różne obszary programistyczne, które ułatwiają tworzenie niestandardowych kanałów.  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Usługi Odbiorniki kanałów i kanały](service-channel-listeners-and-channels.md)|Opisuje Odbiorniki kanałów, które nasłuchują przychodzących kanałów w aplikacji usługi.|  
|[Klient Fabryki kanałów i kanały](client-channel-factories-and-channels.md)|Opisuje fabryki kanałów, które tworzą kanały do łączenia się z aplikacją usługi.|  
|[Opis zmian stanu](understanding-state-changes.md)|Opisuje sposób <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType> zmiany stanu modeli interfejsu w kanałach.|  
|[Wybieranie platformy wymiany komunikatów](choosing-a-message-exchange-pattern.md)|Opisuje sześć podstawowych wzorców wymiany komunikatów, które mogą być obsługiwane przez kanały.|  
|[Obsługa wyjątków i błędów](handling-exceptions-and-faults.md)|Opisuje, jak obsługiwać błędy i wyjątki w niestandardowych kanałach.|  
|[Konfiguracja i obsługa metadanych](configuration-and-metadata-support.md)|Opisuje sposób obsługi kanałów niestandardowych z modelu aplikacji oraz sposób eksportowania i importowania metadanych przy użyciu powiązań i elementów powiązania.|
