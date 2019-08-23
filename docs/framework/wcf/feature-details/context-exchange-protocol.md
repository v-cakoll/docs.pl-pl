---
title: Protokół wymiany kontekstu
ms.date: 03/30/2017
ms.assetid: 3dfd38e0-ae52-491c-94f4-7a862b9843d4
ms.openlocfilehash: 19780cccc74f8c3615dc844e47be7613ca5f8bc1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911204"
---
# <a name="context-exchange-protocol"></a>Protokół wymiany kontekstu
W tej sekcji opisano protokół wymiany kontekstu wprowadzony w Windows Communication Foundation (WCF) Release .NET Framework wersja 3,5. Ten protokół umożliwia kanałowi klienta akceptowanie kontekstu dostarczonego przez usługę i zastosowanie go do wszystkich kolejnych żądań wysyłanych przez to samo wystąpienie kanału klienta. Implementacja protokołu wymiany kontekstu może używać jednego z następujących dwóch mechanizmów do propagowania kontekstu między serwerem a klientem: Pliki cookie protokołu HTTP lub nagłówek protokołu SOAP.  
  
 Protokół wymiany kontekstu jest implementowany w niestandardowej warstwie kanału. Kanał komunikuje kontekst z i z warstwy aplikacji przy użyciu <xref:System.ServiceModel.Channels.ContextMessageProperty> właściwości. W przypadku przesyłania między punktami końcowymi wartość kontekstu jest serializowana jako nagłówek protokołu SOAP w warstwie kanału lub konwertowana na lub z właściwości wiadomości reprezentujących żądanie HTTP i odpowiedź. W tym drugim przypadku oczekuje się, że jedna z warstw źródłowych kanałów konwertuje właściwości żądania HTTP i komunikatu odpowiedzi na i z plików cookie protokołu HTTP. Wybór mechanizmu służącego do wymiany kontekstu odbywa się przy użyciu <xref:System.ServiceModel.Channels.ContextExchangeMechanism> właściwości <xref:System.ServiceModel.Channels.ContextBindingElement>w. Prawidłowe wartości to `HttpCookie` lub `SoapHeader`.  
  
 Na kliencie wystąpienie kanału może działać w dwóch trybach na podstawie ustawień właściwości <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A>kanału.  
  
## <a name="mode-1-channel-context-management"></a>Tryb 1: Zarządzanie kontekstem kanału  
 Jest to domyślny tryb, w <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> którym `true`ustawiono. W tym trybie kanał kontekstu zarządza kontekstem i buforuje kontekst w trakcie okresu istnienia. Kontekst można pobrać ze swojej właściwości `IContextManager` kanału za pośrednictwem kanału, `GetContext` wywołując metodę. Kanał może być również wstępnie zainicjowany przy użyciu określonego kontekstu przed otwarciem przez wywołanie `SetContext` metody we właściwości kanału. Po zainicjowaniu kanału z kontekstem nie można go zresetować.  
  
 Poniżej znajduje się lista nieodmian w tym trybie:  
  
- Każda próba zresetowania kontekstu przy użyciu `SetContext` po otwarciu kanału <xref:System.InvalidOperationException>zgłasza.  
  
- Wszystkie próby wysłania kontekstu przy użyciu <xref:System.ServiceModel.Channels.ContextMessageProperty> w wiadomości wychodzącej <xref:System.InvalidOperationException>zgłaszają.  
  
- Jeśli wiadomość zostanie odebrana z serwera z określonym kontekstem, gdy kanał został już zainicjowany z określonym kontekstem, spowoduje <xref:System.ServiceModel.ProtocolException>to.  
  
    > [!NOTE]
    > Należy uzyskać początkowy kontekst z serwera tylko wtedy, gdy kanał jest otwarty bez jawnie określonego kontekstu.  
  
- <xref:System.ServiceModel.Channels.ContextMessageProperty> Komunikat przychodzący ma zawsze wartość null.  
  
## <a name="mode-2-application-context-management"></a>Tryb 2: Zarządzanie kontekstem aplikacji  
 Jest to tryb, gdy <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> jest ustawiony na `false`. W tym trybie kanał kontekstu nie zarządza kontekstem. Jest on odpowiedzialny za pobieranie, zarządzanie i stosowanie kontekstu przy użyciu <xref:System.ServiceModel.Channels.ContextMessageProperty>. Każda próba wywołania `GetContext` lub `SetContext` wyniku w <xref:System.InvalidOperationException>.  
  
 Niezależnie od tego, który tryb jest wybierany przez fabrykę <xref:System.ServiceModel.Channels.IRequestSessionChannel>kanałów klienta <xref:System.ServiceModel.Channels.IDuplexSessionChannel> obsługuje <xref:System.ServiceModel.Channels.IRequestChannel>, oraz wzorce wymiany komunikatów.  
  
 W usłudze wystąpienie kanału jest odpowiedzialne za konwertowanie kontekstu dostarczonego przez klienta na komunikaty przychodzące do <xref:System.ServiceModel.Channels.ContextMessageProperty>. Do właściwości komunikatu można następnie uzyskać dostęp za pomocą warstwy aplikacji lub innych kanałów w dalszej kolejności w stosie wywołań. Kanały usług umożliwiają także określenie nowej wartości kontekstu, która ma być propagowana do klienta przez dołączenie <xref:System.ServiceModel.Channels.ContextMessageProperty> do komunikatu odpowiedzi. Ta właściwość jest konwertowana na nagłówek protokołu SOAP lub plik cookie HTTP zawierający kontekst, który zależy od konfiguracji powiązania. Odbiornik kanału usługi obsługuje <xref:System.ServiceModel.Channels.IReplyChannel>wzorce wymiany komunikatów, <xref:System.ServiceModel.Channels.IReplySessionChannel> <xref:System.ServiceModel.Channels.IReplySessionChannel>i.  
  
 Protokół wymiany kontekstu wprowadza nowy `wsc:Context` nagłówek protokołu SOAP do reprezentowania informacji kontekstowych, gdy pliki cookie protokołu HTTP nie są używane do propagowania kontekstu. Schemat nagłówka kontekstu umożliwia dowolną liczbę elementów podrzędnych, z których każdy ma klucz ciągu i zawartość ciągu. Poniżej znajduje się przykład nagłówka kontekstu.  
  
 `<Context xmlns="http://schemas.microsoft.com/ws/2006/05/context">`  
  
 `<property name="myContext">context-2</property>`  
  
 `</Context>`  
  
 W trybie `HttpCookie` w przypadku pliki cookie są ustawiane `SetCookie` przy użyciu nagłówka. Nazwa pliku cookie to `WscContext`. Wartość pliku cookie jest kodowaniem `wsc:Context` Base64 nagłówka. Ta wartość jest ujęta w cudzysłów.  
  
 Wartość kontekstu musi być chroniona przed modyfikacją podczas przesyłania. z tego samego powodu nagłówki WS-Addressing są chronione — nagłówek służy do określania, gdzie należy wysłać żądanie do usługi. W `wsc:Context` związku z tym nagłówek musi być cyfrowo podpisany lub podpisany i zaszyfrowany na poziomie protokołu SOAP lub transportu, gdy powiązanie oferuje funkcję ochrony wiadomości. Gdy pliki cookie protokołu HTTP są używane do propagowania kontekstu, powinny być chronione przy użyciu zabezpieczeń transportu.  
  
 Punkty końcowe usługi, które wymagają obsługi protokołu wymiany kontekstu, mogą jawnie wprowadzać je w opublikowane zasady. Wprowadzono dwa nowe potwierdzenia zasad reprezentujące wymaganie, aby klient obsługiwał protokół wymiany kontekstu na poziomie protokołu SOAP lub włączyć obsługę plików cookie protokołu HTTP. Generowanie tych potwierdzeń w zasadach w usłudze jest kontrolowane przez wartość <xref:System.ServiceModel.Channels.ContextBindingElement.ContextExchangeMechanism%2A> właściwości w następujący sposób:  
  
- Dla <xref:System.ServiceModel.Channels.ContextExchangeMechanism.ContextSoapHeader>programu generowane jest następujące potwierdzenie:  
  
    ```xml  
    <IncludeContext   
    xmlns="http://schemas.microsoft.com/ws/2006/05/context"  
    protectionLevel="Sign" />  
    ```  
  
- Dla <xref:System.ServiceModel.Channels.ContextExchangeMechanism.HttpCookie>programu generowane jest następujące potwierdzenie:  
  
    ```xml  
    <HttpUseCookie xmlns="http://schemas.xmlsoap.org/soap/http"/>  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik dotyczący współpracy protokołów usług sieci Web](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)
