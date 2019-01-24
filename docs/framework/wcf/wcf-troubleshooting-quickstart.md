---
title: 'Szybki start: rozwiązywanie problemów z architekturą WCF'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: 5031538c49da34d0fc89442c1170e30ff56a6eff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505695"
---
# <a name="wcf-troubleshooting-quickstart"></a>Szybki start: rozwiązywanie problemów z architekturą WCF
W tym temacie wymieniono znane problemy, których klienci mają wystąpiły podczas tworzenia usług WCF klientów i usług. Jeśli ten problem, który zostały przekroczone nie ma na tej liście, zalecamy Konfigurowanie śledzenia dla Twojej usługi. Spowoduje to wygenerowanie pliku śledzenia można wyświetlić w podglądzie pliku śledzenia i uzyskać szczegółowe informacje dotyczące wyjątków, które mogą mieć miejsce w ramach usługi. Aby uzyskać więcej informacji na temat konfigurowania śledzenia zobacz: [Konfigurowanie śledzenia](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md). Aby uzyskać więcej informacji na temat przeglądarka plików śledzenia zobacz: [Usługa Trace Viewer Tool (SvcTraceViewer.exe)](../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
1.  [Po zainstalowaniu, Windows 7 i IIS, gdy próbuję przejdź do usługi WCF pojawia się następujący komunikat o błędzie: Błąd HTTP 404.3 — nie znaleziono](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#bkmk_0)  
  
     Błąd HTTP 404.3 — nie nie może zostać wyświetlona strona FoundThe żądasz, ze względu na konfigurację rozszerzenia. Jeśli strona znajduje się skrypt, należy dodać program obsługi. Jeśli plik powinny być pobierane, Dodaj mapowanie MIME. InformationModule StaticFileModule szczegółowy komunikat o błędzie.  
  
2.  [Czasami pojawia się messagesecurityexception — na drugie żądanie Jeśli mojego klienta jest w stanie bezczynności przez jakiś czas, po pierwszym żądaniu. Co się dzieje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q1)  
  
3.  [Moja usługa zaczyna odrzucać nowych klientów po około 10 klientów wchodzą w interakcje z nią. Co się dzieje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q2)  
  
4.  [W innym miejscu niż plik konfiguracji aplikacji WCF można załadować konfiguracji mojej usługi?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q3)  
  
5.  [Moja usługa i klient świetnie współpracują, ale nie można pobrać ich pracę, gdy klient znajduje się na innym komputerze? Co się dzieje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q4)  
  
6.  [Kiedy mogę zgłosić FaultException —\<wyjątku > w przypadku, gdy typ jest wyjątek, czy mogę otrzymać typem ogólnym FaultException — na komputerze klienckim i typu ogólnego. Co się dzieje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q5)  
  
7.  [Wydaje się, jak jednokierunkowe, a operacje "żądanie-odpowiedź" zwracają przybliżeniu z taką samą szybkością, gdy odpowiedź nie zawiera żadnych danych. Co się dzieje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q6)  
  
8.  [Używam certyfikatu X.509 przy użyciu usługi i uzyskać System.Security.Cryptography.CryptographicException. Co się dzieje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q77)  
  
9. [Pierwszy parametr operację po zmianie z wielkie litery na małe litery; teraz mojego klienta zgłasza wyjątek. Co się dzieje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q88)  
  
10. [Używam Moje narzędzia śledzenia i uzyskać endpointnotfoundexception —. Co się dzieje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q99)  
  
11. [Podczas wywoływania aplikacji WCF Web HTTP z aplikacji WCF SOAP usługa zwraca następujący błąd: Metoda 405 nie jest dozwolona](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BK_MK99)  
  
 [Co to jest adres podstawowy? Jaki związek między adres punktu końcowego?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q10)  
  
<a name="bkmk_0"></a>   
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a>Po zainstalowaniu, Windows 7 i IIS, gdy próbuję przejdź do usługi WCF pojawia się następujący komunikat o błędzie: Błąd HTTP 404.3 — nie znaleziono  
 Jest pełną treść błędu:  
  
 Błąd HTTP 404.3 — nie nie może zostać wyświetlona strona FoundThe żądasz, ze względu na konfigurację rozszerzenia. Jeśli strona znajduje się skrypt, należy dodać program obsługi. Jeśli plik powinny być pobierane, Dodaj mapowanie MIME. InformationModule StaticFileModule szczegółowy komunikat o błędzie.  
  
 Ten błąd występuje, gdy "Windows Communication Foundation Aktywacja HTTP" nie jest jawnie ustawiona w Panelu sterowania. Aby ustawić przejdź do panelu sterowania, kliknij polecenie Programy, w dolnym lewym dolnym rogu okna. Kliknij funkcje Windows włączyć lub wyłączyć. Rozwiń węzeł Microsoft .NET Framework 3.5.1, a następnie wybierz pozycję Aktywacja HTTP programu Windows Communication Foundation.  
  
<a name="BKMK_q1"></a>   
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a>Czasami pojawia się messagesecurityexception — na drugie żądanie Jeśli mojego klienta jest w stanie bezczynności przez jakiś czas, po pierwszym żądaniu. Co się dzieje?  
 Drugie żądanie może zakończyć się niepowodzeniem głównie dwóch powodów: (1 upłynął limit czasu sesji lub (2 serwera sieci Web, który jest hostem usługi zostanie odtworzona. W pierwszym przypadku sesja jest nieprawidłowa, dopóki nie upłynie limit czasu usługi. Gdy usługa nie otrzyma żądanie od klienta przed upływem czasu określonej w powiązaniu usługi (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), usługa kończy się sesja zabezpieczeń. Kolejne komunikaty spowodować <xref:System.ServiceModel.Security.MessageSecurityException>. Klient musi ponownie ustanowić bezpiecznej sesji przy użyciu usługi do wysyłania komunikatów w przyszłości lub użyj tokenu kontekstu zabezpieczeń stanowych. Tokeny kontekstu zabezpieczeń stanową również umożliwiać bezpiecznej sesji przetrwać serwer sieci Web z odtwarzania. Aby uzyskać więcej informacji na temat w ramach bezpiecznej sesji przy użyciu tokenów stanowych bezpiecznym kontekście zobacz [jak: Utwórz kontekst zabezpieczeń tokenu dla bezpiecznej sesji](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md). Alternatywnie możesz wyłączyć bezpiecznej sesji. Kiedy używać [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) powiązania, można ustawić `establishSecurityContext` właściwości `false` do wyłączanie bezpiecznej sesji. Aby wyłączanie bezpiecznej sesji w przypadku innych powiązań, należy utworzyć niestandardowego powiązania. Aby uzyskać szczegółowe informacje na temat tworzenia niestandardowego powiązania, zobacz [jak: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Przed możesz zastosować żadnej z tych opcji, należy zrozumieć wymagania dotyczące zabezpieczeń aplikacji.  
  
<a name="BKMK_q2"></a>   
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a>Moja usługa zaczyna odrzucać nowych klientów po około 10 klientów wchodzą w interakcje z nią. Co się dzieje?  
 Domyślnie usługi może mieć tylko 10 równoczesnych sesji. W związku z tym użycie sesje, powiązania usługi usługi akceptować nowe połączenia klientów, dopóki nie osiągnie tę liczbę, po upływie którego odrzuca nowe połączenia klientów aż jeden z końców bieżące sesje. Większej liczby klientów może obsługiwać wiele sposobów. Jeśli usługa nie wymaga sesji, należy używać powiązania sesji. (Aby uzyskać więcej informacji, zobacz [przy użyciu sesji](../../../docs/framework/wcf/using-sessions.md).) Innym rozwiązaniem jest zwiększenie limitu czasu sesji, zmieniając wartość <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> liczbę odpowiednie do swojej sytuacji.  
  
<a name="BKMK_q3"></a>   
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a>W innym miejscu niż plik konfiguracji aplikacji WCF można załadować konfiguracji mojej usługi?  
 Tak, można jednak utworzyć niestandardową <xref:System.ServiceModel.ServiceHost> klasę, która zastępuje <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> metody. Wewnątrz tej metody można wywołać podstawy, aby najpierw załadować konfiguracji (Jeśli chcesz ładuje te informacje konfiguracji standardowej), ale możesz również całkowicie zastąpić konfiguracji ładowania systemu. Należy pamiętać, że jeśli chcesz załadować konfiguracji z pliku konfiguracji, który różni się od pliku konfiguracji aplikacji, musisz samodzielnie przeanalizować pliku konfiguracji i załadować konfiguracji.  
  
 Poniższy przykład kodu przedstawia sposób przesłonięcia <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> metody i bezpośredniego konfigurowania punktu końcowego.  
  
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
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a>Moja usługa i klient świetnie współpracują, ale nie można pobrać ich pracę, gdy klient znajduje się na innym komputerze? Co się dzieje?  
 W zależności od wyjątek, może istnieć kilka problemów:  
  
-   Konieczne może się zmienić adresy punktów końcowych klienta na nazwę hosta, a nie "localhost".  
  
-   Może być konieczne otwarcie portu do aplikacji. Aby uzyskać więcej informacji, zobacz [instrukcje dotyczące zapory](../../../docs/framework/wcf/samples/firewall-instructions.md) z przykładowych zestawach SDK.  
  
-   W przypadku pozostałych możliwych problemów, zobacz temat przykłady [uruchamianie przykładów programu w grupie roboczej dla maszyn](https://msdn.microsoft.com/library/a451a525-e7ce-452d-9da9-620221260113).  
  
-   Jeśli klient korzysta z poświadczeń Windows, a wyjątek stanowi <xref:System.ServiceModel.Security.SecurityNegotiationException>, konfigurowanie protokołu Kerberos w następujący sposób.  
  
    1.  Dodaj poświadczenia tożsamości do elementu punktu końcowego w pliku App.config klienta:  
  
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
  
    2.  Uruchom usługę samodzielnie hostowane na koncie systemu lub Usługa sieciowa. Można uruchomić to polecenie, aby utworzyć okno polecenia przy użyciu konta systemowego:  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3.  Hostowanie usługi w obszarze Internet Information Services (IIS), która domyślnie używa konta usługi głównej nazwy (usługi SPN).  
  
    4.  Zarejestruj nowy SPN w domenie za pomocą narzędzia SetSPN. Należy pamiętać, że musisz być administratorem domeny, aby to zrobić.  
  
 Aby uzyskać więcej informacji na temat protokołu Kerberos, zobacz [użyte pojęcia dotyczące zabezpieczeń dla programu WCF](../../../docs/framework/wcf/feature-details/security-concepts-used-in-wcf.md) oraz:  
  
-   [Debugowanie błędów uwierzytelniania systemu Windows](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
  
-   [Zarejestrowanie nazwy głównej usługi Kerberos za pomocą Http.sys](https://go.microsoft.com/fwlink/?LinkId=86943)  
  
-   [Wyjaśniono protokołu Kerberos](https://go.microsoft.com/fwlink/?LinkId=86946)  
  
<a name="BKMK_q5"></a>   
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a>Kiedy mogę zgłosić FaultException —\<wyjątku > w przypadku, gdy typ jest wyjątek, czy mogę otrzymać typem ogólnym FaultException — na komputerze klienckim i typu ogólnego. Co się dzieje?  
 Zdecydowanie zaleca się utworzenie własnych błąd niestandardowy typ danych i zadeklarować, że jako typ szczegółów w kontrakcie usługi błędów. Przyczyną jest fakt, że przy użyciu typów wyjątków dostarczane przez system:  
  
-   Tworzy zależność typu, która usuwa jeden z największych zalet aplikacji usługowych.  
  
-   Nie zależą od wyjątki serializacji w sposób standardowy. Niektóre — takich jak <xref:System.Security.SecurityException>— może nie być możliwe do serializacji w ogóle.  
  
-   Przedstawia szczegóły wewnętrznej implementacji do klientów. Aby uzyskać więcej informacji, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
 Jeśli debugujesz aplikację, jednak można serializować informacje o wyjątku i przywrócić go do klienta przy użyciu <xref:System.ServiceModel.Description.ServiceDebugBehavior> klasy.  
  
<a name="BKMK_q6"></a>   
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a>Wydaje się, jak jednokierunkowe, a operacje "żądanie-odpowiedź" zwracają przybliżeniu z taką samą szybkością, gdy odpowiedź nie zawiera żadnych danych. Co się dzieje?  
 Określanie, czy operacja jest jednym ze sposobów oznacza tylko, że kontrakt operacji akceptuje komunikat wejściowy, a nie zwróci komunikatu wyjściowego. W programie WCF wszystkie wywołania klienta zwracać danych wychodzących został zapisany podczas transmisji lub zostanie zgłoszony wyjątek. Operacje jednokierunkowe działają tak samo, a ich throw, jeśli usługa nie można zlokalizować lub zablokować, jeśli usługa nie jest przygotowana na akceptowanie danych z sieci. Zwykle w programie WCF, powoduje to jednokierunkowe wywołania zwróceniem do klienta znacznie szybciej niż żądanie odpowiedź; ale dowolny warunek, który spowalnia wysyłania danych wychodzących przez sieć spowalnia operacje jednokierunkowe, a także operacji żądanie odpowiedź. Aby uzyskać więcej informacji, zobacz [usług One-Way](../../../docs/framework/wcf/feature-details/one-way-services.md) i [uzyskiwanie dostępu do usług za pomocą klienta WCF](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
<a name="BKMK_q77"></a>   
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a>Używam certyfikatu X.509 przy użyciu usługi i uzyskać System.Security.Cryptography.CryptographicException. Co się dzieje?  
 Zwykle dzieje się tak po zmianie konta użytkownika, pod którym uruchamia proces roboczy usług IIS. Na przykład w [!INCLUDE[wxp](../../../includes/wxp-md.md)], jeśli zmienisz Aspnet_wp.exe jest uruchamiane w ramach ASPNET kontu użytkownika niestandardowego domyślne konto użytkownika, zostanie wyświetlony ten błąd. Jeśli przy użyciu klucza prywatnego, proces, który korzysta z niego musisz mieć uprawnienia dostępu do tego pliku, przechowywanie tego klucza.  
  
 Jest to możliwe, należy nadać uprawnienia dostępu do odczytu do konta przez proces plik zawierający klucz prywatny. Na przykład jeśli proces roboczy usług IIS jest uruchomiony na koncie Roberta, należy udzielić dostępu Odczyt Roberta do pliku zawierającego klucz prywatny.  
  
 Aby uzyskać więcej informacji o tym, jak udzielić dostępu konta odpowiednich użytkowników do pliku który zawiera klucz prywatny dla określonego certyfikatu X.509, zobacz [jak: Udostępnianie certyfikatów X.509 w architekturze WCF](../../../docs/framework/wcf/feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).  
  
<a name="BKMK_q88"></a>   
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a>Pierwszy parametr operację po zmianie z wielkie litery na małe litery; teraz mojego klienta zgłasza wyjątek. Co się dzieje?  
 Wartość nazwy parametrów w podpisie operacji są częścią kontraktu i jest rozróżniana wielkość liter. Użyj <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> atrybutu, gdy trzeba odróżnić nazwy parametrów lokalnych i metadanych, który opisuje operacji dla aplikacji klienckich.  
  
<a name="BKMK_q99"></a>   
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a>Używam Moje narzędzia śledzenia i uzyskać endpointnotfoundexception —. Co się dzieje?  
 Jeśli używasz narzędzia śledzenia, który nie jest mechanizm śledzenia WCF dostarczane przez system i zostanie wyświetlony <xref:System.ServiceModel.EndpointNotFoundException> oznacza to, że wystąpiła niezgodność filtr adresów, należy użyć <xref:System.ServiceModel.Description.ClientViaBehavior> klasy do przekierowywania komunikatów do narzędzia śledzenia i ma narzędzie przekierować te komunikaty do adresu usługi. <xref:System.ServiceModel.Description.ClientViaBehavior> Zmienia klasy `Via` adresowania nagłówka do określania adresu następnego sieci, niezależnie od odbiorcy ultimate, wskazywanym przez `To` adresowania nagłówka. W ten sposób, jednak nie należy zmieniać adresu punktu końcowego, który jest używany do ustanawiania `To` wartość.  
  
 Poniższy przykład kodu pokazuje przykład klienta pliku konfiguracji.  
  
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
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a>Co to jest adres podstawowy? Jaki związek między adres punktu końcowego?  
 Adres podstawowy jest główny adres <xref:System.ServiceModel.ServiceHost> klasy. Domyślnie, jeśli dodasz <xref:System.ServiceModel.Description.ServiceMetadataBehavior> klasy do konfiguracji usługi sieci Web Services Description Language (WSDL) dla wszystkich punktów końcowych, publikuje hosta są pobierane z podstawowy adres HTTP, a także wszelkie adres względny dostarczane z zachowaniem metadanych oraz "? wsdl". Jeśli znasz [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] i IIS, adres podstawowy jest równoważne do katalogu wirtualnego.  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a>Udostępnianie portów między punktu końcowego usługi i punktu końcowego mex przy użyciu NetTcpBinding  
 Jeśli określisz adres podstawowy usługi jako net.tcp://MyServer: 8080/Moja_usługa i dodać następujących punktów końcowych:  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 A Jeśli zmodyfikujesz jedno z ustawień NetTcpBinding jak pokazano w poniższym fragmencie kodu konfiguracji:  
  
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
  
 Zostanie wyświetlony błąd taki jak następujące: Nieobsługiwany wyjątek: System.ServiceModel.AddressAlreadyInUseException: Jest już odbiornik na 0.0.0.0:9000 punktu końcowego adresu IP, który można obejść ten błąd, określając w pełni kwalifikowanym adresem URL za pomocą innego portu dla punktu końcowego MEX, jak pokazano w poniższym fragmencie kodu konfiguracji:  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>   
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a>Podczas wywoływania aplikacji WCF Web HTTP z aplikacji WCF SOAP usługa zwraca następujący błąd: Metoda 405 nie jest dozwolona  
 Wywołanie aplikacji protokołu HTTP sieci Web WCF (usługa, która wykorzystuje <xref:System.ServiceModel.WebHttpBinding> i <xref:System.ServiceModel.Description.WebHttpBehavior>) z platformy WCF service mogą generować następujący wyjątek: `Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: Serwer zdalny zwrócił nieoczekiwaną odpowiedź: (405) metoda nie dozwolone. "ten wyjątek jest spowodowany WCF zastępuje wychodzącej <xref:System.ServiceModel.OperationContext> z przychodzącego <xref:System.ServiceModel.OperationContext>. Aby rozwiązać ten problem utworzyć <xref:System.ServiceModel.OperationContextScope> w ramach operacji usługi WCF Web HTTP. Na przykład:  
  
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
- [Debugowanie błędów uwierzytelniania systemu Windows](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)
