---
title: 'Szybki start: rozwiązywanie problemów z architekturą WCF'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: 86aab2b39aaa9c7d7d92f7d5738482723cf6852f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320179"
---
# <a name="wcf-troubleshooting-quickstart"></a>Szybki start: rozwiązywanie problemów z architekturą WCF
W tym temacie wymieniono kilka znanych problemów, z którymi klienci korzystali podczas opracowywania klientów i usług WCF. Jeśli problem, z którym korzystasz, nie znajduje się na liście, zalecamy skonfigurowanie śledzenia dla usługi. Spowoduje to wygenerowanie pliku śledzenia, który można wyświetlić za pomocą podglądu plików śledzenia i uzyskać szczegółowe informacje o wyjątkach, które mogą wystąpić w ramach usługi. Aby uzyskać więcej informacji na temat konfigurowania śledzenia, zobacz: [Konfigurowanie śledzenia](./diagnostics/tracing/configuring-tracing.md). Aby uzyskać więcej informacji na temat podglądu plików śledzenia, zobacz: [narzędzie Podgląd śledzenia usług (SvcTraceViewer. exe)](service-trace-viewer-tool-svctraceviewer-exe.md).  
  
1. [Po zainstalowaniu systemu Windows 7 i usług IIS podczas próby przeglądania do usługi WCF pojawia się następujący komunikat o błędzie: błąd HTTP 404,3 — nie znaleziono](#bkmk_0)  
  
     Błąd HTTP 404,3 — nie można obsłużyć żądanej strony FoundThe z powodu konfiguracji rozszerzenia. Jeśli strona jest skryptem, Dodaj program obsługi. Jeśli plik powinien zostać pobrany, Dodaj mapę MIME. Szczegóły błędu InformationModule StaticFileModule.  
  
2. [Czasami otrzymuję MessageSecurityException — w drugim żądaniu, jeśli mój klient jest w stanie bezczynności przez pewien czas po pierwszym żądaniu. Co się dzieje?](#BKMK_q1)  
  
3. [Usługa My zaczyna odrzucać nowych klientów po przejściu do niej od około 10 klientów. Co się dzieje?](#BKMK_q2)  
  
4. [Czy mogę załadować moją konfigurację usługi z innej lokalizacji niż plik konfiguracyjny aplikacji WCF?](#BKMK_q3)  
  
5. [Moja usługa i klient są doskonałe, ale nie mogę ich używać, gdy klient znajduje się na innym komputerze? Co się dzieje?](#BKMK_q4)  
  
6. [Gdy zgłaszam wyjątek FaultException @ no__t-1Exception >, gdzie typ jest wyjątkiem, zawsze otrzymuję ogólny typ Błęduexception na kliencie, a nie typ ogólny. Co się dzieje?](#BKMK_q5)  
  
7. [Wygląda na to, że operacje jednokierunkowe i typu żądanie-odpowiedź są zwracane z tą samą szybkością, gdy odpowiedź nie zawiera żadnych danych. Co się dzieje?](#BKMK_q6)  
  
8. [Używam certyfikatu X. 509 z moją usługą i otrzymuję system. Security. Cryptography. CryptographicException. Co się dzieje?](#BKMK_q77)  
  
9. [Pierwszy parametr operacji został zmieniony z wielkich na małe litery; teraz mój klient zgłasza wyjątek. Co się dzieje?](#BKMK_q88)  
  
10. [Używam jednego z narzędzi do śledzenia i otrzymuję EndpointNotFoundException. Co się dzieje?](#BKMK_q99)  
  
11. [Podczas wywoływania aplikacji HTTP sieci Web WCF z aplikacji SOAP WCF usługa zwraca następujący błąd: Metoda 405 nie jest dozwolona](#BK_MK99)  
  
 [Jaki jest adres podstawowy? Jak odnosi się do adresu punktu końcowego?](#BKMK_q10)  
  
<a name="bkmk_0"></a>   
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a>Po zainstalowaniu systemu Windows 7 i usług IIS podczas próby przeglądania do usługi WCF pojawia się następujący komunikat o błędzie: błąd HTTP 404,3 — nie znaleziono  
 Pełny komunikat o błędzie:  
  
 Błąd HTTP 404,3 — nie można obsłużyć żądanej strony FoundThe z powodu konfiguracji rozszerzenia. Jeśli strona jest skryptem, Dodaj program obsługi. Jeśli plik powinien zostać pobrany, Dodaj mapę MIME. Szczegóły błędu InformationModule StaticFileModule.  
  
 Ten komunikat o błędzie występuje, gdy "Windows Communication Foundation Aktywacja HTTP" nie jest jawnie ustawiony w panelu sterowania. Aby ustawić ten sposób, przejdź do panelu sterowania, kliknij pozycję programy w lewym dolnym rogu okna. Kliknij pozycję Włącz lub wyłącz funkcje systemu Windows. Rozwiń węzeł Microsoft .NET Framework 3.5.1 i wybierz pozycję Windows Communication Foundation Aktywacja HTTP.  
  
<a name="BKMK_q1"></a>   
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a>Czasami otrzymuję MessageSecurityException — w drugim żądaniu, jeśli mój klient jest w stanie bezczynności przez pewien czas po pierwszym żądaniu. Co się dzieje?  
 Drugie żądanie może zakończyć się niepowodzeniem głównie z dwóch powodów: (1) upłynął limit czasu sesji lub (2) serwer sieci Web, na którym znajduje się usługa, jest odtwarzany. W pierwszym przypadku sesja jest ważna do momentu przekroczenia limitu czasu usługi. Gdy usługa nie otrzymuje żądania od klienta w okresie określonym w powiązaniu usługi (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), usługa kończy sesję zabezpieczeń. Kolejne komunikaty klienta powodują, że <xref:System.ServiceModel.Security.MessageSecurityException>. Klient musi ponownie nawiązać bezpieczną sesję z usługą w celu wysłania przyszłych komunikatów lub użycia tokenu stanowego kontekstu zabezpieczeń. Tokeny kontekstowe kontekstu zabezpieczeń umożliwiają również bezpieczną sesję przetrwania odtwarzania serwera sieci Web. Aby uzyskać więcej informacji o korzystaniu ze stanowych tokenów bezpiecznego kontekstu w bezpiecznej sesji, zobacz [How to: Create a Security Context token for a Secure Session](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md). Alternatywnie można wyłączyć bezpieczne sesje. Korzystając z powiązania [\<wsHttpBinding >](../configure-apps/file-schema/wcf/wshttpbinding.md) , można ustawić właściwość `establishSecurityContext` na `false`, aby wyłączyć bezpieczne sesje. Aby wyłączyć bezpieczne sesje dla innych powiązań, należy utworzyć niestandardowe powiązanie. Aby uzyskać szczegółowe informacje o tworzeniu niestandardowego powiązania, zobacz [How to: Create a Custom Binding using the elementu SecurityBindingElement](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Przed zastosowaniem dowolnej z tych opcji należy zrozumieć wymagania dotyczące zabezpieczeń aplikacji.  
  
<a name="BKMK_q2"></a>   
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a>Usługa My zaczyna odrzucać nowych klientów po przejściu do niej od około 10 klientów. Co się dzieje?  
 Domyślnie usługi mogą mieć tylko 10 współbieżnych sesji. W związku z tym, jeśli powiązania usługi używają sesji, usługa akceptuje nowe połączenia klienta, dopóki nie osiągnie tego numeru, po upływie którego nowe połączenia z klientami będą odrzucane do momentu zakończenia jednej z bieżących sesji. Więcej klientów można obsłużyć na wiele sposobów. Jeśli usługa nie wymaga sesji, nie należy używać powiązania sesji. (Aby uzyskać więcej informacji, zobacz [Korzystanie z sesji](using-sessions.md)). Innym rozwiązaniem jest zwiększenie limitu sesji przez zmianę wartości właściwości <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> na liczbę odpowiednią do okoliczności.  
  
<a name="BKMK_q3"></a>   
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a>Czy mogę załadować moją konfigurację usługi z innej lokalizacji niż plik konfiguracyjny aplikacji WCF?  
 Tak, jednak trzeba utworzyć niestandardową klasę <xref:System.ServiceModel.ServiceHost>, która zastępuje metodę <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A>. Wewnątrz tej metody można wywołać bazę, aby najpierw załadować konfigurację (Jeśli chcesz również załadować informacje o konfiguracji standardowej), ale możesz również całkowicie zastąpić system ładowania konfiguracji. Należy pamiętać, że jeśli chcesz załadować konfigurację z pliku konfiguracji, który jest inny niż plik konfiguracyjny aplikacji, musisz przeanalizować plik konfiguracji samodzielnie i załadować konfigurację.  
  
 Poniższy przykład kodu pokazuje, jak zastąpić metodę <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> i bezpośrednio skonfigurować punkt końcowy.  
  
```csharp
public class MyServiceHost : ServiceHost  
{  
    public MyServiceHost(Type serviceType, params Uri[] baseAddresses)    
      : base(serviceType, baseAddresses)  
    {
        Console.WriteLine("MyServiceHost Constructor");
    }  
  
    protected override void ApplyConfiguration()  
    {  
        string straddress = GetAddress();  
        Uri address = new Uri(straddress);  
        Binding binding = GetBinding();  
        base.AddServiceEndpoint(typeof(IData), binding, address);  
    }  
  
    string GetAddress()  
    {
        return "http://MyMachine:7777/MyEndpointAddress/";
    }  
  
    Binding GetBinding()  
    {  
        WSHttpBinding binding = new WSHttpBinding();  
        binding.Security.Mode = SecurityMode.None;  
        return binding;  
    }  
}  
```  
  
<a name="BKMK_q4"></a>   
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a>Moja usługa i klient są doskonałe, ale nie mogę ich używać, gdy klient znajduje się na innym komputerze? Co się dzieje?  
 W zależności od wyjątku mogą wystąpić pewne problemy:  
  
- Może zajść potrzeba zmiany adresów punktu końcowego klienta na nazwę hosta, a nie "localhost".  
  
- Może być konieczne otwarcie portu w aplikacji. Aby uzyskać szczegółowe informacje, zobacz [instrukcje zapory](./samples/firewall-instructions.md) w PRZYKŁADACH zestawu SDK.  
  
- Inne możliwe problemy można znaleźć w temacie przykłady z przykładami [Windows Communication Foundation](./samples/running-the-samples.md).  
  
- Jeśli klient korzysta z poświadczeń systemu Windows, a wyjątkiem jest <xref:System.ServiceModel.Security.SecurityNegotiationException>, należy skonfigurować protokół Kerberos w następujący sposób.  
  
    1. Dodaj poświadczenia tożsamości do elementu punktu końcowego w pliku App. config klienta:  
  
        ```xml
        <endpoint   
          address="http://MyServer:8000/MyService/"   
          binding="wsHttpBinding"   
          bindingConfiguration="WSHttpBinding_IServiceExample"   
          contract="IServiceExample"   
          behaviorConfiguration="ClientCredBehavior"   
          name="WSHttpBinding_IServiceExample">  
          <identity>  
            <userPrincipalName value="name@corp.contoso.com"/>  
          </identity>  
        </endpoint>  
        ```  
  
    2. Uruchom usługę samoobsługową w ramach konta system lub NetworkService. Możesz uruchomić to polecenie, aby utworzyć okno polecenia w ramach konta systemowego:  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3. Hostowanie usługi w obszarze Internet Information Services (IIS), która domyślnie używa konta głównej nazwy usługi (SPN).  
  
    4. Zarejestruj nową nazwę SPN z domeną przy użyciu narzędzia SetSPN. Należy pamiętać, że aby to zrobić, musisz być administratorem domeny.  
  
 Aby uzyskać więcej informacji na temat protokołu Kerberos, zobacz [pojęcia dotyczące zabezpieczeń używane w programie WCF](./feature-details/security-concepts-used-in-wcf.md) i:  
  
- [Debugowanie błędów uwierzytelniania systemu Windows](./feature-details/debugging-windows-authentication-errors.md)  
  
- [Rejestrowanie nazw głównych usługi Kerberos przy użyciu protokołu HTTP. sys](https://go.microsoft.com/fwlink/?LinkId=86943)  
  
- [Objaśnienie protokołu Kerberos](https://go.microsoft.com/fwlink/?LinkId=86946)  
  
<a name="BKMK_q5"></a>   
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a>Gdy zgłaszam wyjątek FaultException @ no__t-0Exception >, gdzie typ jest wyjątkiem, zawsze otrzymuję ogólny typ Błęduexception na kliencie, a nie typ ogólny. Co się dzieje?  
 Zdecydowanie zaleca się utworzenie własnego niestandardowego typu danych błędu i zadeklarowanie, że jako typ szczegółowy w umowie dotyczącej błędu. Przyczyną jest użycie typów wyjątków dostarczonych przez system:  
  
- Tworzy zależność typu, która usuwa jedną z największych siły aplikacji zorientowanych na usługę.  
  
- Nie może zależeć od wyjątków serializowanych w standardowy sposób. Niektóre — takie jak <xref:System.Security.SecurityException> — nie można serializować.  
  
- Udostępnia klientom szczegółowe informacje o implementacji wewnętrznej. Aby uzyskać więcej informacji, zobacz [określanie i obsługa błędów w kontraktach i usługach](specifying-and-handling-faults-in-contracts-and-services.md).  
  
 W przypadku debugowania aplikacji można jednak serializować informacje o wyjątkach i zwrócić je do klienta przy użyciu klasy <xref:System.ServiceModel.Description.ServiceDebugBehavior>.  
  
<a name="BKMK_q6"></a>   
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a>Wygląda na to, że operacje jednokierunkowe i typu żądanie-odpowiedź są zwracane z tą samą szybkością, gdy odpowiedź nie zawiera żadnych danych. Co się dzieje?  
 Określenie, że operacja jest jednym ze sposobów, że kontrakt operacji akceptuje komunikat wejściowy i nie zwraca komunikatu wyjściowego. W programie WCF wszystkie wywołania klienta zwracają, gdy dane wychodzące zostały zapisaną do sieci lub zgłoszono wyjątek. Operacje jednokierunkowe działają w ten sam sposób i mogą zgłosić, czy usługa nie może zostać zlokalizowana lub zablokować, jeśli usługa nie jest przygotowana do akceptowania danych z sieci. Zwykle w programie WCF skutkiem wywołania jednokierunkowego powracają do klienta szybciej niż żądanie-odpowiedź; Jednak każdy warunek, który spowalnia wysyłanie danych wychodzących za pośrednictwem sieci, spowalnia operacje jednokierunkowe oraz operacje odpowiedzi na żądanie. Aby uzyskać więcej informacji, zobacz jednokierunkowe [usługi](./feature-details/one-way-services.md) i [dostęp do usług przy użyciu klienta WCF](./feature-details/accessing-services-using-a-client.md).  
  
<a name="BKMK_q77"></a>   
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a>Używam certyfikatu X. 509 z moją usługą i otrzymuję system. Security. Cryptography. CryptographicException. Co się dzieje?  
 Jest to często spowodowane zmianą konta użytkownika, pod którym działa proces roboczy usług IIS. Na przykład w [!INCLUDE[wxp](../../../includes/wxp-md.md)], jeśli zmienisz domyślne konto użytkownika, w ramach którego jest uruchamiany proces aspnet_wp. exe, w obszarze od ASPNET do niestandardowego konta użytkownika, ten błąd może zostać wyświetlony. W przypadku korzystania z klucza prywatnego proces korzystający z niego musi mieć uprawnienia dostępu do pliku przechowującego ten klucz.  
  
 W takim przypadku należy nadać uprawnienia dostępu do odczytu kontu tego procesu dla pliku zawierającego klucz prywatny. Na przykład jeśli proces roboczy usług IIS jest uruchomiony na koncie Roberta, należy dać plikowi z dostępem do odczytu do pliku zawierającego klucz prywatny.  
  
 Aby uzyskać więcej informacji o tym, jak nadawać poprawnemu kontu użytkownika dostęp do pliku, który zawiera klucz prywatny dla określonego certyfikatu X. 509, zobacz [How to: Make x. 509 Certificates dostępne dla WCF](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).  
  
<a name="BKMK_q88"></a>   
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a>Pierwszy parametr operacji został zmieniony z wielkich na małe litery; teraz mój klient zgłasza wyjątek. Co się dzieje?  
 Wartość nazw parametrów w sygnaturze operacji jest częścią kontraktu i jest uwzględniana wielkość liter. Użyj atrybutu <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>, gdy musisz rozróżnić nazwę parametru lokalnego i metadane opisujące operację dla aplikacji klienckich.  
  
<a name="BKMK_q99"></a>   
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a>Używam jednego z narzędzi do śledzenia i otrzymuję EndpointNotFoundException. Co się dzieje?  
 Jeśli używasz narzędzia śledzenia, które nie jest mechanizmem śledzenia WCF dostarczonym przez system i otrzymujesz <xref:System.ServiceModel.EndpointNotFoundException> wskazujące niezgodność filtru adresów, należy użyć klasy <xref:System.ServiceModel.Description.ClientViaBehavior> do kierowania komunikatów do narzędzia śledzenia i uzyskiwania Narzędzie przekierowuje te komunikaty do adresu usługi. Klasa <xref:System.ServiceModel.Description.ClientViaBehavior> modyfikuje nagłówek adresowania `Via` w celu określenia następnego adresu sieciowego niezależnie od odbiorcy końcowego wskazywanego przez nagłówek adresowania `To`. W takim przypadku nie należy zmieniać adresu punktu końcowego, który jest używany do ustanowienia wartości `To`.  
  
 Poniższy przykład kodu przedstawia przykładowy plik konfiguracji klienta.  
  
```xml
<endpoint   
  address="http://localhost:8000/MyServer/"  
  binding="wsHttpBinding"  
  bindingConfiguration="WSHttpBinding_IMyContract"  
  behaviorConfiguration="MyClient"   
  contract="IMyContract"   
  name="WSHttpBinding_IMyContract">  
</endpoint>  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="MyClient">  
      <clientVia viaUri="http://localhost:8001/MyServer/"/>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
<a name="BKMK_q10"></a>   
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a>Jaki jest adres podstawowy? Jak odnosi się do adresu punktu końcowego?  
 Adres podstawowy jest adresem głównym klasy <xref:System.ServiceModel.ServiceHost>. Domyślnie, jeśli dodasz klasę <xref:System.ServiceModel.Description.ServiceMetadataBehavior> do konfiguracji usługi, Web Services Description Language (WSDL) dla wszystkich punktów końcowych publikowanych przez hosta są pobierane z adresu podstawowego HTTP, a także adres względny do zachowania metadanych, a także "? WSDL ". Jeśli znasz usługi ASP.NET i IIS, adres podstawowy jest równoważny z katalogiem wirtualnym.  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a>Udostępnianie portu między punktem końcowym usługi a punktem końcowym MEX przy użyciu NetTcpBinding  
 W przypadku określenia adresu podstawowego dla usługi jako net. TCP://MyServer: 8080/moje usługi i dodania następujących punktów końcowych:  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 A jeśli zmodyfikujesz jedno z ustawień NetTcpBinding, jak pokazano w poniższym fragmencie kodu:  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding closeTimeout="00:01:00" openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00" transactionFlow="false" transferMode="Buffered" transactionProtocol="OleTransactions" hostNameComparisonMode="StrongWildcard" listenBacklog="10" maxBufferPoolSize="524288" maxBufferSize="65536" maxConnections="11" maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384"/>  
      <reliableSession ordered="true" inactivityTimeout="00:10:00" enabled="false"/>  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign"/>  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
 Zobaczysz błąd podobny do następującego: nieobsługiwany wyjątek: System. ServiceModel. AddressAlreadyInUseException —: istnieje już odbiornik w punkcie końcowym IP 0.0.0.0:9000 można obejść ten błąd, określając w pełni kwalifikowany adres URL z innym portem dla punkt końcowy MEX, jak pokazano w poniższym fragmencie kodu:  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>   
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a>Podczas wywoływania aplikacji HTTP sieci Web WCF z aplikacji SOAP WCF usługa zwraca następujący błąd: Metoda 405 nie jest dozwolona  
 Wywołanie aplikacji HTTP sieci Web w programie WCF (usługa, która używa <xref:System.ServiceModel.WebHttpBinding> i <xref:System.ServiceModel.Description.WebHttpBehavior>) z usługi WCF, może wygenerować następujący wyjątek: `Unhandled Exception: System.ServiceModel.FaultException`1 [System. ServiceModel. ExceptionDetail utworzony]: serwer zdalny zwrócił nieoczekiwaną odpowiedź: (405) Metoda nie Dozwolony. "ten wyjątek występuje, ponieważ program WCF zastępuje wychodzące <xref:System.ServiceModel.OperationContext> z przychodzącą <xref:System.ServiceModel.OperationContext>. Aby rozwiązać ten problem, Utwórz <xref:System.ServiceModel.OperationContextScope> w ramach operacji usługi HTTP sieci Web WCF. Na przykład:  
  
```csharp
public string Echo(string input)  
{  
    using (new OperationContextScope(this.InnerChannel))  
    {  
        return base.Channel.Echo(input);  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie błędów uwierzytelniania systemu Windows](./feature-details/debugging-windows-authentication-errors.md)
