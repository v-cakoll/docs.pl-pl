---
title: Rozszerzanie klientów
ms.date: 03/30/2017
helpviewer_keywords:
- proxy extensions [WCF]
ms.assetid: 1328c61c-06e5-455f-9ebd-ceefb59d3867
ms.openlocfilehash: 95340a9ae6ac5a3face81d5fe6f61ea134fb6ad2
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806659"
---
# <a name="extending-clients"></a>Rozszerzanie klientów
W aplikacji wywołującej jest odpowiedzialny za tłumaczenia wywołań metod w kodzie aplikacji w komunikatach wychodzących, wypychanie ich do podstawowej kanałów, tłumaczenia wyników do wartości zwracanych do edycji i parametrów w warstwy modelu usług Kod aplikacji, a następnie zwraca wyniki z powrotem do wywołującego. Rozszerzenia modelu usługi zmodyfikować, lub zaimplementuj wykonywania lub zachowanie komunikacji i funkcje dotyczące klienta lub dyspozytora funkcje, niestandardowe zachowania, wiadomości i przechwytywaniu parametru i innych funkcji rozszerzalności.  
  
 W tym temacie opisano sposób użycia <xref:System.ServiceModel.Dispatcher.ClientRuntime> i <xref:System.ServiceModel.Dispatcher.ClientOperation> klasy w aplikacji klienta usługi Windows Communication Foundation (WCF), aby zmodyfikować domyślne zachowanie wykonywania klienta WCF lub do przechwycenia lub modyfikowanie komunikatów i parametrów lub zwracanych wartości przed lub po wysyłania lub pobierania ich z warstwy kanału. Aby uzyskać więcej informacji na temat rozszerzania środowiska uruchomieniowego usługi, zobacz [rozszerzanie dyspozytorów](../../../../docs/framework/wcf/extending/extending-dispatchers.md). Aby uzyskać więcej informacji dotyczących zachowania, które modyfikowania i wstawiania dostosowania obiektów w czasie wykonywania klienta, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="clients"></a>Klienci  
 Na komputerze klienckim kanału klienta lub obiektu klienta WCF konwertuje wywołań metod wysyła komunikaty wychodzące i przychodzące komunikaty do wyników operacji, które są zwracane do aplikacji wywołującej. (Aby uzyskać więcej informacji na temat typów klientów, zobacz [Architektura klienta WCF](../../../../docs/framework/wcf/feature-details/client-architecture.md).)  
  
 Typy klienta WCF mieć typów środowiska wykonawczego, które obsługują tę funkcję na poziomie punktu końcowego i operacji. Gdy aplikacja wywołuje operację <xref:System.ServiceModel.Dispatcher.ClientOperation> tłumaczy obiekty wychodzące do wiadomości, przetwarza interceptory, potwierdza, że odpowiada kontraktu docelowych wywołań wychodzących i przekazuje komunikat wychodzący <xref:System.ServiceModel.Dispatcher.ClientRuntime>, który jest odpowiedzialne za tworzenie i zarządzanie kanałów wychodzących i kanały przychodzące w przypadku usługi dwukierunkowe, obsługa bardzo wychodzący komunikatów przetwarzania (np. nagłówek modyfikacji), przetwarzania interceptory wiadomości w obu kierunkach i routing ruchu przychodzącego dwustronnego wywołania do odpowiedniego klienta <xref:System.ServiceModel.Dispatcher.DispatchRuntime> obiektu. Zarówno <xref:System.ServiceModel.Dispatcher.ClientOperation> i <xref:System.ServiceModel.Dispatcher.ClientRuntime> świadczenia usług podobne, gdy komunikaty (w tym błędy) są zwracane do klienta.  
  
 Te dwie klasy środowiska uruchomieniowego są głównego rozszerzeniem, aby dostosować przetwarzanie obiektów klienta WCF i kanałów. <xref:System.ServiceModel.Dispatcher.ClientRuntime> Klasa umożliwia użytkownikom przechwytywać i rozszerzyć wykonywania klienta na wszystkie wiadomości w umowie. <xref:System.ServiceModel.Dispatcher.ClientOperation> Klasa umożliwia użytkownikom przechwytywać i rozszerzyć wykonywania klienta dla wszystkich wiadomości w danej operacji.  
  
 Modyfikowanie właściwości lub wstawianie dostosowania są wykonywane przy użyciu kontraktu punktu końcowego i zachowania operacji. Aby uzyskać więcej informacji na temat używania tego rodzaju zachowania do dostosowania środowiska uruchomieniowego klienta, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="scenarios"></a>Scenariusze  
 Istnieje wiele przyczyn rozszerzenie systemu klienta w tym:  
  
-   Niestandardowy komunikat weryfikacji. Użytkownik może chcieć wymuszania, że wiadomość jest prawidłowy dla niektórych schematu. Można to zrobić z zastosowaniem <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interfejsu i przypisywanie wykonania <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A> właściwości. Przykłady można znaleźć [porady: inspekcja lub modyfikowanie komunikatów na komputerze klienckim](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md) i [porady: inspekcja lub modyfikowanie komunikatów na kliencie](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md).  
  
-   Rejestrowanie komunikatów niestandardowych. Użytkownik może chcieć inspekcji i logowania niektórych zestaw komunikatów aplikacji, które wpływają za pośrednictwem punktu końcowego. Ponadto można to zrobić z interfejsami interceptora wiadomości.  
  
-   Niestandardowy komunikat przekształcenia. Zamiast modyfikacji kodu aplikacji, użytkownik może chcieć przekształcane niektórych wiadomości w czasie wykonywania (na przykład w przypadku wersji). Można to zrobić, ponownie z interfejsami interceptora wiadomości.  
  
-   Model danych niestandardowych. Użytkownik może być w modelu danych lub serializacji innym niż obsługiwany przez domyślną w programie WCF (to znaczy, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>, i <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> obiektów). Można to zrobić dzięki implementacji interfejsów program formatujący wiadomości. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType> i <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A?displayProperty=nameWithType> właściwości.  
  
-   Sprawdzanie poprawności parametru niestandardowego. Użytkownik może chcieć wymusić czy parametrów typu są prawidłowe (a nie XML). Można to zrobić za pomocą interfejsów inspektora parametru. Na przykład, zobacz [jak: inspekcja lub modyfikowanie parametrów](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md) lub [weryfikacji klienta](../../../../docs/framework/wcf/samples/client-validation.md).  
  
### <a name="using-the-clientruntime-class"></a>Używanie klasy ClientRuntime  
 <xref:System.ServiceModel.Dispatcher.ClientRuntime> Klasa jest punkcie rozszerzenia, do której można dodać rozszerzenia obiektów, które Przechwytywanie wiadomości i rozszerzyć zachowanie klienta. Przechwycenie obiektów można przetworzyć wszystkie wiadomości w określonej umowy, przetwarzać tylko komunikaty dla określonej operacji, wykonać inicjacji kanału niestandardowych i implementacji inne zachowanie aplikacji klienta.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> Właściwość zwraca obiekt środowiska wykonawczego wysyłania dla klientów usługi inicjowane przez wywołanie zwrotne.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.OperationSelector%2A> Właściwość akceptuje obiektu selektora operacja niestandardowa.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ChannelInitializers%2A> Właściwość umożliwia dodanie inicjatora kanału, który można sprawdzić lub zmodyfikować kanału klienta.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> Właściwości pobiera kolekcję <xref:System.ServiceModel.Dispatcher.ClientOperation> obiektów, do których można dodać interceptory niestandardowe wiadomości, które zapewniają funkcje specyficzne dla wiadomości w tej operacji.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ManualAddressing%2A> Właściwość umożliwia aplikacji wyłączyć niektóre automatyczne nagłówki adresowania bezpośrednio kontrolować adresowania.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.Via%2A> Właściwość ustawia wartości docelowej wiadomości na poziomie transportu do obsługi pośredników i innych scenariuszy.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> Właściwości pobiera kolekcję <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> obiektów, do których można dodać interceptory niestandardową wiadomość dla wszystkich komunikatów przesyłanych za pomocą klienta WCF.  
  
 Ponadto istnieje wiele innych właściwości, które pobrać informacji o kontraktu:  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractName%2A>  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractNamespace%2A>  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractClientType%2A>  
  
 Jeśli klient WCF dupleksu klienta WCF, następujące właściwości również pobierać informacje o kliencie WCF wywołania zwrotnego:  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackClientType%2A>  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A>  
  
 Aby rozszerzyć wykonywania klienta WCF na cały klienta WCF, przejrzyj dostępne na właściwości <xref:System.ServiceModel.Dispatcher.ClientRuntime> klasy, aby zobaczyć, czy modyfikowanie właściwości lub implementacji interfejsów i dodanie go do właściwości tworzy funkcji szukamy. Po wybraniu określonego rozszerzenia do tworzenia, Wstaw rozszerzenie do odpowiedniej <xref:System.ServiceModel.Dispatcher.ClientRuntime> właściwości zaimplementowanie zachowanie klienta, która zapewnia dostęp do <xref:System.ServiceModel.Dispatcher.ClientRuntime> klasy po wywołaniu.  
  
 Obiekty rozszerzenia niestandardowego można wstawić do kolekcji przy użyciu zachowanie operacji (obiekt, który implementuje <xref:System.ServiceModel.Description.IOperationBehavior>), zachowanie kontraktu (obiekt, który implementuje <xref:System.ServiceModel.Description.IContractBehavior>), lub zachowanie punktu końcowego (obiekt, który implementuje <xref:System.ServiceModel.Description.IEndpointBehavior> ). Instalowanie zachowanie jest dodać obiektu do odpowiedniej kolekcji zachowań programowo, deklaratywnego (implementując atrybutu niestandardowego), lub dzięki implementacji niestandardowego <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> obiekt, aby umożliwić działanie ma zostać wstawiony przy użyciu plik konfiguracji aplikacji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Przykłady ilustrujące przechwyceniu przez klienta WCF, zobacz [porady: inspekcja lub modyfikowanie komunikatów na kliencie](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md).  
  
### <a name="using-the-clientoperation-class"></a>Używanie klasy ClientOperation  
 <xref:System.ServiceModel.Dispatcher.ClientOperation> Klasy jest lokalizacji dla klienta środowiska wykonawczego modyfikacji i wstawiania wskaż niestandardowych rozszerzeń, które są w zakresie operacji tylko jedna usługa. (Aby zmodyfikować zachowanie środowiska wykonawczego klienta dla wszystkich wiadomości w umowie, użyj <xref:System.ServiceModel.Dispatcher.ClientRuntime> klasy.)  
  
 Użyj <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> właściwości, aby zlokalizować <xref:System.ServiceModel.Dispatcher.ClientOperation> obiekt reprezentujący operację określonej usługi. Następujące właściwości umożliwiają Wstaw niestandardowe obiekty w systemie klienta WCF:  
  
-   Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> właściwości, aby wstawić niestandardowego <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> wykonania operacji lub zmodyfikować bieżącego elementu formatującego.  
  
-   Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A> właściwości, aby wstawić niestandardowego <xref:System.ServiceModel.Dispatcher.IParameterInspector> implementacji lub zmodyfikować bieżący.  
  
 Następujące właściwości umożliwiają modyfikowanie systemu w interakcji z elementu formatującego i inspektorzy parametru niestandardowego:  
  
-   Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.SerializeRequest%2A> właściwości do sterowania serializacją wiadomości wychodzącej.  
  
-   Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.DeserializeReply%2A> właściwości do kontrolowania deserializacji wiadomości przychodzącej.  
  
-   Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.Action%2A> właściwości do kontrolowania akcji WS-Addressing komunikatu żądania.  
  
-   Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.BeginMethod%2A> i <xref:System.ServiceModel.Dispatcher.ClientOperation.EndMethod%2A> do określenia, które metody klienta WCF są skojarzone z operacji asynchronicznej.  
  
-   Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.FaultContractInfos%2A> właściwości można pobrać kolekcję, która zawiera typy, które mogą być wyświetlane w SOAP błędów typu szczegółów.  
  
-   Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.IsInitiating%2A> i <xref:System.ServiceModel.Dispatcher.ClientOperation.IsTerminating%2A> właściwości, aby określić, czy sesja jest zainicjowana lub podarte odpowiednio po wywołaniu operacji.  
  
-   Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.IsOneWay%2A> właściwości do kontrolowania, czy operacja jest Operacja jednokierunkowa.  
  
-   Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.Parent%2A> właściwości uzyskanie zawierający <xref:System.ServiceModel.Dispatcher.ClientRuntime> obiektu.  
  
-   Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.Name%2A> właściwości można uzyskać nazwy operacji.  
  
-   Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.SyncMethod%2A> właściwości do kontrolowania, która metoda jest zamapowana do operacji.  
  
 Aby rozszerzyć wykonywania klienta WCF na działanie tylko jedna usługa, przejrzyj właściwości dostępne na <xref:System.ServiceModel.Dispatcher.ClientOperation> klasy, aby zobaczyć, czy modyfikowanie właściwości lub implementacji interfejsów i dodanie go do właściwości tworzy funkcje są wyszukiwanie. Po wybraniu określonego rozszerzenia do tworzenia, Wstaw rozszerzenie do odpowiedniej <xref:System.ServiceModel.Dispatcher.ClientOperation> właściwości zaimplementowanie zachowanie klienta, która zapewnia dostęp do <xref:System.ServiceModel.Dispatcher.ClientOperation> klasy po wywołaniu. Wewnątrz tego zachowania można następnie zmodyfikować <xref:System.ServiceModel.Dispatcher.ClientRuntime> właściwości zgodnie z własnymi wymaganiami.  
  
 Zazwyczaj implementacja zachowanie operacji (obiekt, który implementuje <xref:System.ServiceModel.Description.IOperationBehavior> interfejsu) sufiksy, ale można też użyć zachowania punktu końcowego i kontraktu zachowania, aby osiągnąć ten sam efekt dzięki umieszczeniu <xref:System.ServiceModel.Description.OperationDescription> dla określonego kontekstu Operacja i dołączanie zachowanie istnieje. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Aby korzystać z konfiguracji niestandardowe zachowanie, zachowanie podczas instalowania programu przy użyciu modułu obsługi sekcji konfiguracji zachowania niestandardowego. Można także zainstalować Twoje zachowanie, tworząc atrybutu niestandardowego.  
  
 Przykłady ilustrujące przechwyceniu przez klienta WCF, zobacz [jak: inspekcja lub zmodyfikować parametrów](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Dispatcher.ClientRuntime>  
 <xref:System.ServiceModel.Dispatcher.ClientOperation>  
 [Instrukcje: inspekcja lub modyfikowanie komunikatów na kliencie](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md)  
 [Instrukcje: inspekcja lub modyfikowanie parametrów](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md)
