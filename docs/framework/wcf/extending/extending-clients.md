---
title: Rozszerzanie klientów
ms.date: 03/30/2017
helpviewer_keywords:
- proxy extensions [WCF]
ms.assetid: 1328c61c-06e5-455f-9ebd-ceefb59d3867
ms.openlocfilehash: 99b4dd5e4acfce8bea4d3c2cae3a53152585675d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857938"
---
# <a name="extending-clients"></a>Rozszerzanie klientów
W aplikacji wywołującej jest odpowiedzialny za tłumaczenie wywołań metod w kodzie aplikacji do wiadomości wychodzących, wypychanie ich do bazowego kanałów, tłumaczenie wyników do wartości zwracane i parametry w warstwy modelu usług Kod aplikacji i zwraca wyniki z powrotem do obiektu wywołującego. Rozszerzenia modelu usługi modyfikować ani implementować wykonywania lub zachowanie komunikacji i funkcje, obejmujące funkcje klienta lub dyspozytora, niestandardowe zachowania, wiadomości i przejmowanie parametru i innych funkcji rozszerzalności.  
  
 W tym temacie opisano sposób użycia <xref:System.ServiceModel.Dispatcher.ClientRuntime> i <xref:System.ServiceModel.Dispatcher.ClientOperation> klas w aplikacji klienckiej Windows Communication Foundation (WCF), aby zmodyfikować domyślne zachowanie wykonywania klienta WCF lub do przechwycenia lub modyfikowanie komunikatów i parametrów lub zwracanych wartości przed lub po wysyłanie i pobieranie ich z warstwy kanału. Aby uzyskać więcej informacji na temat rozszerzania środowiska uruchomieniowego usługi, zobacz [rozszerzanie dyspozytorów](../../../../docs/framework/wcf/extending/extending-dispatchers.md). Aby uzyskać więcej informacji na temat działania, które modyfikują i wstawianie obiektów dostosowywania środowiska uruchomieniowego klienta, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="clients"></a>Klienci  
 Na komputerze klienckim kanału klienta lub obiektu klienta WCF konwertuje wywołań metody opisywanego komunikaty wychodzące i przychodzące wiadomości do wyniki operacji, które są zwracane do aplikacji wywołującej. (Aby uzyskać więcej informacji na temat typów klientów, zobacz [Architektura klienta programu WCF](../../../../docs/framework/wcf/feature-details/client-architecture.md).)  
  
 Typy klienta WCF mają typów środowiska wykonawczego, które obsługują tę funkcję z poziomu punktu końcowego i operacji. Po uruchomieniu operacji <xref:System.ServiceModel.Dispatcher.ClientOperation> tłumaczy obiekty wychodzące do wiadomości, przetwarza interceptory, potwierdza, że wywołanie ruchu wychodzącego jest zgodny z kontraktu docelowego i przekazuje wiadomości wychodzących do <xref:System.ServiceModel.Dispatcher.ClientRuntime>, czyli odpowiedzialne za tworzenie i zarządzanie nimi wychodzących kanałów i kanały dla ruchu przychodzącego w przypadku usługi dwukierunkowe, obsługi przetwarzania (np. nagłówek modyfikacji) bardzo wychodzących wiadomości, przetwarzanie wiadomości interceptory w obu kierunkach i routing ruchu przychodzącego dwustronnego wywołania do odpowiedniego klienta <xref:System.ServiceModel.Dispatcher.DispatchRuntime> obiektu. Zarówno <xref:System.ServiceModel.Dispatcher.ClientOperation> i <xref:System.ServiceModel.Dispatcher.ClientRuntime> świadczenia usług podobnie, gdy wiadomości (w tym błędów) są zwracane do klienta.  
  
 Te dwie klasy środowiska uruchomieniowego są głównym rozszerzenia dostosowywania przetwarzanie obiektów klienta WCF i kanałów. <xref:System.ServiceModel.Dispatcher.ClientRuntime> Klasy pozwala użytkownikom na przechwytywanie i rozszerzyć klienta wykonywanie na wszystkie komunikaty w kontrakcie. <xref:System.ServiceModel.Dispatcher.ClientOperation> Klasy zezwala użytkownikom na przechwytywanie i rozszerzać wykonywania klienta dla wszystkich komunikatów w danej operacji.  
  
 Modyfikowanie właściwości lub wstawianie dostosowania są wykonywane przy użyciu kontraktu punktu końcowego i zachowania operacji. Aby uzyskać więcej informacji na temat używania tego rodzaju zachowania do dostosowania środowiska uruchomieniowego klienta, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="scenarios"></a>Scenariusze  
 Tam wiele możliwych przyczyn, aby rozszerzyć system klienta, w tym:  
  
- Niestandardowy komunikat sprawdzania poprawności. Użytkownik może chcieć wymusić, czy komunikat jest prawidłowa dla niektórych schematu. Można to zrobić poprzez implementację <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interfejsu i przypisywanie wdrożenie <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A> właściwości. Aby uzyskać przykłady, zobacz [jak: Inspekcja lub modyfikowanie komunikatów na kliencie](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md) i [jak: Inspekcja lub modyfikowanie komunikatów na kliencie](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md).  
  
- Rejestrowanie komunikatów niestandardowych. Użytkownik może być do inspekcji i rejestrować pewne zestaw komunikatów aplikacji, które przepływać za pośrednictwem punktu końcowego. Ponadto można to zrobić za pomocą interfejsów interceptor wiadomości.  
  
- Niestandardowy komunikat przekształcenia. Zamiast modyfikowania kodu aplikacji, użytkownik może chcieć zastosowania przekształcenia niektórych wiadomości w czasie wykonywania (na przykład w przypadku wersji). Można to osiągnąć, również z interfejsami interceptor wiadomości.  
  
- Niestandardowy Model danych. Użytkownik może chcieć modelu danych lub serializacji w innym niż obsługiwany przez domyślną programu WCF (to znaczy, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>, i <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> obiektów). Można to zrobić poprzez implementację interfejsów elementu formatującego wiadomości. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType> i <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A?displayProperty=nameWithType> właściwości.  
  
- Walidacja parametru niestandardowego. Użytkownik może chcieć wymusić, że wpisane parametry są prawidłowe (w przeciwieństwie do XML). Można to zrobić przy użyciu Inspektora interfejsów parametru. Aby uzyskać przykład, zobacz [jak: Inspekcja lub modyfikowanie parametrów](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md) lub [sprawdzanie poprawności klienta](../../../../docs/framework/wcf/samples/client-validation.md).  
  
### <a name="using-the-clientruntime-class"></a>Używanie klasy ClientRuntime  
 <xref:System.ServiceModel.Dispatcher.ClientRuntime> Klasy jest punktem rozszerzalności do której można dodać obiektów rozszerzenia, które Przechwytywanie wiadomości i rozszerzyć zachowanie klienta. Przejmowanie obiektów może przetworzyć wszystkie komunikaty w określonej umowy, przetwarzać tylko wiadomości dla określonej operacji, wykonać inicjowania w niestandardowym kanale i implementować inne niestandardowe zachowanie aplikacji.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> Właściwość zwraca obiekt środowiska wykonawczego wysyłania dla klientów zainicjowanych przez usługę wywołania zwrotnego.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.OperationSelector%2A> Właściwości można określić obiektu selektora działania niestandardowe.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ChannelInitializers%2A> Właściwość umożliwia dodanie inicjatora kanału, inspekcji i modyfikacji kanału klienta.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> Właściwości pobiera kolekcję <xref:System.ServiceModel.Dispatcher.ClientOperation> obiektów, do których można dodać niestandardowy komunikat interceptory, które udostępniają funkcje, które są specyficzne dla wiadomości tej operacji.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ManualAddressing%2A> Właściwość umożliwia aplikacji wyłącz niektóre automatyczne adresowania nagłówki, aby bezpośrednio kontrolują adresowania.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.Via%2A> Właściwość ustawia wartość miejsce docelowe dla wiadomości na poziomie transportu, aby obsługiwać rolę pośredników i innych scenariuszy.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> Właściwości pobiera kolekcję <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> obiektów, do których można dodać niestandardowy komunikat interceptory dla wszystkich wiadomości przesyłane przez klienta programu WCF.  
  
 Ponadto istnieje kilka innych właściwości, które pobierają informacje na temat umowy:  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractName%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractNamespace%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractClientType%2A>  
  
 Jeśli klient WCF jest dupleksowy klienta WCF, następujące właściwości również pobrać wywołanie zwrotne informacje o kliencie programu WCF:  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackClientType%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A>  
  
 Można rozszerzyć wykonywania klienta programu WCF dla całego klienta WCF, zapoznaj się z dostępne na właściwości <xref:System.ServiceModel.Dispatcher.ClientRuntime> klasy, aby zobaczyć, czy modyfikowanie właściwości lub implementującej interfejs i dodanie go do właściwości tworzy funkcje szukamy. Po wybraniu określonego rozszerzenia, aby zbudować Wstawianie rozszerzenia odpowiednie <xref:System.ServiceModel.Dispatcher.ClientRuntime> właściwość implementując zachowania klienta, który zapewnia dostęp do <xref:System.ServiceModel.Dispatcher.ClientRuntime> klasy po wywołaniu.  
  
 Obiekty niestandardowego rozszerzenia można wstawić do kolekcji za pomocą zachowania operacji (obiekt, który implementuje <xref:System.ServiceModel.Description.IOperationBehavior>), zachowanie kontraktu (obiekt, który implementuje <xref:System.ServiceModel.Description.IContractBehavior>), lub zachowanie punktu końcowego (obiekt, który implementuje <xref:System.ServiceModel.Description.IEndpointBehavior> ). Instalowanie obiektu zachowanie zostanie dodany do odpowiedniej kolekcji zachowań programowo, w sposób deklaratywny (implementując atrybut niestandardowy), lub poprzez implementację niestandardową <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> obiektu, aby włączyć zachowanie, które ma zostać wstawiony, za pomocą plik konfiguracji aplikacji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Przykłady demonstrujące przejmowanie przez klienta programu WCF można znaleźć [jak: Inspekcja lub modyfikowanie komunikatów na kliencie](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md).  
  
### <a name="using-the-clientoperation-class"></a>Używanie klasy ClientOperation  
 <xref:System.ServiceModel.Dispatcher.ClientOperation> Klasy znajdują się w przypadku zmiany środowiska wykonawczego klienta oraz wstawiania wskaż niestandardowych rozszerzeń, które są w zakresie operacji tylko jednej usługi. (Aby zmodyfikować zachowanie w czasie wykonywania klienta dla wszystkich komunikatów w umowie, użyj <xref:System.ServiceModel.Dispatcher.ClientRuntime> klasy.)  
  
 Użyj <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> właściwości, aby zlokalizować <xref:System.ServiceModel.Dispatcher.ClientOperation> obiekt reprezentujący operację określonej usługi. Następujące właściwości umożliwiają wstawianie niestandardowych obiektów systemu klienta WCF:  
  
- Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> właściwości, aby wstawić własne <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementację dla operacji lub zmodyfikować bieżącego elementu formatującego.  
  
- Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A> właściwości, aby wstawić własne <xref:System.ServiceModel.Dispatcher.IParameterInspector> implementacji lub zmodyfikować bieżący.  
  
 Następujące właściwości umożliwiają modyfikowanie systemu w interakcję z elementu formatującego i inspektorzy parametru niestandardowego:  
  
- Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.SerializeRequest%2A> właściwości do kontrolowania serializacji wiadomości wychodzących.  
  
- Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.DeserializeReply%2A> właściwości do kontrolowania deserializacji wiadomości przychodzącej.  
  
- Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.Action%2A> właściwości do kontrolowania akcji usługi WS-Addressing komunikatu żądania.  
  
- Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.BeginMethod%2A> i <xref:System.ServiceModel.Dispatcher.ClientOperation.EndMethod%2A> do określenia metody klienta WCF, które są skojarzone z operacją asynchroniczną.  
  
- Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.FaultContractInfos%2A> właściwości do pobrania kolekcję, która zawiera typy, które mogą wystąpić w SOAP błędów jako typ szczegółów.  
  
- Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.IsInitiating%2A> i <xref:System.ServiceModel.Dispatcher.ClientOperation.IsTerminating%2A> właściwości w celu kontrolowania, czy sesja jest inicjowana lub podarte odpowiednio podczas wywoływania operacji.  
  
- Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.IsOneWay%2A> właściwości do kontrolowania, czy operacja jest Operacja jednokierunkowa.  
  
- Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.Parent%2A> właściwości można uzyskać, zawierający <xref:System.ServiceModel.Dispatcher.ClientRuntime> obiektu.  
  
- Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.Name%2A> właściwości można odczytać nazwy operacji.  
  
- Użyj <xref:System.ServiceModel.Dispatcher.ClientOperation.SyncMethod%2A> właściwości do kontrolowania, jakiej metody jest mapowany do operacji.  
  
 Można rozszerzyć wykonywania klienta programu WCF dla operacji tylko jedną usługę, zapoznaj się z dostępne na właściwości <xref:System.ServiceModel.Dispatcher.ClientOperation> klasy, aby zobaczyć, czy modyfikowanie właściwości lub implementującej interfejs i dodanie go do właściwości tworzy funkcje szukamy. Po wybraniu określonego rozszerzenia, aby zbudować Wstawianie rozszerzenia odpowiednie <xref:System.ServiceModel.Dispatcher.ClientOperation> właściwość implementując zachowania klienta, który zapewnia dostęp do <xref:System.ServiceModel.Dispatcher.ClientOperation> klasy po wywołaniu. Wewnątrz tego zachowania można następnie zmodyfikować <xref:System.ServiceModel.Dispatcher.ClientRuntime> właściwości zgodnie z wymaganiami.  
  
 Zazwyczaj Implementowanie zachowania operacji (obiekt, który implementuje <xref:System.ServiceModel.Description.IOperationBehavior> interfejsu) sufiksy, ale można także użyć zachowań punktu końcowego i kontrakt zachowania, aby osiągnąć ten sam efekt, znajdując <xref:System.ServiceModel.Description.OperationDescription> dla określonego Operacja i dołączania ma zachowanie. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Aby korzystać z konfiguracji niestandardowe zachowanie, zachowanie podczas instalowania usługi przy użyciu modułu obsługi sekcji konfiguracji zachowanie niestandardowe. Można także zainstalować swoje zachowanie, tworząc atrybutu niestandardowego.  
  
 Przykłady demonstrujące przejmowanie przez klienta programu WCF można znaleźć [jak: Inspekcja lub modyfikowanie parametrów](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Dispatcher.ClientRuntime>
- <xref:System.ServiceModel.Dispatcher.ClientOperation>
- [Instrukcje: Inspekcja lub modyfikowanie komunikatów na kliencie](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md)
- [Instrukcje: Inspekcja lub modyfikowanie parametrów](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md)
