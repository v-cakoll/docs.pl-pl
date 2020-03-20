---
title: Dostawca członkostwa i ról
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: 117be783c2d4a72ff9d1c4509566274b1043a43d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144464"
---
# <a name="membership-and-role-provider"></a>Dostawca członkostwa i ról
Przykład dostawcy członkostwa i dostawcy roli pokazuje, jak usługa może używać dostawców członkostwa ASP.NET i ról do uwierzytelniania i autoryzowania klientów.  
  
 W tym przykładzie klient jest aplikacją konsoli (.exe), a usługa jest obsługiwana przez internetowe usługi informacyjne (IIS).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W przykładzie pokazano, jak:  
  
- Klient może uwierzytelniać się przy użyciu kombinacji nazwa_użytkownika-hasło.  
  
- Serwer może sprawdzić poprawność poświadczeń klienta względem dostawcy członkostwa ASP.NET.  
  
- Serwer można uwierzytelnić przy użyciu certyfikatu X.509 serwera.  
  
- Serwer może mapować uwierzytelnionego klienta do roli przy użyciu dostawcy roli ASP.NET.  
  
- Serwer może służyć `PrincipalPermissionAttribute` do kontrolowania dostępu do niektórych metod, które są udostępniane przez usługę.  
  
 Dostawcy członkostwa i ról są skonfigurowani do używania magazynu wspieranego przez program SQL Server. W pliku konfiguracji usługi określono parametry połączenia i różne opcje. Dostawcy członkostwa jest nadana nazwa, `SqlMembershipProvider` podczas gdy `SqlRoleProvider`dostawca roli otrzymuje nazwę .  
  
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
  
 Usługa udostępnia pojedynczy punkt końcowy do komunikowania się z usługą, który jest zdefiniowany przy użyciu pliku konfiguracji Web.config. Punkt końcowy składa się z adresu, powiązania i umowy. Powiązanie jest skonfigurowane `wsHttpBinding`ze standardem , który domyślnie używa uwierzytelniania systemu Windows. W tym przykładzie ustawia się standard `wsHttpBinding` używania uwierzytelniania nazwy użytkownika. Zachowanie określa, że certyfikat serwera ma być używany do uwierzytelniania usługi. Certyfikat serwera musi zawierać taką `SubjectName` samą `findValue` wartość jak atrybut w [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element konfiguracji. Ponadto zachowanie określa, że uwierzytelnianie par hasła nazwy użytkownika jest wykonywane przez ASP.NET dostawcy członkostwa i mapowanie ról jest wykonywane przez dostawcę roli ASP.NET, określając nazwy zdefiniowane dla dwóch dostawców.  
  
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
  
 Po uruchomieniu próbki klient wywołuje różne operacje usługi w ramach trzech różnych kont użytkowników: Alicja, Robert i Charlie. Żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Wszystkie cztery wywołania wykonane jako użytkownik "Alicja" powinny zakończyć się pomyślnie. Użytkownik "Bob" powinien uzyskać błąd odmowy dostępu podczas próby wywołania Divide metody. Użytkownik "Charlie" powinien uzyskać błąd odmowy dostępu podczas próby wywołania Multiply metody. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Aby utworzyć wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w [części Uruchamianie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
2. Upewnij się, że skonfigurowano [ASP.NET bazę danych usług aplikacji](https://go.microsoft.com/fwlink/?LinkId=94997).  
  
    > [!NOTE]
    > Jeśli korzystasz z programu SQL Server Express Edition, nazwa serwera to .\SQLEXPRESS. Ten serwer powinien być używany podczas konfigurowania ASP.NET bazy danych usług aplikacji, a także w ciągu połączenia Web.config.  
  
    > [!NOTE]
    > Konto procesu ASP.NET procesu roboczego musi mieć uprawnienia do bazy danych utworzonej w tym kroku. Użyj narzędzia sqlcmd lub SQL Server Management Studio, aby to zrobić.  
  
3. Aby uruchomić próbkę w konfiguracji jedno- lub międzykomputerowej, należy użyć następujących instrukcji.  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić próbkę na tym samym komputerze  
  
1. Upewnij się, że ścieżka zawiera folder, w którym znajduje się plik Makecert.exe.  
  
2. Uruchom plik Setup.bat z przykładowego folderu instalacji w wierszu polecenia dewelopera dla programu Visual Studio z uprawnieniami administratora. Spowoduje to zainstalowanie certyfikatów usługi wymaganych do uruchomienia próbki.  
  
3. Uruchom program Client.exe z pliku \client\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
4. Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić próbkę na różnych komputerach  
  
1. Utwórz katalog na komputerze usługowym. Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu za pomocą narzędzia do zarządzania internetowymi usługami informacyjnymi (IIS).  
  
2. Skopiuj pliki programu serwisowego z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi. Upewnij się, że pliki są kopiowane w podkatalogu \bin. Skopiuj również pliki Setup.bat, GetComputerName.vbs i Cleanup.bat na komputer usługi.  
  
3. Utwórz katalog na komputerze klienckim dla plików binarnych klienta.  
  
4. Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim. Skopiuj również pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.  
  
5. Na serwerze otwórz wiersz polecenia dewelopera dla programu `setup.bat service`Visual Studio z uprawnieniami administracyjnymi i uruchom program . Uruchomiony `setup.bat` z `service` argumentem tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.  
  
6. Edytuj web.config, aby odzwierciedlić nową nazwę certyfikatu (w `findValue` atrybucie w [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), który jest taki sam jak w pełni kwalifikowana nazwa domeny komputera.  
  
7. Skopiuj plik Service.cer z katalogu usługi do katalogu klienta na komputerze klienckim.  
  
8. W pliku Client.exe.config na komputerze klienckim zmień wartość adresu punktu końcowego, aby dopasować go do nowego adresu usługi.  
  
9. Na kliencie otwórz wiersz polecenia dewelopera dla programu Visual Studio z uprawnieniami administracyjnymi i uruchom plik ImportServiceCert.bat. Spowoduje to zaimportować certyfikat usługi z pliku Service.cer do magazynu CurrentUser — TrustedPeople.  
  
10. Na komputerze klienckim uruchom program Client.exe z wiersza polecenia. Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby oczyścić po próbce  
  
- Uruchom Cleanup.bat w folderze przykłady po zakończeniu uruchamiania próbki.  
  
> [!NOTE]
> Ten skrypt nie usuwa certyfikatów usługi na kliencie podczas uruchamiania tego przykładu na komputerach. Jeśli uruchomiono przykłady Programu Windows Communication Foundation (WCF), które używają certyfikatów na różnych komputerach, należy wyczyścić certyfikaty usług, które zostały zainstalowane w magazynie CurrentUser — TrustedPeople. Aby to zrobić, należy `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` użyć następującego polecenia: Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="the-setup-batch-file"></a>Plik wsadowy instalatora  
 Plik wsadowy Setup.bat dołączony do tego przykładu umożliwia skonfigurowanie serwera z odpowiednimi certyfikatami do uruchamiania aplikacji hostowanej samodzielnie, która wymaga zabezpieczeń opartych na certyfikatach serwera. Ten plik wsadowy musi zostać zmodyfikowany, aby działał na różnych komputerach lub działał w przypadku nieobserwowanym.  
  
 Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, dzięki czemu można je zmodyfikować w celu uruchomienia w odpowiedniej konfiguracji.  
  
- Tworzenie certyfikatu serwera.  
  
     Następujące wiersze z pliku wsadowego Setup.bat tworzą certyfikat serwera, który ma być używany. Zmienna %SERVER_NAME% określa nazwę serwera. Zmień tę zmienną, aby określić własną nazwę serwera. Ten plik wsadowy domyślnie go localhost.  
  
     Certyfikat jest przechowywany w sklepie My (Personal) w lokalizacji sklepu LocalMachine.  
  
    ```console
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
- Instalowanie certyfikatu serwera w magazynie zaufanych certyfikatów klienta.  
  
     Następujące wiersze w pliku wsadowym Setup.bat kopiują certyfikat serwera do magazynu zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty generowane przez plik Makecert.exe nie są niejawnie zaufane przez system kliencki. Jeśli masz już certyfikat zakorzeniony w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten etap wypełniania magazynu certyfikatów klienta certyfikatem serwera nie jest wymagany.  
  
    ```bat  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
