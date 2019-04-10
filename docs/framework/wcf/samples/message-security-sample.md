---
title: Zabezpieczenia komunikatów — przykład
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
ms.openlocfilehash: ad579705fa30e9b5179f2de4b829bd7f4a5817c2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302962"
---
# <a name="message-security-sample"></a><span data-ttu-id="2f6a4-102">Zabezpieczenia komunikatów — przykład</span><span class="sxs-lookup"><span data-stu-id="2f6a4-102">Message Security Sample</span></span>
<span data-ttu-id="2f6a4-103">Ten przykład demonstruje sposób implementacji aplikacji, która używa `basicHttpBinding` i zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-103">This sample demonstrates how to implement an application that uses the `basicHttpBinding` and message security.</span></span> <span data-ttu-id="2f6a4-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f6a4-105">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2f6a4-106">Tryb zabezpieczeń `basicHttpBinding` można ustawić następujące wartości: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` i `None`.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-106">The security mode of `basicHttpBinding` can be set to the following values: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` and `None`.</span></span> <span data-ttu-id="2f6a4-107">W poniższym przykładowym pliku App.config usługi, określa definicji punktu końcowego `basicHttpBinding` i zawiera odwołania do konfiguracji powiązania o nazwie `Binding1`, jak pokazano na poniższym Przykładowa konfiguracja:</span><span class="sxs-lookup"><span data-stu-id="2f6a4-107">In the following sample service App.config file, the endpoint definition specifies the `basicHttpBinding` and references a binding configuration named `Binding1`, as shown in the following sample configuration:</span></span>  
  
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
  
 <span data-ttu-id="2f6a4-108">Powiązania zestawów konfiguracyjnych `mode` atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) do `Message` i ustawia `clientCredentialType` atrybutu [ \<komunikatu >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)do `Certificate` jak pokazano w poniższym Przykładowa konfiguracja:</span><span class="sxs-lookup"><span data-stu-id="2f6a4-108">The binding configuration sets the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message` and sets the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) to `Certificate` as shown in the following sample configuration:</span></span>  
  
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
  
 <span data-ttu-id="2f6a4-109">Certyfikat używany przez usługę do samodzielnego uwierzytelnienia klienta znajduje się w sekcji zachowania pliku konfiguracyjnego obszarze `serviceCredentials` elementu.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-109">The certificate that the service uses to authenticate itself to the client is set in the behaviors section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="2f6a4-110">Tryb weryfikacji, który ma zastosowanie do certyfikatu używanego przez klienta do samodzielnego uwierzytelnienia usługi jest również ustawiona w sekcji zachowań w obszarze `clientCertificate` elementu.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-110">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the behaviors section under the `clientCertificate` element.</span></span>  
  
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
  
 <span data-ttu-id="2f6a4-111">Szczegóły tego samego powiązania i zabezpieczenia są określone w pliku konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-111">The same binding and security details are specified in the client configuration file.</span></span>  
  
 <span data-ttu-id="2f6a4-112">Tożsamość obiektu wywołującego jest wyświetlany w oknie konsoli usługi przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="2f6a4-112">The identity of the caller is displayed in the service console window by using the following code:</span></span>  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 <span data-ttu-id="2f6a4-113">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2f6a4-114">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-114">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="2f6a4-115">Aby skonfigurować i skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="2f6a4-115">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="2f6a4-116">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2f6a4-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2f6a4-117">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2f6a4-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="2f6a4-118">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="2f6a4-118">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="2f6a4-119">Uruchom Setup.bat jest z poziomu folderu instalacji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-119">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="2f6a4-120">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-120">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2f6a4-121">Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z wierszem polecenia Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-121">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="2f6a4-122">Wymaga to, że zmienna środowiskowa MSSDK odwołują się do katalogu, w którym jest zainstalowany zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-122">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="2f6a4-123">Ta zmienna środowiskowa jest automatycznie ustawiana w wierszu polecenia Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-123">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
2. <span data-ttu-id="2f6a4-124">Uruchamianie aplikacji usługi z \service\bin.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-124">Run the service application from \service\bin.</span></span>  
  
3. <span data-ttu-id="2f6a4-125">Uruchom aplikację klienta z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-125">Run the client application from \client\bin.</span></span> <span data-ttu-id="2f6a4-126">Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-126">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="2f6a4-127">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="2f6a4-127">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
5. <span data-ttu-id="2f6a4-128">Usuń certyfikaty, uruchamiając Cleanup.bat, po zakończeniu dla próbki.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-128">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="2f6a4-129">Inne przykłady zabezpieczeń za pomocą tych samych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-129">Other security samples use the same certificates.</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="2f6a4-130">Do uruchomienia przykładu na komputerach</span><span class="sxs-lookup"><span data-stu-id="2f6a4-130">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="2f6a4-131">Utwórz katalog na komputerze usługi na potrzeby pliki binarne usługi.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-131">Create a directory on the service machine for the service binaries.</span></span>  
  
2. <span data-ttu-id="2f6a4-132">Skopiuj pliki programu usługi do katalogu usługi na serwerze.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-132">Copy the service program files to the service directory on the server.</span></span> <span data-ttu-id="2f6a4-133">Także skopiować pliki Setup.bat, Cleanup.bat i ImportClientCert.bat do serwera.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-133">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the server.</span></span>  
  
3. <span data-ttu-id="2f6a4-134">Utwórz katalog na komputerze klienckim na potrzeby plików binarnych klienta.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-134">Create a directory on the client machine for the client binaries.</span></span>  
  
4. <span data-ttu-id="2f6a4-135">Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-135">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="2f6a4-136">Także skopiować pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-136">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="2f6a4-137">Na serwerze, uruchom `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-137">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="2f6a4-138">Uruchamianie `setup.bat` z `service` argument tworzy certyfikat usługi z w pełni kwalifikowana nazwa domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-138">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="2f6a4-139">Edytuj Service.exe.config, aby odzwierciedlały nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) elementu) który jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-139">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element) which is the same as the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="2f6a4-140">Również zmienić wartość adres bazowy, określ nazwę maszyny w pełni kwalifikowana zamiast nazwy localhost</span><span class="sxs-lookup"><span data-stu-id="2f6a4-140">Also change the value of the base address to specify a fully-qualified machine name instead of localhost</span></span>`.`  
  
7. <span data-ttu-id="2f6a4-141">Skopiuj plik Service.cer z katalogu usług w katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-141">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8. <span data-ttu-id="2f6a4-142">Na komputerze klienckim, należy uruchomić `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-142">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="2f6a4-143">Uruchamianie `setup.bat` z `client` argument tworzy certyfikat klienta o nazwie client.com i eksportuje certyfikat klienta do pliku o nazwie Client.cer.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-143">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="2f6a4-144">W pliku Client.exe.config na komputerze klienckim należy zmienić wartość adresu punktu końcowego, aby dopasować nowy adres usługi.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-144">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="2f6a4-145">Można to zrobić, zastępując localhost w pełni kwalifikowana nazwa domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-145">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="2f6a4-146">Również zmienić `findValue` atrybutu [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) na nową nazwę certyfikatu usługi, która jest w pełni kwalifikowana nazwa domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-146">Also change the `findValue` attribute of the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) to the new service certificate name which is the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="2f6a4-147">Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-147">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="2f6a4-148">Na komputerze klienckim należy uruchomić ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-148">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="2f6a4-149">To importuje certyfikatu usługi z pliku Service.cer, do CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-149">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="2f6a4-150">Na serwerze, uruchom ImportClientCert.bat to importuje certyfikat klienta z pliku Client.cer do LocalMachine - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-150">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="2f6a4-151">Na komputerze usługi należy uruchomić Service.exe z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-151">On the service machine, run Service.exe from a command prompt.</span></span>  
  
14. <span data-ttu-id="2f6a4-152">Na komputerze klienckim należy uruchomić Client.exe z okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-152">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
    1.  <span data-ttu-id="2f6a4-153">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="2f6a4-153">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="2f6a4-154">Aby wyczyścić zasoby po próbki</span><span class="sxs-lookup"><span data-stu-id="2f6a4-154">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="2f6a4-155">Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-155">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2f6a4-156">Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania tego przykładu na komputerach.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-156">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="2f6a4-157">Po uruchomieniu przykładów Windows Communication Foundation (WCF), które używają certyfikatów na maszynach, pamiętaj wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-157">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="2f6a4-158">Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Na przykład:</span><span class="sxs-lookup"><span data-stu-id="2f6a4-158">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example:</span></span> `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`  
  
> [!IMPORTANT]
>  <span data-ttu-id="2f6a4-159">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-159">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2f6a4-160">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="2f6a4-160">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2f6a4-161">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-161">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2f6a4-162">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2f6a4-162">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
