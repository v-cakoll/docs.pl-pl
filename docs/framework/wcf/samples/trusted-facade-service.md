---
title: Zaufana usługa fasady
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: e7aa5e96fb8104c8140a8cebc6be45d2000821aa
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591322"
---
# <a name="trusted-facade-service"></a>Zaufana usługa fasady
W tym scenariuszu przedstawiono sposób przepływu informacji o tożsamości wywołującego z jednej usługi do innej przy użyciu infrastruktury zabezpieczeń Windows Communication Foundation (WCF).  
  
 Typowym wzorcem projektu jest udostępnienie funkcjonalności oferowanej przez usługę do sieci publicznej za pomocą usługi fasadowej. Usługa elewacji zwykle znajduje się w sieci obwodowej (znanej także jako Strefa DMZ, zdemilitaryzowana Zone i podsieć z osłoną) i komunikuje się z usługą zaplecza, która implementuje logikę biznesową i ma dostęp do danych wewnętrznych. Kanał komunikacyjny między usługą fasady a usługą zaplecza przechodzi przez zaporę i jest zwykle ograniczony tylko do jednego celu.  
  
 Ten przykład składa się z następujących składników:  
  
- Klient kalkulatora  
  
- Usługa "elewacja" usługi Kalkulator  
  
- Usługa zaplecza programu Kalkulator  
  
 Usługa fasady jest odpowiedzialna za sprawdzenie poprawności żądania i uwierzytelnienie obiektu wywołującego. Po pomyślnym uwierzytelnieniu i sprawdzeniu zostanie przekazane żądanie do usługi wewnętrznej bazy danych przy użyciu kontrolowanego kanału komunikacyjnego z sieci obwodowej do sieci wewnętrznej. W ramach przekazanego żądania usługa elewacji zawiera informacje o tożsamości wywołującego, dzięki czemu usługa zaplecza może używać tych informacji w jego przetwarzaniu. Tożsamość obiektu wywołującego jest przekazywana przy użyciu `Username` tokenu zabezpieczającego wewnątrz `Security` nagłówka komunikatu. Przykład używa infrastruktury zabezpieczeń WCF do przesyłania i wyodrębniania tych informacji z `Security` nagłówka.  
  
> [!IMPORTANT]
> Usługa zaplecza ufa usłudze elewacji do uwierzytelniania obiektu wywołującego. W związku z tym usługa zaplecza nie uwierzytelnia ponownie obiektu wywołującego; używa on informacji o tożsamości dostarczonych przez usługę elewacji w żądaniu przekazywanym dalej. Ze względu na tę relację zaufania usługa zaplecza musi uwierzytelnić usługę elewacji, aby upewnić się, że przekazany komunikat pochodzi z zaufanego źródła — w tym przypadku usługi elewacji.  
  
## <a name="implementation"></a>Implementacja  
 W tym przykładzie istnieją dwie ścieżki komunikacji. Po pierwsze jest między klientem a usługą elewacji drugi między usługą elewacji a usługą zaplecza.  
  
### <a name="communication-path-between-client-and-faade-service"></a>Ścieżka komunikacji między klientem a usługą elewacji  
 Klient do ścieżki komunikacji usługi elewacji używa `wsHttpBinding` z `UserName` typem poświadczeń klienta. Oznacza to, że klient używa nazwy użytkownika i hasła do uwierzytelniania w usłudze elewacji, a usługa fasada używa certyfikatu X. 509 do uwierzytelniania na kliencie. Konfiguracja powiązania wygląda podobnie do poniższego przykładu.  
  
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
  
 Usługa elewacji uwierzytelnia obiekt wywołujący przy użyciu `UserNamePasswordValidator` implementacji niestandardowej. W celach demonstracyjnych uwierzytelnianie gwarantuje, że nazwa użytkownika wywołującego jest zgodna z przedstawionym hasłem. W świecie rzeczywistym użytkownik jest prawdopodobnie uwierzytelniany przy użyciu Active Directory lub niestandardowego dostawcy członkostwa ASP.NET. Implementacja modułu sprawdzania poprawności znajduje się w `FacadeService.cs` pliku.  
  
```csharp  
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
  
 Niestandardowy moduł sprawdzania poprawności jest skonfigurowany do użycia wewnątrz `serviceCredentials` zachowania w pliku konfiguracji usługi elewacji. To zachowanie służy również do konfigurowania certyfikatu X. 509 usługi.  
  
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
  
### <a name="communication-path-between-faade-service-and-backend-service"></a>Ścieżka komunikacji między usługą elewacji a usługą zaplecza  
 Podnosząca się do ścieżki komunikacji usługi wewnętrznej bazy danych używa `customBinding` , która składa się z kilku elementów powiązania. To powiązanie wykonuje dwie rzeczy. Usługa ta uwierzytelnia usługę fasady i usługę zaplecza, aby upewnić się, że komunikacja jest bezpieczna i pochodzi z zaufanego źródła. Ponadto również przesyła początkową tożsamość obiektu wywołującego wewnątrz `Username` tokenu zabezpieczającego. W takim przypadku tylko nazwa użytkownika początkowego obiektu wywołującego jest przesyłana do usługi wewnętrznej bazy danych, a hasło nie jest uwzględniane w komunikacie. Wynika to z faktu, że usługa zaplecza ufa usłudze elewacji do uwierzytelniania obiektu wywołującego przed przekazaniem do niego żądania. Ponieważ usługa fasady jest uwierzytelniana w usłudze wewnętrznej bazy danych, usługa zaplecza może ufać informacjom zawartym w żądaniu przekazywanym dalej.  
  
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
  
 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md)Element Binding bierze pod uwagę początkową transmisję i wyodrębnianie nazwy użytkownika. [\<windowsStreamSecurity>](../../configure-apps/file-schema/wcf/windowsstreamsecurity.md)I [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) zapoznaj się z uwierzytelnianiem fasady i usług zaplecza oraz ochrony komunikatów.  
  
 Aby przesłać dalej żądanie, implementacja nieelewacji usługi musi dostarczyć nazwę użytkownika początkowego wywołującego, aby infrastruktura zabezpieczeń WCF mogła je umieścić w przekazywanym komunikacie. Początkowa nazwa użytkownika wywołującego jest udostępniana w implementacji usługi fasadowej przez ustawienie jej we `ClientCredentials` właściwości w wystąpieniu serwera proxy klienta, która elewacji usługi używa do komunikowania się z usługą zaplecza.  
  
 Poniższy kod pokazuje, jak `GetCallerIdentity` Metoda jest zaimplementowana w usłudze elewacji. Inne metody używają tego samego wzorca.  
  
```csharp  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 Jak pokazano w poprzednim kodzie, hasło nie jest ustawione dla `ClientCredentials` właściwości, tylko nazwa użytkownika jest ustawiona. Infrastruktura zabezpieczeń WCF tworzy w tym przypadku token zabezpieczający username bez hasła, co jest dokładnie wymagane w tym scenariuszu.  
  
 W usłudze zaplecza informacje zawarte w tokenie zabezpieczeń username muszą zostać uwierzytelnione. Domyślnie zabezpieczenia WCF próbują zmapować użytkownika na konto systemu Windows przy użyciu podanego hasła. W takim przypadku nie podano hasła i usługa zaplecza nie jest wymagana do uwierzytelnienia nazwy użytkownika, ponieważ uwierzytelnianie zostało już wykonane przez usługę elewacji. W celu zaimplementowania tej funkcji w programie WCF zostanie udostępniona niestandardowa, `UserNamePasswordValidator` która wymusza, że nazwa użytkownika jest określona w tokenie i nie wykonuje dodatkowego uwierzytelniania.  
  
```csharp  
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
  
 Niestandardowy moduł sprawdzania poprawności jest skonfigurowany do użycia wewnątrz `serviceCredentials` zachowania w pliku konfiguracji usługi elewacji.  
  
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
  
 Aby wyodrębnić informacje o nazwie użytkownika i informacje o koncie usługi zaufanej elewacji, implementacja usługi wewnętrznej bazy danych używa `ServiceSecurityContext` klasy. Poniższy kod pokazuje, jak `GetCallerIdentity` Metoda jest zaimplementowana.  
  
```csharp  
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
  
 Informacje o koncie usługi fasady są wyodrębniane przy użyciu `ServiceSecurityContext.Current.WindowsIdentity` właściwości. Aby uzyskać dostęp do informacji o początkowym wywołującym, usługa zaplecza używa `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` właściwości. Szuka on `Identity` zgłoszenia z typem `Name` . To zgłoszenie jest generowane automatycznie przez infrastrukturę zabezpieczeń WCF z informacji zawartych w `Username` tokenie zabezpieczającym.  
  
## <a name="running-the-sample"></a>Uruchamianie przykładowej aplikacji  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu. Aby zamknąć usługi, możesz nacisnąć klawisz ENTER w oknach konsoli usługi elewacji i zaplecza.  
  
```console  
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
  
 Plik wsadowy Setup. bat dołączony do zaufanego przykładowego scenariusza zaufana fasady umożliwia skonfigurowanie serwera z odpowiednim certyfikatem w celu uruchomienia usługi fasady wymagającej zabezpieczeń opartych na certyfikatach do samodzielnego uwierzytelnienia klienta. Aby uzyskać szczegółowe informacje, zobacz procedurę instalacji na końcu tego tematu.  
  
 Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych.  
  
- Tworzenie certyfikatu serwera.  
  
     Poniższe wiersze z pliku wsadowego Setup. bat tworzą certyfikat serwera do użycia.  
  
    ```console  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     `%SERVER_NAME%`Zmienna określa nazwę serwera — wartość domyślna to localhost. Certyfikat jest przechowywany w magazynie LocalMachine.  
  
- Instalowanie certyfikatu usługi elewacji w zaufanym magazynie certyfikatów klienta.  
  
     Poniższy wiersz umożliwia skopiowanie certyfikatu usługi elewacji do magazynu zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta. Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić przykład na tym samym komputerze  
  
1. Upewnij się, że ścieżka zawiera folder, w którym znajduje się Makecert. exe.  
  
2. Uruchom setup. bat z przykładowego folderu instalacyjnego. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.  
  
3. Uruchom BackendService. exe z katalogu \BackendService\bin w osobnym oknie konsoli  
  
4. Uruchom FacadeService. exe z katalogu \FacadeService\bin w osobnym oknie konsoli  
  
5. Uruchamianie programu Client. exe z \client\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
6. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po przykładzie  
  
1. Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
