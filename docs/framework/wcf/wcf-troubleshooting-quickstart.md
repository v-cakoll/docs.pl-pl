---
title: 'Szybki start: rozwiązywanie problemów z architekturą WCF'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: f85d37fde19767d7fd1e3002776b4816666cc7e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183056"
---
# <a name="wcf-troubleshooting-quickstart"></a>Szybki start: rozwiązywanie problemów z architekturą WCF
W tym temacie wymieniono szereg znanych problemów, na które napotkali klienci podczas opracowywania klientów i usług WCF. Jeśli problem, na który się nadajesz, nie znajduje się na tej liście, zaleca się skonfigurowanie śledzenia dla usługi. Spowoduje to wygenerowanie pliku śledzenia, który można wyświetlić za pomocą przeglądarki plików śledzenia i uzyskać szczegółowe informacje o wyjątkach, które mogą występować w usłudze. Aby uzyskać więcej informacji na temat konfigurowania śledzenia, zobacz: [Konfigurowanie śledzenia](./diagnostics/tracing/configuring-tracing.md). Aby uzyskać więcej informacji na temat przeglądarki plików śledzenia, zobacz: [Narzędzie Podgląd śledzenia usług (SvcTraceViewer.exe)](service-trace-viewer-tool-svctraceviewer-exe.md).  
  
1. [Po zainstalowaniu systemu Windows 7 i IIS, gdy próbuję przejść do usługi WCF pojawia się następujący komunikat o błędzie: Błąd HTTP 404.3 — Nie znaleziono](#bkmk_0)  
  
     Błąd HTTP 404.3 — nie znalezionoNa stronie, której żądasz, nie można obsługiwać ze względu na konfigurację rozszerzenia. Jeśli strona jest skryptem, dodaj program obsługi. Jeśli plik powinien zostać pobrany, dodaj mapę MIME. Szczegółowe informacje o błędzieModule statyczny.  
  
2. [Czasami otrzymuję MessageSecurityException na drugie żądanie, jeśli mój klient jest bezczynny przez jakiś czas po pierwszym żądaniu. Co się dzieje?](#BKMK_q1)  
  
3. [Moja usługa zaczyna odrzucać nowych klientów po tym, jak około 10 klientów wchodzi z nią w interakcję. Co się dzieje?](#BKMK_q2)  
  
4. [Czy mogę załadować konfigurację usługi z innego miejsca niż plik konfiguracyjny aplikacji WCF?](#BKMK_q3)  
  
5. [Moja usługa i klient działają świetnie, ale nie mogę ich do pracy, gdy klient jest na innym komputerze? Co się dzieje?](#BKMK_q4)  
  
6. [Gdy zgłaszam Exception FaultException\<>, w którym typ jest wyjątkiem, zawsze otrzymuję ogólny typ FaultException na kliencie, a nie typ ogólny. Co się dzieje?](#BKMK_q5)  
  
7. [Wydaje się, że operacje jednokierunkowe i żądanie odpowiedzi zwracają z grubszą taką samą prędkością, gdy odpowiedź nie zawiera żadnych danych. Co się dzieje?](#BKMK_q6)  
  
8. [Używam certyfikatu X.509 z moją usługą i otrzymuję system.Security.Cryptography.CryptographicException. Co się dzieje?](#BKMK_q77)  
  
9. [Zmieniłem pierwszy parametr operacji z wielkich na małe; teraz mój klient zgłasza wyjątek. Co się dzieje?](#BKMK_q88)  
  
10. [Używam jednego z moich narzędzi śledzenia i otrzymuję EndpointNotFoundException. Co się dzieje?](#BKMK_q99)  
  
11. [Podczas wywoływania aplikacji WCF Web HTTP z aplikacji WCF SOAP usługa zwraca następujący błąd: 405 Metoda niedozwolona](#BK_MK99)  
  
 [Jaki jest adres podstawowy? Jak odnosi się do adresu punktu końcowego?](#BKMK_q10)  
  
<a name="bkmk_0"></a>
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a>Po zainstalowaniu systemu Windows 7 i IIS, gdy próbuję przejść do usługi WCF pojawia się następujący komunikat o błędzie: Błąd HTTP 404.3 — Nie znaleziono  
 Pełny komunikat o błędzie to:  
  
 Błąd HTTP 404.3 — nie znalezionoNa stronie, której żądasz, nie można obsługiwać ze względu na konfigurację rozszerzenia. Jeśli strona jest skryptem, dodaj program obsługi. Jeśli plik powinien zostać pobrany, dodaj mapę MIME. Szczegółowe informacje o błędzieModule statyczny.  
  
 Ten komunikat o błędzie występuje, gdy "Aktywacja HTTP programu Windows Communication Foundation" nie jest jawnie ustawiona w Panelu sterowania. Aby ustawić tę opcję, przejdź do Panelu sterowania, kliknij pozycję Programy w lewym dolnym rogu okna. Kliknij pozycję Włączanie lub wyłączanie funkcji systemu Windows. Rozwiń węzeł Microsoft .NET Framework 3.5.1 i wybierz pozycję Aktywacja HTTP programu Windows Communication Foundation.  
  
<a name="BKMK_q1"></a>
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a>Czasami otrzymuję MessageSecurityException na drugie żądanie, jeśli mój klient jest bezczynny przez jakiś czas po pierwszym żądaniu. Co się dzieje?  
 Drugie żądanie może zakończyć się niepowodzeniem głównie z dwóch powodów: (1) sesja została przesuń lub (2) serwer sieci Web, który hostuje usługę jest odtworzony. W pierwszym przypadku sesja jest prawidłowa do czasu przesunienia się usługi. Gdy usługa nie otrzyma żądania od klienta w okresie określonym w powiązaniu usługi (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), usługa kończy sesję zabezpieczeń. Kolejne komunikaty <xref:System.ServiceModel.Security.MessageSecurityException>klienta powodują . Klient musi ponownie ustanowić bezpieczną sesję z usługą, aby wysyłać przyszłe wiadomości lub używać stanowego tokenu kontekstu zabezpieczeń. Tokeny kontekstu zabezpieczeń stanowe umożliwiają również bezpieczną sesję, aby przetrwać serwer sieci Web poddawany recyklingowi. Aby uzyskać więcej informacji na temat używania stanowych tokenów bezpiecznego kontekstu w bezpiecznej sesji, zobacz [Jak: Tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md). Alternatywnie można wyłączyć bezpieczne sesje. Korzystając z powiązania [ \<>wsHttpBinding,](../configure-apps/file-schema/wcf/wshttpbinding.md) można ustawić `establishSecurityContext` właściwość `false` tak, aby wyłączyła bezpieczne sesje. Aby wyłączyć bezpieczne sesje dla innych powiązań, należy utworzyć niestandardowe powiązanie. Aby uzyskać szczegółowe informacje na temat tworzenia niestandardowego powiązania, zobacz [Jak: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Przed zastosowaniem dowolnej z tych opcji należy zapoznać się z wymaganiami dotyczącymi zabezpieczeń aplikacji.  
  
<a name="BKMK_q2"></a>
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a>Moja usługa zaczyna odrzucać nowych klientów po tym, jak około 10 klientów wchodzi z nią w interakcję. Co się dzieje?  
 Domyślnie usługi mogą mieć tylko 10 równoczesnych sesji. W związku z tym jeśli powiązania usługi używać sesji, usługa akceptuje nowe połączenia klienta, dopóki nie osiągnie tego numeru, po czym odrzuca nowe połączenia klienta, aż do zakończenia jednej z bieżących sesji. Możesz obsługiwać więcej klientów na wiele sposobów. Jeśli usługa nie wymaga sesji, nie należy używać powiązania sesyjnego. (Aby uzyskać więcej informacji, zobacz [Korzystanie z sesji](using-sessions.md).) Inną opcją jest zwiększenie limitu sesji poprzez <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> zmianę wartości właściwości na liczbę odpowiednią do danego okoliczności.  
  
<a name="BKMK_q3"></a>
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a>Czy mogę załadować konfigurację usługi z innego miejsca niż plik konfiguracyjny aplikacji WCF?  
 Tak, jednak należy utworzyć klasę <xref:System.ServiceModel.ServiceHost> niestandardową, która <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> zastępuje metodę. Wewnątrz tej metody można wywołać podstawowej do obciążenia konfiguracji pierwszy (jeśli chcesz załadować standardowe informacje o konfiguracji, jak również), ale można również całkowicie zastąpić system ładowania konfiguracji. Jeśli chcesz załadować konfigurację z pliku konfiguracyjnego, który różni się od pliku konfiguracji aplikacji, należy przeanalizować plik konfiguracyjny samodzielnie i załadować konfigurację.  
  
 Poniższy przykład kodu pokazuje, jak <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> zastąpić metodę i bezpośrednio skonfigurować punkt końcowy.  
  
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
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a>Moja usługa i klient działają świetnie, ale nie mogę ich do pracy, gdy klient jest na innym komputerze? Co się dzieje?  
 W zależności od wyjątku może istnieć kilka problemów:  
  
- Może być konieczna zmiana adresów punktu końcowego klienta na nazwę hosta, a nie na "localhost".  
  
- Może być konieczne otwarcie portu do aplikacji. Aby uzyskać szczegółowe informacje, zobacz [Instrukcje zapory](./samples/firewall-instructions.md) z przykładów SDK.  
  
- Aby uzyskać inne możliwe problemy, zobacz temat przykładów [Uruchamianie przykładów fundacji komunikacji systemu Windows](./samples/running-the-samples.md).  
  
- Jeśli klient używa poświadczeń systemu <xref:System.ServiceModel.Security.SecurityNegotiationException>Windows, a wyjątkiem jest , skonfigurować protokół Kerberos w następujący sposób.  
  
    1. Dodaj poświadczenia tożsamości do elementu punktu końcowego w pliku App.config klienta:  
  
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
  
    2. Uruchom usługę hostowania samodzielnie na koncie System lub NetworkService. To polecenie można uruchomić, aby utworzyć okno polecenia w obszarze konto systemowe:  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3. Hostuj usługę w obszarze internetowe usługi informacyjne (IIS), która domyślnie używa konta głównej nazwy usługi (SPN).  
  
    4. Zarejestruj nową nazwę SPN w domenie przy użyciu SetSPN. Aby to zrobić, musisz być administratorem domeny.  
  
 Aby uzyskać więcej informacji na temat protokołu Kerberos, zobacz [Pojęcia zabezpieczeń używane w WCF](./feature-details/security-concepts-used-in-wcf.md) i:  
  
- [Debugowanie błędów uwierzytelniania systemu Windows](./feature-details/debugging-windows-authentication-errors.md)  
  
- [Rejestrowanie głównych nazw usługi Kerberos przy użyciu protokołu Http.sys](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms178119(v=sql.105))  
  
- [Objaśnienie protokołu Kerberos](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742516(v%3dtechnet.10))  
  
<a name="BKMK_q5"></a>
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a>Gdy zgłaszam Exception FaultException\<>, w którym typ jest wyjątkiem, zawsze otrzymuję ogólny typ FaultException na kliencie, a nie typ ogólny. Co się dzieje?  
 Zdecydowanie zaleca się utworzenie własnego typu danych błędu niestandardowego i zadeklarowanie tego jako typu szczegółów w umowie z błędami. Powodem jest to, że przy użyciu typów wyjątków dostarczonych przez system:  
  
- Tworzy zależność typu, która usuwa jedną z największych zalet aplikacji zorientowanych na usługi.  
  
- Nie może zależeć od wyjątków serializacji w standardowy sposób. Niektóre — <xref:System.Security.SecurityException>jak — mogą nie być serializable w ogóle.  
  
- Udostępnia klientom szczegóły implementacji wewnętrznej. Aby uzyskać więcej informacji, zobacz [Określanie i obsługa usterek w umowach i usługach](specifying-and-handling-faults-in-contracts-and-services.md).  
  
 Jeśli debugowanie aplikacji, jednak można serializować informacje o wyjątku i <xref:System.ServiceModel.Description.ServiceDebugBehavior> zwrócić je do klienta przy użyciu klasy.  
  
<a name="BKMK_q6"></a>
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a>Wydaje się, że operacje jednokierunkowe i żądanie odpowiedzi zwracają z grubszą taką samą prędkością, gdy odpowiedź nie zawiera żadnych danych. Co się dzieje?  
 Określenie, że operacja jest jednym ze sposobów oznacza tylko, że umowa operacji akceptuje komunikat wejściowy i nie zwraca komunikatu wyjściowego. W WCF wszystkie wywołania klienta zwracają, gdy dane wychodzące zostały zapisane w sieci lub zostanie zgłoszony wyjątek. Operacje jednokierunkowe działają w ten sam sposób i mogą zgłosić, jeśli usługa nie może być zlokalizowana lub zablokowana, jeśli usługa nie jest przygotowana do zaakceptowania danych z sieci. Zazwyczaj w WCF powoduje to jednokierunkowe wywołania zwrotne do klienta szybciej niż żądanie odpowiedzi; ale każdy warunek, który spowalnia wysyłanie danych wychodzących przez sieć spowalnia operacje jednokierunkowe, a także operacje żądania odpowiedzi. Aby uzyskać więcej informacji, zobacz [Usługi jednokierunkowe](./feature-details/one-way-services.md) i [uzyskiwanie dostępu do usług przy użyciu klienta WCF](./feature-details/accessing-services-using-a-client.md).  
  
<a name="BKMK_q77"></a>
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a>Używam certyfikatu X.509 z moją usługą i otrzymuję system.Security.Cryptography.CryptographicException. Co się dzieje?  
 Dzieje się tak często po zmianie konta użytkownika, w ramach którego działa proces roboczy IIS. Na przykład w systemie Windows XP, jeśli zmienisz domyślne konto użytkownika, które Aspnet_wp.exe działa w obszarze z ASPNET do niestandardowego konta użytkownika, może pojawić się ten błąd. Jeśli używasz klucza prywatnego, proces, który go używa, będzie musiał mieć uprawnienia dostępu do pliku przechowującego ten klucz.  
  
 W takim przypadku należy przyznać uprawnienia dostępu do odczytu do konta procesu dla pliku zawierającego klucz prywatny. Na przykład jeśli proces roboczy usługi IIS jest uruchomiony na koncie Roberta, należy przyznać Robertowi dostęp do odczytu do pliku zawierającego klucz prywatny.  
  
 Aby uzyskać więcej informacji na temat udzielania poprawnego dostępu do pliku zawierającego klucz prywatny dla określonego certyfikatu X.509, zobacz [Jak: Udostępnić certyfikaty X.509 WCF](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).  
  
<a name="BKMK_q88"></a>
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a>Zmieniłem pierwszy parametr operacji z wielkich na małe; teraz mój klient zgłasza wyjątek. Co się dzieje?  
 Wartości nazw parametrów w podpisie operacji są częścią umowy i są rozróżniane. Użyj <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> atrybutu, gdy trzeba odróżnić nazwę parametru lokalnego i metadanych, które opisuje operację dla aplikacji klienckich.  
  
<a name="BKMK_q99"></a>
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a>Używam jednego z moich narzędzi śledzenia i otrzymuję EndpointNotFoundException. Co się dzieje?  
 Jeśli używasz narzędzia śledzenia, który nie jest mechanizm śledzenia WCF dostarczonych przez system i <xref:System.ServiceModel.EndpointNotFoundException> otrzymasz, który wskazuje, że <xref:System.ServiceModel.Description.ClientViaBehavior> nie było niezgodności filtru adresu, należy użyć klasy, aby skierować wiadomości do narzędzia śledzenia i narzędzie przekierowanie tych wiadomości do adresu usługi. Klasa <xref:System.ServiceModel.Description.ClientViaBehavior> zmienia nagłówek `Via` adresowania, aby określić następny adres sieciowy oddzielnie `To` od odbiornika końcowego, wskazywany przez nagłówek adresowania. Podczas wykonywania tej pracy, jednak nie należy zmieniać adres punktu `To` końcowego, który jest używany do ustalenia wartości.  
  
 Poniższy przykładowy kod przedstawia przykładowy plik konfiguracji klienta.  
  
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
 Adres podstawowy jest adresem głównym <xref:System.ServiceModel.ServiceHost> klasy. Domyślnie po dodaniu <xref:System.ServiceModel.Description.ServiceMetadataBehavior> klasy do konfiguracji usługi język opisu usług sieci Web (WSDL) dla wszystkich punktów końcowych publikowanych przez hosta są pobierane z adresu podstawowego HTTP, a także dowolny adres względny podany do zachowania metadanych oraz "?wsdl". Jeśli znasz ASP.NET i usług IIS, adres podstawowy jest odpowiednikiem katalogu wirtualnego.  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a>Udostępnianie portu między punktem końcowym usługi a punktem końcowym mex przy użyciu nettcpbinding  
 Jeśli określisz adres podstawowy usługi jako net.tcp://MyServer:8080/MyService i dodasz następujące punkty końcowe:  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 A jeśli zmodyfikujesz jedno z ustawień NetTcpBinding, jak pokazano w poniższym fragmentie konfiguracji:  
  
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
  
 Zostanie wyświetlony błąd podobny do następującego: Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: Istnieje już odbiornik w punkcie końcowym IP 0.0.0.0:9000 Można obejść ten błąd, określając w pełni kwalifikowany adres URL z innym portem punktu końcowego MEX, jak pokazano w poniższym urywek konfiguracji:  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a>Podczas wywoływania aplikacji WCF Web HTTP z aplikacji WCF SOAP usługa zwraca następujący błąd: 405 Metoda niedozwolona  
 Wywołanie aplikacji <xref:System.ServiceModel.WebHttpBinding> WCF Web HTTP (usługa, <xref:System.ServiceModel.Description.WebHttpBehavior>która używa i ) z usługi ``Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.`` WCF może wygenerować następujący <xref:System.ServiceModel.OperationContext> wyjątek: Ten wyjątek występuje, ponieważ WCF zastępuje wychodzące z przychodzącym <xref:System.ServiceModel.OperationContext>. Aby rozwiązać ten problem, należy utworzyć <xref:System.ServiceModel.OperationContextScope> w ramach WCF Web HTTP operacji usługi. Przykład:  
  
```csharp
public string Echo(string input)  
{  
    using (new OperationContextScope(this.InnerChannel))  
    {  
        return base.Channel.Echo(input);  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie błędów uwierzytelniania systemu Windows](./feature-details/debugging-windows-authentication-errors.md)
