---
title: "Dostawca członkostwa i ról"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 34d89d937092f0feed9c103f05bf5db55c4a80e9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="membership-and-role-provider"></a>Dostawca członkostwa i ról
Dostawca członkostwa i ról w przykładzie pokazano, jak używać usługi [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawców członkostwa i ról w celu uwierzytelniania i autoryzacji klientów.  
  
 W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana przez Internet Information Services (IIS).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W przykładzie pokazano, jak:  
  
-   Klienta można uwierzytelniać przy użyciu kombinacji nazwy użytkownika i hasła.  
  
-   Serwer można sprawdzić poprawności poświadczeń klienta przed [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy członkostwa.  
  
-   Serwer mogą być uwierzytelniane za pomocą certyfikatu X.509 serwera.  
  
-   Serwer można mapować uwierzytelnionego klienta do roli przy użyciu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról.  
  
-   Serwer może za pomocą `PrincipalPermissionAttribute` kontrolować dostęp do niektórych metod, które są udostępniane przez usługę.  
  
 Dostawców członkostwa i ról są skonfigurowane do używania magazynu, obsługiwanej przez program SQL Server. Ciąg połączenia i różne opcje są określone w pliku konfiguracji usługi. Uzyskuje nazwę dostawcy członkostwa `SqlMembershipProvider` podczas uzyskuje nazwę dostawcy ról `SqlRoleProvider`.  
  
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
  
 Usługa udostępnia jeden punkt końcowy dla komunikacji z usługą, który został zdefiniowany przy użyciu pliku konfiguracji Web.config. Punkt końcowy składa się z adresu, powiązania i kontrakt. Powiązanie jest skonfigurowane z normą `wsHttpBinding`, która domyślnie korzysta z uwierzytelniania systemu Windows. W tym przykładzie ustawia standardowego `wsHttpBinding` uwierzytelniania nazwa użytkownika. Zachowanie Określa, że certyfikat serwera ma być używany do uwierzytelniania usługi. Certyfikat serwera musi zawierać taką samą wartość `SubjectName` jako `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element konfiguracji. Dodatkowo zachowanie Określa, że uwierzytelnianie nazwy użytkownika i hasła pary odbywa się za pośrednictwem [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy członkostwa i mapowanie roli jest wykonywane przez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról, określając nazwy zdefiniowane dla dwóch dostawców.  
  
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
  
 Po uruchomieniu próbki, gdy klient wywołuje różne operacje usługi na trzy różne konta użytkownika: Alicji, Roberta i marek. Operacja żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Wszystkie cztery wywołania jako użytkownik "Alicja" powinien kończą się pomyślnie. Użytkownik "Bob", należy uzyskać dostępu błąd podczas próby wywołania metody dzielenia. Użytkownik "Marek" należy uzyskać dostępu błąd podczas próby wywołania metody wielokrotnie. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
2.  Upewnij się, że skonfigurowano [bazy danych usług aplikacji ASP.NET](http://go.microsoft.com/fwlink/?LinkId=94997).  
  
    > [!NOTE]
    >  Jeśli używasz programu SQL Server Express Edition jest nazwą serwera. \SQLEXPRESS. Ten serwer powinien być używany podczas konfigurowania [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] usługi bazy danych aplikacji oraz jak parametry połączenia w pliku Web.config.  
  
    > [!NOTE]
    >  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Konta procesu roboczego musi mieć uprawnienia w bazie danych, która jest tworzona w tym kroku. Aby to zrobić, należy użyć narzędzia sqlcmd lub SQL Server Management Studio.  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, użyj poniższych instrukcji.  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Upewnij się, że ścieżka zawiera folder, w którym znajduje się Makecert.exe.  
  
2.  Uruchamianie pliku Setup.bat z folderu instalacyjnego próbki w wierszu polecenia programu Visual Studio uruchomione z uprawnieniami administratora. Spowoduje to zainstalowanie certyfikatów usługa wymagana do uruchomienia przykładu.  
  
3.  Uruchom Client.exe z \client\bin. Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.  
  
4.  Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na komputerach  
  
1.  Utwórz katalog na komputerze usługi. Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu przy użyciu narzędzia do zarządzania usług Internet Information Services (IIS).  
  
2.  Skopiuj pliki programu usługi z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi. Upewnij się, skopiuj pliki w podkatalogu \bin. Także skopiować pliki pliku Setup.bat, GetComputerName.vbs i Cleanup.bat na komputerze usługi.  
  
3.  Utwórz katalog na komputerze klienckim, aby pliki binarne klienta.  
  
4.  Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim. Także skopiować pliki pliku Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.  
  
5.  Na serwerze, otwórz wiersz polecenia programu Visual Studio z uprawnieniami administracyjnymi i uruchom `setup.bat service`. Uruchomiona `setup.bat` z `service` argument tworzy certyfikat usługi z domeny w pełni kwalifikowaną nazwę komputera i wyeksportuj certyfikat usługi do pliku o nazwie Service.cer.  
  
6.  Edytuj plik Web.config, aby odzwierciedlić nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), która jest taka sama jak w pełni kwalifikowaną nazwą domeny komputera.  
  
7.  Skopiuj plik Service.cer z katalogu usług do katalogu klienta na komputerze klienckim.  
  
8.  W pliku Client.exe.config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby dopasować nowego adresu usługi.  
  
9. Na komputerze klienckim otwórz wiersz polecenia programu Visual Studio z uprawnieniami administracyjnymi i uruchom ImportServiceCert.bat. Certyfikat usługi to importuje z pliku Service.cer do CurrentUser - TrustedPeople magazynu.  
  
10. Na komputerze klienckim należy uruchomić Client.exe z wiersza polecenia. Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po próbki  
  
-   Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.  
  
> [!NOTE]
>  Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania na komputerach w przykładzie. Jeśli uruchomiono [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] przykłady, które korzystają z certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu. Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="the-setup-batch-file"></a>Instalacyjny plik wsadowy  
 Plik wsadowy pliku Setup.bat uwzględnionych w tym przykładzie pozwala na skonfigurowanie serwera z odpowiednich certyfikatów do uruchomienia siebie aplikację, która wymaga zabezpieczeń na podstawie certyfikatu serwera. Ten plik wsadowy muszą zostać zmodyfikowane, aby pracować na komputerach lub do pracy w przypadku z systemem innym niż obsługiwany.  
  
 Poniżej zawiera krótki przegląd różnych sekcji pliki wsadowe tak, aby można modyfikować w prawidłowej konfiguracji.  
  
-   Tworzenie certyfikatu serwera.  
  
     Następujące wiersze z pliku wsadowego pliku Setup.bat utworzenie certyfikatu serwera do użycia. % Zmienna % nazwa_serwera Określa nazwę serwera. Zmień tę wartość, aby określić nazwę serwera. Ten plik wsadowy domyślnie go localhost.  
  
     Certyfikat jest przechowywany w magazynie LocalMachine lokalizacji w mojej (osobiste).  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta.  
  
     Następujące wiersze w pliku Setup.bat kopii pliku wsadowego certyfikatu serwera do klienta zaufanych osób magazynu. Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta. Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład certyfikat wystawiony przez Microsoft — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
## <a name="see-also"></a>Zobacz też
