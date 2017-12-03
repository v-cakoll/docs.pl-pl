---
title: "Struktura usługi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75f60b87-f80e-4377-ba7c-8e6becaa2b28
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2ced290c0644fcf89fdf3f87778e705794164b0f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="service-framework"></a>Struktura usługi
W tym temacie wymieniono wszystkie wyjątki generowane przez dane struktury usługi.  
  
## <a name="exception-list"></a>Listy wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|ABindingInstanceHasAlreadyBeenAssociatedTo1|Wystąpienie powiązania zostało skojarzone już nasłuchiwanie określony identyfikator. Jeśli dwa punkty końcowe chcą udostępniać wskaźnik tego samego zasobu ListenUniform, musi również współużytkować tego samego wystąpienia obiektu powiązania. Dwa punkty końcowe wywołujące konflikt zostały określone w wywołaniach metody AddServiceEndpoint(), w pliku konfiguracji lub kombinację AddServiceEndpoint() i konfiguracji.|  
|AChannelServiceEndpointIsNull0|Punkt końcowy kanału lub usługi ma wartość null.|  
|AChannelServiceEndpointSContractSNameIsNull0|Nazwa kontraktu punktu końcowego kanału/usługi jest zerowy lub pusty.|  
|AChannelServiceEndpointSContractSNamespace0|Przestrzeń nazw kontraktu punktu końcowego kanału/usługi jest zerowy.|  
|BaseAddressCannotHaveFragment|Adres podstawowy nie może zawierać fragmentu identyfikatora URI.|  
|BaseAddressCannotHaveQuery|Adres podstawowy nie może zawierać ciągu zapytania identyfikatora URI.|  
|BaseAddressCannotHaveUserInfo|Adres podstawowy nie może zawierać sekcji informacji użytkownika identyfikator URI.|  
|BaseAddressDuplicateScheme|Ta kolekcja zawiera już adres ze schematem określony. Dozwolony jest tylko jeden adres dla każdego schematu w tej kolekcji.|  
|BaseAddressMustBeAbsolute|Tylko bezwzględny identyfikator uniform resource identifier może służyć jako adres podstawowy.|  
|BindingDoesnTSupportAnyChannelTypes1|Określone powiązanie nie obsługuje tworzenia żadnych typów kanałów. Elementy wiązania niestandardowego są niepoprawnie ułożone lub w niewłaściwej kolejności. Transport jest musi być na spodzie stosu. Zalecana kolejność elementów powiązania to: TransactionFlow, ReliableSession, Security, CompositeDuplex, OneWay, StreamSecurity, MessageEncoding, Transport.|  
|BindingDoesnTSupportDuplexButContractRequires1|Kontrakt wymaga elementu Duplex. Określone powiązanie nie obsługuje lub jest niepoprawnie skonfigurowany do jego obsługi.|  
|BindingDoesnTSupportOneWayButContractRequires1|Kontrakt wymaga elementu OneWay. Określone powiązanie nie obsługuje lub jest niepoprawnie skonfigurowany do jego obsługi.|  
|BindingDoesnTSupportRequestReplyButContract1|Kontrakt wymaga elementu Request/Reply. Określone powiązanie nie obsługuje lub jest niepoprawnie skonfigurowany do jego obsługi.|  
|BindingDoesnTSupportSessionButContractRequires1|Kontrakt wymaga elementu Session.  Określone powiązanie nie obsługuje lub jest niepoprawnie skonfigurowany do jego obsługi.|  
|BindingDoesnTSupportTwoWayButContractRequires1|Kontrakt wymaga dwukierunkowego (żądanie odpowiedź lub dupleks). Określone powiązanie nie obsługuje lub jest niepoprawnie skonfigurowany do jego obsługi.|  
|BindingRequirementsAttributeDisallowsQueuedDelivery1|Element DeliveryRequirementsAttribute nie zezwala na elementu QueuedDelivery. Powiązanie dla punktu końcowego z kontraktem określonego go obsługuje.|  
|BindingRequirementsAttributeRequiresQueuedDelivery1|Element DeliveryRequirementsAttribute wymaga elementu QueuedDelivery. Powiązanie dla punktu końcowego z kontraktem określonego nie obsługuje lub jest niepoprawnie skonfigurowany do jego obsługi.|  
|channelDoesNotHaveADuplexSession0|Ten kanał nie obsługuje zamykania sesji wyjściowej. Ten kanał nie ma zaimplementowanego elementu ISessionChannel\<IDuplexSession >.|  
|ClientRuntimeRequiresFormatter0|Określony element ClientOperation wymaga wartości formatter, ponieważ SerializeRequest i DeserializeReply nie są zarówno wartość false.|  
|CommunicationObjectAborted1|Nie można użyć obiektu komunikacji określony do komunikacji, ponieważ została zatrzymana.|  
|CommunicationObjectAbortedStack2|Obiektu komunikacyjnego określony nie można użyć do komunikacji, ponieważ została zatrzymana: {1}|  
|CommunicationObjectBaseClassMethodNotCalled|Obiektu komunikacyjnego określonego zastąpiono {1} funkcji wirtualnej, ale nie wywołuje wersji zdefiniowanej w klasie podstawowej.|  
|ContractIsNotSelfConsistentItHasOneOrMore2|Kontrakt określony ma IsTerminating lub inną niż IsInitiating. Nie ma właściwości SessionMode z ustawioną wartością SessionMode.Required. Atrybutów IsInitiating i IsTerminating można używać tylko w kontekście sesji.|  
|CouldnTCreateChannelForChannelType2|Zażądano określony typ kanału, ale określone powiązanie nie obsługuje lub jest niepoprawnie skonfigurowany do jego obsługi.|  
|DispatchRuntimeRequiresFormatter0|Określony element DispatchOperation wymaga wartości Formatter, ponieważ DeserializeRequest i SerializeReply nie są zarówno wartość false.|  
|EndMethodsCannotBeDecoratedWithOperationContractAttribute|Nie można użyć metody End atrybutem OperationContractAttribute, używając wzorzec projektowy IAsyncResult. Jedynie odpowiednia metoda Begin może służyć atrybutem OperationContractAttribute. Ten atrybut ma zastosowanie do pary metod Begin-End.|  
|EndpointListenerRequirementsCannotBeMetBy3|Nie można spełnić wymagań obiektu ChannelDispatcher IChannelListener dla określonego powiązania, ponieważ kontrakt wymaga obsługi jednego z typów kanałów określony. Ale powiązanie obsługuje tylko te typy określonego kanału.|  
|EndpointsMustHaveAValidBinding0|Punkty końcowe muszą mieć prawidłowe powiązanie.|  
|InvalidOrUnrecognizedAction|Wiadomość nie może przetworzyć, ponieważ określona akcja jest nieprawidłowy lub nierozpoznany.|  
|MultipleMebesInParameters|Znaleziono więcej niż jeden element MessageEncodingBindingElement we właściwości BindingParameters elementu BindingContext. CustomBinding nie może mieć wielu elementów MessageEncodingBindingElements. Usuń wszystkie oprócz jednego z tych elementów.|  
|MultipleStreamUpgradeProvidersInParameters|We właściwości BindingParameters elementu BindingContext znaleziono więcej niż jeden element. CustomBinding nie może mieć więcej niż jeden IStreamUpgradeProviderElements. Usuń wszystkie oprócz jednego z tych elementów.|  
|NoChannelBuilderAvailable|Powiązanie nie można utworzyć fabryki kanału lub odbiornika kanałów, ponieważ nie ma elementu TransportBindingElement. Każde powiązanie musi zawierać co najmniej jeden element powiązania pochodzący z klasy TransportBindingElement.|  
|NotAllBindingElementsBuilt|Niektóre elementy tego powiązania nie zostały użyte podczas budowania fabryki kanału i odbiornika kanałów. Elementy powiązania nie są poprawnie określona. Zalecana kolejność elementów powiązania to: TransactionFlow, ReliableSession, Security, CompositeDuplex, OneWay, StreamSecurity, MessageEncoding, Transport.  Należy pamiętać, że element TransportBindingElement musi być ostatni. Elementy określone powiązanie nie zostały skompilowane.|  
|RuntimeRequiresInvoker0|Operacja wysyłania wymaga elementu wywołującego.|  
|ServiceHasZeroAppEndpoints|Określona usługa nie ma aplikacji (z systemem innym niż infrastruktury) punktów końcowych. Może to być, ponieważ plik konfiguracji nie znaleziono aplikacji lub ponieważ brak elementu usługi pasującego do nazwy usługi można znaleźć w pliku konfiguracji lub punkty końcowe nie zostały zdefiniowane w elemencie usługi.|  
|SFxActionMismatch|Nie można utworzyć komunikatu mającego określony typ z powodu niezgodności akcji. Oczekiwano innego napotkano ale określonej akcji|  
|SFxAnonymousTypeNotSupported|Określona część w określony komunikat nie można wyeksportować przez usługę RPC lub zakodowane, ponieważ jej typ jest anonimowy.|  
|SFxBadMetadataLocationNoAppropriateBaseAddress|Adres URL dostarczony do elementu ServiceMetadataBehavior przy użyciu właściwość ExternalMetadataLocation lub atrybut externalMetadataLocation w sekcji serviceMetadata w sekcji konfiguracji był względnym adresem URL i nie ma adresu podstawowego, z której chcesz rozwiązać go.|  
|SFxBadMetadataMustBePolicy|Podać zasady XmlElement z określonego obszaru nazw i nazwę. Ten element XmlElement ma określonego obszaru nazw i nazwę.|  
|SFxBodyObjectTypeCannotBeInherited|Określony typ nie może dziedziczyć z żadnej klasie innej niż obiekt, który ma być używany jako obiekt treści w stylu wywołania RPC.|  
|SFxBodyObjectTypeCannotBeInterface|Określony typ implementuje określonego interfejsu, który nie jest obsługiwany dla obiekt treści w stylu wywołania RPC.|  
|SFxCallbackBehaviorAttributeOnlyOnDuplex|Atrybut CallbackBehaviorAttribute być wykonywany wyłącznie jako zachowanie w punkcie końcowym pomocą kontraktu dwukierunkowego. Kontrakt określony nie jest dupleksowy i zawiera żadnych operacji wywołania zwrotnego.|  
|SFxCallbackRequestReplyInOrder1|Nie można odebrać odpowiedzi od tej operacji, dopóki zakończeniem przetwarzania bieżącego komunikatu. Jeśli chcesz zezwolić na przetwarzanie komunikatów poza kolejnością, określ właściwość ConcurrencyMode elementu Reentrant lub Multiple na określony.|  
|SfxCallbackTypeCannotBeNull|Aby użyć kontraktu określonego obiektu DuplexChannelFactory, kontrakt musi zawierać poprawny kontrakt wywołania zwrotnego. Jeśli dany kontrakt kontrakt wywołania zwrotnego, należy użyć elementu ChannelFactory zamiast elementu DuplexChannelFactory.|  
|SFxCannotGetMetadataFromLocation|Element MetadataExchangeClient może pobierać metadane tylko z protokołu HTTP i HTTPS elementów MetadataLocations typu. Nie może pobierać metadanych z określonego.|  
|SFxCannotHttpGetMetadataFromAddress|Element MetadataExchangeClient może pobierać metadane tylko z adresów HTTP i HTTPS korzystając z metody MetadataExchangeClientMode HttpGet. Nie może pobierać metadanych z określonego.|  
|SFxCannotImportAsParameters_Bare|Trwa generowanie kontraktu komunikatu, ponieważ określona operacja nie jest RPC ani opakowanym dokumentem.|  
|SFxCannotImportAsParameters_DifferentWrapperName|Trwa generowanie kontraktu komunikatu, ponieważ nazwa otoki określony komunikat nie jest zgodna z wartością domyślną.|  
|SFxCannotImportAsParameters_DifferentWrapperNs|Trwa generowanie kontraktu komunikatu, ponieważ przestrzeń nazw otoki określony komunikat jest niezgodna z wartością domyślną.|  
|SFxCannotImportAsParameters_ElementIsNotNillable|Trwa generowanie kontraktu komunikatu, ponieważ określonej nazwy elementu z określonego obszaru nazw nie jest oznaczony jako może być zerowy.|  
|SFxCannotImportAsParameters_HeadersAreUnsupported|Trwa generowanie kontraktu komunikatu, ponieważ określony komunikat zawiera nagłówki.|  
|SFxCannotImportAsParameters_Message|Trwa generowanie kontraktu komunikatu, ponieważ określonej operacji występuje komunikat bez jako argument lub typ zwracany.|  
|SFxCannotImportAsParameters_MessageHasProtectionLevel|Trwa generowanie kontraktu komunikatu, ponieważ określony komunikat wymaga ochrony.|  
|SFxCannotImportAsParameters_NamespaceMismatch|Trwa generowanie kontraktu komunikatu, ponieważ obszar nazw części określony komunikat jest niezgodna z wartością domyślną.|  
|SFxCannotRequireBothSessionAndDatagram3|Kontrakt określony Określa atrybut SessionMode.NotAllowed i określony kontrakt Określa atrybut SessionMode.Required. Zmień jedną z wartości atrybutu SessionMode lub określ inny adres lub identyfikator ListenURI, dla każdego punktu końcowego.|  
|SFxCannotSetExtensionsByIndex|Ta kolekcja nie obsługuje ustawiania rozszerzeń według indeksu. Użyj metody InsertItem lub RemoveItem.|  
|SFxChannelDispatcherDifferentHost0|Element ChannelDispatcher nie jest obecnie dołączony do obiektu ServiceHost, który został dostarczony.|  
|SFxChannelDispatcherMultipleHost0|Nie można dodać elementu ChannelDispatcher do więcej niż jednego elementu ServiceHost.|  
|SFxChannelDispatcherNoHost0|Nie można otworzyć elementu ChannelDispatcher, ponieważ nie jest on dołączony do żadnego elementu ServiceHost.|  
|SfxChannelFactoryDisposed|Nie można otworzyć tego elementu ChannelFactory, ponieważ ChannelFactory został już usunięty. Tworzenie elementu ChannelFactory ponownie przed jego użyciem.|  
|SFxChannelFactoryNoBinding|Nie można otworzyć elementu ChannelFactory, ponieważ żadne powiązanie nie został skojarzony z punktu końcowego. Określanie powiązania z konstruktora lub właściwości endpoint.|  
|SFxChannelTerminated0|Operację oznaczoną jako IsTerminating została już wywołana w tym kanale, co powoduje przerwanie połączenia kanału. Nie ma więcej operacji mogą być przywoływane w tym kanale. Ponowne tworzenie kanału, aby kontynuować komunikację.|  
|SFxCloseTimedOut1|Operacja zamykania elementu ServiceHost zatrzymany po określony. Może to być spowodowane klienta zamknięcie zakończyło się niepowodzeniem podczas zamykania kanału sesji w wymaganym czasie. Czas, w dozwolone dla tej operacji mógł być częścią dłuższego limitu czasu.|  
|SfxCloseTimedOutWaitingForDispatchToComplete|Zamknij proces upłynął limit czasu podczas oczekiwania na zakończenie wysyłania usługi.|  
|SFxCodeGenIsNotAssignableFrom|Nie można przypisać określony.|  
|SFxConfigChannelConfigurationNotFound|Nie można odnaleźć elementu punktu końcowego o określonej nazwie i kontraktu w sekcji konfiguracji klienta ServiceModel.|  
|SFxConflictingGlobalElement|Element najwyższego poziomu Extensible Markup Language o określonej nazwie w określonej przestrzeni nazw nie mogą odwoływać określonego typu. Odwołuje się już innego typu. Użyj innej nazwy operacji lub MessageBodyAttribute, aby określić inną nazwę dla komunikatu lub części wiadomości.|  
|SFxContractHasZeroInitiatingOperations|Kontrakt musi zawierać co najmniej jeden IsInitiating = true operacji.|  
|SFxContractHasZeroOperations|Kontrakt musi zawierać co najmniej jedną operację.|  
|SFxContractInheritanceRequiresInterfaces|Klasa usługi o określonym typie definiuje element ServiceContract i dziedziczy go z określonego typu. Dziedziczenie kontraktów można używać tylko między typami interfejsów. Jeśli klasa jest oznaczona przy użyciu atrybutu ServiceContractAttribute, musi być jedynym typem w hierarchii przy użyciu atrybutu ServiceContractAttribute.  Przejdź do oddzielnych interfejs, który implementuje określonego typu obiektu ServiceContractAttribute określonego typu.|  
|SFxCreateDuplexChannel1|Kontrakt wywołania zwrotnego określonego kontraktu nie istnieje lub nie definiuje żadnych operacji. Jeśli nie jest to kontrakt dupleksowy, należy użyć elementu ChannelFactory zamiast elementu DuplexChannelFactory.|  
|SFxCreateDuplexChannelNoCallback|Nie można wywołać tego przeciążenia metody CreateChannel dla tego wystąpienia obiektu DuplexChannelFactory. Obiekt DuplexChannelFactory nie został zainicjowany z argument typu InstanceContext. Wywołania przeciążenia metody CreateChannel, które przyjmuje argument typu InstanceContext.|  
|SFxCreateDuplexChannelNoCallback1|Nie można wywołać tego przeciążenia metody CreateChannel dla tego wystąpienia obiektu DuplexChannelFactory. Obiekt DuplexChannelFactory został zainicjowany typem i nie został podany nie poprawnego obiektu InstanceContext. Wywołania przeciążenia metody CreateChannel, które przyjmuje argument typu InstanceContext.|  
|SFxCreateDuplexChannelNoCallbackUserObject|Nie można wywołać tego przeciążenia metody CreateChannel dla tego wystąpienia obiektu DuplexChannelFactory. Obiekt InstanceContext przekazany do obiektu DuplexChannelFactory nie zawiera poprawnego obiektu UserObject.|  
|SFxCreateNonDuplexChannel1|ChannelFactory nie obsługuje określonego kontraktu. Obiekt ChannelFactory definiuje kontrakt wywołania zwrotnego z jedną lub więcej operacji. Użyj obiektu DuplexChannelFactory zamiast obiektu ChannelFactory.|  
|SFxCustomBindingNeedsTransport1|W elemencie CustomBinding w obiekcie ServiceEndpoint z kontraktem określony nie zawiera elementu TransportBindingElement. Każde powiązanie musi zawierać co najmniej jeden element powiązania pochodzący z klasy TransportBindingElement.|  
|SFxCustomBindingWithoutTransport|Nie można obliczyć schematu dla tego powiązania niestandardowego, ponieważ nie ma elementu TransportBindingElement. Każde powiązanie musi zawierać co najmniej jeden element powiązania pochodzący z klasy TransportBindingElement.|  
|SFxDataContractSerializerDoesNotSupportBareArray|Obiekt DataContractSerializer nie obsługuje określonej dla określonego elementu kolekcji.|  
|SFxDictionaryIsEmpty|Nie można wykonać operacji, ponieważ słownik jest pusty.|  
|SFxDocEncodedNotSupported|Błąd odzwierciedlający określony. Kodowany w formacie dokumentu nie jest obsługiwana. Zmień "Use" literał lub "Styl" RPC.|  
|SFxDuplicateInitiatingActionAtSameVia|Ta usługa ma wiele punktów końcowych nasłuchujących pod adresem określonym. Punkty końcowe mają tę samą akcję inicjującą określony. Czy można usunąć wiadomości z tej akcji, ponieważ dyspozytor nie będzie w stanie określić właściwego punktu końcowego do obsługi komunikatu.|  
|SFXEndpointBehaviorUsedOnWrongSide|Nie można użyć interfejsu IEndpointBehavior określonego na serwerze. To zachowanie można ma zastosowanie tylko do klientów.|  
|SFxEndpointNoMatchingScheme|Nie można odnaleźć pasującego do określonego schematu dla punktu końcowego z powiązaniem określony adres podstawowy. Schematy adresów podstawowych zarejestrowanych zostały określone.|  
|SFxErrorCreatingMtomReader|Wystąpił błąd podczas tworzenia modułu odczytującego dla komunikatu mechanizmu optymalizacji transmisji wiadomości.|  
|SFxErrorDeserializingFault|Serwer zwrócił błąd protokołu dostępu nieprawidłowy prostego obiektu. Aby uzyskać więcej informacji, zobacz InnerException.|  
|SFxErrorDeserializingHeader|Wystąpił błąd podczas deserializacji jednego z nagłówków określonego komunikatu. Aby uzyskać więcej informacji, zobacz InnerException.|  
|SFxErrorReflectingOnMethod3|Wystąpił błąd podczas ładowania określonego atrybutu na określonej metody w określonym typie.  Aby uzyskać więcej informacji, zobacz InnerException.|  
|SFxErrorReflectingOnParameter4|Wystąpił błąd podczas ładowania określonego atrybutu na określony parametr metody określonej w określonego typu. Aby uzyskać więcej informacji, zobacz InnerException.|  
|SFxErrorReflectingOnType2|Wystąpił błąd podczas ładowania określonego atrybutu dla określonego typu.  Aby uzyskać więcej informacji, zobacz InnerException.|  
|SFxErrorSerializingBody|Wystąpił błąd podczas serializacji treści określonego komunikatu. Aby uzyskać więcej informacji, zobacz InnerException.|  
|SFxErrorSerializingHeader|Wystąpił błąd podczas serializacji jednego z nagłówków określonego komunikatu. Aby uzyskać więcej informacji, zobacz InnerException.|  
|SFxExpectedIMethodCallMessage|Błąd wewnętrzny. Wiadomość musi być poprawnym interfejsem IMethodCallMessage.|  
|SFxExportMustHaveType|Nie można wyeksportować określona część w określonej operacji, ponieważ nie ma prawidłowego typu CLR.|  
|SFxHeaderNotUnderstood|Wiadomość nie została przetworzona. Określony nagłówek z określonego obszaru nazw nie został zrozumiany przez odbiorcę tego komunikatu. Ten błąd zazwyczaj oznacza, że nadawca komunikatu włączył protokół komunikacyjny, którego odbiorca nie może przetworzyć. Upewnij się, że konfiguracja powiązań klienta jest spójna z powiązaniem usługi.|  
|SFxHeadersAreNotSupportedInEncoded|Określony komunikat nie może mieć nagłówków, aby można używać w stylu zakodowane wywołanie procedury zdalnej.|  
|SFxInconsistentWsdlOperationStyleInMessageParts|Wszystkie części komunikatu w określonej operacji musi zawierać typ lub element.|  
|SFxInconsistentWsdlOperationStyleInOperationMessages|Określony styl wywnioskować na podstawie wiadomości w określonej operacji jest niezgodny z określonym oczekiwanemu stylowi określony przy użyciu powiązań.|  
|SFxInvalidCallbackIAsyncResult|IAsyncResult nie jest podany lub jest nieprawidłowego typu.|  
|SFxInvalidMessageBody|Obiekt OperationFormatter napotkał nieprawidłową treść. Oczekiwano typu węzła "Element" z określoną nazwą i przestrzeni nazw. Określony typ węzła o określonej nazwie i przestrzeni nazw został znaleziony.|  
|SFxInvalidMessageBodyEmptyMessage|Obiekt OperationFormatter nie można zdeserializować żadnej informacji z komunikatu, ponieważ komunikat jest pusty.|  
|SFxInvalidMessageBodyErrorDeserializingParameter|Wystąpił błąd podczas próby deserializacji określony parametr. Aby uzyskać więcej informacji, zobacz InnerException.|  
|SFxInvalidMessageBodyErrorSerializingParameter|Wystąpił błąd podczas próby serializowania określony parametr. Określono komunikat InnerException.  Aby uzyskać więcej informacji, zobacz InnerException.|  
|SFxInvalidMessageBodyUnexpectedNode|Napotkano nieoczekiwany określony węzeł, z określonego obszaru nazw podczas deserializacji parametrów.|  
|SFxInvalidMessageContractSignature|Określona operacja ma parametr lub typ zwracany jest oznaczony atrybutem MessageContractAttribute. Reprezentuje komunikat żądania za pomocą kontraktu komunikatu, operacja musi mieć jeden parametr, który jest oznaczony atrybutem MessageContractAttribute. Reprezentuje komunikat odpowiedzi za pomocą kontraktu komunikatu, wartość zwracana operacji musi być typu, który jest oznaczony atrybutem MessageContractAttribute. Operacja nie może mieć żadnych "out" lub "ref" parametrów.|  
|SFxInvalidReplyAction|Wychodzący komunikat odpowiedzi dla operacji ma określonej akcji, ale kontrakt dla danej operacji określa ReplyAction innego. Akcja określonymi w komunikacie musi odpowiadać parametrowi ReplyAction w kontrakcie lub kontrakt operacji musi określać parametr ReplyAction = "*".|  
|SFxInvalidRequestAction|Wychodzący komunikat żądania dla operacji ma określonej akcji, ale kontrakt dla danej operacji określa RequestAction innego. Akcja określonymi w komunikacie musi odpowiadać RequestAction w kontrakcie lub kontrakt operacji musi określać RequestAction = "*".|  
|SFxInvalidStaticOverloadCalledForDuplexChannelFactory1|Statyczna metoda CreateChannel nie można użyć z określonym kontraktem, ponieważ kontrakt definiuje kontrakt wywołania zwrotnego. Użyj jednej z statycznych przeciążeń klasy CreateChannel w kanale DuplexChannelFactory\<TChannel >.|  
|SFxInvalidStreamInRequest|Dla żądania w określonej operacji była strumieniem operacja musi mieć pojedynczy parametr typu Stream.|  
|SFxInvalidStreamInResponse|Odpowiedź w określonej operacji była strumieniem operacja musi mieć pojedynczy parametr wyjściowy lub zwrócić wartość, której typem jest strumienia.|  
|SFxInvalidStreamInTypedMessage|Aby użyć strumieni z kontraktu komunikatu, model programowania, określony typ musi mieć pojedynczego członka Element MessageBody, którego typ jest strumienia.|  
|SFxInvalidUseOfPrimitiveOperationFormatter|Metodzie PrimitiveOperationFormatter podano parametr lub zwracany typ, który nie obsługuje.|  
|SFxMessageContractBaseTypeNotValid|Określony typ definiuje kontrakt MessageContract i pochodzi z określonego typu, który nie definiuje kontrakt MessageContract. Wszystkie obiekty w hierarchii dziedziczenia określonej musi definiować kontrakt MessageContract.|  
|SFxMethodNotSupported1|Określona metoda nie jest obsługiwana dla tego obiektu. Może to się zdarzyć, jeśli metoda nie jest oznaczona atrybutem OperationContractAttribute lub jeśli typ interfejsu nie jest oznaczony atrybutem ServiceContractAttribute.|  
|SFxMethodNotSupportedByType2|Określony typ implementacji ServiceHost nie implementuje kontraktu określonej usługi.|  
|SFxMethodNotSupportedOnCallback1|Metoda określona wywołania zwrotnego nie jest obsługiwana. Może to się zdarzyć, jeśli metoda nie jest oznaczona atrybutem OperationContractAttribute lub jeśli typ interfejsu nie jest element docelowy element CallbackContract z ServiceContractAttribute.|  
|SFxMismatchedOperationParent|Element DispatchOperation lub ClientOperation można dodać tylko do elementu nadrzędnego DispatchRuntime lub ClientRuntime odpowiednio.|  
|SFxNameCannotBeEmpty|Właściwość Name nie może być pustym ciągiem.|  
|SfxNoTypeSpecifiedForParameter|Typ CLR nie został określony dla parametru, który uniemożliwia wykonanie operacji generowania.|  
|SFxOperationBehaviorAttributeOnlyOnServiceClass|OperationBehaviorAttribute może przejść tylko w klasie usługi. Nie można umieścić z interfejsem ServiceContract. Określonej metody dla określonego typu narusza ten warunek.|  
|SFxOperationContractOnNonServiceContract|Określona metoda jest oznaczona atrybutem OperationContractAttribute, ale określony typ otaczający nie jest oznaczony atrybutem ServiceContractAttribute. Atrybut OperationContractAttribute może służyć tylko w metodach typów ServiceContractAttribute lub w ich typach CallbackContract.|  
|SFxParameterCountMismatch|Wystąpiła niezgodność między liczbą przekazanych argumentów a liczbą oczekiwanych argumentów. W szczególności określony argument ma określoną liczbę elementów, podczas gdy oczekiwano argument ma określoną liczbę elementów.|  
|SFxPartNameMustBeUniqueInRpc|Nazwa części określony komunikat nie jest unikatowa w komunikacie wywołanie procedury zdalnej.|  
|SFxReplyActionMismatch3|Otrzymano komunikat odpowiedzi dla określonej operacji z określonej akcji. Jednak kod klienta wymaga określonej akcji.|  
|SFxRequestReplyNone|Odebrano komunikat z nagłówkiem WS-Addressing ReplyTo lub FaultTo celem "None" adres. Te wartości są nieprawidłowe dla operacji żądanie odpowiedź. Użyj operacji jednokierunkowych lub Włącz opcję ManualAddressing, jeśli wymagana jest obsługa ReplyTo lub FaultTo wartości "None".|  
|SFxRequestTimedOut1|Żądanie nie otrzymano odpowiedzi w określonym czasie skonfigurowany. Dozwolony czas mogły być częścią dłuższego limitu czasu. Może to być, ponieważ usługa jest nieukończone przetwarzanie operacji lub usługa nie może wysłać komunikatu odpowiedzi.|  
|SFxRequestTimedOut2|Operacji żądania wysyłane do określonej lokalizacji nie otrzymano odpowiedzi w określonym czasie skonfigurowany. Dozwolony czas mogły być częścią dłuższego limitu czasu. Może to być, ponieważ usługa jest nieukończone przetwarzanie operacji lub usługa nie może wysłać komunikatu odpowiedzi.|  
|SFxSchemaDoesNotContainType|Schemat z przestrzeni nazw określony element docelowy nie zawiera typu o określonej nazwie.|  
|SfxServiceContractAttributeNotFound|Kontrakt określony typ nie jest atrybutem ServiceContractAttribute. Aby zdefiniować prawidłowy kontrakt, określony typ musi mieć atrybut ServiceContractAttribute. Typ może być interfejsu kontraktu lub klasy usługi.|  
|SFxServiceContractGeneratorConfigRequired|Aby wygenerować informacje o konfiguracji przy użyciu metody GenerateServiceEndpoint, wystąpienie ServiceContractGenerator musi zostać zainicjowany z prawidłowym obiektem Configuration.|  
|SFxServiceHostBaseCannotAddEndpointAfterOpen|Nie można dodać punktów końcowych, po ServiceHost jest w jednym z następujących stanów:<br /><br /> -Otwarte<br />— Błąd<br />-Zakończone<br />-Zamknięte|  
|SFxServiceHostBaseCannotAddEndpointWithoutDescription|Nie można dodać punktów końcowych, przed zainicjowaniem właściwości Description.|  
|SFxServiceMetadataBehaviorNoHttpBaseAddress|HttpGetEnabled właściwość ServiceMetadataBehavior ma wartość true, a właściwość HttpGetUrl jest adresem względnym, lecz nie nie adresu podstawowego HTTP. Należy dostarczyć podstawowy adres HTTP, lub ustawić HttpGetUrl jako adres bezwzględny.|  
|SFxServiceMetadataBehaviorNoHttpsBaseAddress|HttpsGetEnabled właściwość ServiceMetadataBehavior ma wartość true, a właściwość HttpsGetUrl jest adresem względnym, lecz nie nie podstawowego adresu HTTPS. Należy dostarczyć podstawowy adres HTTPS, lub ustawić HttpsGetUrl jako adres bezwzględny.|  
|SFxServiceMetadataBehaviorUrlMustBeHttpOrRelative|Zachowanie adresu Url musi być identyfikator URI względną lub identyfikator bezwzględną uniform resource identifier z określonym systemem. Określony adres Url jest bezwzględny identyfikator z określonym systemem.|  
|SFxStreamRequestMessageClosed|Komunikat zawierający dany strumień został zamknięty. Nie można uzyskać dostępu do strumieni żądania po powrocie z operacji usługi.|  
|SFxStreamResponseMessageClosed|Komunikat zawierający dany strumień został zamknięty.|  
|SFxTerminateRequestProcessingException|Rozszerzenie w potoku operacji musi zakończyć przetwarzania tego komunikatu.|  
|SFxTerminatingOperationAlreadyCalled1|Ten kanał nie może wysłać więcej komunikatów, ponieważ operacja IsTerminating została wywołana.|  
|SFxThrottleLimitMustBeGreaterThanZero0|Limit przepustnicy musi być większa niż zero. Aby wyłączyć limit przepustnicy, ustaw wartość Int32.MaxValue.|  
|SFxTypedOrUntypedMessageCannotBeMixedWithVoidInRpc|Używając stylu RPC-encoded typy kontraktu komunikatu lub typ System.ServiceModel.Channels.Message nie używać, jeśli operacja nie ma parametrów lub ma pustą wartość zwracaną. Dodaj pusty typ kontraktu komunikatu jako parametr lub typ zwrotny do określonej operacji.|  
|SFxUserCodeThrewException|Operacja określony użytkownik zgłosił wyjątek, który jest nieobsługiwany w kodzie użytkownika. W przypadku problemu cykliczne może to oznaczać błąd w implementacji określonej metody.|  
|SfxUseTypedMessageForCustomAttributes|Określony parametr nie może być mapowany na parametr operacji, ponieważ wymaga dodatkowych atrybutów.|  
|SFxVersionMismatchInOperationContextAndMessage2|Nie można dodać nagłówków wychodzących do komunikatu, ponieważ MessageVersion w perationContext.Current nie odpowiada wersji nagłówka przetwarzanego komunikatu|  
|SFxWellKnownNonSingleton0|Aby użyć jednego z konstruktorów ServiceHost pobierającego wystąpienie usługi, tryb InstanceContextMode usługi musi mieć ustawioną InstanceContextMode.Single. Tę funkcję można skonfigurować za pomocą atrybutu ServiceBehaviorAttribute. W przeciwnym razie użyj konstruktorów ServiceHost przyjmujących Type argument.|  
|SFxWrapperTypeHasMultipleNamespaces|Typ otoki dla określony komunikat nie może być przekazywany jako typ kontraktu danych, ponieważ ma on wiele obszarów nazw. Za pomocą elementu XmlSerializer.|  
|UriMustBeAbsolute|Identyfikator URI musi być bezwzględny.|
