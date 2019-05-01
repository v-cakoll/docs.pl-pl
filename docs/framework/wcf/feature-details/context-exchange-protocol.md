---
title: Protokół wymiany kontekstu
ms.date: 03/30/2017
ms.assetid: 3dfd38e0-ae52-491c-94f4-7a862b9843d4
ms.openlocfilehash: a6bc0ac45282d94a6aea8dbbdb5a7d34163c692e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857353"
---
# <a name="context-exchange-protocol"></a>Protokół wymiany kontekstu
W tej sekcji opisano protokół wymiany kontekstu, które są wprowadzone w programie Windows Communication Foundation (WCF) w wersji .NET Framework w wersji 3.5. Ten protokół umożliwia kanału klienta akceptować kontekst dostarczonych przez usługę i zastosować je do wszystkich kolejnych żądań wysyłanych za pośrednictwem tego samego wystąpienia kanału klienta usługi. Implementacja protokół wymiany kontekstu, można użyć jednej z dwóch następujących mechanizmów propagowanie kontekstu między serwerem a klientem: Pliki cookie protokołu HTTP lub nagłówek SOAP.  
  
 Protokół wymiany kontekstu jest zaimplementowana w niestandardowym kanale warstwy. Kanał komunikuje się kontekstu do i z warstwy aplikacji przy użyciu <xref:System.ServiceModel.Channels.ContextMessageProperty> właściwości. Dla transmisji między punktami końcowymi wartość kontekstu jest serializowana jako nagłówek SOAP w warstwie kanału albo konwertowana do lub z właściwości komunikatu, które reprezentują żądania HTTP i odpowiedzi. W tym ostatnim przypadku oczekuje się, że jeden z niższych warstwach kanału konwertuje właściwości komunikatów żądań i odpowiedzi HTTP do i z plików cookie protokołu HTTP, odpowiednio. Wybór mechanizm używany do wymiany kontekstu jest wykonywane przy użyciu <xref:System.ServiceModel.Channels.ContextExchangeMechanism> właściwość <xref:System.ServiceModel.Channels.ContextBindingElement>. Prawidłowe wartości to `HttpCookie` lub `SoapHeader`.  
  
 Na komputerze klienckim, wystąpienie kanału może działać w dwóch trybach zgodnie z ustawieniami właściwości kanału <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A>.  
  
## <a name="mode-1-channel-context-management"></a>Tryb 1: Kanał zarządzania kontekstem  
 Jest to domyślny tryb gdzie <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> ustawiono `true`. W tym trybie kanał kontekstu zarządza kontekstu i zapisuje w jego okres istnienia pamięci podręcznej kontekstu. Z kanału za pomocą właściwości kanału można pobrać kontekstu `IContextManager` przez wywołanie metody `GetContext` metody. Kanał można również wstępnie zainicjowana przy użyciu określonego kontekstu przed otwierana, wywołując `SetContext` metody właściwości kanału. Gdy kanał jest inicjowany z kontekstem nie można zresetować.  
  
 Oto lista invariants w tym trybie:  
  
- Dowolne próba zresetowania przy użyciu kontekstu `SetContext` po zgłasza otwarty kanał <xref:System.InvalidOperationException>.  
  
- Dowolne próba wysłania kontekstu przy użyciu <xref:System.ServiceModel.Channels.ContextMessageProperty> w wychodzących wiadomościach zgłasza <xref:System.InvalidOperationException>.  
  
- Gdy wiadomość zostaje odebrana od serwera przy użyciu określonego kontekstu, gdy kanał został już zainicjowany przy użyciu określonego kontekstu, powoduje to <xref:System.ServiceModel.ProtocolException>.  
  
    > [!NOTE]
    >  Jest otrzymywać początkowej kontekstu z serwera, tylko wtedy, gdy kanał zostanie otwarty bez żadnego kontekstu ustawiony w sposób jawny.  
  
- <xref:System.ServiceModel.Channels.ContextMessageProperty> Na przychodzący komunikat jest zawsze wartość null.  
  
## <a name="mode-2-application-context-management"></a>Tryb 2: Zarządzanie kontekstem aplikacji  
 Jest to tryb podczas <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> ustawiono `false`. W tym trybie kanał kontekstu nie zarządza kontekstu. Odpowiada za aplikację do pobrania, zarządzania i zastosować kontekst za pomocą <xref:System.ServiceModel.Channels.ContextMessageProperty>. Dowolne próba wywołania `GetContext` lub `SetContext` skutkuje <xref:System.InvalidOperationException>.  
  
 Niezależnie od tego trybu jest wybierany fabryki kanałów klienta obsługuje <xref:System.ServiceModel.Channels.IRequestChannel>, <xref:System.ServiceModel.Channels.IRequestSessionChannel>, i <xref:System.ServiceModel.Channels.IDuplexSessionChannel> komunikatu wzorców programu exchange.  
  
 W usłudze jest odpowiedzialny za kontekstu dostarczonych przez klienta na komunikaty przychodzące do konwertowania wystąpienia kanału <xref:System.ServiceModel.Channels.ContextMessageProperty>. Właściwość wiadomości mogą następnie dostęp do warstwy aplikacji lub innych kanałów dalsze się w stosie wywołań. Kanały usługi również zezwolić na użycie warstwy aplikacji, aby określić nową wartość kontekstu do jest propagowany z powrotem do klienta przez dołączenie <xref:System.ServiceModel.Channels.ContextMessageProperty> komunikat odpowiedzi. Ta właściwość jest konwertowana na nagłówek SOAP lub pliku cookie HTTP, który zawiera kontekst, który zależy od konfiguracji powiązania. Usługa obsługuje odbiornika kanału <xref:System.ServiceModel.Channels.IReplyChannel>, <xref:System.ServiceModel.Channels.IReplySessionChannel>, i <xref:System.ServiceModel.Channels.IReplySessionChannel> komunikatu wzorców programu exchange.  
  
 Protokół wymiany kontekstu wprowadzono nowy `wsc:Context` nagłówek SOAP reprezentujący informacje o kontekście podczas plików cookie protokołu HTTP nie są używane do propagowania kontekstu. Schemat nagłówka kontekst zezwala na dowolną liczbę elementów podrzędnych, każdy z klucza typu ciąg i zawartość ciągu. Oto przykład nagłówka kontekstu.  
  
 `<Context xmlns="http://schemas.microsoft.com/ws/2006/05/context">`  
  
 `<property name="myContext">context-2</property>`  
  
 `</Context>`  
  
 W `HttpCookie` trybu plików cookie są ustawiane przy użyciu `SetCookie` nagłówka. Nazwa pliku cookie jest `WscContext`. Wartość pliku cookie jest Base64 kodowanie `wsc:Context` nagłówka. Ta wartość jest ujęty w cudzysłów.  
  
 Wartość kontekstu muszą być chronione przed modyfikacjami, podczas przesyłania z tego samego powodu nagłówków WS-Addressing są chronione — nagłówek służy do określania miejsca możesz wysyłać żądania do usługi. `wsc:Context` Nagłówek w związku z tym jest wymagany cyfrowo podpisane lub podpisane i szyfrowane na poziomie protokołu SOAP lub transportu, gdy powiązanie oferuje możliwości ochrony wiadomości. W przypadku używania plików cookie protokołu HTTP do propagowania kontekstu one powinny być chronione za pomocą zabezpieczeń transportu.  
  
 Punkty końcowe usługi, które wymagają obsługi protokół wymiany kontekstu można tworzyć i jawne w opublikowanych zasad. Dwa nowe asercji zasad zostały wprowadzone do reprezentowania potrzebę klient obsługuje protokół wymiany kontekstu na poziomie protokołu SOAP lub włączyć obsługę plików cookie protokołu HTTP. Generowanie tych potwierdzenia do zasad w usłudze jest kontrolowany przez wartość <xref:System.ServiceModel.Channels.ContextBindingElement.ContextExchangeMechanism%2A> właściwości w następujący sposób:  
  
- Aby uzyskać <xref:System.ServiceModel.Channels.ContextExchangeMechanism.ContextSoapHeader>, generowany jest potwierdzenie następujących:  
  
    ```xml  
    <IncludeContext   
    xmlns="http://schemas.microsoft.com/ws/2006/05/context"  
    protectionLevel="Sign" />  
    ```  
  
- Aby uzyskać <xref:System.ServiceModel.Channels.ContextExchangeMechanism.HttpCookie>, generowany jest potwierdzenie następujących:  
  
    ```xml  
    <HttpUseCookie xmlns="http://schemas.xmlsoap.org/soap/http"/>  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik dotyczący współpracy protokołów usług sieci Web](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)
