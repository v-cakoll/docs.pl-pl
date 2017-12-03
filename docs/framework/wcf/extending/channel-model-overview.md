---
title: "Przegląd modelu kanału"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: channel model [WCF]
ms.assetid: 07a81e11-3911-4632-90d2-cca99825b5bd
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9be7f226c331ad20c58a06b5c7497c7942db013d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="channel-model-overview"></a>Przegląd modelu kanału
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Kanału stos jest stos warstwy komunikacji z jednego lub więcej kanałów, które przetwarzania komunikatów. W dolnej części stosu jest kanał transportu, który jest odpowiedzialny za dostosowania stosu kanału do transportu źródłowego (na przykład TCP, HTTP, SMTP i inne rodzaje transportu). Kanały zapewniają niskiego poziomu model programowania do wysyłania i odbierania wiadomości. Ten model programowania opiera się na kilka interfejsów i innych typów nazywanych zbiorczo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model kanału. W tym temacie omówiono kształtów kanału, konstrukcji odbiornika kanałów podstawowa (w usłudze) i fabryki kanałów (na kliencie).  
  
## <a name="channel-stack"></a>Kanał stosu  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]punkty końcowe komunikacji z world przy użyciu stosu komunikacji, nazywany stosu kanału. Poniższy diagram porównuje stosu kanału z innych stosy komunikacji, na przykład protokołu TCP/IP.  
  
 ![Model kanału](../../../../docs/framework/wcf/extending/media/wcfc-channelstackhighlevelc.gif "wcfc_ChannelStackHighLevelc")  
  
 Po pierwsze, podobieństwa: W obu przypadkach poszczególnych warstw stosu zawiera niektóre abstrakcji świecie poniżej warstwy i udostępniane tego abstrakcji tylko do warstwy bezpośrednio nad nim. Każda warstwa używa abstrakcji warstwy bezpośrednio poniżej. Również w obu przypadkach komunikując dwóch stosy, każda warstwa komunikuje się z warstwy odpowiedni ze stosu, na przykład warstwie IP komunikuje się z adresu IP i warstwy TCP z warstwy TCP i tak dalej.  
  
 Teraz, różnice: stosu podczas TCP została zaprojektowana w celu zapewnienia abstrakcję sieci fizycznej, stosu kanału ma na celu zapewnienie abstrakcję nie tylko jak wiadomość zostanie dostarczona, oznacza to, transport, ale także inne funkcje, takie jak zawartość wiadomość lub który protokół używany do komunikacji, łącznie z transportem, ale znacznie więcej niż. Na przykład elementu wiązania niezawodnej sesji jest częścią stosu kanału, ale nie jest poniżej transportu lub dot. Ta warstwa abstrakcji jest to osiągane przez wymaganie kanału dołu w stosie, aby dostosować podstawowy protokół transportu do architektury stosu kanału i następnie polegania na dalsze kanały w górę stosu do zapewnienia komunikacji funkcje, takie jak niezawodności gwarancje i zabezpieczeń.  
  
 Komunikaty przepływ przez stosu komunikacji jako <xref:System.ServiceModel.Channels.Message> obiektów. Jak pokazano na rysunku powyżej, kanał dolnej jest nazywany kanał transportu. Jest kanału, który jest odpowiedzialny za wysyłanie i odbieranie wiadomości do i z innych stron. Dotyczy to również odpowiedzialność przekształcania <xref:System.ServiceModel.Channels.Message> obiektu do i z formatu używanego do komunikacji z innych stron. Powyżej kanał transportu może być dowolną liczbę kanały protokołów każdy odpowiedzialny za zapewnienie funkcji komunikacji niezawodnej dostarczania gwarancje. Kanały protokołów działać na przepływających przez nich w formie wiadomości <xref:System.ServiceModel.Channels.Message> obiektu. One zazwyczaj albo przekształcenie wiadomości, na przykład przez dodawanie nagłówków lub szyfruje treść, lub wysyłania i odbierania wiadomości kontroli własnych protokołu, na przykład potwierdzenia otrzymania.  
  
## <a name="channel-shapes"></a>Kształty kanału  
 Każdy kanał implementuje jeden lub więcej interfejsów nazywana interfejsy kształtu kanału lub kształtów kanału. Te kształty kanału Podaj metody zorientowane na komunikację takich jak wysyłać i odbierać lub żądania i odpowiedzi czy implementuje kanału i wywołuje użytkownika kanału. U podstawy kształtów kanał jest <xref:System.ServiceModel.Channels.IChannel> interfejsu, który jest interfejs, który udostępnia `GetProperty` \<T > Metoda służyć jako mechanizm warstwowego dostęp do dowolnych funkcji udostępnianych przez kanały w stosie. Kanał pięciu kształtów, które rozszerzają <xref:System.ServiceModel.Channels.IChannel> są:  
  
-   <xref:System.ServiceModel.Channels.IInputChannel>  
  
-   <xref:System.ServiceModel.Channels.IOutputChannel>  
  
-   <xref:System.ServiceModel.Channels.IRequestChannel>  
  
-   <xref:System.ServiceModel.Channels.IReplyChannel>  
  
-   <xref:System.ServiceModel.Channels.IDuplexChannel>  
  
 Ponadto każdy z tych kształtów ma równoważny, rozszerzający <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> do obsługi sesji. Są to:  
  
-   <xref:System.ServiceModel.Channels.IInputSessionChannel>  
  
-   <xref:System.ServiceModel.Channels.IOutputSessionChannel>  
  
-   <xref:System.ServiceModel.Channels.IRequestSessionChannel>  
  
-   <xref:System.ServiceModel.Channels.IReplySessionChannel>  
  
-   <xref:System.ServiceModel.Channels.IDuplexSessionChannel>  
  
 Kształty kanału są deseniem po niektóre podstawowe wiadomości exchange wzorce obsługiwane przez istniejącą protokołów transportu. Na przykład wiadomości jednokierunkowe odpowiada <xref:System.ServiceModel.Channels.IInputChannel> / <xref:System.ServiceModel.Channels.IOutputChannel> para "żądanie-odpowiedź" odpowiada <xref:System.ServiceModel.Channels.IRequestChannel> / <xref:System.ServiceModel.Channels.IReplyChannel> pary i dwukierunkowej komunikacji dupleksowej odpowiada <xref:System.ServiceModel.Channels.IDuplexChannel> (który rozszerza zarówno <xref:System.ServiceModel.Channels.IInputChannel> i <xref:System.ServiceModel.Channels.IOutputChannel>).  
  
## <a name="programming-with-the-channel-stack"></a>Programowanie za pomocą kanału stosu  
 Stosy kanału są zwykle tworzone przy użyciu wzorca fabryki, której powiązanie tworzy stosu kanału. Po stronie wysyłającej powiązania jest używany do tworzenia <xref:System.ServiceModel.ChannelFactory>, który z kolei stosu kompilacje kanału i zwraca odwołanie do góry kanału w stosie. Aplikacji można następnie używać tego kanału do wysyłania wiadomości. Aby uzyskać więcej informacji, zobacz [programowania na poziomie kanału klienta](../../../../docs/framework/wcf/extending/client-channel-level-programming.md).  
  
 Po stronie odbierania powiązania jest używany do tworzenia <xref:System.ServiceModel.Channels.IChannelListener>, która nasłuchuje przychodzących wiadomości. <xref:System.ServiceModel.Channels.IChannelListener> Zawiera komunikaty do nasłuchiwania aplikacji, tworząc stosy kanału i przekazywanie odwołanie aplikacji do górnej kanału. Następnie aplikacja użyje tego kanału do odbierania wiadomości przychodzących. Aby uzyskać więcej informacji, zobacz [programowania na poziomie kanału usługi](../../../../docs/framework/wcf/extending/service-channel-level-programming.md).  
  
## <a name="the-channel-object-model"></a>Model obiektu kanału  
 Model kanału obiektu jest podstawowy zestaw interfejsów wymagany, aby zaimplementować kanały, odbiorniki kanałów i fabryk kanałów. Brak niektórych klas podstawowych podane w implementacji niestandardowych.  
  
 Odbiorniki kanałów są zobowiązani do nasłuchiwania dla komunikatów przychodzących, a następnie ich dostarczania do warstwy powyżej kanałami utworzone przez odbiornik kanału.  
  
 Fabryk kanałów, które są zobowiązani do tworzenia kanałów, które są używane do wysyłania wiadomości i zamknięcie wszystkich kanałów one tworzone po zamknięciu fabryki kanałów.  
  
 <xref:System.ServiceModel.ICommunicationObject>to interfejs core, który definiuje automatu stanów podstawowego, który implementuje wszystkie obiekty komunikacji. <xref:System.ServiceModel.Channels.CommunicationObject>udostępnia implementację tego interfejsu core innych klas kanału może pochodzić od zamiast ponownie implementowania interfejsu. Jednak nie jest to wymagane: można zaimplementować w niestandardowym kanale <xref:System.ServiceModel.ICommunicationObject> bezpośrednio i nie dziedziczy z <xref:System.ServiceModel.Channels.CommunicationObject>. Żadna z klas na rysunku 3 są traktowane jako część modelu kanału; są one dostępne dla obiektów implementujących niestandardowym kanale, którzy chcą tworzyć kanały pomocników.  
  
 ![Model kanału](../../../../docs/framework/wcf/extending/media/wcfc-wcfcchannelsigure3omumtreec.gif "wcfc_WCFCChannelsigure3OMUMTreec")  
  
 W poniższych tematach opisano model obiektu kanału, a także różnych obszarach programowanie, które ułatwiają tworzenie niestandardowych kanałów.  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Usługa: Odbiorniki kanałów i kanały](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md)|W tym artykule opisano odbiorniki kanałów, które nasłuchuje przychodzących kanałów w aplikacji usługi.|  
|[Klienta: Fabryk kanałów i kanały](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md)|W tym artykule opisano fabryk kanałów, które tworzenia kanałów nawiązać połączenia z aplikacją usługi.|  
|[Opis zmian stanu](../../../../docs/framework/wcf/extending/understanding-state-changes.md)|Opisuje sposób <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType> interfejsu modele zmian stanu kanałów.|  
|[Wybieranie platformy wymiany komunikatów](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md)|Opisuje sześć wzorce exchange podstawowe wiadomości obsługujących kanałów.|  
|[Obsługa wyjątków i błędów](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)|Opisuje sposób obsługi błędów i wyjątków w kanałów niestandardowych.|  
|[Konfiguracja i Obsługa metadanych](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)|Opisuje sposób obsługują kanałów niestandardowych z modelu aplikacji oraz eksportowanie i Importowanie metadanych za pomocą powiązania i elementy powiązań.|
