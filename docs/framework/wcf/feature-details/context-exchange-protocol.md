---
title: Protokół wymiany kontekstu
ms.date: 03/30/2017
ms.assetid: 3dfd38e0-ae52-491c-94f4-7a862b9843d4
ms.openlocfilehash: 00adb68d96f77ce0953811d13b5377ec4ed1e0ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185263"
---
# <a name="context-exchange-protocol"></a>Protokół wymiany kontekstu
W tej sekcji opisano protokół wymiany kontekstu wprowadzony w programie .NET Framework w wersji 3.5 w wersji programu Windows Communication Foundation (WCF). Ten protokół umożliwia kanałowi klienta zaakceptowanie kontekstu dostarczonego przez usługę i zastosowanie go do wszystkich kolejnych żądań do tej usługi wysłanej za pomocą tego samego wystąpienia kanału klienta. Implementacja protokołu wymiany kontekstu może używać jednego z następujących dwóch mechanizmów do propagowania kontekstu między serwerem a klientem: pliki cookie HTTP lub nagłówek SOAP.  
  
 Protokół wymiany kontekstu jest implementowany w warstwie kanału niestandardowego. Kanał komunikuje kontekst do i z <xref:System.ServiceModel.Channels.ContextMessageProperty> warstwy aplikacji za pomocą właściwości. W przypadku transmisji między punktami końcowymi wartość kontekstu jest serializowana jako nagłówek PROTOKOŁU SOAP w warstwie kanału lub konwertowana na lub z właściwości wiadomości, które reprezentują żądanie i odpowiedź HTTP. W tym ostatnim przypadku oczekuje się, że jedna z podstawowych warstw kanału konwertuje właściwości żądania HTTP i komunikatu odpowiedzi odpowiednio do i z plików cookie HTTP. Wybór mechanizmu używanego do wymiany kontekstu <xref:System.ServiceModel.Channels.ContextExchangeMechanism> odbywa <xref:System.ServiceModel.Channels.ContextBindingElement>się przy użyciu właściwości na . Prawidłowe `HttpCookie` wartości `SoapHeader`są lub .  
  
 Na kliencie wystąpienie kanału może działać w dwóch trybach na podstawie <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A>ustawień właściwości kanału, .  
  
## <a name="mode-1-channel-context-management"></a>Tryb 1: Zarządzanie kontekstem kanału  
 Jest to tryb <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> domyślny, `true`w którym jest ustawiona na . W tym trybie kanał kontekstu zarządza kontekstem i buforuje kontekst w okresie jego istnienia. Kontekst można pobrać z kanału za `IContextManager` pośrednictwem `GetContext` właściwości kanału, wywołując metodę. Kanał można również wstępnie zainicjować z określonym kontekście `SetContext` przed otwarciem przez wywołanie metody na właściwości kanału. Po zainicjowaniu kanału w kontekście nie można go zresetować.  
  
 Poniżej znajduje się lista invariants w tym trybie:  
  
- Każda próba zresetowania `SetContext` kontekstu przy użyciu po <xref:System.InvalidOperationException>otwarciu kanału rzuca .  
  
- Każda próba wysłania kontekstu <xref:System.ServiceModel.Channels.ContextMessageProperty> przy użyciu w <xref:System.InvalidOperationException>wiadomości wychodzącej zgłasza .  
  
- Jeśli wiadomość zostanie odebrana z serwera o określonym kontekście, gdy kanał został już <xref:System.ServiceModel.ProtocolException>zainicjowany z określonym kontekstem, powoduje to .  
  
    > [!NOTE]
    > Należy odbierać kontekst początkowy z serwera tylko wtedy, gdy kanał jest otwarty bez żadnego kontekstu ustawionego jawnie.  
  
- Na <xref:System.ServiceModel.Channels.ContextMessageProperty> przychodzącej wiadomości jest zawsze null.  
  
## <a name="mode-2-application-context-management"></a>Tryb 2: Zarządzanie kontekstem aplikacji  
 Jest to tryb, <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> który `false`jest ustawiony na . W tym trybie kanał kontekstowy nie zarządza kontekstem. Obowiązkiem aplikacji jest pobieranie kontekstu, zarządzanie nim i <xref:System.ServiceModel.Channels.ContextMessageProperty>stosowanie go za pomocą programu . Każda próba `GetContext` wywołania `SetContext` lub <xref:System.InvalidOperationException>powoduje .  
  
 Bez względu na to, który tryb <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IRequestSessionChannel>jest <xref:System.ServiceModel.Channels.IDuplexSessionChannel> wybrany, obsługuje fabryka kanałów klienta i wzorce wymiany wiadomości.  
  
 W usłudze wystąpienie kanału jest odpowiedzialne za konwersję kontekstu dostarczonego <xref:System.ServiceModel.Channels.ContextMessageProperty>przez klienta na przychodzące wiadomości do . Właściwość message może być następnie dostępny przez warstwę aplikacji lub innych kanałów dalej w stosie wywołań. Kanały usługi umożliwiają również warstwy aplikacji, aby określić nową wartość kontekstu, <xref:System.ServiceModel.Channels.ContextMessageProperty> które mają być propagowane z powrotem do klienta przez dołączenie do komunikatu odpowiedzi. Ta właściwość jest konwertowana na nagłówek SOAP lub plik cookie HTTP, który zawiera kontekst, który zależy od konfiguracji powiązania. Odbiornik kanału usługi <xref:System.ServiceModel.Channels.IReplyChannel>obsługuje <xref:System.ServiceModel.Channels.IReplySessionChannel>, <xref:System.ServiceModel.Channels.IReplySessionChannel> i wzorce wymiany wiadomości.  
  
 Protokół wymiany kontekstu wprowadza `wsc:Context` nowy nagłówek SOAP do reprezentowania informacji kontekstowych, gdy pliki cookie HTTP nie są używane do propagowania kontekstu. Schemat nagłówka kontekstu umożliwia dowolną liczbę elementów podrzędnych, z których każdy z kluczem ciągu i zawartością ciągu. Poniżej przedstawiono przykład nagłówka kontekstu.  
  
 `<Context xmlns="http://schemas.microsoft.com/ws/2006/05/context">`  
  
 `<property name="myContext">context-2</property>`  
  
 `</Context>`  
  
 W `HttpCookie` trybie pliki cookie `SetCookie` są ustawiane za pomocą nagłówka. Nazwa pliku `WscContext`cookie to . Wartość pliku cookie jest base64 kodowania `wsc:Context` nagłówka. Ta wartość jest ujęta w cudzysłowie.  
  
 Wartość kontekstu musi być chroniona przed modyfikacją podczas przesyłania z tego samego powodu Nagłówki adresowania WS są chronione — nagłówek jest używany do określenia, gdzie wysłać żądanie do usługi. Nagłówek `wsc:Context` jest zatem wymagane, aby być podpisane cyfrowo lub podpisane i zaszyfrowane na poziomie protokołu SOAP lub transportu, gdy powiązanie oferuje możliwość ochrony wiadomości. Gdy pliki cookie HTTP są używane do propagowania kontekstu, powinny być chronione przy użyciu zabezpieczeń transportu.  
  
 Punkty końcowe usługi, które wymagają obsługi protokołu wymiany kontekstu może uczynić go jawnym w opublikowanych zasad. Wprowadzono dwa nowe potwierdzenia zasad w celu reprezentowania wymagań dla klienta do obsługi protokołu wymiany kontekstu na poziomie PROTOKOŁU SOAP lub w celu włączenia obsługi plików cookie HTTP. Generowanie tych potwierdzeń do zasad usługi jest kontrolowane <xref:System.ServiceModel.Channels.ContextBindingElement.ContextExchangeMechanism%2A> przez wartość właściwości w następujący sposób:  
  
- Dla <xref:System.ServiceModel.Channels.ContextExchangeMechanism.ContextSoapHeader>, generowane jest następujące twierdzenie:  
  
    ```xml  
    <IncludeContext
    xmlns="http://schemas.microsoft.com/ws/2006/05/context"  
    protectionLevel="Sign" />  
    ```  
  
- Dla <xref:System.ServiceModel.Channels.ContextExchangeMechanism.HttpCookie>, generowane jest następujące twierdzenie:  
  
    ```xml  
    <HttpUseCookie xmlns="http://schemas.xmlsoap.org/soap/http"/>  
    ```  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik dotyczący współpracy protokołów usług sieci Web](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)
