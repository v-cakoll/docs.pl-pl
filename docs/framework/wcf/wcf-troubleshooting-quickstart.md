---
title: 'Szybki start: rozwiązywanie problemów z architekturą WCF'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 490b756a9beae09b20a36d3fc6a20c85aad76618
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="wcf-troubleshooting-quickstart"></a>Szybki start: rozwiązywanie problemów z architekturą WCF
W tym temacie zamieszczono listę znanych problemów, które klienci mają uruchamiać do podczas opracowywania WCF klientów i usług. Jeśli problem, którego używasz do nie jest na liście, zaleca się Konfiguruj śledzenie dla usługi. Spowoduje to wygenerowanie pliku śledzenia można wyświetlić podgląd pliku śledzenia i uzyskać szczegółowe informacje dotyczące wyjątków, który może być przeprowadzana w ramach usługi. Aby uzyskać więcej informacji na temat konfigurowania śledzenia, zobacz: [Konfigurowanie śledzenia](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md). Aby uzyskać więcej informacji na przeglądarka plików śledzenia, zobacz: [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
1.  [Po zainstalowaniu systemu Windows 7 i IIS, gdy próbuję przejdź do usługi WCF pojawia się następujący komunikat o błędzie: HTTP Błąd 404.3 — nie znaleziono](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#bkmk_0)  
  
     Błąd HTTP 404.3 — nie żądanej strony FoundThe nie może zostać wyświetlona z powodu konfiguracji rozszerzenia. Jeśli strona jest skryptem, Dodaj program obsługi. Jeśli plik powinien zostać pobrany, Dodaj mapowanie MIME. Szczegółowe informacje o błędzie InformationModule StaticFileModule.  
  
2.  [Czasami pojawia się messagesecurityexception — na drugie żądanie Jeśli mój klient bezczynności przez pewien czas po wykonaniu pierwszego żądania. Co się dzieje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q1)  
  
3.  [Moja usługa jest uruchamiana do odrzucania nowych klientów po około 10 klientów są interakcję z nią. Co się dzieje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q2)  
  
4.  [Czy można załadować Moje konfiguracji usługi, w innym miejscu niż pliku konfiguracji aplikacji WCF?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q3)  
  
5.  [Moje usługi i doskonałym pracy klienta, ale nie można pobrać im pracę, gdy klient znajduje się na innym komputerze? Co się dzieje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q4)  
  
6.  [Gdy I zgłoszenie wyjątku FaultException\<wyjątku > Typ w przypadku wyjątku, wyświetlany jest zawsze ogólne typu wyjątku FaultException na kliencie, a nie typu ogólnego. Co się dzieje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q5)  
  
7.  [Wydaje się, jak jednokierunkowe i operacji żądanie odpowiedź zwracanie w przybliżeniu szybkości odpowiedzi nie zawiera żadnych danych. Co się dzieje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q6)  
  
8.  [Używam certyfikat X.509 z mojej usługi i uzyskać System.Security.Cryptography.CryptographicException. Co się dzieje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q77)  
  
9. [Pierwszy parametr operację po zmianie wielkie na małe litery; teraz moje klienta zgłasza wyjątek. Co się dzieje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q88)  
  
10. [Używam Moje śledzenia narzędzia i uzyskać endpointnotfoundexception —. Co się dzieje?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q99)  
  
11. [Podczas wywoływania aplikacji protokołu HTTP sieci Web WCF z aplikacji WCF SOAP usługi zwraca następujący błąd: niedozwolone 405 — metoda](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BK_MK99)  
  
 [Co to jest adres podstawowy? Jaki związek między adres punktu końcowego?](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q10)  
  
<a name="bkmk_0"></a>   
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a>Po zainstalowaniu systemu Windows 7 i IIS, gdy próbuję przejdź do usługi WCF pojawia się następujący komunikat o błędzie: HTTP Błąd 404.3 — nie znaleziono  
 Jest pełny komunikat o błędzie:  
  
 Błąd HTTP 404.3 — nie żądanej strony FoundThe nie może zostać wyświetlona z powodu konfiguracji rozszerzenia. Jeśli strona jest skryptem, Dodaj program obsługi. Jeśli plik powinien zostać pobrany, Dodaj mapowanie MIME. Szczegółowe informacje o błędzie InformationModule StaticFileModule.  
  
 Ten błąd występuje, gdy "Windows Communication Foundation Aktywacja HTTP" nie jest jawnie ustawiona w Panelu sterowania. Aby ustawić przejdź do panelu sterowania, kliknij polecenie programy w dolnym lewym dolnym rogu okna. Kliknij przycisk Włącz funkcje systemu Windows lub wyłączyć. Rozwiń węzeł systemu Microsoft .NET Framework 3.5.1, a następnie wybierz Aktywacja HTTP programu Windows Communication Foundation.  
  
<a name="BKMK_q1"></a>   
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a>Czasami pojawia się messagesecurityexception — na drugie żądanie Jeśli mój klient bezczynności przez pewien czas po wykonaniu pierwszego żądania. Co się dzieje?  
 Drugie żądanie może zakończyć się niepowodzeniem głównie z dwóch przyczyn: Upłynął limit czasu sesji (1 lub (2 serwera sieci Web, który jest hostem usługi zostanie odtworzony. W pierwszym przypadku sesji jest prawidłowa, dopóki nie upłynie limit czasu usługi. Jeśli usługa nie otrzyma żądanie od klienta w określonym przedziale czasu określony w powiązaniu usługi (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), usługa kończy sesji zabezpieczeń. Powoduje klientów kolejnych komunikatów <xref:System.ServiceModel.Security.MessageSecurityException>. Klient musi ponownie ustanowić bezpiecznej sesji z usługą, aby wysyłać przyszłych lub użyj token kontekstu zabezpieczeń stanowych. Tokenów kontekstów zabezpieczeń stanową również umożliwić bezpiecznej sesji na serwerze sieci Web odtwarzane przetrwanie. [!INCLUDE[crabout](../../../includes/crabout-md.md)] w ramach bezpiecznej sesji przy użyciu tokenów kontekstów bezpiecznego stanowe, zobacz [porady: Tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md). Alternatywnie możesz wyłączyć bezpiecznej sesji. Jeśli używasz [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) powiązanie, można ustawić `establishSecurityContext` właściwości `false` wyłączyć bezpiecznej sesji. Aby wyłączyć bezpiecznej sesji dla pozostałych powiązaniach, należy utworzyć niestandardowego powiązania. Aby uzyskać więcej informacji o tworzeniu niestandardowego powiązania, zobacz [porady: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). Przed zastosowaniem dowolnej z tych opcji, należy zrozumieć wymagania dotyczące zabezpieczeń aplikacji.  
  
<a name="BKMK_q2"></a>   
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a>Moja usługa jest uruchamiana do odrzucania nowych klientów po około 10 klientów są interakcję z nią. Co się dzieje?  
 Domyślnie usługi może mieć tylko 10 równoczesnych sesji. W związku z tym powiązania usługi użycie sesji usługi akceptować nowe połączenia klientów, dopóki nie osiągnie ten numer, po upływie którego odrzuca nowe połączenia klientów do jednego z końców bieżących sesji. Większej liczby klientów może obsługiwać wiele sposobów. Jeśli usługa nie wymaga sesji, nie należy używać powiązania sesyjnych. (Aby uzyskać więcej informacji, zobacz [sesji przy użyciu](../../../docs/framework/wcf/using-sessions.md).) Można zwiększyć, zmieniając wartość limitu czasu sesji <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> właściwości do liczby całkowitej odpowiednią dla Twojego okoliczności.  
  
<a name="BKMK_q3"></a>   
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a>Czy można załadować Moje konfiguracji usługi, w innym miejscu niż pliku konfiguracji aplikacji WCF?  
 Tak, jednak należy utworzyć niestandardowego <xref:System.ServiceModel.ServiceHost> klasy, która zastępuje <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> metody. Wewnątrz tej metody należy wywołać base najpierw załadować konfiguracji (Jeśli chcesz załadować standardowe informacje o konfiguracji również), ale można również całkowicie zastąpić konfiguracji ładowania systemu. Należy pamiętać, że jeśli chcesz załadować konfiguracji z pliku konfiguracji, który różni się od pliku konfiguracji aplikacji, należy przeanalizować pliku konfiguracji użytkownika i załadować konfiguracji.  
  
 Poniższy przykładowy kod przedstawia sposób przesłonięcia <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> — metoda i bezpośrednio Skonfiguruj punkt końcowy.  
  
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
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a>Moje usługi i doskonałym pracy klienta, ale nie można pobrać im pracę, gdy klient znajduje się na innym komputerze? Co się dzieje?  
 W zależności od wyjątek, może istnieć kilka problemów:  
  
-   Może być konieczna zmiana adresy punktów końcowych klienta na nazwę hosta, a nie "localhost".  
  
-   Może być konieczne otwarcie portu używanego do aplikacji. Aby uzyskać więcej informacji, zobacz [instrukcje dotyczące zapory](../../../docs/framework/wcf/samples/firewall-instructions.md) z próbek zestawu SDK.  
  
-   W przypadku innych możliwych problemów, zobacz temat przykłady [uruchamiania przykładów w grupie roboczej przez maszyny](http://msdn.microsoft.com/library/a451a525-e7ce-452d-9da9-620221260113).  
  
-   Jeśli klient korzysta z poświadczeń systemu Windows i jest wyjątek <xref:System.ServiceModel.Security.SecurityNegotiationException>, skonfiguruj protokołu Kerberos w następujący sposób.  
  
    1.  Dodaj poświadczenia tożsamości elementu punktu końcowego w pliku App.config klienta:  
  
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
  
    2.  Uruchom usługę siebie na koncie systemu lub NetworkService. Możesz uruchomić to polecenie, aby utworzyć okno polecenia na koncie systemu:  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3.  Host usługi w obszarze Internet Information Services (IIS), która domyślnie używa głównej nazwy (usługi SPN) konta usługi.  
  
    4.  Zarejestruj nowy SPN z domeny za pomocą narzędzia SetSPN. Należy pamiętać, że musisz być administratorem domeny w tym celu.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)] Protokół Kerberos, zobacz [zabezpieczeń pojęcia używane w programie WCF](../../../docs/framework/wcf/feature-details/security-concepts-used-in-wcf.md) oraz:  
  
-   [Debugowanie błędów uwierzytelniania systemu Windows](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
  
-   [Zarejestrowanie nazwy głównej usługi Kerberos za pomocą pliku Http.sys](http://go.microsoft.com/fwlink/?LinkId=86943)  
  
-   [Opis protokołu Kerberos](http://go.microsoft.com/fwlink/?LinkId=86946)  
  
<a name="BKMK_q5"></a>   
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a>Gdy I zgłoszenie wyjątku FaultException\<wyjątku > Typ w przypadku wyjątku, wyświetlany jest zawsze ogólne typu wyjątku FaultException na kliencie, a nie typu ogólnego. Co się dzieje?  
 Zdecydowanie zaleca się utworzenie własnych błąd niestandardowy typ danych i zadeklarować, że jako typ szczegółów umowy błędów. Przyczyną jest to, że przy użyciu typów wyjątków dostarczane przez system:  
  
-   Tworzy zależność typu, która usuwa jeden z największych sile aplikacje zorientowane na usługę.  
  
-   Nie zależą od serializacji w standardowy sposób wyjątków. Niektóre — podobnie jak <xref:System.Security.SecurityException>— może nie być możliwy do serializacji w ogóle.  
  
-   Przedstawia szczegóły implementacji wewnętrzny do klientów. Aby uzyskać więcej informacji, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
 Jeśli debugowania aplikacji, jednak można serializować informacje o wyjątku i przywrócić go do klienta przy użyciu <xref:System.ServiceModel.Description.ServiceDebugBehavior> klasy.  
  
<a name="BKMK_q6"></a>   
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a>Wydaje się, jak jednokierunkowe i operacji żądanie odpowiedź zwracanie w przybliżeniu szybkości odpowiedzi nie zawiera żadnych danych. Co się dzieje?  
 Określanie, czy operacja jest jednym ze sposobów oznacza tylko, że kontrakt operacji akceptuje komunikat wejściowy i nie może zwracać komunikatu wyjściowego. W [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], wszystkich wywołań klientów zwracanie danych wychodzących został zapisany do przesyłania lub jest zgłaszany wyjątek. Operacje jednokierunkowe działają tak samo, a ich zgłoszenie, jeśli usługi nie można zlokalizować lub zablokować, jeśli usługa nie jest przygotowany do akceptowania danych z sieci. Zwykle w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], powoduje to jednokierunkowe wywołania zwracanie szybciej niż żądanie odpowiedź do klienta, ale wszystkie warunek, który spowalnia wysyłania danych wychodzących za pośrednictwem sieci spowalnia operacji jednokierunkowych, a także operacje żądanie odpowiedź. Aby uzyskać więcej informacji, zobacz [usług One-Way](../../../docs/framework/wcf/feature-details/one-way-services.md) i [dostęp do usług za pomocą klienta WCF](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
<a name="BKMK_q77"></a>   
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a>Używam certyfikat X.509 z mojej usługi i uzyskać System.Security.Cryptography.CryptographicException. Co się dzieje?  
 Częstą przyczyną po zmianie konta użytkownika, w którym uruchamia proces roboczy usług IIS. Na przykład w [!INCLUDE[wxp](../../../includes/wxp-md.md)], w przypadku zmiany domyślnego konta użytkownika, Aspnet_wp.exe zgodną z ASPNET na konto użytkownika, zostanie wyświetlony ten błąd. Jeśli przy użyciu klucza prywatnego, proces, który korzysta z niego należy mieć uprawnienia dostępu do pliku przechowywaniu tego klucza.  
  
 Jest to możliwe, należy nadać uprawnienia dostępu do odczytu dla konta procesu plik zawierający klucz prywatny. Na przykład jeśli proces roboczy programu IIS działa na koncie Roberta, następnie konieczne będzie daje Bob dostęp do odczytu pliku zawierającego klucz prywatny.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)] Aby udzielić dostępu konta użytkownika do pliku, który zawiera klucz prywatny dla określonego certyfikatu X.509, zobacz [porady: X.509 certyfikaty Udostępnij do programu WCF](../../../docs/framework/wcf/feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).  
  
<a name="BKMK_q88"></a>   
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a>Pierwszy parametr operację po zmianie wielkie na małe litery; teraz moje klienta zgłasza wyjątek. Co się dzieje?  
 Wartość nazwy parametrów w podpisie operacji są częścią kontraktu i jest rozróżniana wielkość liter. Użyj <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> atrybutu, gdy potrzebne do rozróżniania nazwę parametru lokalnych i metadanych, które opisują operacji dla aplikacji klienckich.  
  
<a name="BKMK_q99"></a>   
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a>Używam Moje śledzenia narzędzia i uzyskać endpointnotfoundexception —. Co się dzieje?  
 Jeśli używasz narzędzia śledzenia, który nie jest dostarczane przez system [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] mechanizm śledzenia i możesz otrzymywać <xref:System.ServiceModel.EndpointNotFoundException> wskazuje, że wystąpiła niezgodność filtru adresu, należy użyć <xref:System.ServiceModel.Description.ClientViaBehavior> klasy do kierowania wiadomości śledzenie Narzędzia i narzędzie przekierowania tych wiadomości na adres usługi. <xref:System.ServiceModel.Description.ClientViaBehavior> Zmienia klasy `Via` adresowania nagłówka, aby określić adres sieciowy dalej niezależnie od odbiornika ultimate, wskazane przez `To` adresowania nagłówka. W ten sposób, jednak nie należy zmieniać adresu punktu końcowego, który jest używany do ustanawiania `To` wartość.  
  
 Poniższy przykładowy kod przedstawia przykład klienta pliku konfiguracji.  
  
```xml
<endpoint   
  address=http://localhost:8000/MyServer/  
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
 Podstawowy adres jest adresem głównego dla <xref:System.ServiceModel.ServiceHost> klasy. Domyślnie po dodaniu <xref:System.ServiceModel.Description.ServiceMetadataBehavior> klasy do konfiguracji usługi sieci Web Services Description Language (WSDL) dla wszystkich punktów końcowych hosta publikuje są pobierane z podstawowy adres HTTP, a także wszelkie adres względny dostarczony do zachowania metadanych oraz "? wsdl". Jeśli znasz [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] i IIS, adres podstawowy jest odpowiednikiem katalogu wirtualnego.  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a>Udostępnianie portów między punkt końcowy usługi i punktu końcowego mex przy użyciu NetTcpBinding  
 Jeśli adres podstawowy usługi można określić jako net.tcp://MyServer: 8080/Moja_usługa i dodaj następujące punkty końcowe:  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 A jeśli jedno z ustawień NetTcpBinding zmodyfikujesz pokazane na poniższy fragment konfiguracji:  
  
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
  
 Zostanie wyświetlony błąd podobnie do następującej: nieobsługiwany wyjątek: System.ServiceModel.AddressAlreadyInUseException: istnieje już odbiornik na ten błąd można obejść, określając w pełni kwalifikowanego adres URL z innego portu dla 0.0.0.0:9000 punkt końcowy IP punkt końcowy MEX pokazane na poniższy fragment konfiguracji:  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>   
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a>Podczas wywoływania aplikacji protokołu HTTP sieci Web WCF z aplikacji WCF SOAP usługi zwraca następujący błąd: niedozwolone 405 — metoda  
 Wywoływanie aplikacji protokołu HTTP sieci Web WCF (usługa, która używa <xref:System.ServiceModel.WebHttpBinding> i <xref:System.ServiceModel.Description.WebHttpBehavior>) z usługą platformy WCF usługa może generować następujący wyjątek: `Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: serwer zdalny zwrócił nieoczekiwaną odpowiedź : (405) — metoda nie dozwolone. "ten wyjątek spowodowany WCF zastępuje wychodzącej <xref:System.ServiceModel.OperationContext> z przychodzącego <xref:System.ServiceModel.OperationContext>. Aby rozwiązać ten problem utworzyć <xref:System.ServiceModel.OperationContextScope> w ramach operacji usługi WCF Web HTTP. Na przykład:  
  
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
 [Debugowanie błędów uwierzytelniania systemu Windows](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)
