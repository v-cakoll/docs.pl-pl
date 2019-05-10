---
title: Dostawca członkostwa i ról
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: 73084bb766274d6eab497555e82e029f94be0359
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638401"
---
# <a name="membership-and-role-provider"></a>Dostawca członkostwa i ról
Dostawca członkostwa i ról w przykładzie pokazano, jak używać usługi [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawców członkostwa i ról w celu uwierzytelniania i autoryzowania klientów.  
  
 W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana przez Internetowe usługi informacyjne (IIS).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 W przykładzie pokazano sposób:  
  
- Klienta można uwierzytelniać za pomocą kombinacji nazwy użytkownika i hasła.  
  
- Serwer można sprawdzić poprawności poświadczeń klienta względem [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy członkostwa.  
  
- Serwer mogą być uwierzytelniane przy użyciu certyfikatu X.509 serwera.  
  
- Serwer można mapować uwierzytelnionego klienta do roli przy użyciu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról.  
  
- Serwer może używać `PrincipalPermissionAttribute` możesz kontrolować dostęp do niektórych metod, które są udostępniane przez usługę.  
  
 Dostawców członkostwa i ról są skonfigurowane do używania w magazynie kopii przez program SQL Server. Różne opcje i parametry połączenia są określone w pliku konfiguracji usługi. Dostawca członkostwa jest nadawana nazwa `SqlMembershipProvider` podczas dostawcy ról jest nadawana nazwa `SqlRoleProvider`.  
  
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
  
 Usługa udostępnia jeden punkt końcowy do komunikacji z usługą, która jest zdefiniowana za pomocą pliku konfiguracji Web.config. Punkt końcowy składa się z adresu, powiązanie i kontrakt. Powiązanie jest skonfigurowane przy użyciu standardowego `wsHttpBinding`, która domyślnie korzysta z uwierzytelniania Windows. W tym przykładzie ustawia standard `wsHttpBinding` do korzystania z uwierzytelniania nazwy użytkownika. Zachowanie Określa, czy certyfikat serwera ma być używany do uwierzytelniania usługi. Certyfikat serwera musi zawierać taką samą wartość `SubjectName` jako `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element konfiguracji. Ponadto zachowanie oznacza, że uwierzytelnianie nazwy użytkownika i hasła pary odbywa się przez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy członkostwa i ról mapowanie odbywa się przez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról, określając nazwy zdefiniowane dla dwóch dostawców.  
  
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
  
 Po uruchomieniu przykładu, gdy klient wywołuje różne operacje usługi na trzy różne konta użytkownika: Alicji, Roberta i marek. Operacja żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Wszystkie cztery wywołania jako użytkownik "Alicja" powinien kończą się pomyślnie. Użytkownik "Bob" powinna pojawić się błąd odmowy, podczas próby wywołania metody dzielenia dostępu. Użytkownik "Marek" powinien otrzymać dostępu błąd podczas próby wywołania mnożenia metody. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
2. Upewnij się, że skonfigurowano [baza danych usług aplikacji ASP.NET](https://go.microsoft.com/fwlink/?LinkId=94997).  
  
    > [!NOTE]
    >  Jeśli używasz programu SQL Server Express Edition jest nazwą serwera. \SQLEXPRESS. Ten serwer powinna być używana podczas konfigurowania [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] baza danych usług aplikacji oraz jak parametry połączenia w pliku Web.config.  
  
    > [!NOTE]
    >  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Proces roboczy musi mieć uprawnienia w bazie danych, który jest tworzony w tym kroku. Aby to zrobić, należy użyć narzędzia sqlcmd lub SQL Server Management Studio.  
  
3. Do uruchomienia przykładu w konfiguracji o jednym lub wielu komputerze, użyj poniższych instrukcji.  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1. Upewnij się, że ścieżka zawiera folder, w którym znajduje się Makecert.exe.  
  
2. Uruchom Setup.bat jest z poziomu folderu instalacji przykładowej w wierszu polecenia dla deweloperów programu Visual Studio uruchomione z uprawnieniami administratora. Spowoduje to zainstalowanie certyfikaty usługi wymaganej do uruchomienia przykładu.  
  
3. Uruchom Client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.  
  
4. Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Do uruchomienia przykładu na komputerach  
  
1. Utwórz katalog na komputerze usługi. Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu przy użyciu narzędzia do zarządzania usług Internet Information Services (IIS).  
  
2. Skopiuj pliki programu usługi z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi. Upewnij się, skopiuj pliki w podkatalogu \bin. Także skopiować pliki Setup.bat, GetComputerName.vbs i Cleanup.bat na komputerze usługi.  
  
3. Utwórz katalog na komputerze klienckim, aby pliki binarne klienta.  
  
4. Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim. Także skopiować pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.  
  
5. Na serwerze, otwórz wiersz polecenia dla deweloperów programu Visual Studio z uprawnieniami administracyjnymi i uruchom `setup.bat service`. Uruchamianie `setup.bat` z `service` argument tworzy certyfikat usługi z w pełni kwalifikowana nazwa domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.  
  
6. Edytuj plik Web.config, aby odzwierciedlały nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), która jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.  
  
7. Skopiuj plik Service.cer z katalogu usług w katalogu klienta na komputerze klienckim.  
  
8. W pliku Client.exe.config na komputerze klienckim należy zmienić wartość adresu punktu końcowego, aby dopasować nowy adres usługi.  
  
9. Na komputerze klienckim otwórz wiersz polecenia dla deweloperów programu Visual Studio z uprawnieniami administracyjnymi i uruchom ImportServiceCert.bat. To importuje certyfikatu usługi z pliku Service.cer, do CurrentUser - TrustedPeople magazynu.  
  
10. Na komputerze klienckim należy uruchomić Client.exe z poziomu wiersza polecenia. Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić zasoby po próbki  
  
- Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.  
  
> [!NOTE]
>  Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania tego przykładu na komputerach. Po uruchomieniu przykładów Windows Communication Foundation (WCF), które używają certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="the-setup-batch-file"></a>Instalacyjny plik wsadowy  
 Plik wsadowy Setup.bat jest dołączone do tego przykładu umożliwia skonfigurowanie serwera za pomocą odpowiednich certyfikatów do uruchomienia aplikacji własnego wymagającego zabezpieczenia oparte na certyfikatach serwera. Ten plik wsadowy muszą zostać zmodyfikowane, działają na różnych komputerach lub działać w przypadku innych obsługiwanych.  
  
 Poniżej zawiera krótkie omówienie różne sekcje w plikach wsadowych, dzięki czemu można modyfikować do uruchomienia w odpowiedniej konfiguracji.  
  
- Tworzenie certyfikatu serwera.  
  
     Następujące wiersze z pliku wsadowego Setup.bat jest utworzenie certyfikatu serwera, który ma być używany. % Zmienna % nazwa_serwera Określa nazwę serwera. Zmieniać tej zmiennej do określenia nazwy serwera. Ten plik wsadowy ustawi dla niej domyślnie localhost.  
  
     Certyfikat jest przechowywany w magazynie użytkownika (osobistych), znajdujące się w lokalizacji magazynu LocalMachine.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
- Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta.  
  
     Przechowywać następujące wiersze w Setup.bat jest kopia pliku wsadowego certyfikatu serwera do klienta zaufanych osób. Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta. Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony przez Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
