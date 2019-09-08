---
title: Rozszerzanie klientów
ms.date: 03/30/2017
helpviewer_keywords:
- proxy extensions [WCF]
ms.assetid: 1328c61c-06e5-455f-9ebd-ceefb59d3867
ms.openlocfilehash: 91277e1a4d0a1d001d62d677dbd087bec5d875f0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797163"
---
# <a name="extending-clients"></a>Rozszerzanie klientów
W aplikacji wywołującej warstwa modelu usług jest odpowiedzialna za tłumaczenie wywołań metod w kodzie aplikacji na komunikaty wychodzące, wypychanie ich do kanałów bazowych, tłumaczenie wyników z powrotem do wartości zwracanych i parametrów wyjściowych w kod aplikacji i zwracają wyniki z powrotem do obiektu wywołującego. Rozszerzenia modelu usług modyfikują lub implementują zachowanie wykonywania lub komunikacji oraz funkcje, w tym funkcje klienta lub dyspozytora, niestandardowe zachowania, przechwycenie komunikatów i parametrów oraz inne funkcje rozszerzalności.  
  
 W tym temacie opisano sposób użycia <xref:System.ServiceModel.Dispatcher.ClientRuntime> klas i <xref:System.ServiceModel.Dispatcher.ClientOperation> w aplikacji klienckiej programu Windows Communication Foundation (WCF) do modyfikowania domyślnego zachowania klienta programu WCF lub przechwytywania lub modyfikowania komunikatów, parametrów lub wartości zwracanych przed lub po wysłaniu lub pobraniu z warstwy kanału. Aby uzyskać więcej informacji na temat rozszerzania środowiska uruchomieniowego usługi, zobacz [rozszerzanie dyspozytorów](extending-dispatchers.md). Aby uzyskać więcej informacji na temat zachowań modyfikujących i wstawiających obiekty dostosowania do środowiska uruchomieniowego klienta, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="clients"></a>Klienci  
 Na kliencie obiekt klienta programu WCF lub kanał klienta konwertuje wywołania metody na komunikaty wychodzące i komunikaty przychodzące do wyników operacji, które są zwracane do aplikacji wywołującej. (Aby uzyskać więcej informacji na temat typów klientów, zobacz [Architektura klienta WCF](../feature-details/client-architecture.md)).  
  
 Typy klientów WCF mają typy środowiska uruchomieniowego, które obsługują tę funkcję. Gdy aplikacja wywołuje operację, program <xref:System.ServiceModel.Dispatcher.ClientOperation> tłumaczy obiekty wychodzące na komunikat, przetwarza przechwycenia, potwierdza, że wywołanie wychodzące jest zgodne z umową docelową i przekazuje komunikat wychodzący <xref:System.ServiceModel.Dispatcher.ClientRuntime>do, który jest odpowiedzialny za tworzenie kanałów wychodzących (i kanałów przychodzących w przypadku usług dupleksowych) oraz zarządzanie nimi, obsługa dodatkowego przetwarzania komunikatów wychodzących (takich jak modyfikowanie nagłówka), przetwarzanie przechwyceń komunikatów w obu kierunkach i kierowanie ruchu przychodzącego wywołania dupleksowe do odpowiedniego obiektu po stronie <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klienta. Zarówno, <xref:System.ServiceModel.Dispatcher.ClientRuntime> jak i oferują podobne usługi, gdy komunikaty (w tym błędy) są zwracane do klienta. <xref:System.ServiceModel.Dispatcher.ClientOperation>  
  
 Te dwie klasy środowiska uruchomieniowego są głównym rozszerzeniem umożliwiającym dostosowanie przetwarzania obiektów i kanałów klienta programu WCF. <xref:System.ServiceModel.Dispatcher.ClientRuntime> Klasa umożliwia użytkownikom przechwycenie i rozbudowanie wykonywania klienta we wszystkich wiadomościach kontraktu. <xref:System.ServiceModel.Dispatcher.ClientOperation> Klasa umożliwia użytkownikom przechwycenie i rozbudowanie wykonywania klienta dla wszystkich komunikatów w danej operacji.  
  
 Modyfikowanie właściwości lub wstawianie dostosowań odbywa się za pomocą kontraktów, punktów końcowych i zachowań operacji. Aby uzyskać więcej informacji na temat sposobu użycia tego typu zachowań do wykonywania dostosowań w środowisku uruchomieniowym klienta, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="scenarios"></a>Scenariusze  
 Istnieje kilka powodów, dla których można zwiększyć system klienta, w tym:  
  
- Niestandardowa weryfikacja komunikatów. Użytkownik może chcieć wymusić, że komunikat jest prawidłowy dla określonego schematu. Można to zrobić, implementując <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interfejs i przypisując implementację <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A> do właściwości. Aby zapoznać się z [przykładami, zobacz How to: Inspekcja lub modyfikowanie komunikatów na kliencie](how-to-inspect-or-modify-messages-on-the-client.md) oraz [instrukcje: Inspekcja lub modyfikowanie komunikatów na kliencie](how-to-inspect-or-modify-messages-on-the-client.md).  
  
- Niestandardowe rejestrowanie komunikatów. Użytkownik może chcieć sprawdzić i zarejestrować część komunikatów aplikacji przesyłanych przez punkt końcowy. Można to również zrobić przy użyciu interfejsów interceptora komunikatów.  
  
- Niestandardowe przekształcenia komunikatów. Zamiast modyfikować kod aplikacji, użytkownik może chcieć zastosować pewne przekształcenia do wiadomości w środowisku uruchomieniowym (na przykład w celu przechowywania wersji). Można to zrobić ponownie przy użyciu interfejsów interceptora komunikatów.  
  
- Niestandardowy model danych. Użytkownik może chcieć mieć model danych lub serializacji inny niż te obsługiwane domyślnie w programie WCF (mianowicie <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>,, i <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> obiekty). Można to zrobić, implementując interfejsy programu formatującego komunikatów. Aby uzyskać więcej informacji, <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType> zobacz <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A?displayProperty=nameWithType> i właściwość.  
  
- Walidacja parametrów niestandardowych. Użytkownik może chcieć wymusić, że wpisane parametry są prawidłowe (w przeciwieństwie do kodu XML). Można to zrobić za pomocą interfejsów inspektora parametrów. Aby zapoznać się z przykładem, zobacz [How to: Sprawdź lub Modyfikuj parametry](how-to-inspect-or-modify-parameters.md) lub [Walidacja klienta](../samples/client-validation.md).  
  
### <a name="using-the-clientruntime-class"></a>Korzystanie z klasy ClientRuntime  
 <xref:System.ServiceModel.Dispatcher.ClientRuntime> Klasa jest punktem rozszerzalności, do którego można dodawać obiekty rozszerzeń, które przechwytuje komunikaty i rozszerzają zachowanie klienta. Obiekty przechwycenia mogą przetwarzać wszystkie komunikaty w określonym kontrakcie, przetwarzać tylko komunikaty dla określonych operacji, wykonywać inicjalizacje kanałów niestandardowych i implementować inne niestandardowe zachowanie aplikacji klienta.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> Właściwość zwraca obiekt czasu wykonywania wysyłania dla klientów wywołania zwrotnego inicjowanych przez usługę.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.OperationSelector%2A> Właściwość akceptuje obiekt selektora operacji niestandardowej.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ChannelInitializers%2A> Właściwość umożliwia dodanie inicjatora kanału, który może sprawdzić lub zmodyfikować kanał klienta.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> Właściwość Pobiera<xref:System.ServiceModel.Dispatcher.ClientOperation> kolekcję obiektów, do których można dodać niestandardowych interceptorów komunikatów, które udostępniają funkcje specyficzne dla komunikatów tej operacji.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ManualAddressing%2A> Właściwość umożliwia aplikacji wyłączenie niektórych automatycznych nagłówków adresowania w celu bezpośredniej kontroli adresów.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.Via%2A> Właściwość ustawia wartość miejsca docelowego wiadomości na poziomie transportu w celu obsługi pośredników i innych scenariuszy.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> Właściwość Pobiera<xref:System.ServiceModel.Dispatcher.IClientMessageInspector> kolekcję obiektów, do których można dodać niestandardowych interceptorów komunikatów dla wszystkich wiadomości podróżujących przez klienta WCF.  
  
 Ponadto istnieje kilka innych właściwości, które pobierają informacje o kontrakcie:  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractName%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractNamespace%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractClientType%2A>  
  
 Jeśli klient WCF jest klientem programu WCF, następujące właściwości pobierają również informacje o kliencie wywołania zwrotnego programu WCF:  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackClientType%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A>  
  
 Aby zwiększyć wykonanie klienta WCF przez cały klient WCF, przejrzyj właściwości dostępne w klasie, <xref:System.ServiceModel.Dispatcher.ClientRuntime> aby zobaczyć, czy modyfikacja właściwości lub implementacja interfejsu i dodanie go do właściwości powoduje utworzenie funkcji, którą poszukujesz. Po wybraniu określonego rozszerzenia do skompilowania należy wstawić rozszerzenie do odpowiedniej <xref:System.ServiceModel.Dispatcher.ClientRuntime> właściwości, implementując zachowanie klienta, które zapewnia dostęp <xref:System.ServiceModel.Dispatcher.ClientRuntime> do klasy po wywołaniu.  
  
 Niestandardowe obiekty rozszerzeń można wstawiać do kolekcji przy użyciu zachowania operacji (obiektu, który implementuje <xref:System.ServiceModel.Description.IOperationBehavior>), zachowania kontraktu (obiektu, który implementuje <xref:System.ServiceModel.Description.IContractBehavior>) lub zachowania punktu końcowego (obiektu, który implementuje <xref:System.ServiceModel.Description.IEndpointBehavior> ). Obiekt zachowanie podczas instalowania jest dodawany do odpowiedniej kolekcji zachowań programowo, deklaratywnie (przez implementację atrybutu niestandardowego) lub przez implementację niestandardowego <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> obiektu, aby umożliwić Wstawianie zachowania przy użyciu plik konfiguracji aplikacji. Aby uzyskać szczegółowe informacje, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Przykłady pokazujące przechwycenia przez klienta WCF znajdują się [w temacie How to: Inspekcja lub modyfikowanie komunikatów na kliencie](how-to-inspect-or-modify-messages-on-the-client.md).  
  
### <a name="using-the-clientoperation-class"></a>Korzystanie z klasy ClientOperation  
 <xref:System.ServiceModel.Dispatcher.ClientOperation> Klasa jest lokalizacją dla modyfikacji w czasie wykonywania klienta i punktu wstawiania dla rozszerzeń niestandardowych objętych zakresem tylko jednej operacji usługi. (Aby zmodyfikować zachowanie w czasie wykonywania klienta dla wszystkich komunikatów w kontrakcie, użyj <xref:System.ServiceModel.Dispatcher.ClientRuntime> klasy).  
  
 Użyj właściwości, aby zlokalizować obiekt, który reprezentuje konkretną operację usługi. <xref:System.ServiceModel.Dispatcher.ClientOperation> <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> Następujące właściwości umożliwiają wstawianie niestandardowych obiektów do systemu klienta WCF:  
  
- Użyj właściwości <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> , aby wstawić implementację <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> niestandardową dla operacji lub zmodyfikować bieżący program formatujący.  
  
- Użyj właściwości <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A> , aby wstawić implementację <xref:System.ServiceModel.Dispatcher.IParameterInspector> niestandardową lub zmodyfikować bieżącą.  
  
 Następujące właściwości umożliwiają modyfikację systemu w interakcji z programem formatującego i inspektorami parametrów niestandardowych:  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.SerializeRequest%2A> Użyj właściwości, aby kontrolować serializację wiadomości wychodzącej.  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.DeserializeReply%2A> Użyj właściwości, aby kontrolować deserializacja komunikatu przychodzącego.  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.Action%2A> Użyj właściwości, aby kontrolować akcję WS-Addressing komunikatu żądania.  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.BeginMethod%2A> Użyj i <xref:System.ServiceModel.Dispatcher.ClientOperation.EndMethod%2A> , aby określić, które metody klienta WCF są skojarzone z operacją asynchroniczną.  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.FaultContractInfos%2A> Użyj właściwości, aby uzyskać kolekcję zawierającą typy, które mogą występować w błędach SOAP jako typ szczegółowy.  
  
- Użyj właściwości <xref:System.ServiceModel.Dispatcher.ClientOperation.IsTerminating%2A> i, aby określić, czy sesja jest inicjowana lub jest odłączana odpowiednio do momentu wywołania operacji. <xref:System.ServiceModel.Dispatcher.ClientOperation.IsInitiating%2A>  
  
- Użyj właściwości <xref:System.ServiceModel.Dispatcher.ClientOperation.IsOneWay%2A> , aby określić, czy operacja jest operacją jednokierunkową.  
  
- Użyj właściwości <xref:System.ServiceModel.Dispatcher.ClientOperation.Parent%2A> , aby uzyskać obiekt zawierający <xref:System.ServiceModel.Dispatcher.ClientRuntime> .  
  
- Użyj właściwości <xref:System.ServiceModel.Dispatcher.ClientOperation.Name%2A> , aby pobrać nazwę operacji.  
  
- Użyj właściwości <xref:System.ServiceModel.Dispatcher.ClientOperation.SyncMethod%2A> , aby określić, która metoda jest zamapowana na operację.  
  
 Aby zwiększyć wykonanie klienta WCF tylko w jednej operacji usługi, przejrzyj właściwości dostępne w klasie, <xref:System.ServiceModel.Dispatcher.ClientOperation> aby zobaczyć, czy modyfikacja właściwości lub implementacja interfejsu i dodanie go do właściwości powoduje utworzenie funkcji, którą poszukujesz. Po wybraniu określonego rozszerzenia do skompilowania należy wstawić rozszerzenie do odpowiedniej <xref:System.ServiceModel.Dispatcher.ClientOperation> właściwości, implementując zachowanie klienta, które zapewnia dostęp <xref:System.ServiceModel.Dispatcher.ClientOperation> do klasy po wywołaniu. Wewnątrz tego zachowania można następnie zmodyfikować właściwość zgodnie <xref:System.ServiceModel.Dispatcher.ClientRuntime> z wymaganiami.  
  
 Zazwyczaj implementacja zachowania operacji (obiekt implementujący <xref:System.ServiceModel.Description.IOperationBehavior> interfejs) wystarcza, ale można również użyć zachowań punktów końcowych i zachowań kontraktu, aby osiągnąć ten sam efekt <xref:System.ServiceModel.Description.OperationDescription> , wyszukując dla określonego Operacja i dołączenie tego zachowania. Aby uzyskać szczegółowe informacje, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Aby użyć zachowania niestandardowego z konfiguracji, należy zainstalować zachowanie przy użyciu niestandardowej procedury obsługi sekcji konfiguracji zachowania. Możesz również zainstalować zachowanie, tworząc atrybut niestandardowy.  
  
 Przykłady pokazujące przechwycenia przez klienta WCF znajdują się [w temacie How to: Inspekcja lub modyfikowanie](how-to-inspect-or-modify-parameters.md)parametrów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Dispatcher.ClientRuntime>
- <xref:System.ServiceModel.Dispatcher.ClientOperation>
- [Instrukcje: Inspekcja lub modyfikowanie komunikatów na kliencie](how-to-inspect-or-modify-messages-on-the-client.md)
- [Instrukcje: Inspekcja lub modyfikowanie parametrów](how-to-inspect-or-modify-parameters.md)
