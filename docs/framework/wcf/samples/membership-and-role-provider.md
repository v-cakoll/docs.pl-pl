---
title: Dostawca członkostwa i ról
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: e77e353fba194cb25b466387cf9def6773635e00
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591764"
---
# <a name="membership-and-role-provider"></a><span data-ttu-id="659be-102">Dostawca członkostwa i ról</span><span class="sxs-lookup"><span data-stu-id="659be-102">Membership and Role Provider</span></span>
<span data-ttu-id="659be-103">Przykład członkostwa i dostawcy ról pokazuje, jak usługa może używać członkostwa ASP.NET i dostawców ról do uwierzytelniania i autoryzowania klientów.</span><span class="sxs-lookup"><span data-stu-id="659be-103">The Membership and Role Provider sample demonstrates how a service can use the ASP.NET membership and role providers to authenticate and authorize clients.</span></span>  
  
 <span data-ttu-id="659be-104">W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="659be-104">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="659be-105">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="659be-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="659be-106">W przykładzie pokazano, jak:</span><span class="sxs-lookup"><span data-stu-id="659be-106">The sample demonstrates how:</span></span>  
  
- <span data-ttu-id="659be-107">Klient może uwierzytelniać się przy użyciu kombinacji nazwa użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="659be-107">A client can authenticate by using the username-password combination.</span></span>  
  
- <span data-ttu-id="659be-108">Serwer może sprawdzać poprawność poświadczeń klienta względem dostawcy członkostwa ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="659be-108">The server can validate the client credentials against the ASP.NET membership provider.</span></span>  
  
- <span data-ttu-id="659be-109">Serwer można uwierzytelnić przy użyciu certyfikatu X. 509 serwera.</span><span class="sxs-lookup"><span data-stu-id="659be-109">The server can be authenticated by using the server's X.509 certificate.</span></span>  
  
- <span data-ttu-id="659be-110">Serwer programu może mapować uwierzytelnionego klienta na rolę przy użyciu dostawcy roli ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="659be-110">The server can map the authenticated client to a role by using the ASP.NET role provider.</span></span>  
  
- <span data-ttu-id="659be-111">Serwer może korzystać z programu w `PrincipalPermissionAttribute` celu kontrolowania dostępu do niektórych metod, które są udostępniane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="659be-111">The server can use the `PrincipalPermissionAttribute` to control access to certain methods that are exposed by the service.</span></span>  
  
 <span data-ttu-id="659be-112">Dostawcy członkostwa i ról są skonfigurowani do używania magazynu obsługiwanego przez SQL Server.</span><span class="sxs-lookup"><span data-stu-id="659be-112">The membership and role providers are configured to use a store backed by SQL Server.</span></span> <span data-ttu-id="659be-113">W pliku konfiguracji usługi określono parametry połączenia i różne opcje.</span><span class="sxs-lookup"><span data-stu-id="659be-113">A connection string and various options are specified in the service configuration file.</span></span> <span data-ttu-id="659be-114">Dostawca członkostwa ma nazwę, `SqlMembershipProvider` podczas gdy dostawca roli otrzymuje nazwę `SqlRoleProvider` .</span><span class="sxs-lookup"><span data-stu-id="659be-114">The membership provider is given the name `SqlMembershipProvider` while the role provider is given the name `SqlRoleProvider`.</span></span>  
  
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
  
 <span data-ttu-id="659be-115">Usługa udostępnia jeden punkt końcowy do komunikacji z usługą, która jest definiowana przy użyciu pliku konfiguracyjnego Web. config.</span><span class="sxs-lookup"><span data-stu-id="659be-115">The service exposes a single endpoint for communicating with the service, which is defined by using the Web.config configuration file.</span></span> <span data-ttu-id="659be-116">Punkt końcowy składa się z adresu, powiązania i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="659be-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="659be-117">Powiązanie jest skonfigurowane przy użyciu standardu `wsHttpBinding` , który domyślnie używa uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="659be-117">The binding is configured with a standard `wsHttpBinding`, which defaults to using Windows authentication.</span></span> <span data-ttu-id="659be-118">Ten przykład ustawia standard `wsHttpBinding` do korzystania z uwierzytelniania nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="659be-118">This sample sets the standard `wsHttpBinding` to use username authentication.</span></span> <span data-ttu-id="659be-119">Zachowanie określa, że certyfikat serwera ma być używany do uwierzytelniania usługi.</span><span class="sxs-lookup"><span data-stu-id="659be-119">The behavior specifies that the server certificate is to be used for service authentication.</span></span> <span data-ttu-id="659be-120">Certyfikat serwera musi zawierać tę samą wartość `SubjectName` jako `findValue` atrybut w [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) elemencie Configuration.</span><span class="sxs-lookup"><span data-stu-id="659be-120">The server certificate must contain the same value for the `SubjectName` as the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) configuration element.</span></span> <span data-ttu-id="659be-121">Dodatkowo zachowanie określa, że uwierzytelnianie par username-Password jest wykonywane przez dostawcę członkostwa ASP.NET, a mapowanie roli jest wykonywane przez dostawcę roli ASP.NET przez określenie nazw zdefiniowanych dla dwóch dostawców.</span><span class="sxs-lookup"><span data-stu-id="659be-121">In addition the behavior specifies that authentication of username-password pairs is performed by the ASP.NET membership provider and role mapping is performed by the ASP.NET role provider by specifying the names defined for the two providers.</span></span>  
  
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
  
 <span data-ttu-id="659be-122">Po uruchomieniu przykładu klient wywołuje różne operacje usługi pod trzema różnymi kontami użytkowników: Alicja, Robert i Charlie.</span><span class="sxs-lookup"><span data-stu-id="659be-122">When you run the sample, the client calls the various service operations under three different user accounts: Alice, Bob, and Charlie.</span></span> <span data-ttu-id="659be-123">Żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="659be-123">The operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="659be-124">Wszystkie cztery wywołania wykonane jako użytkownik "Alicja" powinny się powieść.</span><span class="sxs-lookup"><span data-stu-id="659be-124">All four calls made as user "Alice" should succeed.</span></span> <span data-ttu-id="659be-125">Użytkownik "Robert" powinien uzyskać błąd odmowy dostępu podczas próby wywołania metody dzielenia.</span><span class="sxs-lookup"><span data-stu-id="659be-125">User "Bob" should get an access denied error when trying to call the Divide method.</span></span> <span data-ttu-id="659be-126">Użytkownik "Charlie" powinien uzyskać błąd odmowy dostępu podczas próby wywołania metody mnożenia.</span><span class="sxs-lookup"><span data-stu-id="659be-126">User "Charlie" should get an access denied error when trying to call the Multiply method.</span></span> <span data-ttu-id="659be-127">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="659be-127">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="659be-128">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="659be-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="659be-129">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="659be-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
2. <span data-ttu-id="659be-130">Upewnij się, że skonfigurowano [bazę danych ASP.NET usługi aplikacji](https://go.microsoft.com/fwlink/?LinkId=94997).</span><span class="sxs-lookup"><span data-stu-id="659be-130">Ensure that you have configured the [ASP.NET Application Services Database](https://go.microsoft.com/fwlink/?LinkId=94997).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="659be-131">Jeśli używasz wersji SQL Server Express, nazwa serwera to .\SQLEXPRESS.</span><span class="sxs-lookup"><span data-stu-id="659be-131">If you are running SQL Server Express Edition, your server name is .\SQLEXPRESS.</span></span> <span data-ttu-id="659be-132">Ten serwer powinien być używany podczas konfigurowania bazy danych ASP.NET Usługi aplikacji, a także parametrów połączenia Web. config.</span><span class="sxs-lookup"><span data-stu-id="659be-132">This server should be used when configuring the ASP.NET Application Services Database as well as in the Web.config connection string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="659be-133">Konto procesu roboczego ASP.NET musi mieć uprawnienia do bazy danych utworzonej w tym kroku.</span><span class="sxs-lookup"><span data-stu-id="659be-133">The ASP.NET worker process account must have permissions on the database that is created in this step.</span></span> <span data-ttu-id="659be-134">Użyj narzędzia sqlcmd lub SQL Server Management Studio, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="659be-134">Use the sqlcmd utility or SQL Server Management Studio to do this.</span></span>  
  
3. <span data-ttu-id="659be-135">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, należy wykonać poniższe instrukcje.</span><span class="sxs-lookup"><span data-stu-id="659be-135">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="659be-136">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="659be-136">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="659be-137">Upewnij się, że ścieżka zawiera folder, w którym znajduje się Makecert. exe.</span><span class="sxs-lookup"><span data-stu-id="659be-137">Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="659be-138">Uruchom setup. bat z przykładowego folderu instalacyjnego w wiersz polecenia dla deweloperów dla programu Visual Studio Uruchom z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="659be-138">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio run with administrator privileges.</span></span> <span data-ttu-id="659be-139">Spowoduje to zainstalowanie certyfikatów usługi wymaganych do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="659be-139">This installs the service certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="659be-140">Uruchamianie programu Client. exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="659be-140">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="659be-141">Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="659be-141">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="659be-142">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="659be-142">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="659be-143">Aby uruchomić przykład na wielu komputerach</span><span class="sxs-lookup"><span data-stu-id="659be-143">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="659be-144">Utwórz katalog na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="659be-144">Create a directory on the service computer.</span></span> <span data-ttu-id="659be-145">Utwórz aplikację wirtualną o nazwie servicemodelsamples dla tego katalogu przy użyciu narzędzia do zarządzania Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="659be-145">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="659be-146">Skopiuj pliki programu usługi z \Inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="659be-146">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="659be-147">Upewnij się, że pliki zostały skopiowane do podkatalogu \Bin.</span><span class="sxs-lookup"><span data-stu-id="659be-147">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="659be-148">Skopiuj także pliki Setup. bat, GetComputerName. vbs i Oczyść. bat do komputera usługi.</span><span class="sxs-lookup"><span data-stu-id="659be-148">Also copy the Setup.bat, GetComputerName.vbs, and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="659be-149">Utwórz katalog na komputerze klienckim dla plików binarnych klienta.</span><span class="sxs-lookup"><span data-stu-id="659be-149">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="659be-150">Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="659be-150">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="659be-151">Skopiuj również do klienta pliki Setup. bat, Oczyść. bat i ImportServiceCert. bat.</span><span class="sxs-lookup"><span data-stu-id="659be-151">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="659be-152">Na serwerze otwórz wiersz polecenia dla deweloperów programu Visual Studio z uprawnieniami administracyjnymi i uruchom polecenie `setup.bat service` .</span><span class="sxs-lookup"><span data-stu-id="659be-152">On the server, open a Developer Command Prompt for Visual Studio with administrative privileges and run `setup.bat service`.</span></span> <span data-ttu-id="659be-153">Uruchomienie `setup.bat` z `service` argumentem tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service. cer.</span><span class="sxs-lookup"><span data-stu-id="659be-153">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="659be-154">Edytuj plik Web. config, aby odzwierciedlić nową nazwę certyfikatu (w `findValue` atrybucie w [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ), która jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="659be-154">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="659be-155">Skopiuj plik. cer usługi z katalogu usługi do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="659be-155">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="659be-156">W pliku Client. exe. config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi.</span><span class="sxs-lookup"><span data-stu-id="659be-156">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="659be-157">Na kliencie Otwórz wiersz polecenia dla deweloperów programu Visual Studio z uprawnieniami administracyjnymi i uruchom ImportServiceCert. bat.</span><span class="sxs-lookup"><span data-stu-id="659be-157">On the client, open a Developer Command Prompt for Visual Studio with administrative privileges and run ImportServiceCert.bat.</span></span> <span data-ttu-id="659be-158">Spowoduje to zaimportowanie certyfikatu usługi z pliku CER usługi do magazynu CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="659be-158">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="659be-159">Na komputerze klienckim uruchom program Client. exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="659be-159">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="659be-160">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="659be-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="659be-161">Aby wyczyścić po przykładzie</span><span class="sxs-lookup"><span data-stu-id="659be-161">To clean up after the sample</span></span>  
  
- <span data-ttu-id="659be-162">Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.</span><span class="sxs-lookup"><span data-stu-id="659be-162">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="659be-163">Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania tego przykładu między komputerami.</span><span class="sxs-lookup"><span data-stu-id="659be-163">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="659be-164">W przypadku uruchamiania przykładów programu Windows Communication Foundation (WCF), które używają certyfikatów między komputerami, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w magazynie CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="659be-164">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="659be-165">Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="659be-165">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="the-setup-batch-file"></a><span data-ttu-id="659be-166">Plik wsadowy konfiguracji</span><span class="sxs-lookup"><span data-stu-id="659be-166">The Setup Batch File</span></span>  
 <span data-ttu-id="659be-167">Plik wsadowy Setup. bat dołączony do tego przykładu umożliwia skonfigurowanie serwera z odpowiednimi certyfikatami w celu uruchomienia aplikacji samohostowanej wymagającej zabezpieczeń opartych na certyfikatach serwera.</span><span class="sxs-lookup"><span data-stu-id="659be-167">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="659be-168">Ten plik wsadowy należy zmodyfikować, aby mógł działać na różnych komputerach lub działać w nieobsługiwanym przypadku.</span><span class="sxs-lookup"><span data-stu-id="659be-168">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="659be-169">Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, dzięki czemu można je zmodyfikować tak, aby były uruchamiane w odpowiedniej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="659be-169">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
- <span data-ttu-id="659be-170">Tworzenie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="659be-170">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="659be-171">Poniższe wiersze z pliku wsadowego Setup. bat tworzą certyfikat serwera do użycia.</span><span class="sxs-lookup"><span data-stu-id="659be-171">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="659be-172">Zmienna% SERVER_NAME% określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="659be-172">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="659be-173">Zmień tę zmienną, aby określić własną nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="659be-173">Change this variable to specify your own server name.</span></span> <span data-ttu-id="659be-174">Ten plik wsadowy jest domyślnie używany jako localhost.</span><span class="sxs-lookup"><span data-stu-id="659be-174">This batch file defaults it to localhost.</span></span>  
  
     <span data-ttu-id="659be-175">Certyfikat jest przechowywany w magazynie (Personal) w lokalizacji magazynu LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="659be-175">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```console
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
- <span data-ttu-id="659be-176">Instalowanie certyfikatu serwera w zaufanym magazynie certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="659be-176">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="659be-177">Następujące wiersze w pliku wsadowym Setup. bat kopiują certyfikat serwera do magazynu zaufanych osób klienta.</span><span class="sxs-lookup"><span data-stu-id="659be-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="659be-178">Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta.</span><span class="sxs-lookup"><span data-stu-id="659be-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="659be-179">Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="659be-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```bat  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
