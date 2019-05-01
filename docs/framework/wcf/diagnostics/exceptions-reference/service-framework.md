---
title: Struktura usługi
ms.date: 03/30/2017
ms.assetid: 75f60b87-f80e-4377-ba7c-8e6becaa2b28
ms.openlocfilehash: 859e718a56ab63c8e012e1851c0730f53cb707be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780760"
---
# <a name="service-framework"></a>Struktura usługi
Ten temat zawiera listę wszystkich wyjątków generowanych przez dane struktury usługi.  
  
## <a name="exception-list"></a>Lista wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|ABindingInstanceHasAlreadyBeenAssociatedTo1|Wystąpienie obiektu binding już zostały skojarzone do nasłuchiwania określonego jednolity identyfikator zasobów. Aby udostępnić ten sam wskaźnik zasobów ListenUniform dwa punkty końcowe, mogą także udostępniać tego samego wystąpienia obiektu powiązania. Dwa punkty końcowe powodujące konflikt zostały określone w wywołaniach, w pliku konfiguracji lub kombinacji AddServiceEndpoint() i konfiguracji.|  
|AChannelServiceEndpointIsNull0|Punkt końcowy kanału lub usługi ma wartość null.|  
|AChannelServiceEndpointSContractSNameIsNull0|Nazwa kontraktu punktu końcowego kanału/usługi ma wartość null lub pusty.|  
|AChannelServiceEndpointSContractSNamespace0|Przestrzeń nazw kontraktu punktu końcowego kanału/usługi ma wartość null.|  
|BaseAddressCannotHaveFragment|Adres podstawowy nie może zawierać fragmentu identyfikatora URI.|  
|BaseAddressCannotHaveQuery|Adres podstawowy nie może zawierać ciągu zapytania identyfikatora URI.|  
|BaseAddressCannotHaveUserInfo|Adres podstawowy nie może zawierać sekcji informacji użytkownika identyfikatora uniform resource identifier.|  
|BaseAddressDuplicateScheme|Ta kolekcja zawiera już adres ze schematem określonym. Dozwolony jest tylko jeden adres dla każdego schematu w tej kolekcji.|  
|BaseAddressMustBeAbsolute|Tylko bezwzględne jednolity identyfikator zasobów może służyć jako adres podstawowy.|  
|BindingDoesnTSupportAnyChannelTypes1|Określone powiązanie nie obsługuje tworzenia żadnych typów kanałów. Elementy powiązania w niestandardowym powiązaniu są niepoprawnie ułożone lub w złej kolejności. Transport jest spodzie stosu. Zalecana kolejność elementów powiązania to: TransactionFlow, ReliableSession, Security, CompositeDuplex, OneWay, StreamSecurity, MessageEncoding, Transport.|  
|BindingDoesnTSupportDuplexButContractRequires1|Kontrakt wymaga elementu Duplex. Określone powiązanie nie obsługuje lub jest niepoprawnie skonfigurowany do jego obsługi.|  
|BindingDoesnTSupportOneWayButContractRequires1|Kontrakt wymaga elementu OneWay. Określone powiązanie nie obsługuje lub jest niepoprawnie skonfigurowany do jego obsługi.|  
|BindingDoesnTSupportRequestReplyButContract1|Kontrakt wymaga elementu żądanie/nietypizowana odpowiedź. Określone powiązanie nie obsługuje lub jest niepoprawnie skonfigurowany do jego obsługi.|  
|BindingDoesnTSupportSessionButContractRequires1|Kontrakt wymaga elementu Session.  Określone powiązanie nie obsługuje lub jest niepoprawnie skonfigurowany do jego obsługi.|  
|BindingDoesnTSupportTwoWayButContractRequires1|Kontrakt wymaga elementu dwukierunkowe (żądanie odpowiedź lub dupleks). Określone powiązanie nie obsługuje lub jest niepoprawnie skonfigurowany do jego obsługi.|  
|BindingRequirementsAttributeDisallowsQueuedDelivery1|Element DeliveryRequirementsAttribute nie zezwala na elementu QueuedDelivery. Powiązanie dla punktu końcowego za pomocą określonego kontraktu obsługuje tę funkcję.|  
|BindingRequirementsAttributeRequiresQueuedDelivery1|Element DeliveryRequirementsAttribute wymaga elementu QueuedDelivery. Powiązanie dla punktu końcowego za pomocą określonego kontraktu nie obsługuje lub jest niepoprawnie skonfigurowany do jego obsługi.|  
|channelDoesNotHaveADuplexSession0|Ten kanał nie obsługuje zamykania sesji wyjściowej. To nie ma zaimplementowanego elementu ISessionChannel\<IDuplexSession >.|  
|ClientRuntimeRequiresFormatter0|Określony element ClientOperation wymaga wartości formatter, ponieważ SerializeRequest i DeserializeReply mają wartość false.|  
|CommunicationObjectAborted1|Nie można użyć obiektu komunikacyjnego określony do komunikacji, ponieważ została zatrzymana.|  
|CommunicationObjectAbortedStack2|Nie można użyć obiektu komunikacyjnego określony do komunikacji, ponieważ została zatrzymana: {1}|  
|CommunicationObjectBaseClassMethodNotCalled|Obiektu komunikacyjnego określonego przesłonił funkcję wirtualną {1} , ale nie wywołuje wersji zdefiniowanej w klasie bazowej.|  
|ContractIsNotSelfConsistentItHasOneOrMore2|Kontrakt określony ma jedną lub więcej operacji IsTerminating lub operacji IsInitiating bez. Nie ma właściwości SessionMode ustawionej na SessionMode.Required. Atrybutów IsInitiating i IsTerminating można używać tylko w kontekście sesji.|  
|CouldnTCreateChannelForChannelType2|Zażądano typ określonego kanału, ale określone powiązanie nie obsługuje lub jest niepoprawnie skonfigurowany do jego obsługi.|  
|DispatchRuntimeRequiresFormatter0|Określony element DispatchOperation wymaga wartości Formatter, ponieważ DeserializeRequest i SerializeReply nie są zarówno wartość false.|  
|EndMethodsCannotBeDecoratedWithOperationContractAttribute|Metoda End nie można używać z OperationContractAttribute, korzystając z wzorzec projektowy IAsyncResult. Tylko odpowiednia metoda Begin może służyć atrybutem OperationContractAttribute. Ten atrybut ma zastosowanie do pary metod Begin-End.|  
|EndpointListenerRequirementsCannotBeMetBy3|Nie można spełnić wymagania dotyczące elementu ChannelDispatcher ChannelDispatcher dla określonego powiązania, ponieważ kontrakt wymaga obsługi jednego z tych typów w określonym kanale. Ale powiązanie obsługuje tylko tych typów w określonym kanale.|  
|EndpointsMustHaveAValidBinding0|Punkty końcowe muszą mieć prawidłowe powiązanie.|  
|InvalidOrUnrecognizedAction|Komunikat nie można przetworzyć, ponieważ określonej akcji jest nieprawidłowy lub nierozpoznany.|  
|MultipleMebesInParameters|Więcej niż jeden obiekt MessageEncodingBindingElement został znaleziony we właściwości BindingParameters elementu BindingContext. CustomBinding nie może mieć wielu elementów MessageEncodingBindingElements. Usuń wszystkie oprócz jednego z tych elementów.|  
|MultipleStreamUpgradeProvidersInParameters|Więcej niż jeden element IStreamUpgradeProviderElement we właściwości BindingParameters elementu BindingContext. CustomBinding nie może mieć więcej niż jeden IStreamUpgradeProviderElements. Usuń wszystkie oprócz jednego z tych elementów.|  
|NoChannelBuilderAvailable|Powiązanie nie można utworzyć fabryki kanału lub odbiornika kanałów, ponieważ nie zawiera elementu TransportBindingElement. Każde powiązanie musi zawierać co najmniej jeden element powiązania, który pochodzi od elementu TransportBindingElement.|  
|NotAllBindingElementsBuilt|Niektóre elementy tego powiązania nie były używane podczas tworzenia fabryka kanałów i odbiornika kanałów. Elementy powiązania nie są uporządkowane poprawnie. Zalecana kolejność elementów powiązania to: TransactionFlow, ReliableSession, Security, CompositeDuplex, OneWay, StreamSecurity, MessageEncoding, Transport.  Należy pamiętać, że element TransportBindingElement musi być ostatni. Elementy określone powiązanie nie zostały zbudowane.|  
|RuntimeRequiresInvoker0|Operacja wysyłania wymaga elementu wywołującego.|  
|ServiceHasZeroAppEndpoints|Określona usługa nie ma aplikacji (bez infrastruktury) punktów końcowych. Może to być, ponieważ plik konfiguracji nie znaleziono aplikacji lub ponieważ żaden element usługi pasujące do nazwy usługi można odnaleźć w pliku konfiguracji lub punkty końcowe nie zostały zdefiniowane w elemencie usługi.|  
|SFxActionMismatch|Nie można utworzyć typizowany komunikatu z powodu niezgodności akcji. Oczekiwano innego napotkano ale określonej akcji|  
|SFxAnonymousTypeNotSupported|Określona część w określony komunikat nie można wyeksportować przez zdalne wywołanie procedury lub zakodowane, ponieważ jej typ jest anonimowy.|  
|SFxBadMetadataLocationNoAppropriateBaseAddress|Adres URL dostarczony do elementu ServiceMetadataBehavior przy użyciu przez właściwość ExternalMetadataLocation lub atrybut externalMetadataLocation w sekcji serviceMetadata w sekcji konfiguracji był względnym adresem URL i nie ma żadnych adres podstawowy, za pomocą którego można rozpoznać go.|  
|SFxBadMetadataMustBePolicy|Należy podać zasady XmlElement, z określonego obszaru nazw i nazwę. Ten element XmlElement ma określonego obszaru nazw i nazwę.|  
|SFxBodyObjectTypeCannotBeInherited|Określony typ nie może dziedziczyć z dowolnej klasy innej niż obiekt, który ma być używany jako obiekt treści w stylu RPC.|  
|SFxBodyObjectTypeCannotBeInterface|Określony typ implementuje określonego interfejsu, który nie jest obsługiwany dla obiektu treści w stylu RPC.|  
|SFxCallbackBehaviorAttributeOnlyOnDuplex|CallbackBehaviorAttribute może być uruchamiany jako zachowanie w punkcie końcowym za pomocą kontraktu dwukierunkowego. Kontrakt określony nie jest dupleksowy i zawiera żadnych operacji wywołania zwrotnego.|  
|SFxCallbackRequestReplyInOrder1|Nie można odebrać odpowiedzi z tej operacji, do momentu zakończeniem przetwarzania bieżącego komunikatu. Jeśli chcesz zezwolić na przetwarzanie komunikatów poza kolejnością, określ właściwość ConcurrencyMode elementu Reentrant lub wielu na określony.|  
|SfxCallbackTypeCannotBeNull|Aby można było używać kontrakt określony za pomocą obiektu DuplexChannelFactory, kontrakt musi zawierać poprawny kontrakt wywołania zwrotnego. Jeśli Twoja Umowa kontrakt wywołania zwrotnego, należy użyć elementu ChannelFactory zamiast elementu DuplexChannelFactory.|  
|SFxCannotGetMetadataFromLocation|Element MetadataExchangeClient może pobierać metadane tylko z protokołu HTTP i HTTPS elementów MetadataLocations typu. Nie może pobierać metadanych z określonego.|  
|SFxCannotHttpGetMetadataFromAddress|Element MetadataExchangeClient może pobierać metadane tylko z adresów HTTP lub HTTPS podczas korzystania z metody MetadataExchangeClientMode HttpGet. Nie może pobierać metadanych z określonego.|  
|SFxCannotImportAsParameters_Bare|Trwa generowanie kontraktu komunikatu, ponieważ określona operacja nie jest ani RPC, ani opakowanym dokumentem.|  
|SFxCannotImportAsParameters_DifferentWrapperName|Trwa generowanie kontraktu komunikatu, ponieważ nazwa otoki określony komunikat nie jest zgodny z wartością domyślną.|  
|SFxCannotImportAsParameters_DifferentWrapperNs|Trwa generowanie kontraktu komunikatu, ponieważ przestrzeń nazw otoki określony komunikat nie jest zgodny z wartością domyślną.|  
|SFxCannotImportAsParameters_ElementIsNotNillable|Trwa generowanie kontraktu komunikatu, ponieważ nazwa określony element z określonego obszaru nazw nie jest oznaczony jako może być zerowy.|  
|SFxCannotImportAsParameters_HeadersAreUnsupported|Trwa generowanie kontraktu komunikatu, ponieważ określony komunikat zawiera nagłówki.|  
|SFxCannotImportAsParameters_Message|Trwa generowanie kontraktu komunikatu, ponieważ określona operacja występuje komunikat bez jako argument lub zwracany typ.|  
|SFxCannotImportAsParameters_MessageHasProtectionLevel|Trwa generowanie kontraktu komunikatu, ponieważ określony komunikat wymaga ochrony.|  
|SFxCannotImportAsParameters_NamespaceMismatch|Trwa generowanie kontraktu komunikatu, ponieważ przestrzeń nazw część określony komunikat nie jest zgodny z wartością domyślną.|  
|SFxCannotRequireBothSessionAndDatagram3|Kontrakt określony określa SessionMode.NotAllowed i określonego kontrakt określa SessionMode.Required. Zmień jedną z wartości SessionMode lub określ inny adres lub identyfikatorze ListenURI, dla każdego punktu końcowego.|  
|SFxCannotSetExtensionsByIndex|Ta kolekcja nie obsługuje ustawiania rozszerzeń według indeksu. Użyj metody InsertItem lub RemoveItem.|  
|SFxChannelDispatcherDifferentHost0|Element ChannelDispatcher nie jest obecnie dołączony do elementu ServiceHost, który został dostarczony.|  
|SFxChannelDispatcherMultipleHost0|Element ChannelDispatcher nie można dodać do więcej niż jednego elementu ServiceHost.|  
|SFxChannelDispatcherNoHost0|Nie można otworzyć elementu ChannelDispatcher, ponieważ nie jest podłączona do żadnego elementu ServiceHost.|  
|SfxChannelFactoryDisposed|Nie można otworzyć tego elementu ChannelFactory, ponieważ elementu ChannelFactory został już usunięty. Tworzenie elementu ChannelFactory ponownie przed jego użyciem.|  
|SFxChannelFactoryNoBinding|Nie można otworzyć elementu ChannelFactory, ponieważ żadne powiązanie nie został skojarzony z punktem końcowym. Określanie wiązań z Konstruktor lub właściwości punktu końcowego.|  
|SFxChannelTerminated0|Operacja oznaczona jako IsTerminating zostało już wywołane w tym kanale, powodując połączenia kanału zakończyć. Żadne dalsze operacje mogą być wywoływane w tym kanale. Ponownie utwórz kanał, aby kontynuować komunikacji.|  
|SFxCloseTimedOut1|Operacja zamykania ServiceHost zatrzymany po określonym. Może to być, ponieważ klient nie powiodło się zamknięcie kanału sesji w wymaganym czasie. Czas dozwolony dla tej operacji mógł stanowić część większego limitu czasu.|  
|SfxCloseTimedOutWaitingForDispatchToComplete|Zamknij proces upłynął limit czasu podczas oczekiwania na zakończenie wysyłania usługi.|  
|SFxCodeGenIsNotAssignableFrom|Nie można przypisać określony.|  
|SFxConfigChannelConfigurationNotFound|Nie można odnaleźć elementu punktu końcowego o określonej nazwie i umowy w sekcji Konfiguracja modelu ServiceModel klienta.|  
|SFxConflictingGlobalElement|Extensible Markup Language element najwyższego poziomu o określonej nazwie w określonej przestrzeni nazw nie może odwoływać się do określonego typu. Już odwołuje się innego typu. Użyj innej nazwy operacji lub MessageBodyAttribute, aby określić inną nazwę dla komunikatu lub części wiadomości.|  
|SFxContractHasZeroInitiatingOperations|Kontrakt musi zawierać co najmniej jeden IsInitiating = true operacji.|  
|SFxContractHasZeroOperations|Kontrakt musi zawierać co najmniej jedną operację.|  
|SFxContractInheritanceRequiresInterfaces|Klasa usługi o określonym typie definiuje obiekt ServiceContract i dziedziczy go z określonego typu. Dziedziczenie kontraktów należy używać tylko między typami interfejsów. Jeśli klasa jest oznaczona przy użyciu atrybutu ServiceContractAttribute, musi ona jedynym typem w hierarchii przy użyciu atrybutu ServiceContractAttribute.  Przejdź do oddzielny interfejs, który implementuje określony typ ServiceContractAttribute określonego typu.|  
|SFxCreateDuplexChannel1|Kontrakt wywołania zwrotnego kontraktu określonego nie istnieje lub nie definiuje żadnych operacji. Jeśli nie jest to kontrakt dupleksowy, należy użyć elementu ChannelFactory zamiast elementu DuplexChannelFactory.|  
|SFxCreateDuplexChannelNoCallback|Nie można wywołać tego przeciążenia metody CreateChannel dla tego wystąpienia obiektu DuplexChannelFactory. Obiekt DuplexChannelFactory nie został zainicjowany przy użyciu typu InstanceContext. Wywołanie przeciążenia metody CreateChannel, które przyjmuje argument typu InstanceContext.|  
|SFxCreateDuplexChannelNoCallback1|Nie można wywołać tego przeciążenia metody CreateChannel dla tego wystąpienia obiektu DuplexChannelFactory. Obiekt DuplexChannelFactory został zainicjowany typem, a następnie obiektu InstanceContext nie prawidłowy. Wywołanie przeciążenia metody CreateChannel, które przyjmuje argument typu InstanceContext.|  
|SFxCreateDuplexChannelNoCallbackUserObject|Nie można wywołać tego przeciążenia metody CreateChannel dla tego wystąpienia obiektu DuplexChannelFactory. Obiekt InstanceContext przekazany do obiektu DuplexChannelFactory nie zawiera poprawnego obiektu UserObject.|  
|SFxCreateNonDuplexChannel1|Obiekt ChannelFactory nie obsługuje kontraktu określony. Obiekt ChannelFactory definiuje kontrakt wywołania zwrotnego z co najmniej jednej operacji. Use DuplexChannelFactory instead of ChannelFactory.|  
|SFxCustomBindingNeedsTransport1|W elemencie CustomBinding w punktu końcowego usługi za pomocą określonego kontraktu nie zawiera elementu TransportBindingElement. Każde powiązanie musi zawierać co najmniej jeden element powiązania, który pochodzi od elementu TransportBindingElement.|  
|SFxCustomBindingWithoutTransport|Nie można obliczyć schematu dla tego powiązania niestandardowego, ponieważ nie zawiera elementu TransportBindingElement. Każde powiązanie musi zawierać co najmniej jeden element powiązania, który pochodzi od elementu TransportBindingElement.|  
|SFxDataContractSerializerDoesNotSupportBareArray|Obiekt DataContractSerializer nie obsługuje kolekcji określonej w określonym elemencie.|  
|SFxDictionaryIsEmpty|Nie można wykonać operacji, ponieważ słownika jest pusta.|  
|SFxDocEncodedNotSupported|Błąd odzwierciedlające określony. Zakodowane w formacie dokumentu nie jest obsługiwane. Zmień "Use" literał lub "Styl" RPC.|  
|SFxDuplicateInitiatingActionAtSameVia|Ta usługa ma wiele punktów końcowych nasłuchujących w danym. Punktów końcowych udostępnić tę samą akcję inicjującą określony. Czy można usunąć wiadomości za pomocą tej akcji, ponieważ dyspozytor nie będzie w stanie określić właściwego punktu końcowego obsługi wiadomości.|  
|SFXEndpointBehaviorUsedOnWrongSide|Nie można użyć interfejsu IEndpointBehavior określonego na serwerze. To zachowanie można dotyczy tylko klientów.|  
|SFxEndpointNoMatchingScheme|Nie można odnaleźć adres podstawowy, który odpowiada określony schemat dla punktu końcowego określonego powiązania. Podano schematów zarejestrowanych adres podstawowy.|  
|SFxErrorCreatingMtomReader|Wystąpił błąd podczas tworzenia modułu odczytującego komunikatu mechanizmu optymalizacji transmisji wiadomości.|  
|SFxErrorDeserializingFault|Serwer zwrócił błąd nieprawidłowego prostego obiektu dostępu protokołu. Aby uzyskać więcej informacji, zobacz element InnerException.|  
|SFxErrorDeserializingHeader|Wystąpił błąd podczas deserializacji jednego z nagłówków komunikatu określony. Aby uzyskać więcej informacji, zobacz element InnerException.|  
|SFxErrorReflectingOnMethod3|Wystąpił błąd podczas ładowania określonego atrybutu w określonej metodzie w określonym typie.  Aby uzyskać więcej informacji, zobacz element InnerException.|  
|SFxErrorReflectingOnParameter4|Wystąpił błąd podczas ładowania określonego atrybutu na określony parametr określonej metodzie w określonym typie. Aby uzyskać więcej informacji, zobacz element InnerException.|  
|SFxErrorReflectingOnType2|Wystąpił błąd podczas ładowania określonego atrybutu dla określonego typu.  Aby uzyskać więcej informacji, zobacz element InnerException.|  
|SFxErrorSerializingBody|Wystąpił błąd podczas serializacji treści określony komunikat. Aby uzyskać więcej informacji, zobacz element InnerException.|  
|SFxErrorSerializingHeader|Wystąpił błąd podczas serializacji jednego z nagłówków komunikatu określony. Aby uzyskać więcej informacji, zobacz element InnerException.|  
|SFxExpectedIMethodCallMessage|Błąd wewnętrzny. Wiadomość musi być prawidłową IMethodCallMessage.|  
|SFxExportMustHaveType|Nie można wyeksportować określona część w określonej operacji, ponieważ nie ma prawidłowego typu CLR.|  
|SFxHeaderNotUnderstood|Wiadomość nie została przetworzona. Określony nagłówek z określonego obszaru nazw, nie został zrozumiany przez odbiorcę tego komunikatu. Ten błąd zazwyczaj oznacza, że nadawca komunikatu ma włączone protokół komunikacyjny, którego odbiorca nie może przetworzyć. Upewnij się, że konfiguracja powiązań klienta jest spójna z powiązaniem usługi.|  
|SFxHeadersAreNotSupportedInEncoded|Określony komunikat nie może mieć nagłówki, które ma być używany w stylu zakodowane wywołanie procedury zdalnej.|  
|SFxInconsistentWsdlOperationStyleInMessageParts|Wszystkie części komunikatu w określonej operacji musi zawierać typ lub element.|  
|SFxInconsistentWsdlOperationStyleInOperationMessages|Określony styl wywnioskować na podstawie wiadomości w określonej operacji jest niezgodna z określoną oczekiwanemu stylowi określony za pomocą powiązania.|  
|SFxInvalidCallbackIAsyncResult|IAsyncResult nie zostanie podany lub jest nieprawidłowego typu.|  
|SFxInvalidMessageBody|Obiekt OperationFormatter napotkał nieprawidłową treść. Oczekiwano typu węzła "Element" o określonej nazwie i przestrzeni nazw. Znaleziono typu określonego węzła o określonej nazwie i przestrzeni nazw.|  
|SFxInvalidMessageBodyEmptyMessage|Obiekt OperationFormatter nie można zdeserializować żadnej informacji z komunikatu, ponieważ komunikat jest pusty.|  
|SFxInvalidMessageBodyErrorDeserializingParameter|Wystąpił błąd podczas próby deserializacji określony parametr. Aby uzyskać więcej informacji, zobacz element InnerException.|  
|SFxInvalidMessageBodyErrorSerializingParameter|Wystąpił błąd podczas próby serializowania określony parametr. Określono komunikat InnerException.  Aby uzyskać więcej informacji, zobacz element InnerException.|  
|SFxInvalidMessageBodyUnexpectedNode|Napotkano określonego nieoczekiwany węzeł z określonego obszaru nazw podczas deserializacji parametrów.|  
|SFxInvalidMessageContractSignature|Określona operacja ma parametr lub zwracany typ, który jest oznaczony atrybutem MessageContractAttribute. Reprezentuje komunikat żądania za pomocą kontraktu komunikatu, operacja musi mieć jeden parametr, który jest oznaczony atrybutem MessageContractAttribute. Reprezentuje komunikat odpowiedzi za pomocą kontraktu komunikatu, wartość zwrotna operacji musi być typu, który jest oznaczony atrybutem MessageContractAttribute. Operacja nie może mieć żadnych "out" lub "ref" parametrów.|  
|SFxInvalidReplyAction|Wychodzący komunikat odpowiedzi dla operacji ma określoną akcję, ale kontrakt dla danej operacji określa ReplyAction innego. Z akcją określoną w komunikacie musi odpowiadać parametrowi ReplyAction w kontrakcie lub kontrakt operacji musi określać parametr ReplyAction = "*".|  
|SFxInvalidRequestAction|Wychodzący komunikat żądania dla operacji ma określoną akcję, ale kontrakt dla danej operacji określa RequestAction innego. Z akcją określoną w komunikacie musi odpowiadać RequestAction w kontrakcie lub kontrakt operacji musi określać RequestAction = "*".|  
|SFxInvalidStaticOverloadCalledForDuplexChannelFactory1|Statyczna metoda CreateChannel nie można użyć za pomocą określonego kontraktu, ponieważ kontrakt ten definiuje kontrakt wywołania zwrotnego. Użyj jednej z statyczne przeciążenia metody CreateChannel w kanale DuplexChannelFactory\<TChannel >.|  
|SFxInvalidStreamInRequest|Żądania w określonej operacji była strumieniem operacja musi mieć pojedynczy parametr typu Stream.|  
|SFxInvalidStreamInResponse|Odpowiedź w określonej operacji była strumieniem operacja musi mieć pojedynczy parametr out ani zwracają wartość, której typem jest Stream.|  
|SFxInvalidStreamInTypedMessage|Aby użyć strumieni z kontraktu komunikatu, model programowania, określony typ musi mieć jeden składnik Element MessageBody, którego typem jest Stream.|  
|SFxInvalidUseOfPrimitiveOperationFormatter|Metodzie PrimitiveOperationFormatter przekazano parametr lub zwracany typ, który nie obsługuje.|  
|SFxMessageContractBaseTypeNotValid|Określony typ definiuje kontrakt MessageContract i pochodzi z określonego typu, który nie definiuje kontrakt MessageContract. Wszystkie obiekty w hierarchii dziedziczenia określonego musi definiować kontrakt MessageContract.|  
|SFxMethodNotSupported1|Określona metoda nie jest obsługiwana dla tego obiektu. Może to nastąpić, jeśli metoda nie jest oznaczona atrybutem OperationContractAttribute lub jeśli typ interfejsu nie jest oznaczony atrybutem ServiceContractAttribute.|  
|SFxMethodNotSupportedByType2|Określony typ implementacji elementu ServiceHost nie implementuje kontraktu określonej usługi.|  
|SFxMethodNotSupportedOnCallback1|Metodą określonego wywołania zwrotnego nie jest obsługiwane. Może to nastąpić, jeśli metoda nie jest oznaczona atrybutem OperationContractAttribute lub jeśli typ interfejsu nie jest celem ServiceContractAttribute CallbackContract.|  
|SFxMismatchedOperationParent|Element DispatchOperation lub ClientOperation mogą być dodawane tylko do elementu nadrzędnego DispatchRuntime lub ClientRuntime odpowiednio.|  
|SFxNameCannotBeEmpty|Właściwość Name nie może być ciągiem pustym.|  
|SfxNoTypeSpecifiedForParameter|Typ CLR nie został określony dla parametru, co uniemożliwia uniemożliwiło wygenerowanie operacji.|  
|SFxOperationBehaviorAttributeOnlyOnServiceClass|Gdy tylko można przejść na klasę usługi. Nie można umieścić w interfejsie ServiceContract. Określonej metody dla określonego typu narusza tę zasadę.|  
|SFxOperationContractOnNonServiceContract|Określona metoda jest oznaczona atrybutem OperationContractAttribute, ale otaczającej określony typ nie jest oznaczony atrybutem ServiceContractAttribute. Atrybut OperationContractAttribute należy używać tylko w metodach typów ServiceContractAttribute lub w ich typach CallbackContract.|  
|SFxParameterCountMismatch|Wystąpiła niezgodność między liczbą przekazanych argumentów a liczbą oczekiwanych argumentów. W szczególności określony argument ma określoną liczbę elementów, podczas gdy oczekiwano argumentu ma określoną liczbę elementów.|  
|SFxPartNameMustBeUniqueInRpc|Nazwy części określony komunikat nie jest unikatowa w komunikacie wywołanie procedury zdalnej.|  
|SFxReplyActionMismatch3|Odebrano komunikat odpowiedzi dla określonej operacji za pomocą określonej akcji. Kod klienta wymaga jednak wykonania określonej akcji.|  
|SFxRequestReplyNone|Odebrano komunikat z nagłówkiem WS-Addressing ReplyTo lub FaultTo celem "None" adres. Te wartości są nieprawidłowe dla operacji żądanie odpowiedź. Użyj operacji jednokierunkowych lub Włącz opcję ManualAddressing, jeśli wymagana jest obsługa ReplyTo lub FaultTo kierowanym wartości "None".|  
|SFxRequestTimedOut1|Żądanie nie otrzymała odpowiedzi w określonym czasie skonfigurowany. Czas dozwolone mógł stanowić część większego limitu czasu. Może to być nieukończone przetwarzanie operacji lub usługa nie może wysłać komunikatu odpowiedzi.|  
|SFxRequestTimedOut2|Operację żądania wysyłane do określonej lokalizacji nie otrzymała odpowiedzi w określonym czasie skonfigurowany. Czas dozwolone mógł stanowić część większego limitu czasu. Może to być nieukończone przetwarzanie operacji lub usługa nie może wysłać komunikatu odpowiedzi.|  
|SFxSchemaDoesNotContainType|Schemat z określonego docelowego obszaru nazw nie zawiera typu o określonej nazwie.|  
|SfxServiceContractAttributeNotFound|Kontrakt określony typ nie jest atrybut ServiceContractAttribute. Aby zdefiniować prawidłowego kontraktu, określony typ musi mieć atrybut ServiceContractAttribute. Typ może być interfejsu kontraktu lub klasy usługi.|  
|SFxServiceContractGeneratorConfigRequired|Aby wygenerować informacje o konfiguracji przy użyciu metody GenerateServiceEndpoint, wystąpienia elementu ServiceContractGenerator musi zostać zainicjowany przy użyciu prawidłowego obiektu konfiguracji.|  
|SFxServiceHostBaseCannotAddEndpointAfterOpen|Nie można dodać punktów końcowych, po elementu ServiceHost znajduje się w jednej z następujących stanów:<br /><br /> -Otwarte<br />-Komunikacji niezawodnej<br />-Zakończone<br />— Zamknięte|  
|SFxServiceHostBaseCannotAddEndpointWithoutDescription|Nie można dodać punktów końcowych, zanim właściwość Description jest zainicjowany.|  
|SFxServiceMetadataBehaviorNoHttpBaseAddress|Właściwość elementu ServiceMetadataBehavior jest ustawiona na wartość PRAWDA, a właściwość HttpGetUrl HttpGetEnabled jest adres względny, ale brak adresu podstawowego HTTP. Podaj podstawowy adres HTTP albo ustawić HttpGetUrl adresu bezwzględnego.|  
|SFxServiceMetadataBehaviorNoHttpsBaseAddress|Właściwość elementu ServiceMetadataBehavior jest ustawiona na wartość PRAWDA, a właściwość HttpsGetUrl HttpsGetEnabled jest adres względny, ale nie ma adresu HTTPS. Należy dostarczyć bazowy adres HTTPS, lub ustawić HttpsGetUrl adresu bezwzględnego.|  
|SFxServiceMetadataBehaviorUrlMustBeHttpOrRelative|Adres Url zachowanie musi być względna jednolity identyfikator zasobów lub bezwzględny identyfikator z określonym schematem. Określony adres Url jest bezwzględny identyfikator z określonym schematem.|  
|SFxStreamRequestMessageClosed|Komunikat zawierający dany strumień został zamknięty. Nie można uzyskać dostępu do strumieni żądania po powrocie z operacji usługi.|  
|SFxStreamResponseMessageClosed|Komunikat zawierający dany strumień został zamknięty.|  
|SFxTerminateRequestProcessingException|Zamknij rozszerzenia w potoku operacji przetwarzania tej wiadomości.|  
|SFxTerminatingOperationAlreadyCalled1|Ten kanał nie może wysłać więcej wiadomości, ponieważ operacji IsTerminating została wywołana.|  
|SFxThrottleLimitMustBeGreaterThanZero0|Ograniczenie przepustowości musi być większa niż zero. Aby wyłączyć ograniczenie przepustowości, ustaw wartość Int32.MaxValue.|  
|SFxTypedOrUntypedMessageCannotBeMixedWithVoidInRpc|Używając stylu RPC-encoded typy kontraktu komunikatu lub typ System.ServiceModel.Channels.Message nie używać, jeśli operacja nie ma parametrów lub ma pustą wartość zwracaną. Dodaj pusty typ kontraktu komunikatu jako parametr lub zwracany typ do określonej operacji.|  
|SFxUserCodeThrewException|Operacja określony użytkownik zgłosił wyjątek, który jest nieobsługiwany w kodzie użytkownika. W przypadku cyklicznego problemu może to oznaczać błąd podczas stosowania określonej metody.|  
|SfxUseTypedMessageForCustomAttributes|Nie można zamapować określony parametr do parametru operacji, ponieważ wymaga dodatkowych atrybutów.|  
|SFxVersionMismatchInOperationContextAndMessage2|Nie można dodać nagłówków wychodzących do komunikatu, ponieważ element MessageVersion w elemencie perationContext.Current nie odpowiada wersji nagłówka przetwarzanego komunikatu|  
|SFxWellKnownNonSingleton0|Aby użyć jednego z konstruktorów ServiceHost, które wystąpienie usługi, tryb InstanceContextMode usługi musi być równa InstanceContextMode.Single. Można to skonfigurować za pomocą ServiceBehaviorAttribute. W przeciwnym razie użyj elementu ServiceHost konstruktorów, które przyjmują argument typu.|  
|SFxWrapperTypeHasMultipleNamespaces|Typ otoki dla określonego komunikatu nie może być przekazywany jako typ kontraktu danych, ponieważ ma on wiele przestrzeni nazw. Za pomocą elementu XmlSerializer.|  
|UriMustBeAbsolute|Identyfikator URI musi być bezwzględna.|
