---
title: Rozszerzanie dyspozytorów
ms.date: 03/30/2017
helpviewer_keywords:
- dispatcher extensions [WCF]
ms.assetid: d0ad15ac-fa12-4f27-80e8-7ac2271e5985
ms.openlocfilehash: ac20e24eb9148ed9d403b7a9c2c260009f39d492
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967621"
---
# <a name="extending-dispatchers"></a>Rozszerzanie dyspozytorów
Dystrybucja jest odpowiedzialny za ściąganie komunikaty przychodzące poza podstawowym kanały, tłumaczenie je na wywołania metody w kodzie aplikacji i wyniki są wysyłane do obiektu wywołującego. Rozszerzenia dyspozytorów umożliwiają modyfikowanie tego przetwarzania.  Możesz zaimplementować wiadomości lub parametr inspektorzy inspekcja lub modyfikowanie zawartości wiadomości lub parametrów.  Możesz zmienić sposób komunikaty są kierowane do operacji lub podaj niektórych innych funkcji.  
  
 W tym temacie opisano sposób użycia <xref:System.ServiceModel.Dispatcher.DispatchRuntime> i <xref:System.ServiceModel.Dispatcher.DispatchOperation> aplikacji, aby zmodyfikować domyślne zachowanie wykonywania dyspozytora lub przechwycenia lub modyfikowanie komunikatów i parametrów lub zwróć usługi klas w Windows Communication Foundation (WCF) wartości przed lub po wysyłanie i pobieranie ich z warstwy kanału. Aby uzyskać więcej informacji na temat przetwarzania komunikatów środowiska uruchomieniowego klienta równoważne zobacz [rozszerzanie klientów](../../../../docs/framework/wcf/extending/extending-clients.md). Aby zrozumieć rolę, <xref:System.ServiceModel.IExtensibleObject%601> rodzaje play podczas uzyskiwania dostępu do udostępnionego stanu między różnymi obiektami dostosowywania środowiska uruchomieniowego, zobacz [obiekty rozszerzalne](../../../../docs/framework/wcf/extending/extensible-objects.md).  
  
## <a name="dispatchers"></a>Dystrybucja  
 Warstwy modelu usług wykonuje konwersję między modelem programowania dla deweloperów i podstawowych wymianę komunikatów, często nazywane warstwy kanału. W kanale usługi WCF i dyspozytorów punktu końcowego (<xref:System.ServiceModel.Dispatcher.ChannelDispatcher> i <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>odpowiednio) odpowiadają składniki usługi do akceptowania nowych kanałów i odbieranie wiadomości, operacja wysyłania i wywołania i przetwarzanie odpowiedzi. Dyspozytor obiekty są obiektami odbiorcy, ale implementacje kontrakt wywołania zwrotnego w usługi dwukierunkowe również udostępnić w nich obiekty dyspozytora dla inspekcji, modyfikacji lub rozszerzenia.  
  
 Dyspozytor kanału (i towarzyszące <xref:System.ServiceModel.Channels.IChannelListener>) baza danych ściąga wiadomości z kanału bazowego i przekazuje komunikaty do ich dyspozytorów odpowiednich punktu końcowego. Dyspozytor każdy punkt końcowy ma <xref:System.ServiceModel.Dispatcher.DispatchRuntime> które kieruje komunikaty do odpowiedniego <xref:System.ServiceModel.Dispatcher.DispatchOperation>, która odpowiada za wywołanie metody, która implementuje operację. Różne klasy opcjonalnych i wymaganych rozszerzenia są wywoływane po drodze. W tym temacie wyjaśniono, jak te elementy współdziałają ze sobą i jak może zmodyfikować właściwości i dołączyć własnego kodu rozszerzenie podstawowe funkcje.  
  
 Dyspozytor właściwości i obiekty zmodyfikowane dostosowania są wstawiane przy użyciu obiektów zachowanie usługi, punkt końcowy, umowy lub operacji. W tym temacie opisano sposób użycia zachowania. Aby uzyskać więcej informacji o typach służy do wstawiania dyspozytora modyfikacje, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Na rysunku poniżej przedstawiono ogólny widok architektury elementów w usłudze.  
  
 ![Architektura środowiska uruchomieniowego wysyłania](../../../../docs/framework/wcf/extending/media/wcfc-dispatchruntimearchc.gif "wcfc_DispatchRuntimeArchc")  
  
### <a name="channel-dispatchers"></a>Dystrybucja kanału  
 A <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> obiekt zostanie utworzony, aby skojarzyć <xref:System.ServiceModel.Channels.IChannelListener> u określonego identyfikatora URI (nazywane identyfikatora URI nasłuchiwania) z wystąpienia usługi. Każdy <xref:System.ServiceModel.ServiceHost> obiekt może mieć wiele <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> obiektów, każdy skojarzony tylko jeden odbiornik i analizują identyfikatora URI. Po odebraniu wiadomości <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> odpytuje każdy skojarzonego <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> obiektów, czy punkt końcowy może zaakceptować komunikat i przekazuje komunikat do tego, która może być.  
  
 Wszystkie właściwości, które kontrolują, okres istnienia i zachowanie kanału sesji są dostępne dla inspekcji lub modyfikacji w <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> obiektu. Należą do nich inicjatory w niestandardowym kanale odbiornika kanałów, host, skojarzonego <xref:System.ServiceModel.InstanceContext>i tak dalej.  
  
### <a name="endpoint-dispatchers"></a>Punkt końcowy dyspozytorów  
 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Obiekt jest odpowiedzialna za przetwarzanie komunikatów z <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> po adres docelowy komunikat odpowiada <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> i dopasowania akcji komunikat <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> właściwości. Jeśli dwa <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> obiektów może zaakceptować komunikat <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.FilterPriority%2A> wartość właściwości określa wyższy priorytet punktu końcowego.  
  
 Użyj <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> można uzyskać dwa punkty rozszerzenia modelu głównego usługi — <xref:System.ServiceModel.Dispatcher.DispatchRuntime> i <xref:System.ServiceModel.Dispatcher.DispatchOperation> klasy — służące do dostosowywania przetwarzania Dyspozytor. <xref:System.ServiceModel.Dispatcher.DispatchRuntime> Klasy pozwala użytkownikom na przechwytywanie i rozszerzanie dyspozytorów w zakresie kontraktu (oznacza to, że dla wszystkich komunikatów w umowie). <xref:System.ServiceModel.Dispatcher.DispatchOperation> Klasy pozwala użytkownikom na przechwytywanie i rozszerzanie dyspozytorów w zakresie operacji (oznacza to, że dla wszystkich komunikatów w operacji).  
  
## <a name="scenarios"></a>Scenariusze  
 Tam wiele możliwych przyczyn, aby rozszerzyć Dyspozytor:  
  
- Niestandardowy komunikat sprawdzania poprawności. Użytkownicy mogą wymusić, czy komunikat jest prawidłowa dla niektórych schematu. Można to zrobić poprzez implementację interfejsów interceptor wiadomości. Aby uzyskać przykład, zobacz [inspektorzy komunikatów](../../../../docs/framework/wcf/samples/message-inspectors.md).  
  
- Rejestrowanie komunikatów niestandardowych. Użytkownicy mogą sprawdzić i rejestrować pewne zestaw komunikatów aplikacji, które przepływać za pośrednictwem punktu końcowego. Ponadto można to zrobić za pomocą interfejsów interceptor wiadomości.  
  
- Niestandardowy komunikat przekształcenia. Użytkownicy mogą stosować przekształcenia niektórych do wiadomości w czasie wykonywania (na przykład w przypadku wersji). Można to osiągnąć, również z interfejsami interceptor wiadomości.  
  
- Niestandardowy Model danych. Użytkownicy mogą mieć modelu serializacji danych niż te obsługiwane domyślnie w programie WCF (to znaczy, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>oraz nieprzetworzone komunikaty). Można to zrobić, implementowanie interfejsów elementu formatującego wiadomości. Aby uzyskać przykład, zobacz [element formatujący operacji i selektor operacji](../../../../docs/framework/wcf/samples/operation-formatter-and-operation-selector.md).  
  
- Walidacja parametru niestandardowego. Użytkownicy mogą wymusić, że wpisane parametry są prawidłowe (w przeciwieństwie do XML). Można to zrobić przy użyciu Inspektora interfejsów parametru.  
  
- Wywoływanie operacji niestandardowej. Użytkownicy mogą zaimplementować, wysyłki na coś innego niż akcji — na przykład elementu body lub właściwość niestandardową wiadomość. Można to zrobić za pomocą <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interfejsu. Aby uzyskać przykład, zobacz [element formatujący operacji i selektor operacji](../../../../docs/framework/wcf/samples/operation-formatter-and-operation-selector.md).  
  
- Obiekt, buforowanie. Użytkownicy mogą puli wystąpień a nie na poświęcaniu nową za każde wywołanie. Można to zaimplementować przy użyciu interfejsów dostawcy wystąpienia. Aby uzyskać przykład, zobacz [Pooling](../../../../docs/framework/wcf/samples/pooling.md).  
  
- Wystąpienie dzierżawy. Użytkownicy mogą zaimplementować wzorzec dzierżawienia na przykład okres istnienia, podobnie jak w przypadku wywołaniem funkcji zdalnych .NET Framework. Można to zrobić przy użyciu interfejsów okresu istnienia wystąpienia kontekstu.  
  
- Obsługa błędów niestandardowych. Użytkownicy mogą kontrolować sposób zarówno lokalne błędy są przetwarzane i jak błędy są przekazywane do klientów. Można to zaimplementować przy użyciu <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejsów.  
  
- Autoryzacja niestandardowa zachowania. Użytkownicy mogą zaimplementować kontroli dostępu niestandardowych rozszerzanie elementów środowiska wykonawczego umowy lub operacji i dodając kontrole zabezpieczeń na podstawie tokenów w wiadomości. Można to osiągnąć przy użyciu przechwytujący lub parametr interceptor interfejsów. Aby uzyskać przykłady, zobacz [rozszerzalność zabezpieczeń](../../../../docs/framework/wcf/samples/security-extensibility.md).  
  
    > [!CAUTION]
    >  Ponieważ zmiany właściwości zabezpieczeń może naruszyć bezpieczeństwo aplikacji WCF, zdecydowanie zaleca się zmiany związane z zabezpieczeniami, ostrożnie podejmować i dokładnie przetestować przed wdrożeniem.  
  
- WCF niestandardowe moduły środowiska uruchomieniowego. Można zainstalować poprawności niestandardowych, które zbadać usług, kontrakty i powiązania do wymuszania zasad klasy korporacyjnej w odniesieniu do aplikacji WCF. (Na przykład zobacz [jak: Blokowanie punktów końcowych w przedsiębiorstwie](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).)  
  
### <a name="using-the-dispatchruntime-class"></a>Używanie klasy DispatchRuntime  
 Użyj <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klasy zmodyfikować zachowanie domyślne usługi lub poszczególnych punktu końcowego, lub wstawić obiekty, które implementują niestandardowe modyfikacje jedno lub oba z następujących procesów usługi (lub procesy klienta w przypadku klienta dupleks):  
  
- Przekształcenie komunikatów przychodzących do obiektów i zwolnienie tych obiektów jako wywołania metod obiektu usługi.  
  
- Przekształcanie obiektów odebrana odpowiedź na wywołania operacji usługi do wiadomości wychodzących.  
  
 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> Umożliwia przechwytywanie i rozszerzyć Dyspozytor kanału lub punkt końcowy dla wszystkich komunikatów na określonej umowy, nawet wtedy, gdy wiadomość nie została rozpoznana. Po umieszczeniu komunikatu, który nie pasuje do żadnego zadeklarowane w umowie wywoływane jest operacji, zwracany przez <xref:System.ServiceModel.Dispatcher.DispatchRuntime.UnhandledDispatchOperation%2A> właściwości. Aby przechwycić lub rozszerzyć na wszystkie komunikaty dla określonej operacji, zobacz <xref:System.ServiceModel.Dispatcher.DispatchOperation> klasy.  
  
 Istnieją cztery główne obszary rozszerzalności dyspozytora udostępnianych przez <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klasy:  
  
1. Kanał składniki używane właściwości <xref:System.ServiceModel.Dispatcher.DispatchRuntime> i wysyłający skojarzony kanał zwracany przez <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ChannelDispatcher%2A> właściwości, aby dostosować akceptuje i zamyka kanały Dyspozytor kanału. Ta kategoria obejmuje <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ChannelInitializers%2A> i <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InputSessionShutdownHandlers%2A> właściwości.  
  
2. Składniki wiadomości są dostosowane dla każdego komunikatu przetworzone. Ta kategoria obejmuje <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A>, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A>, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A>i <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ErrorHandlers%2A> właściwości.  
  
3. Składniki wystąpienia dostosować tworzenia, okres istnienia i usuwania wystąpień typu usługi. Aby uzyskać więcej informacji na temat okresów istnienia obiektu usługi zobacz <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwości. Ta kategoria obejmuje <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> i <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> właściwości.  
  
4. Składniki związane z zabezpieczeniami można użyć następujących właściwości:  
  
    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A> Wskazuje, gdzie zdarzenia inspekcji są zapisywane.  
  
    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ImpersonateCallerForAllOperations%2A> Określa, czy usługa próbuje personifikować przy użyciu poświadczeń dostarczonych przez wiadomości przychodzącej.  
  
    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageAuthenticationAuditLevel%2A> Określa, czy komunikat pomyślne uwierzytelnianie zdarzenia są zapisywane w dzienniku zdarzeń określony przez <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A>.  
  
    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.PrincipalPermissionMode%2A> Formanty sposób, w jaki <xref:System.Threading.Thread.CurrentPrincipal%2A> właściwość jest ustawiona.  
  
    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ServiceAuthorizationAuditLevel%2A> Określa, jak odbywa się inspekcji zdarzeń autoryzacji.  
  
    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SuppressAuditFailure%2A> Określa, czy pominąć Niekrytyczne wyjątki, które występują w procesie rejestracji.  
  
 Zazwyczaj rozszerzenia niestandardowe obiekty są przypisywane do <xref:System.ServiceModel.Dispatcher.DispatchRuntime> właściwości lub włożenia do kolekcji przez zachowanie usługi (obiekt, który implementuje <xref:System.ServiceModel.Description.IServiceBehavior>), zachowanie kontraktu (obiekt, który implementuje <xref:System.ServiceModel.Description.IContractBehavior>), lub punktu końcowego zachowanie (obiekt, który implementuje <xref:System.ServiceModel.Description.IEndpointBehavior>). Instalowanie obiektu zachowanie jest dodawana do odpowiedniej kolekcji zachowań, programowo lub poprzez implementację niestandardową <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> obiektu, aby włączyć zachowanie, które ma zostać wstawiony, przy użyciu pliku konfiguracji aplikacji.  
  
 Dwukierunkowe (liczba klientów, które implementują kontrakt wywołania zwrotnego, określony przez usługi duplex) mają <xref:System.ServiceModel.Dispatcher.DispatchRuntime> obiekt, który jest możliwy za pomocą <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> właściwości.  
  
### <a name="using-the-dispatchoperation-class"></a>Używanie klasy Element DispatchOperation  
 <xref:System.ServiceModel.Dispatcher.DispatchOperation> Klasy to lokalizacja, dla środowiska wykonawczego modyfikacje i wstawiania wskaż niestandardowych rozszerzeń, które są w zakresie operacji tylko jednej usługi. (Aby zmodyfikować zachowanie środowiska wykonawczego usługi dla wszystkich komunikatów w umowie, użyj <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klasy.)  
  
 Zainstaluj <xref:System.ServiceModel.Dispatcher.DispatchOperation> modyfikacje, za pomocą obiektu zachowanie niestandardowe usługi.  
  
 Użyj <xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A> właściwości, aby zlokalizować <xref:System.ServiceModel.Dispatcher.DispatchOperation> obiekt reprezentujący operację określonej usługi.  
  
 Następujące właściwości kontrolować wykonywanie środowiska uruchomieniowego na poziomie operacji:  
  
- <xref:System.ServiceModel.Dispatcher.DispatchOperation.Action%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReplyAction%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.FaultContractInfos%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsOneWay%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsTerminating%2A>, I <xref:System.ServiceModel.Dispatcher.DispatchOperation.Name%2A> właściwości uzyskać odpowiednie wartości dla tej operacji.  
  
- <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionAutoComplete%2A> i <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionRequired%2A> określić zachowanie transakcji.  
  
- <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceBeforeCall%2A> i <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceAfterCall%2A> właściwości formantu okresu istnienia obiektu użytkownika usługi względem <xref:System.ServiceModel.InstanceContext>.  
  
- <xref:System.ServiceModel.Dispatcher.DispatchOperation.DeserializeRequest%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.SerializeReply%2A>i <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> właściwości Włącz jawną kontrolę nad tym konwersja wiadomości na obiekty i komunikatów.  
  
- <xref:System.ServiceModel.Dispatcher.DispatchOperation.Impersonation%2A> Właściwość określa poziom personifikacji operacji.  
  
- <xref:System.ServiceModel.Dispatcher.DispatchOperation.CallContextInitializers%2A> Właściwość wstawia rozszerzenia kontekstu niestandardowe wywołania operacji.  
  
- <xref:System.ServiceModel.Dispatcher.DispatchOperation.AutoDisposeParameters%2A> Właściwości kontrolki, gdy parametr obiekty są niszczone.  
  
- <xref:System.ServiceModel.Dispatcher.DispatchOperation.Invoker%2A> Właściwości, aby wstawić obiekt wywołujący niestandardowego.  
  
- <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A> Właściwość umożliwia wstawianie Inspektor parametru niestandardowego, który umożliwia sprawdzanie lub modyfikowanie parametrów i wartości zwracane.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Dispatcher.DispatchRuntime>
- <xref:System.ServiceModel.Dispatcher.DispatchOperation>
- [Instrukcje: Sprawdzanie i modyfikowanie komunikatów w usłudze](../../../../docs/framework/wcf/extending/how-to-inspect-and-modify-messages-on-the-service.md)
- [Instrukcje: Inspekcja lub modyfikowanie parametrów](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md)
- [Instrukcje: Blokowanie punktów końcowych w przedsiębiorstwie](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md)
