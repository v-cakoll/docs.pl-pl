---
title: Zaufana usługa fasady
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: 4b18f0eb4183a9dd6d0801dd022176cd3220c62c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640423"
---
# <a name="trusted-facade-service"></a>Zaufana usługa fasady
Ten przykładowy scenariusz pokazuje, jak przepływ informacji o tożsamości wywołującego z jednej usługi do innego za pomocą usługi Windows Communication Foundation (WCF) infrastruktura zabezpieczeń.  
  
 Jest wspólny wzorzec projektowania, aby udostępnić funkcje udostępniane przez usługi w sieci publicznej przy użyciu usługi fasady. Usługa fasady zazwyczaj znajduje się w sieci obwodowej (znany także jako DMZ, strefa zdemilitaryzowana i podsieć ekranowana) i komunikuje się za pomocą usługi zaplecza, która implementuje logikę biznesową i ma dostęp do danych wewnętrznych. Kanał komunikacyjny między usługą fasady i usługą zaplecza przechodzi przez zaporę i jest zwykle ograniczony tylko do jednego celu.  
  
 W tym przykładzie składa się z następujących składników:  
  
-   Kalkulator klienta  
  
-   Usługa fasady Kalkulator  
  
-   Kalkulator usługi zaplecza  
  
 Usługa fasady jest odpowiedzialna za weryfikowanie żądania i uwierzytelniania obiektu wywołującego. Po pomyślnym uwierzytelnieniu i sprawdzania poprawności przesyła żądanie do usługi zaplecza przy użyciu kanału komunikacyjnego kontrolowany w sieci obwodowej z siecią wewnętrzną. Jako część żądania przekazywane usługa fasady zawiera informacje o tożsamości elementu wywołującego, tak aby usługi wewnętrznej bazy danych można użyć tych informacji w zakresie przetwarzania. Tożsamość obiektu wywołującego jest przesyłane przy użyciu `Username` tokenu zabezpieczającego w komunikacie `Security` nagłówka. W przykładzie użyto infrastruktura zabezpieczeń programu WCF do przesyłania i wyodrębnić te informacje z `Security` nagłówka.  
  
> [!IMPORTANT]
>  Usługi wewnętrznej bazy danych i relacje zaufania usługi fasady do uwierzytelniania obiektu wywołującego. W związku z tym usługa zaplecza nie uwierzytelnia obiektu wywołującego ponownie; informacje o tożsamości, usługa fasady w żądaniu przekazywane go używa. Ze względu na tę relację zaufania usługi wewnętrznej bazy danych muszą zostać uwierzytelnione Usługa fasady, aby upewnić się, że przekazany dalej komunikat pochodzi z zaufanego źródła — w tym przypadku usługa fasady.  
  
## <a name="implementation"></a>Implementacja  
 W tym przykładzie istnieją dwie ścieżki komunikacji. Najpierw jest między klientem a usługa fasady drugą jest wartość między usługą fasady i usługą zaplecza.  
  
### <a name="communication-path-between-client-and-faade-service"></a>Ścieżka komunikacji między klientem a usługą fasady  
 Korzysta z klienta do ścieżki komunikacji usługi fasady `wsHttpBinding` z `UserName` typu poświadczeń klienta. Oznacza to, że klient używa nazwy użytkownika i hasło do uwierzytelniania usługa fasady i usługa fasady używa certyfikatu X.509 do uwierzytelniania klienta. Konfiguracja powiązania wygląda podobnie jak w poniższym przykładzie.  
  
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
  
 Usługa fasady uwierzytelnia wywołującemu, korzystając z niestandardowego `UserNamePasswordValidator` implementacji. Dla celów demonstracyjnych uwierzytelniania tylko zapewnia zgodność nazwy użytkownika wywołującego prezentowane hasła. W rzeczywistych sytuacji prawdopodobnie uwierzytelnieniu użytkownika przy użyciu usługi Active Directory lub niestandardowego dostawcy członkostwa ASP.NET. Implementacja modułu sprawdzania poprawności, który znajduje się w `FacadeService.cs` pliku.  
  
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
  
 Niestandardowy moduł sprawdzania poprawności jest skonfigurowana do używania wewnątrz `serviceCredentials` zachowanie w pliku konfiguracji usługi fasady. To zachowanie umożliwia również konfigurowanie certyfikacie X.509.  
  
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
  
### <a name="communication-path-between-faade-service-and-backend-service"></a>Ścieżka komunikacji między usługą fasady i usługi zaplecza  
 Usługa fasady do ścieżki komunikacji usługi wewnętrznej bazy danych używa `customBinding` składający się z kilku elementów powiązania. Dwie rzeczy w ramach tego powiązania. Usługa ta uwierzytelnia usługa fasady i usługi zaplecza, aby upewnić się, że komunikacja jest bezpieczna i pochodzi z zaufanego źródła. Ponadto również przesyła tożsamości elementu wywołującego początkowej wewnątrz `Username` tokenu zabezpieczającego. W tym przypadku tylko nazwy użytkownika wywołującego początkowej są przesyłane do usługi zaplecza, hasło nie znajduje się w komunikacie. Jest to spowodowane usługi wewnętrznej bazy danych i relacje zaufania usługi fasady do uwierzytelniania obiektu wywołującego przed przekazaniem żądania do niego. Ponieważ usługa fasady uwierzytelnia do usługi zaplecza, usługi zaplecza mogą ufać informacji zawartych w żądaniu przesyłanych dalej.  
  
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
  
 [ \<Zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element powiązania dba o przesyłania nazwy użytkownika i wyodrębniania początkowego obiektu wywołującego. [ \<WindowsStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) i [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) obsługi uwierzytelniania usługi frontonu i wewnętrznej bazy danych i ochrona wiadomości.  
  
 Do przesyłania żądania, fasady implementacji usługi należy podać username początkowego wywołującego, tak że infrastruktura zabezpieczeń programu WCF można umieścić ten przekazany dalej komunikat. Username początkowego wywołującego znajduje się w implementacji usługi fasady ustawiając w `ClientCredentials` właściwość w wystąpieniu serwera proxy klienta usługi fasady używa do komunikowania się z usługą zaplecza.  
  
 Poniższy kod przedstawia sposób `GetCallerIdentity` metoda jest implementowana w usłudze fasady. Inne metody używają tego samego wzorca.  
  
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
  
 Jak pokazano w poprzednim kodzie, hasło nie jest ustawiona na `ClientCredentials` , tylko nazwy użytkownika ustawiono właściwość. Infrastruktura zabezpieczeń WCF tworzy token zabezpieczający nazwy użytkownika bez hasła w tym przypadku, co jest dokładnie co jest wymagane w tym scenariuszu.  
  
 W usłudze zaplecza informacji zawartych w tokenie zabezpieczającym nazwa użytkownika musi zostać uwierzytelnione. Domyślnie zabezpieczeń WCF próbuje mapowanie użytkownika do konta Windows przy użyciu podanego hasła. W tym przypadku jest nie podano hasła i usługi wewnętrznej bazy danych nie jest wymagane do uwierzytelniania nazwy użytkownika, ponieważ uwierzytelnianie zostało już wykonane przez usługa fasady. Aby zaimplementować tę funkcję w programie WCF, niestandardowe `UserNamePasswordValidator` zostanie podana, tylko wymusza, że nazwa użytkownika jest określona w tokenie i niewykonywanie żadnego dodatkowego uwierzytelniania.  
  
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
  
 Niestandardowy moduł sprawdzania poprawności jest skonfigurowana do używania wewnątrz `serviceCredentials` zachowanie w pliku konfiguracji usługi fasady.  
  
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
  
 Aby wyodrębnić informacje nazwy użytkownika i informacje o koncie usługi zaufanej fasady, korzysta z implementacji usługi zaplecza `ServiceSecurityContext` klasy. Poniższy kod przedstawia sposób, w jaki `GetCallerIdentity` metoda jest implementowana.  
  
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
  
 Informacje o koncie usługi fasady jest wyodrębniany przy użyciu `ServiceSecurityContext.Current.WindowsIdentity` właściwości. Aby uzyskać dostęp do informacji o obiekcie wywołującym początkowej, używa usługi wewnętrznej bazy danych `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` właściwości. Szuka `Identity` oświadczenie z typem `Name`. To oświadczenie jest generowany automatycznie przez infrastrukturę zabezpieczeń programu WCF z informacji zawartych w `Username` tokenu zabezpieczającego.  
  
## <a name="running-the-sample"></a>Działa aplikacja przykładowa  
 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta. Można naciśnij klawisz ENTER w oknach konsoli usługi frontonu i zaplecza, aby zamknąć usługi.  
  
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
  
 Plik wsadowy Setup.bat jest dołączone do zaufanych fasady przykładowy scenariusz umożliwia skonfigurowanie serwera przy użyciu certyfikatu odpowiedniego do uruchamiania usługi fasady wymagającego opartego na certyfikatach zabezpieczeń, aby uwierzytelniać się klient. Zapoznaj się z procedurą konfiguracji na końcu tego tematu, aby uzyskać szczegółowe informacje.  
  
 Poniżej zawiera krótkie omówienie różnych sekcji w plikach wsadowych.  
  
-   Tworzenie certyfikatu serwera.  
  
     Następujące wiersze z pliku wsadowego Setup.bat jest utworzenie certyfikatu serwera, który ma być używany.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     `%SERVER_NAME%` Zmienna Określa nazwę serwera — wartość domyślna to hosta lokalnego. Certyfikat jest przechowywany w magazynie LocalMachine.  
  
-   Instalowanie usługi fasady certyfikat do magazynu zaufanych certyfikatów klienta.  
  
     Następujący wiersz kopiuje usługa fasady certyfikat w magazynie zaufanych osób klienta. Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta. Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony przez Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Upewnij się, że ścieżka zawiera folder, w którym znajduje się Makecert.exe.  
  
2.  Uruchom Setup.bat jest z poziomu folderu instalacji przykładowej. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.  
  
3.  Uruchom BackendService.exe \BackendService\bin katalog w oknie konsoli oddzielne  
  
4.  Uruchom FacadeService.exe \FacadeService\bin katalog w oknie konsoli oddzielne  
  
5.  Uruchom Client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.  
  
6.  Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić zasoby po próbki  
  
1.  Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
  
## <a name="see-also"></a>Zobacz także
