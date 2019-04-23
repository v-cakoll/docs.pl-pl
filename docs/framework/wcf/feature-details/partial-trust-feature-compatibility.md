---
title: Zgodność funkcji zaufania częściowego
ms.date: 03/30/2017
ms.assetid: a36a540b-1606-4e63-88e0-b7c59e0e6ab7
ms.openlocfilehash: b0d9b7bd8bd5f33ca344ea5674d08507ced209f5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124569"
---
# <a name="partial-trust-feature-compatibility"></a>Zgodność funkcji zaufania częściowego
Windows Communication Foundation (WCF) obsługuje ograniczony podzestaw funkcji podczas uruchamiania w środowisku częściowo zaufany. Funkcje obsługiwane w częściowej relacji zaufania są projektowane na podstawie określonego zestawu scenariuszy zgodnie z opisem w [obsługiwane scenariusze wdrażania](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md) tematu.  
  
## <a name="minimum-permission-requirements"></a>Wymagania dotyczące minimalnych uprawnień  
 Usługi WCF obsługuje podzbiór funkcji w aplikacjach działających w ramach jednej z następujących standardowych nazwanych zestawów uprawnień:  
  
-   Średnie uprawnienia zaufania  
  
-   Uprawnień strefy Internet  
  
 Podjęto próbę użycia usługi WCF w częściowo zaufanych aplikacji przy użyciu bardziej restrykcyjne uprawnienia mogą spowodować wystąpienie wyjątków zabezpieczeń w czasie wykonywania.  
  
## <a name="contracts"></a>Kontrakty  
 Kontrakty podlegają następującym ograniczeniom, podczas uruchamiania w częściowej relacji zaufania:  
  
-   Klasa usługi, która implementuje `[ServiceContract]` interfejs musi być `public` i `public` konstruktora. Jeśli definiuje `[OperationContract]` metod, muszą to być `public`. Jeśli zamiast tego implementuje `[ServiceContract]` interfejs, te implementacje metod może być jawne lub `private`pod warunkiem, że `[ServiceContract]` interfejs `public`.  
  
-   Korzystając z `[ServiceKnownType]` atrybut, musi być określona metoda `public`.  
  
-   `[MessageContract]` klasy i składowe mogą być `public`. Jeśli `[MessageContract]` klasa jest zdefiniowana w zestawie aplikacji może być `internal` i `internal` elementów członkowskich.  
  
## <a name="system-provided-bindings"></a>Wiązania dostarczane przez system  
 <xref:System.ServiceModel.BasicHttpBinding> i <xref:System.ServiceModel.WebHttpBinding> są w pełni obsługiwane w środowisku częściowej relacji zaufania. <xref:System.ServiceModel.WSHttpBinding> Jest obsługiwana w przypadku tylko tryb zabezpieczeń Transport.  
  
 Powiązania używających transportu innego niż HTTP, takich jak <xref:System.ServiceModel.NetTcpBinding>, <xref:System.ServiceModel.NetNamedPipeBinding>, lub <xref:System.ServiceModel.NetMsmqBinding>, nie są obsługiwane w przypadku uruchamiania w środowisku częściowej relacji zaufania.  
  
## <a name="custom-bindings"></a>Powiązania niestandardowe  
 Powiązania niestandardowe mogą być tworzone i używane w środowisku częściowej relacji zaufania, ale musi stosować ograniczenia określone w tej sekcji.  
  
### <a name="transports"></a>Transporty  
 Jedyną dozwoloną powiązania transportu elementy są <xref:System.ServiceModel.Channels.HttpTransportBindingElement> i <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.  
  
### <a name="encoders"></a>Koderów  
 Następujące kodery są dozwolone:  
  
-   Koder tekstu (<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>).  
  
-   Kodera binarnego (<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>).  
  
-   Koder komunikatów w sieci Web (<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>).  
  
 Kodery komunikat transmisji optymalizacji mechanizm (MTOM) nie są obsługiwane.  
  
### <a name="security"></a>Zabezpieczenia  
 Częściowo zaufane aplikacje mogą używać funkcji zabezpieczenia na poziomie transportu dla usługi WCF, do zabezpieczania komunikacji. Zabezpieczenia na poziomie komunikatu nie jest obsługiwana. Konfigurowanie powiązania do użycia zabezpieczenia na poziomie komunikatu powoduje wyjątek w czasie wykonywania.  
  
### <a name="unsupported-bindings"></a>Nieobsługiwane powiązania  
 Powiązania, które używają niezawodną obsługę komunikatów, transakcji lub zabezpieczenia na poziomie komunikatu nie są obsługiwane.  
  
## <a name="serialization"></a>Serializacja  
 Zarówno <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Xml.Serialization.XmlSerializer> są obsługiwane w środowisku częściowej relacji zaufania. Jednak użycie <xref:System.Runtime.Serialization.DataContractSerializer> podlega następujące warunki:  
  
-   Wszystkie możliwe do serializacji `[DataContract]` typy muszą być `public`.  
  
-   Wszystkie możliwe do serializacji `[DataMember]` pól lub właściwości w `[DataContract]` typu muszą być publiczne i odczytu/zapisu. Serializacja i deserializacja [tylko do odczytu](https://go.microsoft.com/fwlink/?LinkID=98854) pola nie jest obsługiwana podczas uruchamiania usługi WCF w częściowo zaufanych aplikacji.  
  
-    `[Serializable]` /ISerializable model programowania nie jest obsługiwany w środowisku częściowej relacji zaufania.  
  
-   Znane typy, należy określić w kodzie lub konfiguracji poziomie komputera (machine.config). Znane typy nie może być określona w konfiguracji dodatku poziomu aplikacji ze względów bezpieczeństwa.  
  
-   Typami, które implementują <xref:System.Runtime.Serialization.IObjectReference> zgłoszenie wyjątku w środowisku częściowo zaufany.  
  
 Zobacz sekcję serializacji w [częściowego zaufania najlepszych rozwiązań](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) Aby uzyskać więcej informacji o zabezpieczeniach, używając <xref:System.Runtime.Serialization.DataContractSerializer> bezpiecznie w aplikacji częściowo zaufanej.  
  
### <a name="collection-types"></a>Typy kolekcji  
 Niektóre typy kolekcji zaimplementować obu <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.Collections.IEnumerable>. Przykłady obejmują typy, które implementują <xref:System.Collections.Generic.ICollection%601>. Typy takie można zaimplementować `public` implementacji `GetEnumerator()`i jawnych implementacji `GetEnumerator()`. W tym przypadku <xref:System.Runtime.Serialization.DataContractSerializer> wywołuje `public` implementacji `GetEnumerator()`, a nie jawnych implementacji `GetEnumerator()`. Jeśli żadna z `GetEnumerator()` implementacje są `public` i wszystkie jawne implementacje <xref:System.Runtime.Serialization.DataContractSerializer> wywołuje `IEnumerable.GetEnumerator()`.  
  
 Dla typów kolekcji podczas uruchamiania usługi WCF w środowisku częściowej relacji zaufania, jeśli żadna z `GetEnumerator()` implementacje są `public`, lub żaden z nich jest jawne implementacje interfejsu, a następnie jest zgłaszany wyjątek zabezpieczeń.  
  
### <a name="netdatacontractserializer"></a>NetDataContractSerializer  
 Wiele typów kolekcji .NET Framework, takich jak <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ArrayList>, <xref:System.Collections.Generic.Dictionary%602> i <xref:System.Collections.Hashtable> nie są obsługiwane przez <xref:System.Runtime.Serialization.NetDataContractSerializer> w częściowej relacji zaufania. Te typy mają `[Serializable]` ustawiony atrybut i jak wspomniano wcześniej, w sekcji serializacji, ten atrybut nie jest obsługiwany w częściowej relacji zaufania. <xref:System.Runtime.Serialization.DataContractSerializer> Traktuje kolekcje w specjalny sposób i dlatego jest w stanie obejść to ograniczenie, ale <xref:System.Runtime.Serialization.NetDataContractSerializer> ma nie mechanizmów na obejście tego ograniczenia.  
  
 <xref:System.DateTimeOffset> Typ nie jest obsługiwany przez <xref:System.Runtime.Serialization.NetDataContractSerializer> w częściowej relacji zaufania.  
  
 Zastępczy nie można używać z <xref:System.Runtime.Serialization.NetDataContractSerializer> (przy użyciu <xref:System.Runtime.Serialization.SurrogateSelector> mechanizm) podczas uruchamiania w trybie częściowego zaufania. Należy pamiętać, że to ograniczenie dotyczy za pomocą zastępczych, nie należy go serializacji.  
  
## <a name="enabling-common-behaviors-to-run"></a>Włączanie wspólny zbiór wykonywanych czynności do uruchomienia  
 Zachowania usługi lub punkt końcowy nie jest oznaczony atrybutem <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu (APTCA), które są dodawane do [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) sekcję pliku konfiguracji nie są uruchamiane, gdy aplikacja zostanie uruchomiona w częściowej relacji zaufania środowisko i żaden wyjątek jest zgłaszany w takiej sytuacji. Aby wymusić uruchomienie wspólny zbiór wykonywanych czynności, należy wykonać jedną z następujących opcji:  
  
-   Oznacz swoje wspólnego zachowania za pomocą <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu, dzięki czemu może działać w przypadku wdrażania jako częściowo zaufanych aplikacji. Należy pamiętać, że wpis rejestru można ustawić na komputerze, aby zapobiec oznaczone APTCA zestawy uruchamianie. .  
  
-   Upewnij się, że jeśli aplikacja jest wdrażana jako w pełni zaufanych aplikacji, użytkownicy nie mogą modyfikować ustawienia zabezpieczeń dostępu kodu do uruchomienia aplikacji w środowisku częściowej relacji zaufania. Jeśli tak jest, więc, zachowanie nie działa i nie jest zgłaszany żaden wyjątek. Aby to zapewnić, zobacz **levelfinal** opcji za pomocą [Caspol.exe (narzędzie zasad zabezpieczeń dostępu kodu)](../../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).  
  
 Na przykład wspólnego zachowania zobacz [jak: Blokowanie punktów końcowych w przedsiębiorstwie](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).  
  
## <a name="configuration"></a>Konfiguracja  
 Z jednym wyjątkiem, częściowo zaufany kod może ładować wyłącznie sekcji konfiguracyjnych WCF w lokalnym `app.config` pliku. Aby załadować sekcji konfiguracji WCF, które odwołują się usługi WCF w sekcji w pliku machine.config lub w katalogu głównym pliku web.config wymaga ConfigurationPermission(Unrestricted). Bez tego uprawnienia odwołuje się do usługi WCF sekcji konfiguracji (zachowań, powiązania) poza lokalnej konfiguracji wyniki plik w wyjątek podczas ładowania konfiguracji.  
  
 Jedynym wyjątkiem jest znany typ konfiguracji do serializacji, zgodnie z opisem w sekcji serializacji w tym temacie.  
  
> [!IMPORTANT]
>  Rozszerzenia konfiguracji są obsługiwane tylko w sytuacji, gdy uruchomiona w ramach pełnego zaufania.  
  
## <a name="diagnostics"></a>Diagnostyka  
  
### <a name="event-logging"></a>Rejestrowanie zdarzeń  
 Rejestrowanie zdarzeń ograniczony jest obsługiwane w częściowej relacji zaufania. Tylko usługi aktywacji błędy i awarie rejestrowanie śledzenia/wiadomości są rejestrowane w dzienniku zdarzeń. Maksymalna liczba zdarzeń, które mogą być rejestrowane przez proces wynosi 5, aby uniknąć nadmiernej liczby komunikatów w dzienniku zdarzeń.  
  
### <a name="message-logging"></a>Rejestrowanie komunikatów  
 Rejestrowanie komunikatów nie działa po uruchomieniu usługi WCF w środowisku częściowej relacji zaufania. Jeśli włączona w częściowej relacji zaufania, nie wystąpi niepowodzenie aktywacji usługi, ale nie jest rejestrowany.  
  
### <a name="tracing"></a>Śledzenie  
 Funkcja śledzenia ograniczony jest dostępna podczas uruchamiania w środowisku częściowej relacji zaufania. W <`listeners`> są tylko typy, które można dodać elementu w pliku konfiguracji, <xref:System.Diagnostics.TextWriterTraceListener> i nowym <xref:System.Diagnostics.EventSchemaTraceListener>. Użyj standardowych <xref:System.Diagnostics.XmlWriterTraceListener> może spowodować niepełną lub nieprawidłową dzienniki.  
  
 Źródła śledzenia obsługiwane są:  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.Runtime.Serialization>  
  
-   <xref:System.IdentityModel.Claims>, <xref:System.IdentityModel.Policy>, <xref:System.IdentityModel.Selectors>, i <xref:System.IdentityModel.Tokens>.  
  
 Nie są obsługiwane następujące źródła śledzenia:  
  
-   CardSpace  
  
-   <xref:System.IO.Log>  

-   [System.ServiceModel.Internal.TransactionBridge](https://docs.microsoft.com/previous-versions/aa346556(v=vs.110))]
  
 Następujące elementy członkowskie z <xref:System.Diagnostics.TraceOptions> wyliczenia nie należy określać:  
  
-   <xref:System.Diagnostics.TraceOptions.Callstack?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceOptions.ProcessId?displayProperty=nameWithType>  
  
 Jeśli śledzenie w środowisku częściowej relacji zaufania, upewnij się, że aplikacja ma wystarczające uprawnienia do przechowywania danych wyjściowych odbiornik śledzenia. Na przykład w przypadku korzystania z <xref:System.Diagnostics.TextWriterTraceListener> można zapisywać dane wyjściowe śledzenia do pliku tekstowego, sprawdź, czy aplikacja ma niezbędne FileIOPermission, które trzeba zapisać do pliku śledzenia.  
  
> [!NOTE]
>  Aby zapobiec przepełnieniu pliki śledzenia błędów zduplikowane, WCF wyłącza śledzenie zasobów lub akcji po pierwszym niepowodzeniu zabezpieczeń. Istnieje jeden śledzenia wyjątków dla każdego dostępu zasobu nie powiodło się po raz pierwszy zostanie podjęta próba dostępu do zasobu lub wykonania akcji.  
  
## <a name="wcf-service-host"></a>Host usługi WCF  
 Host usługi WCF nie obsługuje częściowej relacji zaufania. Jeśli chcesz użyć usługi WCF w częściowej relacji zaufania, nie używaj szablonu projektu biblioteki usługi WCF w programie Visual Studio do tworzenia usługi. Zamiast tego należy utworzyć nową witrynę sieci Web w programie Visual Studio, wybierając szablon witryny sieci Web usługi WCF, który może obsługiwać usługi na serwerze sieci Web, na którym jest obsługiwany WCF częściowej relacji zaufania.  
  
## <a name="other-limitations"></a>Pozostałe ograniczenia  
 Usługi WCF jest zazwyczaj ograniczona do zagadnienia dotyczące zabezpieczeń nałożonych przez hostingu aplikacji. Na przykład, jeśli WCF jest hostowana w aplikacji przeglądarki XAML (XBAP), podlega ograniczenia XBAP zgodnie z opisem w [Windows Presentation Foundation częściowego zaufania zabezpieczeń](https://go.microsoft.com/fwlink/?LinkId=89138).  
  
 Następujące dodatkowe funkcje nie są włączone, podczas uruchamiania indigo2 w środowisku częściowej relacji zaufania:  
  
-   Instrumentacja zarządzania Windows (WMI)  
  
-   Rejestrowanie zdarzeń jest tylko częściowo włączona (zobacz Omówienie w **diagnostyki** sekcji).  
  
-   Liczniki wydajności  
  
 Korzystanie z funkcji WCF, które nie są obsługiwane w środowisku częściowej relacji zaufania może spowodować wyjątków w czasie wykonywania.  
  
## <a name="unlisted-features"></a>Funkcje nieznajdujące się na liście  
 Najlepszym sposobem odnajdywanie informacji lub akcja jest niedostępna, podczas uruchamiania w środowisku częściowej relacji zaufania spróbuj uzyskać dostęp do zasobu lub wykonaj akcję wewnątrz `try` bloku, a następnie `catch` awarii. Aby zapobiec przepełnieniu pliki śledzenia błędów zduplikowane, WCF wyłącza śledzenie zasobów lub akcji po pierwszym niepowodzeniu zabezpieczeń. Istnieje jeden śledzenia wyjątków dla każdego dostępu zasobu nie powiodło się po raz pierwszy zostanie podjęta próba dostępu do zasobu lub wykonania akcji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [Obsługiwane scenariusze wdrażania](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)
- [Najlepsze rozwiązania dotyczące częściowego zaufania](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)
