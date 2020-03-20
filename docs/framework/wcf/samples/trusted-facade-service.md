---
title: Zaufana usługa fasady
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: 17901b7a68d4701287d02bc7ee3174683e777fd1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143749"
---
# <a name="trusted-facade-service"></a>Zaufana usługa fasady
W tym przykładzie scenariusza pokazano, jak przepływ informacji o tożsamości wywołującego z jednej usługi do drugiej przy użyciu infrastruktury zabezpieczeń Programu Windows Communication Foundation (WCF).  
  
 Jest to typowy wzorzec projektu, aby udostępnić funkcje udostępniane przez usługę do sieci publicznej za pomocą usługi fasadowej. Usługa fasadowa zazwyczaj znajduje się w sieci obwodowej (znanej również jako STREFA DMZ, strefa zdemilitaryzowana i podsieć ekranowana) i komunikuje się z usługą zaplecza, która implementuje logikę biznesową i ma dostęp do danych wewnętrznych. Kanał komunikacji między usługą elewacji a usługą wewnętrznej bazy danych przechodzi przez zaporę i jest zwykle ograniczony tylko do jednego celu.  
  
 Ten przykład składa się z następujących składników:  
  
- Klient kalkulatora  
  
- Usługa elewacji kalkulatora  
  
- Usługa zaplecza kalkulatora  
  
 Usługa fasady jest odpowiedzialna za sprawdzanie poprawności żądania i uwierzytelnianie rozmówcy. Po pomyślnym uwierzytelnieniu i weryfikacji przekazuje żądanie do usługi wewnętrznej bazy danych przy użyciu kontrolowanego kanału komunikacyjnego z sieci obwodowej do sieci wewnętrznej. W ramach żądania przekazanego usługa fasadowa zawiera informacje o tożsamości wywołującego, dzięki czemu usługa zaplecza może używać tych informacji w jego przetwarzaniu. Tożsamość wywołującego jest przesyłany `Username` przy użyciu tokenu zabezpieczającego wewnątrz nagłówka wiadomości. `Security` Przykład używa infrastruktury zabezpieczeń WCF do przesyłania i `Security` wyodrębniania tych informacji z nagłówka.  
  
> [!IMPORTANT]
> Usługa wewnętrznej bazy danych ufa usłudze fasadowej w celu uwierzytelnienia wywołującego. Z tego powodu usługa wewnętrznej bazy danych nie uwierzytelnia obiektu wywołującego ponownie; wykorzystuje informacje o tożsamości podane przez usługę fasadową w przesłanym żądaniu. Z powodu tej relacji zaufania usługa zaplecza musi uwierzytelnić usługę fasadową, aby upewnić się, że przekazywany komunikat pochodzi z zaufanego źródła — w tym przypadku usługi fasadowej.  
  
## <a name="implementation"></a>Wdrażanie  
 Istnieją dwie ścieżki komunikacji w tym przykładzie. Pierwszy znajduje się między klientem a usługą elewacji, drugi znajduje się między serwisem elewacji a usługą zaplecza.  
  
### <a name="communication-path-between-client-and-faade-service"></a>Ścieżka komunikacji między obsługą klienta i fasady  
 Klient do ścieżki komunikacji usługi elewacji `wsHttpBinding` `UserName` używa z typem poświadczeń klienta. Oznacza to, że klient używa nazwy użytkownika i hasła do uwierzytelniania w usłudze fasadowej, a usługa fasadowa używa certyfikatu X.509 do uwierzytelniania klienta. Konfiguracja powiązania wygląda jak w poniższym przykładzie.  
  
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
  
 Usługa fasady uwierzytelnia wywołującego przy `UserNamePasswordValidator` użyciu implementacji niestandardowej. W celach demonstracyjnych uwierzytelnianie zapewnia tylko, że nazwa użytkownika wywołującego jest zgodna z prezentowanym hasłem. W sytuacji rzeczywistych użytkownik jest prawdopodobnie uwierzytelniony przy użyciu usługi Active Directory lub niestandardowego dostawcy członkostwa ASP.NET. Implementacja walidatora `FacadeService.cs` znajduje się w pliku.  
  
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
  
 Niestandardowy walidator jest skonfigurowany `serviceCredentials` do użycia wewnątrz zachowania w pliku konfiguracyjnym usługi fasadowej. To zachowanie jest również używane do konfigurowania certyfikatu X.509 usługi.  
  
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
  
### <a name="communication-path-between-faade-service-and-backend-service"></a>Ścieżka komunikacji między usługą fasadową a usługą zaplecza  
 Usługa elewacji do ścieżki komunikacji usługi wewnętrznej `customBinding` bazy danych używa, który składa się z kilku elementów wiązania. To powiązanie osiąga dwie rzeczy. Uwierzytelnia usługę elewacji i usługę zaplecza, aby upewnić się, że komunikacja jest bezpieczna i pochodzi z zaufanego źródła. Ponadto przesyła również tożsamość początkowego obiektu wywołującego `Username` wewnątrz tokenu zabezpieczającego. W takim przypadku tylko początkowa nazwa użytkownika wywołującego jest przesyłana do usługi wewnętrznej bazy danych, hasło nie jest zawarte w wiadomości. Dzieje się tak, ponieważ usługa wewnętrznej bazy danych ufa usłudze fasadowej w celu uwierzytelnienia wywołującego przed przekazaniem żądania do niego. Ponieważ usługa fasadowa uwierzytelnia się w usłudze wewnętrznej bazy danych, usługa zaplecza może ufać informacjom zawartym w żądaniu przesyłania dalej.  
  
 Poniżej przedstawiono konfigurację powiązania dla tej ścieżki komunikacji.  
  
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
  
 Element wiązania [ \<zabezpieczeń>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) zajmuje się przesyłaniem i wyodrębnianiem nazwy użytkownika początkowego wywołującego. [ \<WindowsStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) i [ \<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) dbać o usługi elewacji i wewnętrznej bazy danych oraz ochrony wiadomości.  
  
 Aby przesłać dalej żądanie, implementacja usługi fasadowej musi podać nazwę użytkownika początkowego wywołującego, aby infrastruktura zabezpieczeń WCF mogła umieścić to w wiadomości przesyłanej dalej. Nazwa użytkownika początkowego obiektu wywołującego jest dostępna w implementacji `ClientCredentials` usługi fasadowej, ustawiając ją we właściwości w wystąpieniu serwera proxy klienta, którego usługa fasadowa używa do komunikowania się z usługą zaplecza.  
  
 Poniższy kod `GetCallerIdentity` pokazuje, jak metoda jest implementowana w usłudze fasadowej. Inne metody używają tego samego wzorca.  
  
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
  
 Jak pokazano w poprzednim kodzie, hasło `ClientCredentials` nie jest ustawione na właściwości, tylko nazwa użytkownika jest ustawiona. Infrastruktura zabezpieczeń WCF tworzy token zabezpieczający nazwy użytkownika bez hasła w tym przypadku, co jest dokładnie to, co jest wymagane w tym scenariuszu.  
  
 W usłudze wewnętrznej bazy danych informacje zawarte w tokenie zabezpieczającym nazwy użytkownika muszą być uwierzytelnione. Domyślnie zabezpieczenia WCF próbują zamapować użytkownika na konto systemu Windows przy użyciu podanego hasła. W takim przypadku nie ma hasła i usługa wewnętrznej bazy danych nie jest wymagana do uwierzytelniania nazwy użytkownika, ponieważ uwierzytelnianie zostało już wykonane przez usługę fasadową. Aby zaimplementować tę funkcję `UserNamePasswordValidator` w WCF, niestandardowe jest pod warunkiem, że tylko wymusza, że nazwa użytkownika jest określona w tokenie i nie wykonuje żadnych dodatkowych uwierzytelniania.  
  
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
  
 Niestandardowy walidator jest skonfigurowany `serviceCredentials` do użycia wewnątrz zachowania w pliku konfiguracyjnym usługi fasadowej.  
  
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
  
 Aby wyodrębnić informacje o nazwie użytkownika i informacje o zaufanego konta `ServiceSecurityContext` usługi fasadowej, implementacja usługi wewnętrznej bazy danych używa klasy. Poniższy kod pokazuje, `GetCallerIdentity` jak metoda jest implementowana.  
  
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
  
 Informacje o koncie usługi elewacyjnej są pobierane za pomocą `ServiceSecurityContext.Current.WindowsIdentity` obiektu. Aby uzyskać dostęp do informacji o wywołaniu początkowym usługa wewnętrznej bazy danych używa `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` właściwości. Szuka `Identity` roszczenia z typem `Name`. To oświadczenie jest automatycznie generowane przez infrastrukturę zabezpieczeń WCF na podstawie informacji zawartych w tokenie zabezpieczającym. `Username`  
  
## <a name="running-the-sample"></a>Uruchamianie przykładowej aplikacji  
 Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta. Aby wyłączyć usługi, można nacisnąć klawisz ENTER w oknach konsoli elewacji i konsoli wewnętrznej bazy danych.  
  
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
  
 Plik wsadowy Setup.bat dołączony do przykładu scenariusza Zaufana fasada umożliwia skonfigurowanie serwera z odpowiednim certyfikatem do uruchomienia usługi fasadowej, która wymaga zabezpieczeń opartych na certyfikatach do uwierzytelniania się w kliencie. Szczegółowe informacje można znaleźć w procedurze konfiguracji na końcu tego tematu.  
  
 Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych.  
  
- Tworzenie certyfikatu serwera.  
  
     Następujące wiersze z pliku wsadowego Setup.bat tworzą certyfikat serwera, który ma być używany.  
  
    ```console  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     Zmienna `%SERVER_NAME%` określa nazwę serwera - wartością domyślną jest localhost. Certyfikat jest przechowywany w magazynie LocalMachine.  
  
- Instalowanie certyfikatu usługi fasadowej w magazynie certyfikatów zaufanych klienta.  
  
     Poniższy wiersz kopiuje certyfikat usługi fasadowej do magazynu zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty generowane przez plik Makecert.exe nie są niejawnie zaufane przez system kliencki. Jeśli masz już certyfikat zakorzeniony w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten etap wypełniania magazynu certyfikatów klienta certyfikatem serwera nie jest wymagany.  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić próbkę na tym samym komputerze  
  
1. Upewnij się, że ścieżka zawiera folder, w którym znajduje się plik Makecert.exe.  
  
2. Uruchom plik Setup.bat z przykładowego folderu instalacyjnego. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia próbki.  
  
3. Uruchamianie programu BackendService.exe z katalogu \BackendService\bin w osobnym oknie konsoli  
  
4. Uruchamianie programu FacadeService.exe z katalogu \FacadeService\bin w osobnym oknie konsoli  
  
5. Uruchom program Client.exe z pliku \client\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
6. Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby oczyścić po próbce  
  
1. Uruchom Cleanup.bat w folderze przykłady po zakończeniu uruchamiania próbki.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
