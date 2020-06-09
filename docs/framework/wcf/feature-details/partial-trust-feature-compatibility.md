---
title: Zgodność funkcji zaufania częściowego
ms.date: 03/30/2017
ms.assetid: a36a540b-1606-4e63-88e0-b7c59e0e6ab7
ms.openlocfilehash: 85e34e365d125fe4f00756549ba5bda4311b78f8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579166"
---
# <a name="partial-trust-feature-compatibility"></a>Zgodność funkcji zaufania częściowego
Windows Communication Foundation (WCF) obsługuje ograniczoną część funkcjonalności w przypadku uruchamiania w środowisku częściowo zaufanym. Funkcje obsługiwane w częściowej relacji zaufania są przeznaczone dla określonego zestawu scenariuszy, zgodnie z opisem w temacie [obsługiwane scenariusze wdrażania](supported-deployment-scenarios.md) .  
  
## <a name="minimum-permission-requirements"></a>Minimalne wymagania dotyczące uprawnień  
 Usługa WCF obsługuje podzestaw funkcji w aplikacjach uruchamianych w ramach jednego z następujących standardowych zestawów uprawnień:  
  
- Uprawnienia średniego zaufania  
  
- Uprawnienia strefy internetowej  
  
 Próba użycia programu WCF w aplikacjach częściowo zaufanych z bardziej restrykcyjnymi uprawnieniami może skutkować wyjątkami zabezpieczeń w czasie wykonywania.  
  
## <a name="contracts"></a>Kontrakty  
 Umowy podlegają następującym ograniczeniom w przypadku uruchamiania w ramach częściowej relacji zaufania:  
  
- Klasa usługi implementująca `[ServiceContract]` interfejs musi mieć `public` `public` konstruktora. Jeśli definiuje `[OperationContract]` metody, muszą one być `public` . Jeśli zamiast tego implementuje `[ServiceContract]` interfejs, te implementacje metod mogą być jawne lub `private` , pod warunkiem, że `[ServiceContract]` interfejs to `public` .  
  
- W przypadku korzystania z `[ServiceKnownType]` atrybutu należy określić metodę `public` .  
  
- `[MessageContract]`klasy i ich członkowie mogą być `public` . Jeśli `[MessageContract]` Klasa jest zdefiniowana w zestawie aplikacji, może być `internal` i mieć `internal` członków.  
  
## <a name="system-provided-bindings"></a>Wiązania dostarczane przez system  
 <xref:System.ServiceModel.BasicHttpBinding>I <xref:System.ServiceModel.WebHttpBinding> są w pełni obsługiwane w środowisku częściowej relacji zaufania. <xref:System.ServiceModel.WSHttpBinding>Jest obsługiwana tylko w trybie zabezpieczenia transportu.  
  
 Powiązania wykorzystujące transporty inne niż HTTP, takie jak <xref:System.ServiceModel.NetTcpBinding> ,, <xref:System.ServiceModel.NetNamedPipeBinding> lub <xref:System.ServiceModel.NetMsmqBinding> , nie są obsługiwane w przypadku uruchamiania w środowisku częściowej relacji zaufania.  
  
## <a name="custom-bindings"></a>Powiązania niestandardowe  
 Niestandardowe powiązania mogą być tworzone i używane w środowisku częściowej relacji zaufania, ale muszą być zgodne z ograniczeniami określonymi w tej sekcji.  
  
### <a name="transports"></a>Transporty  
 Jedyne dozwolone elementy powiązania transportu to <xref:System.ServiceModel.Channels.HttpTransportBindingElement> i <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> .  
  
### <a name="encoders"></a>Koderów  
 Następujące kodery są dozwolone:  
  
- Koder tekstowy ( <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> ).  
  
- Koder binarny ( <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> ).  
  
- Koder komunikatów sieci Web ( <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> ).  
  
 Kodery mechanizmu optymalizacji transmisji wiadomości (MTOM) nie są obsługiwane.  
  
### <a name="security"></a>Zabezpieczenia  
 Częściowo zaufane aplikacje mogą korzystać z funkcji zabezpieczeń na poziomie transportu WCF w celu zabezpieczania komunikacji. Zabezpieczenia na poziomie wiadomości nie są obsługiwane. Skonfigurowanie powiązania do korzystania z wyników zabezpieczeń na poziomie komunikatu w czasie wykonywania.  
  
### <a name="unsupported-bindings"></a>Nieobsługiwane powiązania  
 Powiązania korzystające z niezawodnej obsługi komunikatów, transakcji lub zabezpieczeń na poziomie wiadomości nie są obsługiwane.  
  
## <a name="serialization"></a>Serializacja  
 Zarówno, <xref:System.Runtime.Serialization.DataContractSerializer> jak i <xref:System.Xml.Serialization.XmlSerializer> są obsługiwane w środowisku częściowej relacji zaufania. Jednak użycie programu <xref:System.Runtime.Serialization.DataContractSerializer> podlega następującym warunkom:  
  
- Wszystkie typy możliwe do serializacji `[DataContract]` muszą być `public` .  
  
- Wszystkie możliwe do serializacji `[DataMember]` pola lub właściwości w `[DataContract]` typie muszą być publiczne i odczytywane i zapisywane. Serializacja i deserializacja pól [tylko do odczytu](https://go.microsoft.com/fwlink/?LinkID=98854) nie jest obsługiwana w przypadku uruchamiania programu WCF w częściowo zaufanej aplikacji.  
  
- `[Serializable]`Model programowania/ISerializable nie jest obsługiwany w środowisku częściowej relacji zaufania.  
  
- Znane typy muszą być określone w kodzie lub konfiguracji na poziomie komputera (Machine. config). Nie można określić znanych typów w konfiguracji na poziomie aplikacji ze względów bezpieczeństwa.  
  
- Typy, które implementują <xref:System.Runtime.Serialization.IObjectReference> zgłoszenie wyjątku w środowisku częściowo zaufanym.  
  
 Zapoznaj się z sekcją serializacji w [części częściowe zaufanie najlepsze rozwiązania](partial-trust-best-practices.md) , aby uzyskać więcej informacji o zabezpieczeniach <xref:System.Runtime.Serialization.DataContractSerializer> w przypadku bezpiecznego korzystania z aplikacji częściowo zaufanej.  
  
### <a name="collection-types"></a>Typy kolekcji  
 Niektóre typy kolekcji implementują zarówno <xref:System.Collections.Generic.IEnumerable%601> , jak i <xref:System.Collections.IEnumerable> . Przykłady obejmują typy, które implementują <xref:System.Collections.Generic.ICollection%601> . Takie typy mogą implementować `public` implementację `GetEnumerator()` i jawną implementację programu `GetEnumerator()` . W takim przypadku <xref:System.Runtime.Serialization.DataContractSerializer> wywołuje `public` implementację `GetEnumerator()` , a nie jawną implementację `GetEnumerator()` . Jeśli żadna z `GetEnumerator()` implementacji nie jest `public` i wszystkie są jawnymi implementacjami, następnie <xref:System.Runtime.Serialization.DataContractSerializer> wywołuje `IEnumerable.GetEnumerator()` .  
  
 W przypadku typów kolekcji, gdy usługa WCF jest uruchomiona w środowisku częściowej relacji zaufania, jeśli żadna z tych `GetEnumerator()` implementacji nie jest `public` lub żadna z nich nie jest jawną implementacją interfejsu, zgłaszany jest wyjątek zabezpieczeń.  
  
### <a name="netdatacontractserializer"></a>NetDataContractSerializer  
 Wiele typów kolekcji .NET Framework, takich <xref:System.Collections.Generic.List%601> jak <xref:System.Collections.ArrayList> , <xref:System.Collections.Generic.Dictionary%602> i <xref:System.Collections.Hashtable> nie są obsługiwane przez <xref:System.Runtime.Serialization.NetDataContractSerializer> w częściowej relacji zaufania. Te typy mają `[Serializable]` ustawiony atrybut i jak określono wcześniej w sekcji serializacji, ten atrybut nie jest obsługiwany w częściowej relacji zaufania. <xref:System.Runtime.Serialization.DataContractSerializer>Program traktuje kolekcje w specjalny sposób i w związku z tym jest w stanie obsłużyć to ograniczenie, ale <xref:System.Runtime.Serialization.NetDataContractSerializer> nie ma takiego mechanizmu do obejścia tego ograniczenia.  
  
 <xref:System.DateTimeOffset>Typ nie jest obsługiwany przez <xref:System.Runtime.Serialization.NetDataContractSerializer> w częściowej relacji zaufania.  
  
 Nie można używać surogatu z <xref:System.Runtime.Serialization.NetDataContractSerializer> (przy użyciu <xref:System.Runtime.Serialization.SurrogateSelector> mechanizmu) w przypadku uruchamiania w częściowej relacji zaufania. Należy zauważyć, że to ograniczenie dotyczy przy użyciu surogatu, a nie do serializacji go.  
  
## <a name="enabling-common-behaviors-to-run"></a>Włączanie wykonywania wspólnych zachowań  
 Zachowania usług lub punktów końcowych, które nie są oznaczone <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutem (APTCA), które są dodawane do [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) sekcji pliku konfiguracji nie są uruchamiane, gdy aplikacja działa w środowisku częściowej relacji zaufania, a w takim przypadku nie jest zgłaszany żaden wyjątek. Aby wymusić uruchamianie typowych zachowań, należy wykonać jedną z następujących czynności:  
  
- Oznacz wspólne zachowanie przy użyciu <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu, aby można go było uruchomić w przypadku wdrożenia jako częściowo zaufanej aplikacji. Należy pamiętać, że na komputerze można ustawić wpis rejestru, aby zapobiec uruchamianiu zestawów oznaczonych przez APTCA. .  
  
- Upewnij się, że jeśli aplikacja jest wdrożona jako w pełni zaufana aplikacja, której użytkownicy nie mogą modyfikować ustawień zabezpieczeń dostępu kodu w celu uruchamiania aplikacji w środowisku częściowej relacji zaufania. Jeśli tak się stanie, zachowanie nie zostanie uruchomione i żaden wyjątek nie jest zgłaszany. Aby to sprawdzić, zobacz opcję **levelfinal** za pomocą [Narzędzia Caspol. exe (narzędzie do uzyskiwania dostępu do kodu)](../../tools/caspol-exe-code-access-security-policy-tool.md).  
  
 Przykład typowego zachowania można znaleźć [w temacie How to: Lock down Endpoints in the Enterprise](../extending/how-to-lock-down-endpoints-in-the-enterprise.md).  
  
## <a name="configuration"></a>Konfigurowanie  
 Po jednym wyjątku kod częściowo zaufany może ładować tylko sekcje konfiguracji WCF w `app.config` pliku lokalnym. Aby załadować sekcje konfiguracyjne WCF, które odwołują się do sekcji WCF w pliku Machine. config lub w katalogu głównym Web. config wymaga ConfigurationPermission (bez ograniczeń). Bez tego uprawnienia odwołania do sekcji konfiguracji WCF (zachowania, powiązania) poza lokalnym plikiem konfiguracji powoduje wyjątek podczas ładowania konfiguracji.  
  
 Jedynym wyjątkiem jest konfiguracja typu dla serializacji, zgodnie z opisem w sekcji serializacji tego tematu.  
  
> [!IMPORTANT]
> Rozszerzenia konfiguracji są obsługiwane tylko wtedy, gdy działa w trybie pełnego zaufania.  
  
## <a name="diagnostics"></a>Diagnostyka  
  
### <a name="event-logging"></a>Rejestrowanie zdarzeń  
 Rejestrowanie zdarzeń ograniczonych jest obsługiwane w ramach częściowej relacji zaufania. W dzienniku zdarzeń rejestrowane są tylko błędy aktywacji usługi i śledzenie komunikatów i komunikaty o błędach. Maksymalna liczba zdarzeń, które mogą być rejestrowane przez proces to 5, aby uniknąć zapisywania nadmiernych komunikatów w dzienniku zdarzeń.  
  
### <a name="message-logging"></a>Rejestrowanie komunikatów  
 Rejestrowanie komunikatów nie działa w przypadku uruchamiania programu WCF w środowisku częściowej relacji zaufania. Jeśli ta opcja jest włączona w obszarze częściowe zaufanie, nie kończy się aktywacją usługi, ale komunikat nie jest rejestrowany.  
  
### <a name="tracing"></a>Śledzenie  
 Funkcja śledzenia z ograniczeniami jest dostępna w przypadku uruchamiania w środowisku częściowej relacji zaufania. W <`listeners`> elementu w pliku konfiguracji, jedyne typy, które można dodać, to <xref:System.Diagnostics.TextWriterTraceListener> i nowe <xref:System.Diagnostics.EventSchemaTraceListener> . Użycie standardu <xref:System.Diagnostics.XmlWriterTraceListener> może spowodować niekompletne lub nieprawidłowe dzienniki.  
  
 Obsługiwane źródła śledzenia to:  
  
- <xref:System.ServiceModel>  
  
- <xref:System.Runtime.Serialization>  
  
- <xref:System.IdentityModel.Claims>, <xref:System.IdentityModel.Policy> , <xref:System.IdentityModel.Selectors> i <xref:System.IdentityModel.Tokens> .  
  
 Następujące źródła śledzenia nie są obsługiwane:  
  
- CardSpace  
  
- <xref:System.IO.Log>  

- [System. ServiceModel. Internal. TransactionBridge](https://docs.microsoft.com/previous-versions/aa346556(v=vs.110))]
  
 <xref:System.Diagnostics.TraceOptions>Nie należy określać następujących elementów członkowskich wyliczenia:  
  
- <xref:System.Diagnostics.TraceOptions.Callstack?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceOptions.ProcessId?displayProperty=nameWithType>  
  
 W przypadku korzystania ze śledzenia w środowisku częściowej relacji zaufania upewnij się, że aplikacja ma wystarczające uprawnienia do przechowywania danych wyjściowych odbiornika śledzenia. Na przykład podczas używania <xref:System.Diagnostics.TextWriterTraceListener> do zapisywania danych wyjściowych śledzenia do pliku tekstowego należy upewnić się, że aplikacja wymaga FileIOPermission wymaganych do pomyślnego zapisu w pliku śledzenia.  
  
> [!NOTE]
> Aby uniknąć zalewania plików śledzenia ze zduplikowanymi błędami, WCF wyłącza śledzenie zasobu lub akcji po pierwszym błędzie zabezpieczeń. Istnieje jeden ślad wyjątku dla każdego niepowodzenia dostępu do zasobu, podczas gdy podejmowana jest próba uzyskania dostępu do zasobu lub wykonania akcji.  
  
## <a name="wcf-service-host"></a>Host usługi WCF  
 Host usługi WCF nie obsługuje częściowej relacji zaufania. Jeśli chcesz używać usługi WCF w częściowej relacji zaufania, nie należy używać szablonu projektu biblioteki usług WCF w programie Visual Studio do kompilowania usługi. Zamiast tego Utwórz nową witrynę sieci Web w programie Visual Studio, wybierając szablon witryna sieci Web usługi WCF, który może hostować usługę na serwerze sieci Web, na którym jest obsługiwana częściowe zaufanie WCF.  
  
## <a name="other-limitations"></a>Inne ograniczenia  

  Funkcja WCF jest ogólnie ograniczona do zagadnień związanych z zabezpieczeniami nałożonych przez aplikację hostingu. Jeśli na przykład WCF jest hostowana w aplikacji przeglądarki XAML (XBAP), podlegają ograniczeniam XBAP, zgodnie z opisem w [części Windows Presentation Foundation zabezpieczenia relacji zaufania](../../wpf/wpf-partial-trust-security.md).  
  
 Następujące dodatkowe funkcje nie są włączone w przypadku uruchamiania programu indigO2 w środowisku częściowej relacji zaufania:  
  
- Instrumentacja zarządzania Windows (WMI)  
  
- Rejestrowanie zdarzeń jest tylko częściowo włączone (zobacz dyskusje w sekcji **Diagnostyka** ).  
  
- Liczniki wydajności  
  
 Korzystanie z funkcji WCF, które nie są obsługiwane w środowisku częściowej relacji zaufania, może spowodować wyjątki w czasie wykonywania.  
  
## <a name="unlisted-features"></a>Funkcje nieznajdujące się na liście  
 Najlepszym sposobem, aby poznać, że informacja lub akcja jest niedostępna w przypadku uruchamiania w środowisku częściowego zaufania, jest próba uzyskania dostępu do zasobu lub wykonania akcji wewnątrz `try` bloku, a następnie `catch` błędu. Aby uniknąć zalewania plików śledzenia ze zduplikowanymi błędami, WCF wyłącza śledzenie zasobu lub akcji po pierwszym błędzie zabezpieczeń. Istnieje jeden ślad wyjątku dla każdego niepowodzenia dostępu do zasobu, podczas gdy podejmowana jest próba uzyskania dostępu do zasobu lub wykonania akcji.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [Obsługiwane scenariusze wdrażania](supported-deployment-scenarios.md)
- [Najlepsze rozwiązania dotyczące częściowego zaufania](partial-trust-best-practices.md)
