---
title: Zgodność funkcji zaufania częściowego
ms.date: 03/30/2017
ms.assetid: a36a540b-1606-4e63-88e0-b7c59e0e6ab7
ms.openlocfilehash: f8c63079161e6be16e2d36f721aeb98937f72097
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496789"
---
# <a name="partial-trust-feature-compatibility"></a>Zgodność funkcji zaufania częściowego
Windows Communication Foundation (WCF) obsługuje ograniczone funkcji podczas uruchamiania w środowisku częściowo zaufany. Funkcje obsługiwane w częściowej relacji zaufania są została zaprojektowana dla określonych scenariuszy zgodnie z opisem w [obsługiwane scenariusze wdrażania](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md) tematu.  
  
## <a name="minimum-permission-requirements"></a>Wymagania dotyczące minimalnych uprawnień  
 Usługi WCF obsługuje podzbiór funkcji aplikacji uruchomionych w jednej z następujących zestawów standardowe uprawnienie o nazwie:  
  
-   Średnia uprawnień zaufania  
  
-   Uprawnienia strefy Internet  
  
 Podjęto próbę użycia usługi WCF w częściowo zaufane aplikacje z bardziej restrykcyjnymi uprawnieniami może skutkować wyjątki zabezpieczeń w czasie wykonywania.  
  
## <a name="contracts"></a>Kontrakty  
 Kontrakty obowiązują następujące ograniczenia, gdy w częściowej relacji zaufania działa:  
  
-   Klasy usługi, który implementuje `[ServiceContract]` interfejs musi być `public` i mieć `public` konstruktora. Jeśli definiuje `[OperationContract]` metod, muszą być `public`. Jeśli zamiast tego implementuje `[ServiceContract]` interfejs, może być jawne implementacje tych metod lub `private`, pod warunkiem że `[ServiceContract]` interfejs jest `public`.  
  
-   Korzystając z `[ServiceKnownType]` atrybut, musi być określona metoda `public`.  
  
-   `[MessageContract]` klasy i ich elementy Członkowskie mogą być `public`. Jeśli `[MessageContract]` klasa jest zdefiniowana w zestawie aplikacji może być `internal` i mieć `internal` elementów członkowskich.  
  
## <a name="system-provided-bindings"></a>Powiązania dostarczane przez system  
 <xref:System.ServiceModel.BasicHttpBinding> i <xref:System.ServiceModel.WebHttpBinding> są w pełni obsługiwane w środowisku częściowej relacji zaufania. <xref:System.ServiceModel.WSHttpBinding> Jest obsługiwana w przypadku tylko tryb zabezpieczeń Transport.  
  
 Powiązań, które używają transportu innego niż HTTP, takie jak <xref:System.ServiceModel.NetTcpBinding>, <xref:System.ServiceModel.NetNamedPipeBinding>, lub <xref:System.ServiceModel.NetMsmqBinding>, nie są obsługiwane podczas uruchamiania w środowisku częściowej relacji zaufania.  
  
## <a name="custom-bindings"></a>Powiązania niestandardowe  
 Powiązania niestandardowe mogą być tworzone i używane w środowisku częściowej relacji zaufania, ale musi wykonać ograniczenia określone w tej sekcji.  
  
### <a name="transports"></a>Transporty  
 Jedyną dozwoloną są elementy powiązania transportu <xref:System.ServiceModel.Channels.HttpTransportBindingElement> i <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.  
  
### <a name="encoders"></a>Kodery  
 Następujące kodery są dozwolone:  
  
-   Koder tekstu (<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>).  
  
-   Kodera binarnego (<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>).  
  
-   Koder komunikatów sieci Web (<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>).  
  
 Kodery mechanizmu optymalizacji transmisji wiadomości (MTOM) nie są obsługiwane.  
  
### <a name="security"></a>Zabezpieczenia  
 Częściowo zaufane aplikacje mogą używać funkcji zabezpieczeń na poziomie transportu WCF na do zabezpieczania komunikacji. Zabezpieczenia na poziomie komunikatu nie jest obsługiwana. Konfigurowanie powiązania w celu użycia zabezpieczenia na poziomie komunikatu powoduje wyjątek w czasie wykonywania.  
  
### <a name="unsupported-bindings"></a>Nieobsługiwany powiązania  
 Powiązań używających niezawodna obsługa komunikatów, transakcje lub zabezpieczenia na poziomie komunikatu nie są obsługiwane.  
  
## <a name="serialization"></a>Serializacja  
 Zarówno <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Xml.Serialization.XmlSerializer> są obsługiwane w środowisku częściowej relacji zaufania. Jednak użycie <xref:System.Runtime.Serialization.DataContractSerializer> podlega następujące warunki:  
  
-   Wszystkie serializacji `[DataContract]` typy muszą być `public`.  
  
-   Wszystkie serializacji `[DataMember]` pola lub właściwości w `[DataContract]` typu musi być publiczny i odczytu/zapisu. Serializacja i deserializacja [tylko do odczytu](http://go.microsoft.com/fwlink/?LinkID=98854) pola nie jest obsługiwane podczas uruchamiania usługi WCF w częściowo zaufanych aplikacji.  
  
-   `[Serializable]` /ISerializable model programowania nie jest obsługiwana w środowisku częściowej relacji zaufania.  
  
-   Znane typy musi określona w konfiguracji poziomie komputera (machine.config) lub kodu. W aplikacjach na poziomie konfiguracji ze względów bezpieczeństwa nie można określić znanych typów.  
  
-   Typy, które implementują <xref:System.Runtime.Serialization.IObjectReference> Zgłoś wyjątek w środowisku częściowo zaufany.  
  
 W sekcji serializacji w [częściowego zaufania najlepsze rozwiązania w zakresie](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) Aby uzyskać więcej informacji o zabezpieczeniach, używając <xref:System.Runtime.Serialization.DataContractSerializer> bezpiecznie w aplikacji częściowo zaufany.  
  
### <a name="collection-types"></a>Typy kolekcji  
 Niektóre typy kolekcji implementować jednocześnie <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.Collections.IEnumerable>. Przykłady typów, które implementują <xref:System.Collections.Generic.ICollection%601>. Można zaimplementować takich typów `public` implementacja `GetEnumerator()`i jawną implementację elementu `GetEnumerator()`. W takim przypadku <xref:System.Runtime.Serialization.DataContractSerializer> wywołuje `public` implementacja `GetEnumerator()`, a nie jawną implementację elementu `GetEnumerator()`. Jeśli żadna z `GetEnumerator()` są implementacje `public` i wszystkie jawnej implementacji, następnie <xref:System.Runtime.Serialization.DataContractSerializer> wywołuje `IEnumerable.GetEnumerator()`.  
  
 Dla typów kolekcji uruchomionej usługi WCF w środowisku częściowej relacji zaufania, jeśli żadna z `GetEnumerator()` są implementacje `public`, lub żaden z nich nie jest jawne implementacje interfejsu, a następnie jest zgłaszany wyjątek zabezpieczeń.  
  
### <a name="netdatacontractserializer"></a>NetDataContractSerializer  
 Wiele typów kolekcji .NET Framework, takich jak <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ArrayList>, <xref:System.Collections.Generic.Dictionary%602> i <xref:System.Collections.Hashtable> nie są obsługiwane przez <xref:System.Runtime.Serialization.NetDataContractSerializer> w częściowej relacji zaufania. Te typy mają `[Serializable]` ustawiony atrybut i jak wspomniano wcześniej, w sekcji serializacji, ten atrybut nie jest obsługiwany w częściowej relacji zaufania. <xref:System.Runtime.Serialization.DataContractSerializer> Traktuje kolekcje w specjalny sposób i w związku z tym jest możliwość obejścia tego ograniczenia, ale <xref:System.Runtime.Serialization.NetDataContractSerializer> ma taki mechanizm obejść to ograniczenie.  
  
 <xref:System.DateTimeOffset> Typ nie jest obsługiwany przez <xref:System.Runtime.Serialization.NetDataContractSerializer> w częściowej relacji zaufania.  
  
 Surogat nie można używać z <xref:System.Runtime.Serialization.NetDataContractSerializer> (przy użyciu <xref:System.Runtime.Serialization.SurrogateSelector> mechanizmu) podczas uruchamiania w częściowej relacji zaufania. Należy pamiętać, że to ograniczenie dotyczy przy użyciu Surogat, aby nie szeregując go.  
  
## <a name="enabling-common-behaviors-to-run"></a>Włączanie zachowań wspólnych do uruchomienia  
 Zachowania usługi lub punkt końcowy nie jest oznaczony atrybutem <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu (APTCA), które są dodawane do [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) sekcji pliku konfiguracji nie są uruchamiane, gdy aplikacja działa w częściowej relacji zaufania środowisko i żaden wyjątek jest zgłaszany w takiej sytuacji. Aby wymusić uruchamianie zachowań wspólnych, wykonaj jedną z następujących opcji:  
  
-   Oznacz z typowych zachowanie w przypadku <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu, dzięki czemu można uruchamiać, gdy wdrożony jako aplikacja częściowej relacji zaufania. Należy pamiętać, że wpis rejestru można ustawić na komputerze, aby zapobiec oznaczone atrybutem APTCA zestawy uruchamianie. .  
  
-   Upewnij się, że jeśli aplikacja jest wdrażana jako aplikacja całkowicie zaufane, że użytkownicy nie mogą modyfikować ustawienia zabezpieczeń dostępu kodu do uruchomienia aplikacji w środowisku częściowej relacji zaufania. Mogą one to robić, zachowanie nie jest uruchamiane, a nie wyjątek. Aby to zapewnić, zobacz **levelfinal** opcję przy użyciu [Caspol.exe (narzędzie zasad zabezpieczenia dostępu kodu)](../../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).  
  
 Na przykład wspólnego zachowania, zobacz [porady: blokowanie dół punktów końcowych w przedsiębiorstwie](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).  
  
## <a name="configuration"></a>Konfiguracja  
 Z jednym wyjątkiem częściowo zaufanego kodu można ładować tylko sekcji konfiguracji usługi WCF w lokalnej `app.config` pliku. Aby załadować sekcji konfiguracji WCF odwołujące się do usługi WCF w sekcji w pliku machine.config lub głównym pliku web.config wymaga ConfigurationPermission(Unrestricted). Bez tego uprawnienia odwołań do WCF sekcji konfiguracyjnych (zachowania, powiązania) poza skutkuje pliku lokalnej konfiguracji wystąpił wyjątek podczas ładowania konfiguracji.  
  
 Jedynym wyjątkiem jest znany typ konfiguracji do serializacji, zgodnie z opisem w sekcji serializacji tego tematu.  
  
> [!IMPORTANT]
>  Rozszerzenia konfiguracji są obsługiwane tylko w przypadku, gdy uruchomiona w ramach pełnego zaufania.  
  
## <a name="diagnostics"></a>Diagnostyka  
  
### <a name="event-logging"></a>Rejestrowanie zdarzeń  
 Rejestrowanie zdarzeń ograniczone jest obsługiwane w częściowej relacji zaufania. Tylko usługi aktywacji usterek i błędów rejestrowania śledzenia/wiadomości są rejestrowane w dzienniku zdarzeń. Maksymalna liczba zdarzeń, które mogą być rejestrowane przez proces wynosi 5, aby uniknąć zapisywania nadmiernej liczby komunikatów w dzienniku zdarzeń.  
  
### <a name="message-logging"></a>Rejestrowanie komunikatów  
 Rejestrowanie komunikatów nie działa, gdy WCF jest uruchamiana w środowisku częściowej relacji zaufania. Jeśli włączona w częściowej relacji zaufania, nie wystąpi niepowodzenie usługi aktywacji, ale nie jest rejestrowany.  
  
### <a name="tracing"></a>Śledzenie  
 Funkcja śledzenia z ograniczeniami jest dostępna podczas uruchamiania w środowisku częściowej relacji zaufania. W <`listeners`> są tylko typy, które można dodać elementu w pliku konfiguracji, <xref:System.Diagnostics.TextWriterTraceListener> i nowych <xref:System.Diagnostics.EventSchemaTraceListener>. Użyj standardowego <xref:System.Diagnostics.XmlWriterTraceListener> może spowodować dzienniki niekompletne lub niepoprawne.  
  
 Źródła śledzenia obsługiwane są:  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.Runtime.Serialization>  
  
-   <xref:System.IdentityModel.Claims>, <xref:System.IdentityModel.Policy>, <xref:System.IdentityModel.Selectors>, i <xref:System.IdentityModel.Tokens>.  
  
 Następujące źródła śledzenia nie są obsługiwane:  
  
-   CardSpace  
  
-   <xref:System.IO.Log>  

-   [System.ServiceModel.Internal.TransactionBridge](https://msdn.microsoft.com/library/system.servicemodel.internal.transactionbridge.aspx)]
  
 Następujące elementy członkowskie z <xref:System.Diagnostics.TraceOptions> wyliczenie nie należy określać:  
  
-   <xref:System.Diagnostics.TraceOptions.Callstack?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceOptions.ProcessId?displayProperty=nameWithType>  
  
 Korzystając z śledzenie w środowisku częściowej relacji zaufania, upewnij się, że aplikacja ma wystarczające uprawnienia do przechowywania danych wyjściowych obiektu nasłuchującego śledzenia. Na przykład w przypadku korzystania z <xref:System.Diagnostics.TextWriterTraceListener> do zapisywania danych wyjściowych śledzenia w pliku tekstowym, sprawdź, czy aplikacja ma niezbędne FileIOPermission, trzeba zapisać do pliku śledzenia.  
  
> [!NOTE]
>  Aby zapobiec przepełnieniu pliki śledzenia z błędami zduplikowanych, WCF wyłącza śledzenie zasobów lub akcji po pierwszym błędzie zabezpieczeń. Istnieje jeden wyjątek śledzenia dla każdego dostęp do zasobów nie powiodło się, próby dostępu do zasobu lub wykonanie akcji po raz pierwszy.  
  
## <a name="wcf-service-host"></a>Host usługi WCF  
 Host usługi WCF nie obsługuje częściowej relacji zaufania. Jeśli chcesz użyć usługi WCF w częściowej relacji zaufania, nie należy używać szablonu projektu biblioteki usługi WCF w programie Visual Studio do tworzenia usługi. Zamiast tego należy utworzyć nową witrynę sieci Web w programie Visual Studio, wybierając szablon witryny sieci Web usługi WCF, który może obsługiwać usługi na serwerze sieci Web, na którym jest obsługiwany WCF częściowej relacji zaufania.  
  
## <a name="other-limitations"></a>Inne ograniczenia  
 Usługi WCF jest zazwyczaj ograniczone do zagadnienia dotyczące zabezpieczeń nakłada na nią hostingu aplikacji. Na przykład, jeśli WCF jest hostowana w aplikacji przeglądarki XAML (XBAP), jego podlega XBAP ograniczenia, zgodnie z opisem w [zabezpieczenia systemu Windows Presentation Foundation częściowego zaufania](http://go.microsoft.com/fwlink/?LinkId=89138).  
  
 Podczas uruchamiania indigo2 w środowisku częściowej relacji zaufania, nie są włączone następujące dodatkowe funkcje:  
  
-   Instrumentacja zarządzania Windows (WMI)  
  
-   Rejestrowanie zdarzeń jest tylko częściowo włączona (zobacz Omówienie w **diagnostyki** sekcji).  
  
-   Liczniki wydajności  
  
 Użycie funkcji WCF, które nie są obsługiwane w środowisku częściowej relacji zaufania może spowodować wystąpienie wyjątków w czasie wykonywania.  
  
## <a name="unlisted-features"></a>Funkcje nieznajdujące się na liście  
 Najlepszym sposobem, aby dowiedzieć się, że informacji lub akcja jest niedostępna, jeśli działające w środowisku częściowej relacji zaufania jest próba dostępu do zasobu lub akcję wewnątrz `try` bloku, a następnie `catch` awarii. Aby zapobiec przepełnieniu pliki śledzenia z błędami zduplikowanych, WCF wyłącza śledzenie zasobów lub akcji po pierwszym błędzie zabezpieczeń. Istnieje jeden wyjątek śledzenia dla każdego dostęp do zasobów nie powiodło się, próby dostępu do zasobu lub wykonanie akcji po raz pierwszy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>  
 [Obsługiwane scenariusze wdrażania](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)  
 [Najlepsze rozwiązania dotyczące częściowego zaufania](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)
