---
title: Dostawca członkostwa i ról
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: 7fba608d6d0ed3b7caab62ff16926d7b03516ed1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424667"
---
# <a name="membership-and-role-provider"></a>Dostawca członkostwa i ról
Przykład członkostwa i dostawcy ról pokazuje, jak usługa może używać członkostwa ASP.NET i dostawców ról do uwierzytelniania i autoryzowania klientów.  
  
 W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W przykładzie pokazano, jak:  
  
- Klient może uwierzytelniać się przy użyciu kombinacji nazwa użytkownika i hasło.  
  
- Serwer może sprawdzać poprawność poświadczeń klienta względem dostawcy członkostwa ASP.NET.  
  
- Serwer można uwierzytelnić przy użyciu certyfikatu X. 509 serwera.  
  
- Serwer programu może mapować uwierzytelnionego klienta na rolę przy użyciu dostawcy roli ASP.NET.  
  
- Serwer może używać `PrincipalPermissionAttribute`, aby kontrolować dostęp do niektórych metod, które są udostępniane przez usługę.  
  
 Dostawcy członkostwa i ról są skonfigurowani do używania magazynu obsługiwanego przez SQL Server. W pliku konfiguracji usługi określono parametry połączenia i różne opcje. Dostawca członkostwa otrzymuje nazwę `SqlMembershipProvider` podczas gdy dostawca roli ma nazwę `SqlRoleProvider`.  
  
```xml  
<!-- Set the connection string for SQL Server -->  
<connectionStrings>  
  <add name="SqlConn"   
       connectionString="Data Source=localhost;Integrated Security=SSPI;Initial Catalog=aspnetdb;" />  
</connectionStrings>  
  
<system.web>  
  <!-- Configure the Sql Membership Provider -->  
  <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">  
    <providers>  
      <clear />  
      <add   
        name="SqlMembershipProvider"   
        type="System.Web.Security.SqlMembershipProvider"   
        connectionStringName="SqlConn"  
        applicationName="MembershipAndRoleProviderSample"  
        enablePasswordRetrieval="false"  
        enablePasswordReset="false"  
        requiresQuestionAndAnswer="false"  
        requiresUniqueEmail="true"  
        passwordFormat="Hashed" />  
    </providers>  
  </membership>  
  
  <!-- Configure the Sql Role Provider -->  
  <roleManager enabled ="true"   
               defaultProvider ="SqlRoleProvider" >  
    <providers>  
      <add name ="SqlRoleProvider"   
           type="System.Web.Security.SqlRoleProvider"   
           connectionStringName="SqlConn"   
           applicationName="MembershipAndRoleProviderSample"/>  
    </providers>  
  </roleManager>  
</system.web>  
```  
  
 Usługa udostępnia jeden punkt końcowy do komunikacji z usługą, która jest definiowana przy użyciu pliku konfiguracyjnego Web. config. Punkt końcowy składa się z adresu, powiązania i kontraktu. Powiązanie jest skonfigurowane przy użyciu standardowej `wsHttpBinding`, która domyślnie używa uwierzytelniania systemu Windows. Ten przykład ustawia standardowy `wsHttpBinding` do korzystania z uwierzytelniania nazwy użytkownika. Zachowanie określa, że certyfikat serwera ma być używany do uwierzytelniania usługi. Certyfikat serwera musi zawierać taką samą wartość `SubjectName` jak atrybut `findValue` w elemencie konfiguracji [\<serviceCertificate](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) . Dodatkowo zachowanie określa, że uwierzytelnianie par username-Password jest wykonywane przez dostawcę członkostwa ASP.NET, a mapowanie roli jest wykonywane przez dostawcę roli ASP.NET przez określenie nazw zdefiniowanych dla dwóch dostawców.  
  
```xml  
<system.serviceModel>  
  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- Set up a binding that uses Username as the client credential type -->  
      <binding>  
        <security mode ="Message">  
          <message clientCredentialType ="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!-- Configure role based authorization to use the Role Provider -->  
        <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                              roleProviderName ="SqlRoleProvider" />  
        <serviceCredentials>  
          <!-- Configure user name authentication to use the Membership Provider -->  
          <userNameAuthentication userNamePasswordValidationMode ="MembershipProvider"   
                                  membershipProviderName ="SqlMembershipProvider"/>  
          <!-- Configure the service certificate -->  
          <serviceCertificate storeLocation ="LocalMachine"   
                              storeName ="My"   
                              x509FindType ="FindBySubjectName"  
                              findValue ="localhost" />  
        </serviceCredentials>  
        <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
        <serviceDebug includeExceptionDetailInFaults="false" />  
        <serviceMetadata httpGetEnabled="true"/>  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 Po uruchomieniu przykładu klient wywołuje różne operacje usługi pod trzema różnymi kontami użytkowników: Alicja, Robert i Charlie. Żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Wszystkie cztery wywołania wykonane jako użytkownik "Alicja" powinny się powieść. Użytkownik "Robert" powinien uzyskać błąd odmowy dostępu podczas próby wywołania metody dzielenia. Użytkownik "Charlie" powinien uzyskać błąd odmowy dostępu podczas próby wywołania metody mnożenia. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
2. Upewnij się, że skonfigurowano [bazę danych ASP.NET usługi aplikacji](https://go.microsoft.com/fwlink/?LinkId=94997).  
  
    > [!NOTE]
    > Jeśli używasz wersji SQL Server Express, nazwa serwera to .\SQLEXPRESS. Ten serwer powinien być używany podczas konfigurowania bazy danych ASP.NET Usługi aplikacji, a także parametrów połączenia Web. config.  
  
    > [!NOTE]
    > Konto procesu roboczego ASP.NET musi mieć uprawnienia do bazy danych utworzonej w tym kroku. Użyj narzędzia sqlcmd lub SQL Server Management Studio, aby to zrobić.  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, należy wykonać poniższe instrukcje.  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1. Upewnij się, że ścieżka zawiera folder, w którym znajduje się Makecert. exe.  
  
2. Uruchom setup. bat z przykładowego folderu instalacyjnego w wiersz polecenia dla deweloperów dla programu Visual Studio Uruchom z uprawnieniami administratora. Spowoduje to zainstalowanie certyfikatów usługi wymaganych do uruchomienia przykładu.  
  
3. Uruchamianie programu Client. exe z \client\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
4. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na wielu komputerach  
  
1. Utwórz katalog na komputerze usługi. Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu przy użyciu narzędzia do zarządzania Internet Information Services (IIS).  
  
2. Skopiuj pliki programu usługi z \Inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi. Upewnij się, że pliki zostały skopiowane do podkatalogu \Bin. Skopiuj także pliki Setup. bat, GetComputerName. vbs i Oczyść. bat do komputera usługi.  
  
3. Utwórz katalog na komputerze klienckim dla plików binarnych klienta.  
  
4. Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim. Skopiuj również do klienta pliki Setup. bat, Oczyść. bat i ImportServiceCert. bat.  
  
5. Na serwerze otwórz wiersz polecenia dla deweloperów programu Visual Studio z uprawnieniami administracyjnymi i uruchom `setup.bat service`. Uruchomienie `setup.bat` z argumentem `service` tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service. cer.  
  
6. Edytuj plik Web. config, aby odzwierciedlić nową nazwę certyfikatu (w atrybucie `findValue` w [\<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), która jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.  
  
7. Skopiuj plik. cer usługi z katalogu usługi do katalogu klienta na komputerze klienckim.  
  
8. W pliku Client. exe. config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi.  
  
9. Na kliencie Otwórz wiersz polecenia dla deweloperów programu Visual Studio z uprawnieniami administracyjnymi i uruchom ImportServiceCert. bat. Spowoduje to zaimportowanie certyfikatu usługi z pliku CER usługi do magazynu CurrentUser-TrustedPeople.  
  
10. Na komputerze klienckim uruchom program Client. exe z wiersza polecenia. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po przykładzie  
  
- Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.  
  
> [!NOTE]
> Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania tego przykładu między komputerami. W przypadku uruchamiania przykładów programu Windows Communication Foundation (WCF), które używają certyfikatów między komputerami, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w magazynie CurrentUser-TrustedPeople. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="the-setup-batch-file"></a>Plik wsadowy konfiguracji  
 Plik wsadowy Setup. bat dołączony do tego przykładu umożliwia skonfigurowanie serwera z odpowiednimi certyfikatami w celu uruchomienia aplikacji samohostowanej wymagającej zabezpieczeń opartych na certyfikatach serwera. Ten plik wsadowy należy zmodyfikować, aby mógł działać na różnych komputerach lub działać w nieobsługiwanym przypadku.  
  
 Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, dzięki czemu można je zmodyfikować tak, aby były uruchamiane w odpowiedniej konfiguracji.  
  
- Tworzenie certyfikatu serwera.  
  
     Poniższe wiersze z pliku wsadowego Setup. bat tworzą certyfikat serwera do użycia. Zmienna% nazwa_serwera% określa nazwę serwera. Zmień tę zmienną, aby określić własną nazwę serwera. Ten plik wsadowy jest domyślnie używany jako localhost.  
  
     Certyfikat jest przechowywany w magazynie (Personal) w lokalizacji magazynu LocalMachine.  
  
    ```console
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
- Instalowanie certyfikatu serwera w zaufanym magazynie certyfikatów klienta.  
  
     Następujące wiersze w pliku wsadowym Setup. bat kopiują certyfikat serwera do magazynu zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta. Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.  
  
    ```bat  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
