---
title: Rozszerzanie dyspozytorów
ms.date: 03/30/2017
helpviewer_keywords:
- dispatcher extensions [WCF]
ms.assetid: d0ad15ac-fa12-4f27-80e8-7ac2271e5985
ms.openlocfilehash: 9250ca09fb5e28655e39f8d91d991fdb3bffcdbd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795746"
---
# <a name="extending-dispatchers"></a>Rozszerzanie dyspozytorów
Dyspozytory są odpowiedzialni za ściąganie komunikatów przychodzących z kanałów, tłumaczenie ich na wywołania metod w kodzie aplikacji i wysyłanie wyników z powrotem do obiektu wywołującego. Rozszerzenia dyspozytora umożliwiają modyfikowanie tego przetwarzania.  Można zaimplementować inspektorów komunikatów lub parametrów kontrolujących lub modyfikujących zawartość komunikatów lub parametrów.  Można zmienić sposób, w jaki komunikaty są kierowane do operacji, lub udostępnić inne funkcje.

W tym temacie opisano sposób używania <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klas i <xref:System.ServiceModel.Dispatcher.DispatchOperation> w aplikacji usługi Windows Communication Foundation (WCF) do modyfikowania domyślnego zachowania wykonywania dyspozytora lub przechwytywania lub modyfikowania komunikatów, parametrów lub powrotu wartości przed lub po ich wysłaniu lub pobraniu z warstwy kanału. Aby uzyskać więcej informacji na temat równoważnego przetwarzania komunikatów przez środowisko uruchomieniowe klienta, zobacz [Rozszerzanie klientów](extending-clients.md). Aby zrozumieć rolę, która <xref:System.ServiceModel.IExtensibleObject%601> umożliwia odczytywanie informacji o stanie udostępnionym między różnymi obiektami dostosowania środowiska uruchomieniowego, zobacz [Rozszerzalne obiekty](extensible-objects.md).

## <a name="dispatchers"></a>Dyspozytorów

Warstwa modelu usług wykonuje konwersję między modelem programowania dewelopera a podstawową wymianą komunikatów, powszechnie nazywaną warstwą kanału. W programie WCF elementy do wysłania kanału i punktu<xref:System.ServiceModel.Dispatcher.ChannelDispatcher> końcowego <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>(odpowiednio) to składniki usługi odpowiedzialne za akceptowanie nowych kanałów, otrzymywanie komunikatów, wysyłanie i wywoływanie operacji oraz przetwarzanie odpowiedzi. Obiekty dyspozytora są obiektami odbiornika, ale implementacje kontraktu wywołania zwrotnego w usługach dupleksowych uwidaczniają także obiekty dyspozytora na potrzeby inspekcji, modyfikacji lub rozszerzenia.

Dyspozytor kanału (i pomocnik <xref:System.ServiceModel.Channels.IChannelListener>) ściąga komunikaty z kanału w obszarze i przekazuje komunikaty do odpowiednich odnoszących się do nich punktów końcowych. Każdy Dyspozytor punktu końcowego ma <xref:System.ServiceModel.Dispatcher.DispatchRuntime> kierowanie komunikatów do odpowiednich <xref:System.ServiceModel.Dispatcher.DispatchOperation>, które są odpowiedzialne za wywołanie metody implementującej operację. Różne opcjonalne i wymagane klasy rozszerzeń są wywoływane w sposób. W tym temacie wyjaśniono, jak te fragmenty pasują do siebie i jak można zmodyfikować właściwości i podłączyć własny kod w celu poszerzenia podstawowej funkcjonalności.

Właściwości dyspozytora i zmodyfikowane obiekty dostosowania są wstawiane przy użyciu obiektów usługi, punktu końcowego, kontraktu lub zachowania operacji. W tym temacie nie opisano, jak używać zachowań. Aby uzyskać więcej informacji na temat typów używanych do wstawiania modyfikacji dyspozytora, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](configuring-and-extending-the-runtime-with-behaviors.md).

Poniższa ilustracja przedstawia ogólny widok elementów architektury w usłudze.

![Architektura środowiska uruchomieniowego wysyłania](./media/wcfc-dispatchruntimearchc.gif "wcfc_DispatchRuntimeArchc")

### <a name="channel-dispatchers"></a>Dyspozytorzy kanałów

Obiekt jest tworzony w celu <xref:System.ServiceModel.Channels.IChannelListener> skojarzenia z określonym identyfikatorem URI (nazywanym identyfikatorem URI nasłuchiwania) z wystąpieniem usługi. <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> Każdy <xref:System.ServiceModel.ServiceHost> obiekt może zawierać wiele <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> obiektów, z których każdy jest skojarzony tylko z jednym odbiornikiem i identyfikatorem URI nasłuchiwania. Po nadejściu <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> wiadomości wysyła zapytanie do każdego ze skojarzonych <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> obiektów, czy punkt końcowy może zaakceptować komunikat i przekazuje komunikat do tego, który może.

Wszystkie właściwości kontrolujące okres istnienia sesji kanału są dostępne do inspekcji lub modyfikacji <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> obiektu. Należą do nich inicjatory kanału niestandardowego, odbiornik kanału, host, skojarzone <xref:System.ServiceModel.InstanceContext>i tak dalej.

### <a name="endpoint-dispatchers"></a>Dyspozytorzy punktów końcowych

Obiekt jest odpowiedzialny za przetwarzanie komunikatów <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> od momentu, gdy adres docelowy wiadomości jest zgodny z <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> i Akcja komunikatu jest zgodna z <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> właściwością. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Jeśli dwa <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> obiekty mogą akceptować komunikat <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.FilterPriority%2A> , wartość właściwości określa punkt końcowy o wyższym priorytecie.

Użyj, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Aby uzyskać dwa główne punkty rozszerzenia modelu usług <xref:System.ServiceModel.Dispatcher.DispatchRuntime> — klasy i <xref:System.ServiceModel.Dispatcher.DispatchOperation> — służą do dostosowywania przetwarzania dyspozytora. <xref:System.ServiceModel.Dispatcher.DispatchRuntime> Klasa umożliwia użytkownikom przechwycenie i rozciągnięcie dyspozytora w zakresie kontraktu (czyli dla wszystkich komunikatów w kontrakcie). <xref:System.ServiceModel.Dispatcher.DispatchOperation> Klasa umożliwia użytkownikom przechwycenie i rozciągnięcie dyspozytora w zakresie operacji (czyli dla wszystkich komunikatów w operacji).

## <a name="scenarios"></a>Scenariusze

Istnieje kilka powodów, dla których należy zwiększyć dyspozytora:

- Niestandardowa weryfikacja komunikatów. Użytkownicy mogą wymusić, że komunikat jest prawidłowy dla określonego schematu. Można to zrobić, implementując interfejsy interceptora komunikatów. Aby zapoznać się z przykładem, zobacz [inspektorzy komunikatów](../samples/message-inspectors.md).

- Niestandardowe rejestrowanie komunikatów. Użytkownicy mogą przeprowadzać inspekcję i rejestrowanie niektórych komunikatów aplikacji przepływających przez punkt końcowy. Można to również zrobić przy użyciu interfejsów interceptora komunikatów.

- Niestandardowe przekształcenia komunikatów. Użytkownicy mogą zastosować pewne przekształcenia do wiadomości w środowisku uruchomieniowym (na przykład w celu przechowywania wersji). Można to zrobić ponownie przy użyciu interfejsów interceptora komunikatów.

- Niestandardowy model danych. Użytkownicy mogą mieć model serializacji danych inny niż te obsługiwane domyślnie w programie WCF (mianowicie <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>,, i nieprzetworzonych wiadomości). Można to zrobić, implementując interfejsy programu formatującego komunikatów. Aby zapoznać się z przykładem, zobacz Program [formatujący operacje i selektor operacji](../samples/operation-formatter-and-operation-selector.md).

- Walidacja parametrów niestandardowych. Użytkownicy mogą wymusić, że wpisane parametry są prawidłowe (w przeciwieństwie do formatu XML). Można to zrobić za pomocą interfejsów inspektora parametrów.

- Wysyłanie operacji niestandardowej. Użytkownicy mogą zaimplementować wysyłanie na coś innego niż akcja — na przykład w elemencie body lub w niestandardowej właściwości wiadomości. Można to zrobić za pomocą <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interfejsu. Aby zapoznać się z przykładem, zobacz Program [formatujący operacje i selektor operacji](../samples/operation-formatter-and-operation-selector.md).

- Buforowanie obiektów. Użytkownicy mogą tworzyć wystąpienia w puli, a nie przydzielać nowych danych dla każdego wywołania. Można to zaimplementować przy użyciu interfejsów dostawcy wystąpień. Aby zapoznać się z przykładem, zobacz [Pule](../samples/pooling.md).

- Dzierżawa wystąpienia. Użytkownicy mogą zaimplementować wzorzec dzierżawy dla okresu istnienia wystąpienia, podobnie jak w przypadku komunikacji zdalnej .NET Framework. Można to zrobić przy użyciu interfejsów czasu istnienia kontekstu wystąpienia.

- Niestandardowa obsługa błędów. Użytkownicy mogą kontrolować sposób przetwarzania zarówno błędów lokalnych, jak i komunikatów o błędach przesyłanych z powrotem do klientów. Można to zaimplementować przy użyciu <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejsów.

- Niestandardowe zachowania autoryzacji. Użytkownicy mogą zaimplementować niestandardową kontrolę dostępu, rozszerzając elementy kontraktu lub czasu wykonywania operacji oraz sprawdzając zabezpieczenia na podstawie tokenów znajdujących się w wiadomości. Można to zrobić przy użyciu interfejsu interceptora komunikatów lub interfejsów interceptorów parametrów. Aby zapoznać się z przykładami, zobacz [rozszerzalność zabezpieczeń](../samples/security-extensibility.md).

  > [!CAUTION]
  > Ze względu na to, że zmiana właściwości zabezpieczeń ma potencjalną ochronę aplikacji WCF, zdecydowanie zaleca się podejmowanie modyfikacji związanych z bezpieczeństwem i dokładne sprawdzenie przed wdrożeniem.

- Niestandardowe moduły sprawdzania środowiska uruchomieniowego WCF. Można zainstalować niestandardowe moduły sprawdzania poprawności, które badają usługi, kontrakty i powiązania, aby wymusić zasady na poziomie przedsiębiorstwa w odniesieniu do aplikacji WCF. (Na przykład zobacz [How to: Zablokuj punkty końcowe w](how-to-lock-down-endpoints-in-the-enterprise.md)przedsiębiorstwie.

### <a name="using-the-dispatchruntime-class"></a>Korzystanie z klasy DispatchRuntime

<xref:System.ServiceModel.Dispatcher.DispatchRuntime> Użyj klasy, aby zmodyfikować domyślne zachowanie usługi lub pojedynczego punktu końcowego lub wstawić obiekty implementujące modyfikacje niestandardowe do jednego lub obu następujących procesów usługi (lub procesów klienta w przypadku klienta dupleksowego):

- Przekształcanie komunikatów przychodzących do obiektów i zwalnianie tych obiektów jako wywołań metod w obiekcie usługi.

- Przekształcanie obiektów odebranych z odpowiedzi na wywołania operacji usługi do komunikatów wychodzących.

<xref:System.ServiceModel.Dispatcher.DispatchRuntime> Umożliwia przechwycenie i rozłożenie dyspozytora kanału lub punktu końcowego dla wszystkich komunikatów w danej umowie, nawet jeśli komunikat nie został rozpoznany. Po nadejściu komunikatu, który nie jest zgodny z żadnym zadeklarowanym w umowie kontraktu, jest wysyłany do operacji zwróconej przez <xref:System.ServiceModel.Dispatcher.DispatchRuntime.UnhandledDispatchOperation%2A> właściwość. Aby przechwycić lub rozłożyć wszystkie komunikaty dla określonej operacji, zobacz <xref:System.ServiceModel.Dispatcher.DispatchOperation> Klasa.

Istnieją cztery główne obszary rozszerzalności dyspozytora uwidocznione przez <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klasę:

1. Składniki kanału używają właściwości <xref:System.ServiceModel.Dispatcher.DispatchRuntime> i skojarzonych dyspozytorów kanałów zwracanych <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ChannelDispatcher%2A> przez właściwość w celu dostosowania sposobu akceptowania i zamykania kanałów przez dyspozytora kanału. Ta kategoria zawiera <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ChannelInitializers%2A> właściwości i <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InputSessionShutdownHandlers%2A> .

2. Składniki komunikatów są dostosowane do poszczególnych przetworzonych komunikatów. Ta kategoria zawiera <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A> <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ErrorHandlers%2A> właściwości <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A>,, i. <xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A>

3. Składniki wystąpienia dostosowują tworzenie, okres istnienia i usuwanie wystąpień typu usługi. Aby uzyskać więcej informacji na temat okresów istnienia obiektu <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> usługi, zobacz Właściwość. Ta kategoria zawiera <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> właściwości i.

4. Składniki związane z zabezpieczeniami mogą korzystać z następujących właściwości:

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A>wskazuje, gdzie są zapisywane zdarzenia inspekcji.

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ImpersonateCallerForAllOperations%2A>Określa, czy usługa próbuje dokonać personifikacji przy użyciu poświadczeń dostarczonych przez komunikat przychodzący.

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageAuthenticationAuditLevel%2A>Określa, czy zdarzenia uwierzytelniania komunikatów pomyślnych są zapisywane w dzienniku zdarzeń <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A>określonym przez.

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.PrincipalPermissionMode%2A>kontroluje sposób <xref:System.Threading.Thread.CurrentPrincipal%2A> ustawiania właściwości.

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ServiceAuthorizationAuditLevel%2A>Określa sposób przeprowadzania inspekcji zdarzeń autoryzacji.

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SuppressAuditFailure%2A>Określa, czy pomijać niekrytyczne wyjątki, które występują podczas procesu rejestrowania.

Zazwyczaj niestandardowe obiekty rozszerzeń są przypisywane do <xref:System.ServiceModel.Dispatcher.DispatchRuntime> właściwości lub wstawiane do kolekcji przez zachowanie usługi (obiekt, który implementuje <xref:System.ServiceModel.Description.IServiceBehavior>), zachowanie kontraktu (obiekt, który implementuje <xref:System.ServiceModel.Description.IContractBehavior>) lub punkt końcowy zachowanie (obiekt, który implementuje <xref:System.ServiceModel.Description.IEndpointBehavior>). Następnie obiekt zachowania podczas instalowania jest dodawany do odpowiedniej kolekcji zachowań programowo lub przez zaimplementowanie niestandardowego <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> obiektu, aby umożliwić wstawienie zachowania przy użyciu pliku konfiguracyjnego aplikacji.

Klienci dwustronni (klienci implementujący kontrakt wywołania zwrotnego określone przez usługę dupleks) mają <xref:System.ServiceModel.Dispatcher.DispatchRuntime> również obiekt, do którego można uzyskać <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> dostęp za pomocą właściwości.

### <a name="using-the-dispatchoperation-class"></a>Korzystanie z klasy element DispatchOperation

<xref:System.ServiceModel.Dispatcher.DispatchOperation> Klasa jest lokalizacją modyfikacji w czasie wykonywania i punktem wstawiania dla rozszerzeń niestandardowych, które są objęte zakresem tylko jedną operacją usługi. (Aby zmodyfikować zachowanie w czasie wykonywania usługi dla wszystkich komunikatów w kontrakcie, użyj <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klasy).

Zainstaluj <xref:System.ServiceModel.Dispatcher.DispatchOperation> modyfikacje przy użyciu niestandardowego obiektu zachowania usługi.

Użyj właściwości, aby zlokalizować obiekt, który reprezentuje konkretną operację usługi. <xref:System.ServiceModel.Dispatcher.DispatchOperation> <xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A>

Następujące właściwości kontrolują wykonywanie w czasie wykonywania na poziomie operacji:

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.Action%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReplyAction%2A>, ,,<xref:System.ServiceModel.Dispatcher.DispatchOperation.IsTerminating%2A>I Właściwościuzyskująodpowiednie<xref:System.ServiceModel.Dispatcher.DispatchOperation.Name%2A> wartości dla operacji. <xref:System.ServiceModel.Dispatcher.DispatchOperation.FaultContractInfos%2A> <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsOneWay%2A>

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionAutoComplete%2A> I<xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionRequired%2A> Określ zachowanie transakcji.

- Właściwości <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceBeforeCall%2A> <xref:System.ServiceModel.InstanceContext>i <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceAfterCall%2A> kontrolują okres istnienia obiektu usługi zdefiniowanego przez użytkownika względem elementu.

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.DeserializeRequest%2A>, ,<xref:System.ServiceModel.Dispatcher.DispatchOperation.SerializeReply%2A> I<xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> właściwości umożliwiają jawną kontrolę nad konwersją z komunikatów do obiektów i obiektów do komunikatów.

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.Impersonation%2A> Właściwość określa poziom personifikacji operacji.

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.CallContextInitializers%2A> Właściwość wstawia niestandardowe rozszerzenia kontekstu wywołania dla operacji.

- Właściwość <xref:System.ServiceModel.Dispatcher.DispatchOperation.AutoDisposeParameters%2A> kontroluje, kiedy obiekty parametrów są niszczone.

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.Invoker%2A> Właściwość służąca do wstawiania niestandardowego obiektu źródło.

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A> Właściwość umożliwia wstawienie niestandardowego inspektora parametrów, którego można użyć do sprawdzenia lub modyfikacji parametrów i zwracanych wartości.

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Dispatcher.DispatchRuntime>
- <xref:System.ServiceModel.Dispatcher.DispatchOperation>
- [Instrukcje: Inspekcja i modyfikowanie komunikatów w usłudze](how-to-inspect-and-modify-messages-on-the-service.md)
- [Instrukcje: Inspekcja lub modyfikowanie parametrów](how-to-inspect-or-modify-parameters.md)
- [Instrukcje: Blokowanie punktów końcowych w przedsiębiorstwie](how-to-lock-down-endpoints-in-the-enterprise.md)
