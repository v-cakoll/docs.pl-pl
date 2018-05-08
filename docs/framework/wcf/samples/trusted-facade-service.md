---
title: Zaufana usługa fasady
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: 08e115d297439910c16601051539a23a5a6bebc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="trusted-facade-service"></a>Zaufana usługa fasady
W tym przykładzie scenariuszu pokazano, jak przepływ informacji o tożsamości obiektu wywołującego z jedną usługę do drugiego za pomocą usługi Windows Communication Foundation (WCF) infrastruktura zabezpieczeń.  
  
 Jest wspólnego wzorca projektowego do udostępnienia funkcji udostępnianych przez usługę do publicznej sieci przy użyciu usługi fasad. Usługa fasad zazwyczaj znajduje się w sieci obwodowej (znanej także jako strefa DMZ, strefą zdemilitaryzowaną i podsiecią ekranowaną), a także komunikuje się za pomocą usługi wewnętrznej bazy danych, która implementuje logiki biznesowej i ma dostęp do danych wewnętrznych. Kanał komunikacji między usługą fasad i usługi wewnętrznej bazy danych przechodzi przez zaporę i jest zazwyczaj ograniczone do tylko jednej celu.  
  
 Ten przykład obejmuje następujące składniki:  
  
-   Kalkulator klienta  
  
-   Kalkulator fasad usługi  
  
-   Kalkulator usługi wewnętrznej bazy danych  
  
 Usługa fasad jest odpowiedzialna za sprawdzanie poprawności żądania i uwierzytelniania obiektu wywołującego. Po pomyślnym uwierzytelnieniu i sprawdzania poprawności przesyła żądanie do usługi zaplecza przy użyciu kanału komunikacyjnego kontrolowane w sieci obwodowej z siecią wewnętrzną. Jako część przekazane żądanie usługi fasad zawiera informacje o tożsamości obiektu wywołującego, dzięki czemu usługi wewnętrznej bazy danych można użyć tych informacji podczas jego przetwarzania. Tożsamość obiektu wywołującego są przesyłane przy użyciu `Username` tokenów zabezpieczających w komunikacie `Security` nagłówka. W przykładzie użyto [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury zabezpieczeń do przesyłania i wyodrębnić te informacje z `Security` nagłówka.  
  
> [!IMPORTANT]
>  Do usługi zaplecza ufa usługi fasad do uwierzytelniania obiektu wywołującego. W związku z tym usługi wewnętrznej bazy danych nie uwierzytelnia wywołującego ponownie; używa informacji o tożsamości udostępnianych przez usługę fasad w przekazane żądanie. Z powodu tej relacji zaufania usługi wewnętrznej bazy danych musi uwierzytelniać usługi fasad w celu zapewnienia, że przekazany dalej komunikat pochodzi z zaufanego źródła — w takim przypadku usługa fasad.  
  
## <a name="implementation"></a>Implementacja  
 Istnieją dwie ścieżki komunikacji, w tym przykładzie. Najpierw jest między klientem a usługą fasad drugą jest wartość między usługą fasad i usługi wewnętrznej bazy danych.  
  
### <a name="communication-path-between-client-and-faade-service"></a>Ścieżki komunikacji między klientem a usługą fasad  
 Klient do komunikacji usługi fasad ścieżki używa `wsHttpBinding` z `UserName` typu poświadczeń klienta. Oznacza to, że klient używa nazwy użytkownika i hasła do uwierzytelnienia usługi fasad i fasad używa certyfikatu X.509 do uwierzytelniania klienta. Konfiguracja powiązania wygląda jak w następującym przykładzie.  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="Binding1">  
      <security mode="Message">  
        <message clientCredentialType="UserName"/>  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 Usługa fasad uwierzytelnia wywołującemu, korzystając z niestandardowych `UserNamePasswordValidator` implementacji. Dla celów demonstracyjnych uwierzytelnianie tylko zapewnia zgodność nazwy użytkownika wywołującego przedstawioną hasła. W przypadku rzeczywistych prawdopodobnie uwierzytelnieniu użytkownika przy użyciu usługi Active Directory lub niestandardowego dostawcy członkostwa ASP.NET. Implementacja modułu sprawdzania poprawności znajduje się w `FacadeService.cs` pliku.  
  
```  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // check that username matches password  
        if (null == userName || userName != password)  
        {  
            Console.WriteLine("Invalid username or password");  
            throw new SecurityTokenValidationException(  
                       "Invalid username or password");  
        }  
    }  
}  
```  
  
 Niestandardowy moduł sprawdzania poprawności jest skonfigurowana do używania wewnątrz `serviceCredentials` zachowania w pliku konfiguracji usługi fasad. To zachowanie umożliwia również konfigurowanie certyfikatu X.509 usługi.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="FacadeServiceBehavior">  
      <!--The serviceCredentials behavior allows you to define -->  
      <!--a service certificate. -->  
      <!--A service certificate is used by the service to  -->  
      <!--authenticate itself to its clients and to provide  -->  
      <!--message protection. -->  
      <!--This configuration references the "localhost"  -->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate   
               findValue="localhost"   
               storeLocation="LocalMachine"   
               storeName="My"   
               x509FindType="FindBySubjectName" />  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
            customUserNamePasswordValidatorType=  
           "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,  
            FacadeService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
### <a name="communication-path-between-faade-service-and-backend-service"></a>Ścieżki komunikacji między usługą fasad i usługi wewnętrznej bazy danych  
 Usługa fasadowym przeznaczonym do ścieżki komunikacji usługi wewnętrznej bazy danych używa `customBinding` składający się z kilku elementów powiązania. To powiązanie wykonuje dwie czynności. Uwierzytelnia fasad usługi i usługi wewnętrznej bazy danych, aby upewnić się, że komunikacja jest bezpieczna i pochodzi z zaufanego źródła. Ponadto również przesyła tożsamości obiektu wywołującego początkowej wewnątrz `Username` tokenu zabezpieczającego. W takim przypadku tylko początkowego wywołującego username są przesyłane do usługi zaplecza, hasło nie jest zawarte w wiadomości. Jest to spowodowane usługi zaplecza relacje zaufania usługi fasad do uwierzytelniania wywołującego przed przekazaniem żądania do niego. Ponieważ usługa fasad uwierzytelnia się do usługi zaplecza, do usługi zaplecza można ufać informacji zawartych w przekazane żądanie.  
  
 Poniżej znajduje się Konfiguracja powiązania dla tej ścieżki komunikacji.  
  
```xml  
<bindings>  
  <customBinding>  
    <binding name="ClientBinding">  
      <security authenticationMode="UserNameOverTransport"/>  
      <windowsStreamSecurity/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 [ \<Zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element powiązania zajmuje się przesyłania nazwy użytkownika i wyodrębniania początkowego wywołującego. [ \<Obiekt windowsStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) i [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) zajmie się uwierzytelniania usługi fasad i wewnętrznej bazy danych i komunikatów ochrony.  
  
 Do przesyłania żądania, implementacji usługi fasad podać nazwę użytkownika do obiektu wywołującego początkowej, aby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] umieść dla infrastruktury zabezpieczeń do przekazany dalej komunikat. Username początkowego wywołującego znajduje się w implementacji usługi fasad ustawiając w `ClientCredentials` właściwość w wystąpieniu serwera proxy klienta usługi fasad używa do komunikacji z usługą wewnętrznej bazy danych.  
  
 Poniższy kod przedstawia sposób `GetCallerIdentity` metoda jest zaimplementowana w usłudze fasad. Inne metody korzystają z tego samego wzorca.  
  
```  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 Jak pokazano w poprzednim kodzie, hasło nie jest ustawiona na `ClientCredentials` właściwość jest ustawiona tylko nazwy użytkownika. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Infrastruktura zabezpieczeń tworzy tokenu zabezpieczającego nazwy użytkownika bez hasła w tym przypadku, czyli dokładnie co jest wymagane w tym scenariuszu.  
  
 W usłudze zaplecza informacji zawartych w tokenie zabezpieczającym, nazwa użytkownika musi zostać uwierzytelniony. Domyślnie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczeń próbuje zamapować użytkownika na konto systemu Windows przy użyciu podanego hasła. W takim przypadku nie jest żadne hasło podane i usługi wewnętrznej bazy danych nie jest wymagane do uwierzytelniania nazwa użytkownika, ponieważ usługa fasad już zostało przeprowadzone uwierzytelnianie. Aby zaimplementować tę funkcję w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], niestandardowego `UserNamePasswordValidator` jest pod warunkiem, że tylko wymusza czy nazwę użytkownika w tokenie określono i nie wykonuje żadnego dodatkowego uwierzytelniania.  
  
```  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // Ignore the password because it is empty,   
        // we trust the facade service to authenticate the client.  
        // Accept the username information here so that the   
        // application gets access to it.  
        if (null == userName)  
        {  
            Console.WriteLine("Invalid username");  
            throw new   
             SecurityTokenValidationException("Invalid username");  
        }  
    }  
}  
```  
  
 Niestandardowy moduł sprawdzania poprawności jest skonfigurowana do używania wewnątrz `serviceCredentials` zachowania w pliku konfiguracji usługi fasad.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="BackendServiceBehavior">  
      <serviceCredentials>  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
           customUserNamePasswordValidatorType=  
          "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,   
           BackendService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Aby wyodrębnić informacje nazwy użytkownika i informacje o koncie usługi zaufanej fasad, korzysta z implementacji usługi wewnętrznej bazy danych `ServiceSecurityContext` klasy. Poniższy kod przedstawia sposób `GetCallerIdentity` metoda jest zaimplementowana.  
  
```  
public string GetCallerIdentity()  
{  
    // Facade service is authenticated using Windows authentication.  
    //Its identity is accessible.  
    // On ServiceSecurityContext.Current.WindowsIdentity.  
    string facadeServiceIdentityName =   
          ServiceSecurityContext.Current.WindowsIdentity.Name;  
  
    // The client name is transmitted using Username authentication on   
    //the message level without the password  
    // using a supporting encrypted UserNameToken.  
    // Claims extracted from this supporting token are available in   
    // ServiceSecurityContext.Current.AuthorizationContext.ClaimSets   
    // collection.  
    string clientName = null;  
    foreach (ClaimSet claimSet in   
        ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)  
    {  
        foreach (Claim claim in claimSet)  
        {  
            if (claim.ClaimType == ClaimTypes.Name &&   
                                   claim.Right == Rights.Identity)  
            {  
                clientName = (string)claim.Resource;  
                break;  
            }  
        }  
    }  
    if (clientName == null)  
    {  
        // In case there was no UserNameToken attached to the request.  
        // In the real world implementation the service should reject   
        // this request.  
        return "Anonymous caller via " + facadeServiceIdentityName;  
    }  
  
    return clientName + " via " + facadeServiceIdentityName;  
}  
```  
  
 Informacje o koncie usługi fasad jest wyodrębniany przy użyciu `ServiceSecurityContext.Current.WindowsIdentity` właściwości. Aby uzyskać dostęp do informacji o elemencie wywołującym początkowej używa usługi wewnętrznej bazy danych `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` właściwości. Szuka `Identity` oświadczenie z typem `Name`. To oświadczenie jest generowana automatycznie przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury zabezpieczeń z informacji zawartych w `Username` tokenu zabezpieczającego.  
  
## <a name="running-the-sample"></a>Uruchomiona próbki  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta. Naciśnij klawisz ENTER w oknach konsoli fasad i wewnętrznej bazy danych usługi, aby zamknąć usługi.  
  
```  
Username authentication required.  
Provide a valid machine or domain ac  
   Enter username:  
user  
   Enter password:  
****  
user via MyMachine\testaccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Plik wsadowy pliku Setup.bat dołączonego przykładowy scenariusz zaufane fasady umożliwia skonfigurowanie serwera przy użyciu odpowiedniego certyfikatu do uruchamiania usługi fasad wymagające zabezpieczenia oparte na certyfikatach do samodzielnego uwierzytelnienia klienta. Zapoznaj się z procedurą instalacji na końcu tego tematu, aby uzyskać szczegółowe informacje.  
  
 Poniżej znajdują się krótki przegląd różnych sekcji pliki wsadowe.  
  
-   Tworzenie certyfikatu serwera.  
  
     Następujące wiersze z pliku wsadowego pliku Setup.bat utworzenie certyfikatu serwera do użycia.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     `%SERVER_NAME%` Zmiennej określa nazwę serwera — wartość domyślna to localhost. Certyfikat jest przechowywany w magazynie LocalMachine.  
  
-   Instalowanie usługi fasad certyfikatu do magazynu zaufanych certyfikatów klienta.  
  
     Następujący wiersz kopiuje usługi fasad certyfikatu w magazynie zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta. Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład certyfikat wystawiony przez Microsoft — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Upewnij się, że ścieżka zawiera folder, w którym znajduje się Makecert.exe.  
  
2.  Uruchamianie pliku Setup.bat z folderu instalacyjnego próbki. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.  
  
3.  Uruchom BackendService.exe \BackendService\bin katalog w oknie konsoli oddzielne  
  
4.  Uruchom FacadeService.exe \FacadeService\bin katalog w oknie konsoli oddzielne  
  
5.  Uruchom Client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.  
  
6.  Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po próbki  
  
1.  Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
  
## <a name="see-also"></a>Zobacz też
