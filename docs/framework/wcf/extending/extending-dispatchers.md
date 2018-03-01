---
title: "Rozszerzanie dyspozytorów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dispatcher extensions [WCF]
ms.assetid: d0ad15ac-fa12-4f27-80e8-7ac2271e5985
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4240a19401d97cd0636d13a94fd07ad4ef753388
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="extending-dispatchers"></a>Rozszerzanie dyspozytorów
Dystrybucja są odpowiedzialne za ściąganie wiadomości przychodzących poza podstawowej kanały, tłumaczenia je do wywołania metody w kodzie aplikacji i wysłaniem wyniki z powrotem do wywołującego. Rozszerzenia dyspozytorów umożliwiają modyfikowanie tego przetwarzania.  Można zaimplementować inspektorzy komunikatów lub parametr, które inspekcja lub modyfikowanie zawartość wiadomości lub parametrów.  Możesz zmienić sposób komunikaty są kierowane do operacji lub podaj niektóre inne funkcje.  
  
 W tym temacie opisano sposób użycia <xref:System.ServiceModel.Dispatcher.DispatchRuntime> i <xref:System.ServiceModel.Dispatcher.DispatchOperation> klas w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji, aby zmodyfikować domyślne zachowanie wykonywania dyspozytora lub do przechwycenia lub modyfikowanie komunikatów, parametry, usługi lub zwracanych wartości przed lub kolejnych wysyłanie lub pobierania ich z warstwy kanału. Aby uzyskać więcej informacji o przetwarzaniu komunikat środowiska uruchomieniowego równoważne klienta, zobacz [rozszerzanie klientów](../../../../docs/framework/wcf/extending/extending-clients.md). Aby zrozumieć rolę który <xref:System.ServiceModel.IExtensibleObject%601> typy odtwarzania podczas uzyskiwania dostępu do stanu udostępnionego między różnymi obiektami dostosowania środowiska uruchomieniowego, zobacz [obiekty rozszerzalne](../../../../docs/framework/wcf/extending/extensible-objects.md).  
  
## <a name="dispatchers"></a>Dystrybucja  
 Warstwy modelu usług wykonuje konwersję między dewelopera model programowania i podstawowej wymiany wiadomości, często nazywane warstwie kanału. W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dyspozytorów kanału i punktu końcowego (<xref:System.ServiceModel.Dispatcher.ChannelDispatcher> i <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>odpowiednio) są zobowiązani do akceptowania nowych kanałów, odbierania wiadomości, operacji wysyłania i wywołania i przetwarzanie odpowiedzi składników usługi. Dyspozytor obiekty są obiektami odbiornika, ale implementacje kontrakt wywołania zwrotnego w usługi dwukierunkowe również ujawniać ich obiektów dyspozytora do inspekcji, modyfikacji lub rozszerzenia.  
  
 Dyspozytor kanału (i Pomocnika <xref:System.ServiceModel.Channels.IChannelListener>) pobiera komunikaty z kanału podstawowy i przekazuje komunikaty do ich dystrybucja odpowiednich punktu końcowego. Dyspozytor każdego punktu końcowego ma <xref:System.ServiceModel.Dispatcher.DispatchRuntime> który kieruje komunikaty do odpowiednich <xref:System.ServiceModel.Dispatcher.DispatchOperation>, który jest odpowiedzialny dla wywołania metody, która implementuje operację. Różnych klas opcjonalne i wymagane rozszerzenia są wywoływane na bieżąco. W tym temacie opisano sposób sztuk dopasowania i jak może zmodyfikować właściwości i dołączyć własnego kodu rozszerzenie podstawowych funkcji.  
  
 Dyspozytor właściwości i dostosowywania zmodyfikowane obiekty są wstawiane za pomocą obiektów zachowania usługi, punkt końcowy, umowy lub operacji. W tym temacie opisano sposób użycia zachowania. Aby uzyskać więcej informacji o typach służy do wstawiania dyspozytora modyfikacje, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Poniższa ilustracja przedstawia ogólny widok architektury elementów w usłudze.  
  
 ![Architektura środowiska uruchomieniowego wysyłania](../../../../docs/framework/wcf/extending/media/wcfc-dispatchruntimearchc.gif "wcfc_DispatchRuntimeArchc")  
  
### <a name="channel-dispatchers"></a>Dystrybucja kanału  
 A <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> utworzeniu obiektu do skojarzenia <xref:System.ServiceModel.Channels.IChannelListener> w określonego identyfikatora URI (nazywane nasłuchiwania URI) z wystąpienia usługi. Każdy <xref:System.ServiceModel.ServiceHost> obiekt może mieć wiele <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> obiekty, każde skojarzone z tylko jednego odbiornika i identyfikator URI nasłuchiwania. Po nadejściu wiadomości, <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> odpytuje każdy skojarzonego <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> obiekty czy punkt końcowy może zaakceptować komunikat i przekazaniem do tego, który można.  
  
 Wszystkie właściwości, które kontrolują okres istnienia i zachowania kanału sesji są dostępne dla inspekcji lub zmiana na <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> obiektu. Należą inicjatory niestandardowym kanale, odbiornika kanałów, hosta, skojarzony <xref:System.ServiceModel.InstanceContext>i tak dalej.  
  
### <a name="endpoint-dispatchers"></a>Dystrybucja punktu końcowego  
 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Obiekt jest odpowiedzialna za przetwarzanie komunikatów z <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> po adres docelowy komunikat odpowiada <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> i dopasowań akcji komunikat <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> właściwości. Jeśli dwa <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> obiektów może zaakceptować komunikat <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.FilterPriority%2A> wartość właściwości określa wyższy priorytet punktu końcowego.  
  
 Użyj <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> uzyskanie dwa punkty rozszerzeń modelu głównego usługi — <xref:System.ServiceModel.Dispatcher.DispatchRuntime> i <xref:System.ServiceModel.Dispatcher.DispatchOperation> klasy — czy służy do dostosowywania przetwarzanie dyspozytora. <xref:System.ServiceModel.Dispatcher.DispatchRuntime> Klasa umożliwia użytkownikom przechwytywać i rozszerzyć dyspozytora w zakresie kontraktu (to znaczy dla wszystkich wiadomości w umowie). <xref:System.ServiceModel.Dispatcher.DispatchOperation> Klasa umożliwia użytkownikom przechwytywać i rozszerzyć dyspozytora w zakresie operacji (to znaczy, że wszystkie wiadomości w operacji).  
  
## <a name="scenarios"></a>Scenariusze  
 Istnieje wiele przyczyn, aby rozszerzyć Dyspozytor:  
  
-   Niestandardowy komunikat weryfikacji. Użytkownicy mogą wymusić, że wiadomość jest prawidłowy dla niektórych schematu. Można to zrobić przez implementacji interfejsów interceptora komunikat. Na przykład zobacz [Messageinspector](../../../../docs/framework/wcf/samples/message-inspectors.md).  
  
-   Rejestrowanie komunikatów niestandardowych. Użytkownicy mogą sprawdzać i rejestrować pewne zestaw komunikatów aplikacji, które wpływają za pośrednictwem punktu końcowego. Ponadto można to zrobić z interfejsami interceptora wiadomości.  
  
-   Niestandardowy komunikat przekształcenia. Użytkownicy mogą stosować określonych przekształceń do wiadomości w czasie wykonywania (na przykład w przypadku wersji). Można to zrobić, ponownie z interfejsami interceptora wiadomości.  
  
-   Model danych niestandardowych. Użytkownicy mogą mieć modelem serializacji danych niż obsługiwany przez domyślną w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (to znaczy, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>i komunikaty raw). Można to zrobić przez wdrożenie interfejsy program formatujący wiadomości. Na przykład zobacz [programu formatującego operacji i selektor operacji](../../../../docs/framework/wcf/samples/operation-formatter-and-operation-selector.md).  
  
-   Sprawdzanie poprawności parametru niestandardowego. Użytkownicy mogą wymusić czy parametrów typu są prawidłowe (a nie XML). Można to zrobić za pomocą interfejsów inspektora parametru.  
  
-   Operacja niestandardowa wysyłki. Użytkownicy mogą zaimplementować wysyłki na inną niż akcja — na przykład na elemencie body lub na właściwości niestandardowe komunikatu. Można to zrobić przy użyciu <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interfejsu. Na przykład zobacz [programu formatującego operacji i selektor operacji](../../../../docs/framework/wcf/samples/operation-formatter-and-operation-selector.md).  
  
-   Obiekt, korzystanie z puli. Użytkownicy mogą puli wystąpień zamiast alokacji nowego filtru dla każdego wywołania. To może być zaimplementowany przy użyciu interfejsów wystąpienie dostawcy. Na przykład zobacz [buforowanie](../../../../docs/framework/wcf/samples/pooling.md).  
  
-   Dzierżawa wystąpienia. Użytkownicy mogą zaimplementować wzorzec dzierżawienia dla wystąpienia okres istnienia podobny do komunikacji zdalnej programu .NET Framework. Można to zrobić za pomocą interfejsów okres istnienia wystąpienia kontekstu.  
  
-   Obsługa błędów niestandardowych. Użytkownicy mogą kontrolować sposób zarówno lokalnych błędy są przetwarzane i jak błędy są przekazywane do klientów. To może być implementowane za pomocą <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejsów.  
  
-   Autoryzacja niestandardowa zachowania. Użytkownicy mogą zaimplementować kontroli dostępu niestandardowe rozszerzenie części środowiska wykonawczego umowy lub operacji i dodając kontroli zabezpieczeń oparte na tokeny w wiadomości. Można to zrobić za pomocą przechwytujący lub parametr interceptora interfejsów. Aby uzyskać przykłady, zobacz [rozszerzalność zabezpieczeń](../../../../docs/framework/wcf/samples/security-extensibility.md).  
  
    > [!CAUTION]
    >  Ponieważ zmiany właściwości zabezpieczeń może naruszyć bezpieczeństwo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji, zdecydowanie zaleca się podejmowania związanych z zabezpieczeniami modyfikacje ostrożnie, a dokładnie przetestować przed wdrożeniem.  
  
-   WCF niestandardowe moduły weryfikacji środowiska wykonawczego. Sprawdź, czy usługi, kontrakty i powiązania wymuszać zasady na poziomie przedsiębiorstwa w odniesieniu do niestandardowych modułów weryfikacji można zainstalować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji. (Na przykład, zobacz [porady: blokowanie dół punktów końcowych w przedsiębiorstwie](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).)  
  
### <a name="using-the-dispatchruntime-class"></a>Używanie klasy obiektu DispatchRuntime  
 Użyj <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klasy zmodyfikować domyślne zachowanie usługi lub poszczególnych punktu końcowego, lub Wstaw obiektów implementujących niestandardowymi modyfikacjami do jednej lub obu następujących procesów usługi (lub procesów klienta w przypadku klienta dupleks):  
  
-   Transformacja komunikatów przychodzących do obiektów i zwolnienie tych obiektów jako wywołania metod na obiekt usługi.  
  
-   Transformacja obiektów odebranych z odpowiedź na wywołania operacji usługi w komunikatach wychodzących.  
  
 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> Umożliwia przechwytywanie i rozszerzyć dyspozytora kanału lub punkt końcowy dla wszystkich wiadomości na określonej umowy, nawet wtedy, gdy komunikat nie został rozpoznany. Gdy nadejścia wiadomości, który nie pasuje do żadnego zadeklarowany w kontrakt jest wysyłane do zwrócony przez operację <xref:System.ServiceModel.Dispatcher.DispatchRuntime.UnhandledDispatchOperation%2A> właściwości. Aby przechwycić lub rozszerzyć na wszystkie komunikaty dla określonej operacji, zobacz <xref:System.ServiceModel.Dispatcher.DispatchOperation> klasy.  
  
 Istnieją cztery główne obszary rozszerzalności dyspozytora udostępnianych przez <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klasy:  
  
1.  Właściwości użyj składników kanału <xref:System.ServiceModel.Dispatcher.DispatchRuntime> , a także dyspozytora kanału skojarzone zwrócony przez <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ChannelDispatcher%2A> właściwości, aby dostosować akceptuje i zamyka kanały dyspozytora kanału. Ta kategoria zawiera <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ChannelInitializers%2A> i <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InputSessionShutdownHandlers%2A> właściwości.  
  
2.  Składniki wiadomości są dostosowane dla każdego komunikatu przetworzone. Ta kategoria zawiera <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A>, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A>, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A>i <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ErrorHandlers%2A> właściwości.  
  
3.  Składniki wystąpienia dostosować tworzenie, okres istnienia i usuwania wystąpienia typu usługi. Aby uzyskać więcej informacji na temat okresy istnienia obiektu usługi, zobacz <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> właściwości. Ta kategoria zawiera <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> i <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> właściwości.  
  
4.  Składniki związane z zabezpieczeniami można użyć następujących właściwości:  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A>Wskazuje, gdzie są zapisywane zdarzenia inspekcji.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ImpersonateCallerForAllOperations%2A>Określa, czy usługa próbuje dokonać personifikacji, używając poświadczeń dostarczonych w komunikacie przychodzącym.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageAuthenticationAuditLevel%2A>Określa, czy pomyślnie komunikatów uwierzytelniania zdarzenia są zapisywane w dzienniku zdarzeń określony przez <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A>.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.PrincipalPermissionMode%2A>Formanty jak <xref:System.Threading.Thread.CurrentPrincipal%2A> właściwość jest ustawiona.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ServiceAuthorizationAuditLevel%2A>Określa, jak wykonać inspekcji zdarzeń autoryzacji.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SuppressAuditFailure%2A>Określa, czy pominąć Niekrytyczne wyjątki, które występują w procesie rejestracji.  
  
 Zazwyczaj rozszerzenia niestandardowego obiekty są przypisywane do <xref:System.ServiceModel.Dispatcher.DispatchRuntime> właściwości lub wstawione do kolekcji przez zachowanie usługi (obiekt, który implementuje <xref:System.ServiceModel.Description.IServiceBehavior>), zachowanie kontraktu (obiekt, który implementuje <xref:System.ServiceModel.Description.IContractBehavior>), lub punktu końcowego zachowanie (obiekt, który implementuje <xref:System.ServiceModel.Description.IEndpointBehavior>). Instalowanie obiektu zachowanie jest dodawana do odpowiedniej kolekcji zachowań programowo lub dzięki implementacji niestandardowego <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> obiekt, aby umożliwić działanie ma zostać wstawiony przy użyciu pliku konfiguracji aplikacji.  
  
 Dupleks (klientów, którzy zaimplementować kontrakt wywołania zwrotnego, określony przez usługi duplex) mają <xref:System.ServiceModel.Dispatcher.DispatchRuntime> obiekt, który można uzyskać dostęp za pomocą <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> właściwości.  
  
### <a name="using-the-dispatchoperation-class"></a>Używanie klasy DispatchOperation  
 <xref:System.ServiceModel.Dispatcher.DispatchOperation> Klasy to lokalizacja w modyfikacje w czasie wykonywania i dodanie punktu niestandardowych rozszerzeń, które są ograniczone do operacji tylko jedna usługa. (Aby zmodyfikować zachowanie usługi czasu wykonywania dla wszystkich wiadomości w umowie, użyj <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klasy.)  
  
 Zainstaluj <xref:System.ServiceModel.Dispatcher.DispatchOperation> modyfikacje przy użyciu obiektu zachowanie usługi niestandardowej.  
  
 Użyj <xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A> właściwości, aby zlokalizować <xref:System.ServiceModel.Dispatcher.DispatchOperation> obiekt reprezentujący operację określonej usługi.  
  
 Następujące właściwości formantu wykonywania środowiska uruchomieniowego na poziomie operacji:  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.Action%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReplyAction%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.FaultContractInfos%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsOneWay%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsTerminating%2A>, I <xref:System.ServiceModel.Dispatcher.DispatchOperation.Name%2A> właściwości uzyskać odpowiednie wartości dla tej operacji.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionAutoComplete%2A> i <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionRequired%2A> Określ zachowanie transakcji.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceBeforeCall%2A> i <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceAfterCall%2A> właściwości formantu okres istnienia obiektu użytkownika usługi względem <xref:System.ServiceModel.InstanceContext>.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.DeserializeRequest%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.SerializeReply%2A>i <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> właściwości włączyć jawną kontrolę nad konwersja z wiadomości na obiekty i do wiadomości.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.Impersonation%2A> Właściwość określa poziom personifikacji operacji.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.CallContextInitializers%2A> Właściwość wstawia rozszerzenia kontekstu wywołania niestandardowych dla tej operacji.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.AutoDisposeParameters%2A> Właściwość kontroluje, gdy parametr obiekty zostaną zniszczone.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.Invoker%2A> Właściwości, aby wstawić obiekt wywołujący niestandardowego.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A> Właściwości umożliwia wstawianie inspektora parametru niestandardowego, który służy do sprawdzania lub modyfikowanie parametrów i wartości zwracane.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Dispatcher.DispatchRuntime>  
 <xref:System.ServiceModel.Dispatcher.DispatchOperation>  
 [Instrukcje: sprawdzanie i modyfikowanie komunikatów w usłudze](../../../../docs/framework/wcf/extending/how-to-inspect-and-modify-messages-on-the-service.md)  
 [Instrukcje: inspekcja lub modyfikowanie parametrów](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md)  
 [Instrukcje: blokowanie punktów końcowych w przedsiębiorstwie](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md)
