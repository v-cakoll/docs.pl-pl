---
title: Zabezpieczenia komunikatów — przykład
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
ms.openlocfilehash: 85108e7d1a04f39ea9e0402b0e22e9d3f609f19e
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424092"
---
# <a name="message-security-sample"></a><span data-ttu-id="70bdf-102">Zabezpieczenia komunikatów — przykład</span><span class="sxs-lookup"><span data-stu-id="70bdf-102">Message Security Sample</span></span>
<span data-ttu-id="70bdf-103">Ten przykład pokazuje, jak zaimplementować aplikację, która używa `basicHttpBinding` i zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="70bdf-103">This sample demonstrates how to implement an application that uses the `basicHttpBinding` and message security.</span></span> <span data-ttu-id="70bdf-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) , który implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="70bdf-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="70bdf-105">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="70bdf-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="70bdf-106">Tryb zabezpieczeń `basicHttpBinding` można ustawić na następujące wartości: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` i `None`.</span><span class="sxs-lookup"><span data-stu-id="70bdf-106">The security mode of `basicHttpBinding` can be set to the following values: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` and `None`.</span></span> <span data-ttu-id="70bdf-107">W poniższym przykładowym pliku App Service. config definicja punktu końcowego określa `basicHttpBinding` i odwołuje się do konfiguracji powiązania o nazwie `Binding1`, jak pokazano w poniższej konfiguracji przykładowej:</span><span class="sxs-lookup"><span data-stu-id="70bdf-107">In the following sample service App.config file, the endpoint definition specifies the `basicHttpBinding` and references a binding configuration named `Binding1`, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- This endpoint is exposed at the base address provided by -->  
     <!-- host: http://localhost:8000/ServiceModelSamples/service.-->  
     <endpoint address=""  
               binding="basicHttpBinding"  
               bindingConfiguration="Binding1"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="70bdf-108">Konfiguracja powiązania ustawia atrybut `mode` [\<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) na `Message` i ustawia `clientCredentialType`\<[komunikat](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) >, jak pokazano w poniższej konfiguracji przykładowej:</span><span class="sxs-lookup"><span data-stu-id="70bdf-108">The binding configuration sets the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message` and sets the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) to `Certificate` as shown in the following sample configuration:</span></span>  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
    <binding name="Binding1" >  
      <security mode = "Message">  
        <message clientCredentialType="Certificate"/>  
      </security>  
    </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="70bdf-109">Certyfikat, którego używa Usługa do samodzielnego uwierzytelnienia klienta, jest ustawiany w sekcji zachowania w pliku konfiguracji w obszarze `serviceCredentials` elementu.</span><span class="sxs-lookup"><span data-stu-id="70bdf-109">The certificate that the service uses to authenticate itself to the client is set in the behaviors section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="70bdf-110">Tryb walidacji, który ma zastosowanie do certyfikatu używanego przez klienta do samodzielnego uwierzytelnienia w usłudze, jest również ustawiany w sekcji zachowania pod `clientCertificate` elementu.</span><span class="sxs-lookup"><span data-stu-id="70bdf-110">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the behaviors section under the `clientCertificate` element.</span></span>  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <!--The serviceCredentials behavior allows one to define a -->  
      <!--service certificate. A service certificate is used by a -->  
      <!--client to authenticate the service and provide message -->  
      <!-- protection. This configuration references the "localhost"-->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate findValue="localhost"  
               storeLocation="LocalMachine"   
               storeName="My" x509FindType="FindBySubjectName" />  
        <clientCertificate>  
          <!-- Setting the certificateValidationMode to -->  
          <!-- PeerOrChainTrust means that if the certificate -->  
          <!--is in the user's Trusted People store, then it is -->  
          <!-- trusted without performing a validation of the -->  
          <!-- certificate's issuer chain. This setting is used -->  
          <!-- here for convenience so that the sample can be run -->  
          <!-- without having to have certificates issued by a -->  
          <!-- certification authority (CA). -->  
          <!-- This setting is less secure than the default, -->  
          <!-- ChainTrust. The security implications of this -->  
          <!-- setting should be carefully considered before using -->  
          <!-- PeerOrChainTrust in production code. -->  
          <authentication   
                       certificateValidationMode="PeerOrChainTrust" />  
        </clientCertificate>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="70bdf-111">W pliku konfiguracji klienta określono te same informacje o powiązaniu i zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="70bdf-111">The same binding and security details are specified in the client configuration file.</span></span>  
  
 <span data-ttu-id="70bdf-112">Tożsamość obiektu wywołującego jest wyświetlana w oknie konsoli usługi przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="70bdf-112">The identity of the caller is displayed in the service console window by using the following code:</span></span>  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 <span data-ttu-id="70bdf-113">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="70bdf-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="70bdf-114">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="70bdf-114">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="70bdf-115">Aby skonfigurować i skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="70bdf-115">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="70bdf-116">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="70bdf-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="70bdf-117">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="70bdf-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="70bdf-118">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="70bdf-118">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="70bdf-119">Uruchom setup. bat z przykładowego folderu instalacyjnego.</span><span class="sxs-lookup"><span data-stu-id="70bdf-119">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="70bdf-120">Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="70bdf-120">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="70bdf-121">Plik wsadowy Setup. bat został zaprojektowany tak, aby można go było uruchomić z poziomu wiersza polecenia Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="70bdf-121">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="70bdf-122">Wymaga, aby zmienna środowiskowa MSSDK wskazywała katalog, w którym zainstalowano zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="70bdf-122">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="70bdf-123">Ta zmienna środowiskowa jest ustawiana automatycznie w wierszu polecenia Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="70bdf-123">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
2. <span data-ttu-id="70bdf-124">Uruchom aplikację usługi z \service\bin.</span><span class="sxs-lookup"><span data-stu-id="70bdf-124">Run the service application from \service\bin.</span></span>  
  
3. <span data-ttu-id="70bdf-125">Uruchom aplikację kliencką z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="70bdf-125">Run the client application from \client\bin.</span></span> <span data-ttu-id="70bdf-126">Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="70bdf-126">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="70bdf-127">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="70bdf-127">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
5. <span data-ttu-id="70bdf-128">Usuń certyfikaty, uruchamiając Oczyść. bat po zakończeniu korzystania z przykładu.</span><span class="sxs-lookup"><span data-stu-id="70bdf-128">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="70bdf-129">Inne przykłady zabezpieczeń używają tych samych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="70bdf-129">Other security samples use the same certificates.</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="70bdf-130">Aby uruchomić przykład na wielu maszynach</span><span class="sxs-lookup"><span data-stu-id="70bdf-130">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="70bdf-131">Utwórz katalog na komputerze usługi dla plików binarnych usługi.</span><span class="sxs-lookup"><span data-stu-id="70bdf-131">Create a directory on the service machine for the service binaries.</span></span>  
  
2. <span data-ttu-id="70bdf-132">Skopiuj pliki programu Service Files do katalogu usługi na serwerze programu.</span><span class="sxs-lookup"><span data-stu-id="70bdf-132">Copy the service program files to the service directory on the server.</span></span> <span data-ttu-id="70bdf-133">Skopiuj także pliki Setup. bat, Oczyść. bat i ImportClientCert. bat na serwer.</span><span class="sxs-lookup"><span data-stu-id="70bdf-133">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the server.</span></span>  
  
3. <span data-ttu-id="70bdf-134">Utwórz katalog na komputerze klienckim dla plików binarnych klienta.</span><span class="sxs-lookup"><span data-stu-id="70bdf-134">Create a directory on the client machine for the client binaries.</span></span>  
  
4. <span data-ttu-id="70bdf-135">Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="70bdf-135">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="70bdf-136">Skopiuj również do klienta pliki Setup. bat, Oczyść. bat i ImportServiceCert. bat.</span><span class="sxs-lookup"><span data-stu-id="70bdf-136">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="70bdf-137">Na serwerze programu Uruchom `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="70bdf-137">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="70bdf-138">Uruchomienie `setup.bat` z argumentem `service` tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny maszyny i eksportuje certyfikat usługi do pliku o nazwie Service. cer.</span><span class="sxs-lookup"><span data-stu-id="70bdf-138">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="70bdf-139">Edytuj plik Service. exe. config, aby odzwierciedlić nową nazwę certyfikatu (w atrybucie `findValue` w elemencie [\<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ), która jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="70bdf-139">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element) which is the same as the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="70bdf-140">Zmień również wartość adresu podstawowego, aby określić w pełni kwalifikowaną nazwę komputera zamiast hosta lokalnego`.`</span><span class="sxs-lookup"><span data-stu-id="70bdf-140">Also change the value of the base address to specify a fully-qualified machine name instead of localhost`.`</span></span>  
  
7. <span data-ttu-id="70bdf-141">Skopiuj plik. cer usługi z katalogu usługi do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="70bdf-141">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8. <span data-ttu-id="70bdf-142">Na kliencie Uruchom `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="70bdf-142">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="70bdf-143">Uruchomienie `setup.bat` z argumentem `client` tworzy certyfikat klienta o nazwie client.com i eksportuje certyfikat klienta do pliku o nazwie Client. cer.</span><span class="sxs-lookup"><span data-stu-id="70bdf-143">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="70bdf-144">W pliku Client. exe. config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi.</span><span class="sxs-lookup"><span data-stu-id="70bdf-144">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="70bdf-145">Można to zrobić, zastępując localhost nazwą domeny, w której jest w pełni kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="70bdf-145">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="70bdf-146">Zmień również atrybut `findValue` [\<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) na nową nazwę certyfikatu usługi, która jest w pełni kwalifikowaną nazwą domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="70bdf-146">Also change the `findValue` attribute of the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) to the new service certificate name which is the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="70bdf-147">Skopiuj plik. cer programu Client z katalogu Client do katalogu usługi na serwerze programu.</span><span class="sxs-lookup"><span data-stu-id="70bdf-147">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="70bdf-148">Na kliencie Uruchom program ImportServiceCert. bat.</span><span class="sxs-lookup"><span data-stu-id="70bdf-148">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="70bdf-149">Spowoduje to zaimportowanie certyfikatu usługi z pliku CER usługi do magazynu CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="70bdf-149">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="70bdf-150">Na serwerze programu Uruchom program ImportClientCert. bat, który importuje certyfikat klienta z pliku Client. cer do magazynu LocalMachine-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="70bdf-150">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="70bdf-151">Na maszynie usługi Uruchom program Service. exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="70bdf-151">On the service machine, run Service.exe from a command prompt.</span></span>  
  
14. <span data-ttu-id="70bdf-152">Na komputerze klienckim uruchom program Client. exe w oknie wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="70bdf-152">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
    1. <span data-ttu-id="70bdf-153">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="70bdf-153">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="70bdf-154">Aby wyczyścić po przykładzie</span><span class="sxs-lookup"><span data-stu-id="70bdf-154">To clean up after the sample</span></span>  
  
- <span data-ttu-id="70bdf-155">Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.</span><span class="sxs-lookup"><span data-stu-id="70bdf-155">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="70bdf-156">Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania tego przykładu między maszynami.</span><span class="sxs-lookup"><span data-stu-id="70bdf-156">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="70bdf-157">W przypadku uruchamiania przykładów programu Windows Communication Foundation (WCF), które używają certyfikatów między maszynami, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w magazynie CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="70bdf-157">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="70bdf-158">Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span><span class="sxs-lookup"><span data-stu-id="70bdf-158">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="70bdf-159">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="70bdf-159">The samples may already be installed on your machine.</span></span> <span data-ttu-id="70bdf-160">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="70bdf-160">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="70bdf-161">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70bdf-161">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="70bdf-162">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="70bdf-162">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
