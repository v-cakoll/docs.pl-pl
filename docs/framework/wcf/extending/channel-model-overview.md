---
title: Przegląd modelu kanału
ms.date: 03/30/2017
helpviewer_keywords:
- channel model [WCF]
ms.assetid: 07a81e11-3911-4632-90d2-cca99825b5bd
ms.openlocfilehash: c29b3e3d5eff426ac573ddf5224259f0a6c28e53
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664929"
---
# <a name="channel-model-overview"></a>Przegląd modelu kanału
Stos kanał Windows Communication Foundation (WCF) jest stos warstwowej komunikacji z co najmniej jednego kanału, które przetwarzają komunikaty. W dolnej części stosu jest kanał transportu, który jest odpowiedzialny za dostosowanie stosu kanału do transportu źródłowego (na przykład protokołu TCP, HTTP, SMTP i innych rodzajów transportu). Kanały zapewnia model programowania niskiego poziomu do wysyłania i odbierania komunikatów. Ten model programowania opiera się na kilka interfejsów i innych typów nazywanych zbiorczo model kanału WCF. W tym temacie omówiono kształty kanału, konstrukcja odbiornika podstawowego kanałów (na usługę) i fabryki kanałów (na kliencie).  
  
## <a name="channel-stack"></a>Kanał stosu  
 Punktami końcowymi programu WCF komunikują się ze świata, za pomocą stosu komunikacji, o nazwie stosu kanału. Poniższy diagram zawiera porównanie stosu kanału, za pomocą innych stosów komunikacji, na przykład protokołu TCP/IP.  
  
 ![Model kanału](../../../../docs/framework/wcf/extending/media/wcfc-channelstackhighlevelc.gif "wcfc_ChannelStackHighLevelc")  
  
 Najpierw podobieństwa: W obu przypadkach każdej warstwie stosu zawiera niektóre abstrakcji świata poniżej warstwy, która tego abstrakcji tylko do warstwy bezpośrednio znad niej widoczne. Każda warstwa używa pozyskiwania tylko warstwę bezpośrednio pod nim. Również w obu przypadkach, gdy komunikują się dwóch stosów, każda warstwa komunikuje się za pomocą odpowiedniej warstwy ze stosu na przykład warstwy IP komunikuje się z warstwy IP i warstwie TCP w warstwie TCP i tak dalej.  
  
 Teraz różnice: Gdy dotyczącą stosu TCP zaprojektowano tak, aby zapewnić abstrakcję sieci fizycznej, stos kanał ma na celu zapewnienie klasą abstrakcyjną nie tylko sposób wiadomość jest dostarczany, oznacza to, transport, ale też inne funkcje, takie jak co to jest komunikat lub Protokół używany do komunikacji, w tym transportu, ale znacznie więcej niż. Na przykład elementu powiązania niezawodnej sesji jest częścią stosu kanału, ale nie poniżej transportu lub z dot. Ta warstwa abstrakcji odbywa się poprzez wymaganie kanału dołu w stosie, aby dostosować protokół transportowy podstawowej architektury stosu kanału i opierając się na dalsze kanałów w stosie, aby zapewnić funkcji komunikacji, takich jak niezawodność w górę gwarancje i zabezpieczeń.  
  
 Komunikaty przepływ przez stos komunikacji jako <xref:System.ServiceModel.Channels.Message> obiektów. Jak pokazano na rysunku powyżej, kanał dolnej nosi nazwę kanał transportu. Jest to kanał, który jest odpowiedzialny za wysyłanie i odbieranie wiadomości do i z innych stron. Dotyczy to również odpowiedzialny za przekształcania <xref:System.ServiceModel.Channels.Message> obiektów do i z formatu używany do komunikacji z innych stron. Powyżej kanał transportowy może być dowolną liczbę kanały protokołów każdej osoby odpowiedzialnej za podawanie funkcja komunikacji, takich jak gwarantuje niezawodne dostarczanie. Kanały protokołów działają na wiadomości przepływają przez ich w formie <xref:System.ServiceModel.Channels.Message> obiektu. Są zazwyczaj albo przekształcenia komunikatu, na przykład przez dodawanie nagłówków lub szyfrowanie treści, lub wysyłania i odbierania komunikatów sterujących własne protokołu, na przykład potwierdzenia otrzymania.  
  
## <a name="channel-shapes"></a>Kształty kanału  
 Każdy kanał implementuje jeden lub więcej interfejsów, znane jako interfejsy kształtu kanału lub kształtów kanału. Te kształty kanału zawierają metody zorientowane na komunikacji takich jak wysyłania oraz odbierania lub żądania i odpowiedzi czy implementuje kanału i wywołuje użytkownika kanału. Podstawową kształtów kanał jest <xref:System.ServiceModel.Channels.IChannel> interfejsu, który stanowi interfejs, który zapewnia `GetProperty` \<T > Metoda przeznaczony jako mechanizm warstwowej dostęp do dowolnych funkcji udostępnianych przez kanały w stosie. 5 kanału kształty, które rozszerzają <xref:System.ServiceModel.Channels.IChannel> są:  
  
- <xref:System.ServiceModel.Channels.IInputChannel>  
  
- <xref:System.ServiceModel.Channels.IOutputChannel>  
  
- <xref:System.ServiceModel.Channels.IRequestChannel>  
  
- <xref:System.ServiceModel.Channels.IReplyChannel>  
  
- <xref:System.ServiceModel.Channels.IDuplexChannel>  
  
 Ponadto każdy z tych kształtów ma odpowiednika, która rozszerza <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> do obsługi sesji. Są to:  
  
- <xref:System.ServiceModel.Channels.IInputSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IOutputSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IRequestSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IReplySessionChannel>  
  
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel>  
  
 Kształty kanału są wzorowane po niektóre podstawowe wiadomości programu exchange wzorców obsługiwane przez istniejące protokołów transportowych. Na przykład, jednokierunkowe komunikaty odpowiada <xref:System.ServiceModel.Channels.IInputChannel> / <xref:System.ServiceModel.Channels.IOutputChannel> para "żądanie-odpowiedź" odnosi się do <xref:System.ServiceModel.Channels.IRequestChannel> / <xref:System.ServiceModel.Channels.IReplyChannel> pary i dwukierunkową komunikację dwukierunkowego odpowiada <xref:System.ServiceModel.Channels.IDuplexChannel> (który rozszerza zarówno <xref:System.ServiceModel.Channels.IInputChannel> i <xref:System.ServiceModel.Channels.IOutputChannel>).  
  
## <a name="programming-with-the-channel-stack"></a>Programowanie za pomocą stosu kanału  
 Kanał stosy są zwykle tworzone przy użyciu wzorca fabryki, której powiązanie tworzy stosu kanału. Na stronie wysyłania powiązania jest używany do tworzenia <xref:System.ServiceModel.ChannelFactory>, który z kolei stosu kompilacje kanału i zwraca odwołanie do góry kanału w stosie. Aplikacja można następnie używać tego kanału do wysyłania wiadomości. Aby uzyskać więcej informacji, zobacz [programowania na poziomie kanału klienta](../../../../docs/framework/wcf/extending/client-channel-level-programming.md).  
  
 Po stronie odbierającej powiązania jest używany do tworzenia <xref:System.ServiceModel.Channels.IChannelListener>, która nasłuchuje komunikatów przychodzących. <xref:System.ServiceModel.Channels.IChannelListener> Zapewnia komunikatów do nasłuchiwania aplikacji, tworząc kanał stosy i przekazywanie odwołania aplikacji do górnej kanału. Następnie aplikacja użyje tego kanału do odbierania wiadomości przychodzących. Aby uzyskać więcej informacji, zobacz [programowania na poziomie kanału usługi](../../../../docs/framework/wcf/extending/service-channel-level-programming.md).  
  
## <a name="the-channel-object-model"></a>Model obiektu kanału  
 Model obiektu kanału jest podstawowy zestaw interfejsów, które trzeba do zaimplementowania kanały, odbiorniki kanałów i fabryki kanałów. Istnieją również pewne klas bazowych, pod warunkiem, aby pomóc w niestandardowych implementacji.  
  
 Odbiorniki kanałów jest odpowiedzialny za nasłuchiwanie przychodzących wiadomości, a następnie dostarczanie ich do warstwy powyżej za pośrednictwem kanałów utworzonych przez odbiornik kanału.  
  
 Fabryki kanałów jest odpowiedzialny za tworzenie kanałów, które są używane do wysyłania wiadomości i zamknięcie wszystkich kanałów one utworzone po zamknięciu fabryki kanałów.  
  
 <xref:System.ServiceModel.ICommunicationObject> to interfejs core, który definiuje automatu stanów podstawowego, który implementuje wszystkie obiekty komunikacji. <xref:System.ServiceModel.Channels.CommunicationObject> udostępnia implementację tego interfejsu core, która innych klas kanału może pochodzić z zamiast ponownej implementacji interfejsu. Jednak nie jest to wymagane: można zaimplementować niestandardowy kanał <xref:System.ServiceModel.ICommunicationObject> bezpośrednio i dziedziczy <xref:System.ServiceModel.Channels.CommunicationObject>. Żadna z klas na rysunku 3 są traktowane jako część model kanału; są one dostępne implementacje niestandardowym kanale, którzy chcą tworzyć kanały pomocników.  
  
 ![Model kanału](../../../../docs/framework/wcf/extending/media/wcfc-wcfcchannelsigure3omumtreec.gif "wcfc_WCFCChannelsigure3OMUMTreec")  
  
 W poniższych tematach opisano model obiektów kanał, a także różne obszary rozwoju, które pomagają tworzyć niestandardowe kanały.  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Usługa: Odbiorniki kanałów i kanały](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md)|W tym artykule opisano odbiorniki kanałów, które nasłuchiwanie przychodzących kanałów w aplikacji usługi.|  
|[Klient: Fabryki kanałów i kanały](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md)|W tym artykule opisano fabryki kanałów, które tworzą kanały, aby nawiązać połączenie z aplikacją usługi.|  
|[Opis zmian stanu](../../../../docs/framework/wcf/extending/understanding-state-changes.md)|W tym artykule opisano sposób, w jaki <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType> interfejsu modele zmiany stanu w kanałach.|  
|[Wybieranie platformy wymiany komunikatów](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md)|Opisuje sześć wzorców podstawowe wiadomości programu exchange, obsługujące kanałów.|  
|[Obsługa wyjątków i błędów](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)|W tym artykule opisano sposób obsługi błędów i wyjątków w ramach kanałów niestandardowych.|  
|[Konfiguracja i obsługa metadanych](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)|W tym artykule opisano, jak do obsługi kanałów niestandardowych z modelu aplikacji i jak eksportować i importować metadane przy użyciu powiązania i elementy powiązań.|
