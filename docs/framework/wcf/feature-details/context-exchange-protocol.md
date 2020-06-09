---
title: Protokół wymiany kontekstu
ms.date: 03/30/2017
ms.assetid: 3dfd38e0-ae52-491c-94f4-7a862b9843d4
ms.openlocfilehash: 86d2a19b086fbd5d6be6f1a084bfd7aaace0e250
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597439"
---
# <a name="context-exchange-protocol"></a>Protokół wymiany kontekstu
W tej sekcji opisano protokół wymiany kontekstu wprowadzony w Windows Communication Foundation (WCF) Release .NET Framework wersja 3,5. Ten protokół umożliwia kanałowi klienta akceptowanie kontekstu dostarczonego przez usługę i zastosowanie go do wszystkich kolejnych żądań wysyłanych przez to samo wystąpienie kanału klienta. Implementacja protokołu wymiany kontekstu może używać jednego z następujących dwóch mechanizmów do propagowania kontekstu między serwerem a klientem: pliki cookie HTTP lub nagłówek protokołu SOAP.  
  
 Protokół wymiany kontekstu jest implementowany w niestandardowej warstwie kanału. Kanał komunikuje kontekst z i z warstwy aplikacji przy użyciu <xref:System.ServiceModel.Channels.ContextMessageProperty> właściwości. W przypadku przesyłania między punktami końcowymi wartość kontekstu jest serializowana jako nagłówek protokołu SOAP w warstwie kanału lub konwertowana na lub z właściwości wiadomości reprezentujących żądanie HTTP i odpowiedź. W tym drugim przypadku oczekuje się, że jedna z warstw źródłowych kanałów konwertuje właściwości żądania HTTP i komunikatu odpowiedzi na i z plików cookie protokołu HTTP. Wybór mechanizmu służącego do wymiany kontekstu odbywa się przy użyciu <xref:System.ServiceModel.Channels.ContextExchangeMechanism> właściwości w <xref:System.ServiceModel.Channels.ContextBindingElement> . Prawidłowe wartości to `HttpCookie` lub `SoapHeader` .  
  
 Na kliencie wystąpienie kanału może działać w dwóch trybach na podstawie ustawień właściwości kanału <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> .  
  
## <a name="mode-1-channel-context-management"></a>Tryb 1: zarządzanie kontekstem kanału  
 Jest to domyślny tryb, w którym <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> ustawiono `true` . W tym trybie kanał kontekstu zarządza kontekstem i buforuje kontekst w trakcie okresu istnienia. Kontekst można pobrać ze swojej właściwości kanału za pośrednictwem kanału, `IContextManager` wywołując `GetContext` metodę. Kanał może być również wstępnie zainicjowany przy użyciu określonego kontekstu przed otwarciem przez wywołanie `SetContext` metody we właściwości kanału. Po zainicjowaniu kanału z kontekstem nie można go zresetować.  
  
 Poniżej znajduje się lista nieodmian w tym trybie:  
  
- Każda próba zresetowania kontekstu przy użyciu `SetContext` po otwarciu kanału zgłasza <xref:System.InvalidOperationException> .  
  
- Wszystkie próby wysłania kontekstu przy użyciu <xref:System.ServiceModel.Channels.ContextMessageProperty> w wiadomości wychodzącej zgłaszają <xref:System.InvalidOperationException> .  
  
- Jeśli wiadomość zostanie odebrana z serwera z określonym kontekstem, gdy kanał został już zainicjowany z określonym kontekstem, spowoduje to <xref:System.ServiceModel.ProtocolException> .  
  
    > [!NOTE]
    > Należy uzyskać początkowy kontekst z serwera tylko wtedy, gdy kanał jest otwarty bez jawnie określonego kontekstu.  
  
- <xref:System.ServiceModel.Channels.ContextMessageProperty>Komunikat przychodzący ma zawsze wartość null.  
  
## <a name="mode-2-application-context-management"></a>Tryb 2: zarządzanie kontekstem aplikacji  
 Jest to tryb, gdy <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> jest ustawiony na `false` . W tym trybie kanał kontekstu nie zarządza kontekstem. Jest on odpowiedzialny za pobieranie, zarządzanie i stosowanie kontekstu przy użyciu <xref:System.ServiceModel.Channels.ContextMessageProperty> . Każda próba wywołania `GetContext` lub `SetContext` wyniku w <xref:System.InvalidOperationException> .  
  
 Niezależnie od tego, który tryb jest wybierany przez fabrykę kanałów klienta obsługuje <xref:System.ServiceModel.Channels.IRequestChannel> , <xref:System.ServiceModel.Channels.IRequestSessionChannel> oraz <xref:System.ServiceModel.Channels.IDuplexSessionChannel> wzorce wymiany komunikatów.  
  
 W usłudze wystąpienie kanału jest odpowiedzialne za konwertowanie kontekstu dostarczonego przez klienta na komunikaty przychodzące do <xref:System.ServiceModel.Channels.ContextMessageProperty> . Do właściwości komunikatu można następnie uzyskać dostęp za pomocą warstwy aplikacji lub innych kanałów w dalszej kolejności w stosie wywołań. Kanały usług umożliwiają także określenie nowej wartości kontekstu, która ma być propagowana do klienta przez dołączenie <xref:System.ServiceModel.Channels.ContextMessageProperty> do komunikatu odpowiedzi. Ta właściwość jest konwertowana na nagłówek protokołu SOAP lub plik cookie HTTP zawierający kontekst, który zależy od konfiguracji powiązania. Odbiornik kanału usługi obsługuje <xref:System.ServiceModel.Channels.IReplyChannel> <xref:System.ServiceModel.Channels.IReplySessionChannel> <xref:System.ServiceModel.Channels.IReplySessionChannel> wzorce wymiany komunikatów, i.  
  
 Protokół wymiany kontekstu wprowadza nowy `wsc:Context` nagłówek protokołu SOAP do reprezentowania informacji kontekstowych, gdy pliki cookie protokołu HTTP nie są używane do propagowania kontekstu. Schemat nagłówka kontekstu umożliwia dowolną liczbę elementów podrzędnych, z których każdy ma klucz ciągu i zawartość ciągu. Poniżej znajduje się przykład nagłówka kontekstu.  
  
 `<Context xmlns="http://schemas.microsoft.com/ws/2006/05/context">`  
  
 `<property name="myContext">context-2</property>`  
  
 `</Context>`  
  
 W trybie w przypadku `HttpCookie` pliki cookie są ustawiane przy użyciu `SetCookie` nagłówka. Nazwa pliku cookie to `WscContext` . Wartość pliku cookie jest kodowaniem Base64 `wsc:Context` nagłówka. Ta wartość jest ujęta w cudzysłów.  
  
 Wartość kontekstu musi być chroniona przed modyfikacją podczas przesyłania. z tego samego powodu nagłówki WS-Addressing są chronione — nagłówek służy do określania, gdzie należy wysłać żądanie do usługi. W `wsc:Context` związku z tym nagłówek musi być cyfrowo podpisany lub podpisany i zaszyfrowany na poziomie protokołu SOAP lub transportu, gdy powiązanie oferuje funkcję ochrony wiadomości. Gdy pliki cookie protokołu HTTP są używane do propagowania kontekstu, powinny być chronione przy użyciu zabezpieczeń transportu.  
  
 Punkty końcowe usługi, które wymagają obsługi protokołu wymiany kontekstu, mogą jawnie wprowadzać je w opublikowane zasady. Wprowadzono dwa nowe potwierdzenia zasad reprezentujące wymaganie, aby klient obsługiwał protokół wymiany kontekstu na poziomie protokołu SOAP lub włączyć obsługę plików cookie protokołu HTTP. Generowanie tych potwierdzeń w zasadach w usłudze jest kontrolowane przez wartość <xref:System.ServiceModel.Channels.ContextBindingElement.ContextExchangeMechanism%2A> właściwości w następujący sposób:  
  
- Dla programu <xref:System.ServiceModel.Channels.ContextExchangeMechanism.ContextSoapHeader> generowane jest następujące potwierdzenie:  
  
    ```xml  
    <IncludeContext
    xmlns="http://schemas.microsoft.com/ws/2006/05/context"  
    protectionLevel="Sign" />  
    ```  
  
- Dla programu <xref:System.ServiceModel.Channels.ContextExchangeMechanism.HttpCookie> generowane jest następujące potwierdzenie:  
  
    ```xml  
    <HttpUseCookie xmlns="http://schemas.xmlsoap.org/soap/http"/>  
    ```  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik dotyczący współpracy protokołów usług sieci Web](web-services-protocols-interoperability-guide.md)
