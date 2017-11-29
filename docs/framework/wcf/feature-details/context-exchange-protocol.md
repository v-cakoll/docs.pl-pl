---
title: "Protokół wymiany kontekstu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3dfd38e0-ae52-491c-94f4-7a862b9843d4
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 582ff24f9f7935f6bbb143685826fc10df1ab432
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="context-exchange-protocol"></a>Protokół wymiany kontekstu
W tej sekcji opisano protokół wymiany kontekstu wprowadzone w systemie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] wersji. Protokół ten umożliwia kanału klienta zaakceptować kontekst dostarczonych przez usługę i zastosować je do wszystkich kolejnych żądań do tej usługi, wysyłane za pośrednictwem tego samego wystąpienia kanału klienta. Implementacja protokołu wymiany kontekstu można użyć jednej z dwóch następujących mechanizmów propagację kontekstu między serwerem a klientem: plików cookie protokołu HTTP lub nagłówka SOAP.  
  
 Protokół wymiany kontekstu jest zaimplementowana w niestandardowym kanale warstwy. Kanał komunikacji kontekstu do i z warstwy aplikacji przy użyciu <xref:System.ServiceModel.Channels.ContextMessageProperty> właściwości. Transmisji między punktami końcowymi wartość kontekstu jest serializowany jako nagłówka SOAP w warstwie kanału albo przekonwertować do lub z właściwości wiadomości, które reprezentują żądania HTTP i odpowiedzi. W drugim przypadku oczekuje się, że jeden z podstawowych warstwach kanału konwertuje właściwości komunikatów żądań i odpowiedzi HTTP do i z plików cookie protokołu HTTP, odpowiednio. Wybór mechanizmu używanego do wymiany kontekstu jest wykonywane przy użyciu <xref:System.ServiceModel.Channels.ContextExchangeMechanism> właściwość <xref:System.ServiceModel.Channels.ContextBindingElement>. Prawidłowe wartości to `HttpCookie` lub `SoapHeader`.  
  
 Na komputerze klienckim wystąpienia kanału może działać w dwóch trybach zgodnie z ustawieniami właściwości kanału <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A>.  
  
## <a name="mode-1-channel-context-management"></a>Tryb 1: Zarządzania kontekstem kanału  
 Jest to domyślny tryb gdzie <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> ma ustawioną wartość `true`. W tym trybie kanał kontekstu zarządza kontekstu i buforuje kontekst przez jego okres istnienia. Z kanału za pomocą właściwości kanału można pobrać kontekstu `IContextManager` przez wywołanie metody `GetContext` metody. Kanał można również wstępnie zainicjowane z określonego kontekstu przed otwierany przez wywołanie metody `SetContext` metody dla właściwości kanału. Gdy kanał jest inicjowany z kontekstu nie może być resetowany.  
  
 Poniżej przedstawiono listę invariants w tym trybie:  
  
-   Próby resetowania przy użyciu kontekstu `SetContext` po kanał został otwarty zgłasza <xref:System.InvalidOperationException>.  
  
-   Próby wysłania kontekstu przy użyciu <xref:System.ServiceModel.Channels.ContextMessageProperty> w komunikacie wychodzącym zgłasza <xref:System.InvalidOperationException>.  
  
-   Jeśli wiadomość zostanie odebrana z serwera z określonego kontekstu, gdy kanał został już zainicjowany z określonym kontekstem, powoduje to <xref:System.ServiceModel.ProtocolException>.  
  
    > [!NOTE]
    >  Jest początkowej kontekstu odbierania z serwera, tylko wtedy, gdy kanał jest otwarty bez żadnego kontekstu ustawiony w sposób jawny.  
  
-   <xref:System.ServiceModel.Channels.ContextMessageProperty> Na komunikat przychodzący ma zawsze wartość null.  
  
## <a name="mode-2-application-context-management"></a>Tryb 2: Zarządzanie kontekstem aplikacji  
 Jest to tryb podczas <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> ma ustawioną wartość `false`. W tym trybie kanał kontekstu nie zarządza kontekstu. Odpowiedzialność aplikacji do pobrania, zarządzania i zastosować kontekstu za pomocą <xref:System.ServiceModel.Channels.ContextMessageProperty>. Próby wywołania `GetContext` lub `SetContext` powoduje <xref:System.InvalidOperationException>.  
  
 Niezależnie od tego, który tryb jest wybierany fabryki kanału klienta obsługuje <xref:System.ServiceModel.Channels.IRequestChannel>, <xref:System.ServiceModel.Channels.IRequestSessionChannel>, i <xref:System.ServiceModel.Channels.IDuplexSessionChannel> komunikatu wzorce programu exchange.  
  
 W usłudze jest odpowiedzialny za konwertowanie kontekstu dostarczany przez klienta w komunikatach przychodzących do wystąpienia kanału <xref:System.ServiceModel.Channels.ContextMessageProperty>. Właściwość wiadomości mają dostęp przez warstwę aplikacji lub innych kanałów się bardziej szczegółowo w stosie wywołań. Kanały usługi również umożliwić warstwy aplikacji określić nową wartość kontekstu być propagowane do klienta przez dołączenie <xref:System.ServiceModel.Channels.ContextMessageProperty> komunikat odpowiedzi. Ta właściwość jest konwertowana na nagłówka SOAP lub plik cookie HTTP, który zawiera kontekst, w zależności od konfiguracji powiązania. Usługa obsługuje odbiornika kanału <xref:System.ServiceModel.Channels.IReplyChannel>, <xref:System.ServiceModel.Channels.IReplySessionChannel>, i <xref:System.ServiceModel.Channels.IReplySessionChannel> komunikatu wzorce programu exchange.  
  
 Protokół wymiany kontekstu wprowadzono nowy `wsc:Context` nagłówek SOAP reprezentujący informacje o kontekście podczas plików cookie protokołu HTTP nie są używane do propagacji kontekstu. Zezwala schemat nagłówka kontekstu dla dowolnej liczby elementów podrzędnych, każda z ciągu klucza i zawartość ciągu. Oto przykład nagłówka kontekstu.  
  
 `<Context xmlns="http://schemas.microsoft.com/ws/2006/05/context">`  
  
 `<property name="myContext">context-2</property>`  
  
 `</Context>`  
  
 W czasie `HttpCookie` trybie pliki cookie są ustawiane przy użyciu `SetCookie` nagłówka. Nazwa pliku cookie jest `WscContext`. Wartość pliku cookie jest Base64 kodowanie `wsc:Context` nagłówka. Ta wartość jest ujęta w cudzysłowy.  
  
 Wartość kontekstu musi być chroniony przed modyfikacją podczas przesyłania z tego samego powodu są chronione nagłówków WS-Addressing — nagłówek służy do określenia miejsca wysłane żądanie usługi. `wsc:Context` Nagłówka w związku z tym będzie musiał być cyfrowo podpisane lub podpisane i zaszyfrowane na poziomie protokołu SOAP albo transportu podczas wiązania oferuje możliwości ochrony wiadomości. W przypadku używania plików cookie protokołu HTTP propagację kontekstu one powinny być chronione za pomocą zabezpieczeń transportu.  
  
 Punkty końcowe usługi, które wymagają obsługi protokół wymiany kontekstu można tworzyć jawne opublikowanych zasad. Dwa nowe potwierdzeń zasad zostały wprowadzone do reprezentowania wymaganie klient obsługuje protokół wymiany kontekstu na poziomie protokołu SOAP lub włączyć obsługę plików cookie HTTP. Generowanie potwierdzeń te do zasad w usłudze jest kontrolowany przez wartość <xref:System.ServiceModel.Channels.ContextBindingElement.ContextExchangeMechanism%2A> właściwości w następujący sposób:  
  
-   Aby uzyskać <xref:System.ServiceModel.Channels.ContextExchangeMechanism.ContextSoapHeader>, generowany jest potwierdzenie następujące:  
  
    ```xml  
    <IncludeContext   
    xmlns="http://schemas.microsoft.com/ws/2006/05/context"  
    protectionLevel="Sign" />  
    ```  
  
-   Aby uzyskać <xref:System.ServiceModel.Channels.ContextExchangeMechanism.HttpCookie>, generowany jest potwierdzenie następujące:  
  
    ```xml  
    <HttpUseCookie xmlns="http://schemas.xmlsoap.org/soap/http"/>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik dotyczący współpracy protokołów usług sieci Web](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)
