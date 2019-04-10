---
title: Dostawca członkostwa i ról
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: b5cb743fb3533d2f3a8016c9357d6ead498a5878
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330093"
---
# <a name="membership-and-role-provider"></a><span data-ttu-id="5bd37-102">Dostawca członkostwa i ról</span><span class="sxs-lookup"><span data-stu-id="5bd37-102">Membership and Role Provider</span></span>
<span data-ttu-id="5bd37-103">Dostawca członkostwa i ról w przykładzie pokazano, jak używać usługi [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawców członkostwa i ról w celu uwierzytelniania i autoryzowania klientów.</span><span class="sxs-lookup"><span data-stu-id="5bd37-103">The Membership and Role Provider sample demonstrates how a service can use the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership and role providers to authenticate and authorize clients.</span></span>  
  
 <span data-ttu-id="5bd37-104">W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana przez Internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="5bd37-104">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5bd37-105">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5bd37-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5bd37-106">W przykładzie pokazano sposób:</span><span class="sxs-lookup"><span data-stu-id="5bd37-106">The sample demonstrates how:</span></span>  
  
-   <span data-ttu-id="5bd37-107">Klienta można uwierzytelniać za pomocą kombinacji nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="5bd37-107">A client can authenticate by using the username-password combination.</span></span>  
  
-   <span data-ttu-id="5bd37-108">Serwer można sprawdzić poprawności poświadczeń klienta względem [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy członkostwa.</span><span class="sxs-lookup"><span data-stu-id="5bd37-108">The server can validate the client credentials against the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider.</span></span>  
  
-   <span data-ttu-id="5bd37-109">Serwer mogą być uwierzytelniane przy użyciu certyfikatu X.509 serwera.</span><span class="sxs-lookup"><span data-stu-id="5bd37-109">The server can be authenticated by using the server's X.509 certificate.</span></span>  
  
-   <span data-ttu-id="5bd37-110">Serwer można mapować uwierzytelnionego klienta do roli przy użyciu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról.</span><span class="sxs-lookup"><span data-stu-id="5bd37-110">The server can map the authenticated client to a role by using the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider.</span></span>  
  
-   <span data-ttu-id="5bd37-111">Serwer może używać `PrincipalPermissionAttribute` możesz kontrolować dostęp do niektórych metod, które są udostępniane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="5bd37-111">The server can use the `PrincipalPermissionAttribute` to control access to certain methods that are exposed by the service.</span></span>  
  
 <span data-ttu-id="5bd37-112">Dostawców członkostwa i ról są skonfigurowane do używania w magazynie kopii przez program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5bd37-112">The membership and role providers are configured to use a store backed by SQL Server.</span></span> <span data-ttu-id="5bd37-113">Różne opcje i parametry połączenia są określone w pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="5bd37-113">A connection string and various options are specified in the service configuration file.</span></span> <span data-ttu-id="5bd37-114">Dostawca członkostwa jest nadawana nazwa `SqlMembershipProvider` podczas dostawcy ról jest nadawana nazwa `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="5bd37-114">The membership provider is given the name `SqlMembershipProvider` while the role provider is given the name `SqlRoleProvider`.</span></span>  
  
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
  
 <span data-ttu-id="5bd37-115">Usługa udostępnia jeden punkt końcowy do komunikacji z usługą, która jest zdefiniowana za pomocą pliku konfiguracji Web.config.</span><span class="sxs-lookup"><span data-stu-id="5bd37-115">The service exposes a single endpoint for communicating with the service, which is defined by using the Web.config configuration file.</span></span> <span data-ttu-id="5bd37-116">Punkt końcowy składa się z adresu, powiązanie i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="5bd37-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="5bd37-117">Powiązanie jest skonfigurowane przy użyciu standardowego `wsHttpBinding`, która domyślnie korzysta z uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="5bd37-117">The binding is configured with a standard `wsHttpBinding`, which defaults to using Windows authentication.</span></span> <span data-ttu-id="5bd37-118">W tym przykładzie ustawia standard `wsHttpBinding` do korzystania z uwierzytelniania nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5bd37-118">This sample sets the standard `wsHttpBinding` to use username authentication.</span></span> <span data-ttu-id="5bd37-119">Zachowanie Określa, czy certyfikat serwera ma być używany do uwierzytelniania usługi.</span><span class="sxs-lookup"><span data-stu-id="5bd37-119">The behavior specifies that the server certificate is to be used for service authentication.</span></span> <span data-ttu-id="5bd37-120">Certyfikat serwera musi zawierać taką samą wartość `SubjectName` jako `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5bd37-120">The server certificate must contain the same value for the `SubjectName` as the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) configuration element.</span></span> <span data-ttu-id="5bd37-121">Ponadto zachowanie oznacza, że uwierzytelnianie nazwy użytkownika i hasła pary odbywa się przez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy członkostwa i ról mapowanie odbywa się przez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról, określając nazwy zdefiniowane dla dwóch dostawców.</span><span class="sxs-lookup"><span data-stu-id="5bd37-121">In addition the behavior specifies that authentication of username-password pairs is performed by the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider and role mapping is performed by the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider by specifying the names defined for the two providers.</span></span>  
  
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
  
 <span data-ttu-id="5bd37-122">Po uruchomieniu przykładu, gdy klient wywołuje różne operacje usługi na trzy różne konta użytkownika: Alicji, Roberta i marek.</span><span class="sxs-lookup"><span data-stu-id="5bd37-122">When you run the sample, the client calls the various service operations under three different user accounts: Alice, Bob, and Charlie.</span></span> <span data-ttu-id="5bd37-123">Operacja żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="5bd37-123">The operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5bd37-124">Wszystkie cztery wywołania jako użytkownik "Alicja" powinien kończą się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5bd37-124">All four calls made as user "Alice" should succeed.</span></span> <span data-ttu-id="5bd37-125">Użytkownik "Bob" powinna pojawić się błąd odmowy, podczas próby wywołania metody dzielenia dostępu.</span><span class="sxs-lookup"><span data-stu-id="5bd37-125">User "Bob" should get an access denied error when trying to call the Divide method.</span></span> <span data-ttu-id="5bd37-126">Użytkownik "Marek" powinien otrzymać dostępu błąd podczas próby wywołania mnożenia metody.</span><span class="sxs-lookup"><span data-stu-id="5bd37-126">User "Charlie" should get an access denied error when trying to call the Multiply method.</span></span> <span data-ttu-id="5bd37-127">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="5bd37-127">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5bd37-128">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="5bd37-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5bd37-129">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5bd37-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
2. <span data-ttu-id="5bd37-130">Upewnij się, że skonfigurowano [baza danych usług aplikacji ASP.NET](https://go.microsoft.com/fwlink/?LinkId=94997).</span><span class="sxs-lookup"><span data-stu-id="5bd37-130">Ensure that you have configured the [ASP.NET Application Services Database](https://go.microsoft.com/fwlink/?LinkId=94997).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5bd37-131">Jeśli używasz programu SQL Server Express Edition jest nazwą serwera. \SQLEXPRESS.</span><span class="sxs-lookup"><span data-stu-id="5bd37-131">If you are running SQL Server Express Edition, your server name is .\SQLEXPRESS.</span></span> <span data-ttu-id="5bd37-132">Ten serwer powinna być używana podczas konfigurowania [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] baza danych usług aplikacji oraz jak parametry połączenia w pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="5bd37-132">This server should be used when configuring the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Application Services Database as well as in the Web.config connection string.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5bd37-133">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Proces roboczy musi mieć uprawnienia w bazie danych, który jest tworzony w tym kroku.</span><span class="sxs-lookup"><span data-stu-id="5bd37-133">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account must have permissions on the database that is created in this step.</span></span> <span data-ttu-id="5bd37-134">Aby to zrobić, należy użyć narzędzia sqlcmd lub SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="5bd37-134">Use the sqlcmd utility or SQL Server Management Studio to do this.</span></span>  
  
3. <span data-ttu-id="5bd37-135">Do uruchomienia przykładu w konfiguracji o jednym lub wielu komputerze, użyj poniższych instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5bd37-135">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="5bd37-136">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="5bd37-136">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="5bd37-137">Upewnij się, że ścieżka zawiera folder, w którym znajduje się Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="5bd37-137">Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="5bd37-138">Uruchom Setup.bat jest z poziomu folderu instalacji przykładowej w wierszu polecenia dla deweloperów programu Visual Studio uruchomione z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="5bd37-138">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio run with administrator privileges.</span></span> <span data-ttu-id="5bd37-139">Spowoduje to zainstalowanie certyfikaty usługi wymaganej do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="5bd37-139">This installs the service certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="5bd37-140">Uruchom Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="5bd37-140">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="5bd37-141">Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.</span><span class="sxs-lookup"><span data-stu-id="5bd37-141">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="5bd37-142">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="5bd37-142">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="5bd37-143">Do uruchomienia przykładu na komputerach</span><span class="sxs-lookup"><span data-stu-id="5bd37-143">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="5bd37-144">Utwórz katalog na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="5bd37-144">Create a directory on the service computer.</span></span> <span data-ttu-id="5bd37-145">Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu przy użyciu narzędzia do zarządzania usług Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="5bd37-145">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="5bd37-146">Skopiuj pliki programu usługi z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="5bd37-146">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="5bd37-147">Upewnij się, skopiuj pliki w podkatalogu \bin.</span><span class="sxs-lookup"><span data-stu-id="5bd37-147">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="5bd37-148">Także skopiować pliki Setup.bat, GetComputerName.vbs i Cleanup.bat na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="5bd37-148">Also copy the Setup.bat, GetComputerName.vbs, and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="5bd37-149">Utwórz katalog na komputerze klienckim, aby pliki binarne klienta.</span><span class="sxs-lookup"><span data-stu-id="5bd37-149">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="5bd37-150">Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="5bd37-150">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="5bd37-151">Także skopiować pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="5bd37-151">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="5bd37-152">Na serwerze, otwórz wiersz polecenia dla deweloperów programu Visual Studio z uprawnieniami administracyjnymi i uruchom `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="5bd37-152">On the server, open a Developer Command Prompt for Visual Studio with administrative privileges and run `setup.bat service`.</span></span> <span data-ttu-id="5bd37-153">Uruchamianie `setup.bat` z `service` argument tworzy certyfikat usługi z w pełni kwalifikowana nazwa domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.</span><span class="sxs-lookup"><span data-stu-id="5bd37-153">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="5bd37-154">Edytuj plik Web.config, aby odzwierciedlały nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), która jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="5bd37-154">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="5bd37-155">Skopiuj plik Service.cer z katalogu usług w katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="5bd37-155">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="5bd37-156">W pliku Client.exe.config na komputerze klienckim należy zmienić wartość adresu punktu końcowego, aby dopasować nowy adres usługi.</span><span class="sxs-lookup"><span data-stu-id="5bd37-156">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="5bd37-157">Na komputerze klienckim otwórz wiersz polecenia dla deweloperów programu Visual Studio z uprawnieniami administracyjnymi i uruchom ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="5bd37-157">On the client, open a Developer Command Prompt for Visual Studio with administrative privileges and run ImportServiceCert.bat.</span></span> <span data-ttu-id="5bd37-158">To importuje certyfikatu usługi z pliku Service.cer, do CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="5bd37-158">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="5bd37-159">Na komputerze klienckim należy uruchomić Client.exe z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="5bd37-159">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="5bd37-160">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="5bd37-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="5bd37-161">Aby wyczyścić zasoby po próbki</span><span class="sxs-lookup"><span data-stu-id="5bd37-161">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="5bd37-162">Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.</span><span class="sxs-lookup"><span data-stu-id="5bd37-162">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5bd37-163">Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania tego przykładu na komputerach.</span><span class="sxs-lookup"><span data-stu-id="5bd37-163">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="5bd37-164">Po uruchomieniu przykładów Windows Communication Foundation (WCF), które używają certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="5bd37-164">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="5bd37-165">Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="5bd37-165">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="the-setup-batch-file"></a><span data-ttu-id="5bd37-166">Instalacyjny plik wsadowy</span><span class="sxs-lookup"><span data-stu-id="5bd37-166">The Setup Batch File</span></span>  
 <span data-ttu-id="5bd37-167">Plik wsadowy Setup.bat jest dołączone do tego przykładu umożliwia skonfigurowanie serwera za pomocą odpowiednich certyfikatów do uruchomienia aplikacji własnego wymagającego zabezpieczenia oparte na certyfikatach serwera.</span><span class="sxs-lookup"><span data-stu-id="5bd37-167">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="5bd37-168">Ten plik wsadowy muszą zostać zmodyfikowane, działają na różnych komputerach lub działać w przypadku innych obsługiwanych.</span><span class="sxs-lookup"><span data-stu-id="5bd37-168">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="5bd37-169">Poniżej zawiera krótkie omówienie różne sekcje w plikach wsadowych, dzięki czemu można modyfikować do uruchomienia w odpowiedniej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5bd37-169">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
-   <span data-ttu-id="5bd37-170">Tworzenie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="5bd37-170">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="5bd37-171">Następujące wiersze z pliku wsadowego Setup.bat jest utworzenie certyfikatu serwera, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="5bd37-171">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="5bd37-172">% Zmienna % nazwa_serwera Określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="5bd37-172">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="5bd37-173">Zmieniać tej zmiennej do określenia nazwy serwera.</span><span class="sxs-lookup"><span data-stu-id="5bd37-173">Change this variable to specify your own server name.</span></span> <span data-ttu-id="5bd37-174">Ten plik wsadowy ustawi dla niej domyślnie localhost.</span><span class="sxs-lookup"><span data-stu-id="5bd37-174">This batch file defaults it to localhost.</span></span>  
  
     <span data-ttu-id="5bd37-175">Certyfikat jest przechowywany w magazynie użytkownika (osobistych), znajdujące się w lokalizacji magazynu LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="5bd37-175">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="5bd37-176">Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="5bd37-176">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="5bd37-177">Przechowywać następujące wiersze w Setup.bat jest kopia pliku wsadowego certyfikatu serwera do klienta zaufanych osób.</span><span class="sxs-lookup"><span data-stu-id="5bd37-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="5bd37-178">Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta.</span><span class="sxs-lookup"><span data-stu-id="5bd37-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="5bd37-179">Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony przez Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="5bd37-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
