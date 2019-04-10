---
title: Zabezpieczenia komunikatów w ramach kolejkowania komunikatów
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: 9e9067c38d86bb74c569b6d648d84c7c9ff6fac6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318601"
---
# <a name="message-security-over-message-queuing"></a><span data-ttu-id="47e80-102">Zabezpieczenia komunikatów w ramach kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="47e80-102">Message Security over Message Queuing</span></span>
<span data-ttu-id="47e80-103">Ten przykład demonstruje sposób implementacji aplikacji, która korzysta z protokołu WS-Security przy użyciu uwierzytelniania certyfikatu X.509v3 dla klienta i wymaga uwierzytelnienia serwera za pomocą certyfikatu X.509v3 serwera za pośrednictwem usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="47e80-103">This sample demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span> <span data-ttu-id="47e80-104">Komunikat zabezpieczeń jest czasem korzystniejsze, aby upewnić się, że komunikaty w magazynie usługi MSMQ pozostają zaszyfrowane i aplikacji można wykonać swoje własne uwierzytelniania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="47e80-104">Message security is sometimes more desirable to ensure that the messages in the MSMQ store stay encrypted and the application can perform its own authentication of the message.</span></span>

 <span data-ttu-id="47e80-105">Ten przykład jest oparty na [dokonana transakcja powiązania usługi MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="47e80-105">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="47e80-106">Komunikaty są szyfrowane i podpisany.</span><span class="sxs-lookup"><span data-stu-id="47e80-106">The messages are encrypted and signed.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="47e80-107">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="47e80-107">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="47e80-108">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="47e80-108">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="47e80-109">Jeśli usługa jest uruchamiana pierwszy, będzie sprawdzał, aby upewnić się, że kolejka jest obecny.</span><span class="sxs-lookup"><span data-stu-id="47e80-109">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="47e80-110">Jeśli kolejka nie jest obecny, będzie utworzyć usługę.</span><span class="sxs-lookup"><span data-stu-id="47e80-110">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="47e80-111">Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub możesz je utworzyć za pomocą Menedżera kolejki usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="47e80-111">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="47e80-112">Wykonaj następujące kroki, aby utworzyć kolejkę w programie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="47e80-112">Follow these steps to create a queue in Windows 2008.</span></span>

    1.  <span data-ttu-id="47e80-113">Otwórz Menedżera serwera w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="47e80-113">Open Server Manager in Visual Studio 2012.</span></span>

    2.  <span data-ttu-id="47e80-114">Rozwiń **funkcji** kartę.</span><span class="sxs-lookup"><span data-stu-id="47e80-114">Expand the **Features** tab.</span></span>

    3.  <span data-ttu-id="47e80-115">Kliknij prawym przyciskiem myszy **prywatnej kolejki komunikatów**i wybierz **New**, **kolejki prywatnej**.</span><span class="sxs-lookup"><span data-stu-id="47e80-115">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4.  <span data-ttu-id="47e80-116">Sprawdź **transakcyjna** pole.</span><span class="sxs-lookup"><span data-stu-id="47e80-116">Check the **Transactional** box.</span></span>

    5.  <span data-ttu-id="47e80-117">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="47e80-117">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="47e80-118">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="47e80-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="47e80-119">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="47e80-119">To run the sample on the same computer</span></span>

1. <span data-ttu-id="47e80-120">Upewnij się, że ścieżka zawiera folder, który zawiera Makecert.exe i FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="47e80-120">Ensure that the path includes the folder that contains Makecert.exe and FindPrivateKey.exe.</span></span>

2. <span data-ttu-id="47e80-121">Uruchom Setup.bat jest z poziomu folderu instalacji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="47e80-121">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="47e80-122">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="47e80-122">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="47e80-123">Upewnij się, usunąć certyfikaty, uruchamiając Cleanup.bat po zakończeniu dla próbki.</span><span class="sxs-lookup"><span data-stu-id="47e80-123">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="47e80-124">Inne przykłady zabezpieczeń za pomocą tych samych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="47e80-124">Other security samples use the same certificates.</span></span>  
  
3. <span data-ttu-id="47e80-125">Uruchom Service.exe z \service\bin.</span><span class="sxs-lookup"><span data-stu-id="47e80-125">Launch Service.exe from \service\bin.</span></span>  
  
4. <span data-ttu-id="47e80-126">Uruchom Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="47e80-126">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="47e80-127">Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.</span><span class="sxs-lookup"><span data-stu-id="47e80-127">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="47e80-128">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="47e80-128">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="47e80-129">Do uruchomienia przykładu na komputerach</span><span class="sxs-lookup"><span data-stu-id="47e80-129">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="47e80-130">Skopiuj pliki Setup.bat, Cleanup.bat i ImportClientCert.bat komputer usługi.</span><span class="sxs-lookup"><span data-stu-id="47e80-130">Copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
2. <span data-ttu-id="47e80-131">Utwórz katalog na komputerze klienckim, aby pliki binarne klienta.</span><span class="sxs-lookup"><span data-stu-id="47e80-131">Create a directory on the client computer for the client binaries.</span></span>  
  
3. <span data-ttu-id="47e80-132">Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="47e80-132">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="47e80-133">Także skopiować pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="47e80-133">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
4. <span data-ttu-id="47e80-134">Na serwerze, uruchom `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="47e80-134">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="47e80-135">Uruchamianie `setup.bat` z `service` argument tworzy certyfikat usługi z w pełni kwalifikowana nazwa domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.</span><span class="sxs-lookup"><span data-stu-id="47e80-135">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
5. <span data-ttu-id="47e80-136">Edytuj service.exe.config usługi, aby odzwierciedlały nową nazwę certyfikatu (w `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) który jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="47e80-136">Edit service's service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
6. <span data-ttu-id="47e80-137">Skopiuj plik Service.cer z katalogu usług w katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="47e80-137">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
7. <span data-ttu-id="47e80-138">Na komputerze klienckim, należy uruchomić `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="47e80-138">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="47e80-139">Uruchamianie `setup.bat` z `client` argument tworzy certyfikat klienta o nazwie client.com i eksportuje certyfikat klienta do pliku o nazwie Client.cer.</span><span class="sxs-lookup"><span data-stu-id="47e80-139">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
8. <span data-ttu-id="47e80-140">W pliku Client.exe.config na komputerze klienckim należy zmienić wartość adresu punktu końcowego, aby dopasować nowy adres usługi.</span><span class="sxs-lookup"><span data-stu-id="47e80-140">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="47e80-141">To zrobić, zastępując localhost w pełni kwalifikowana nazwa domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="47e80-141">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  <span data-ttu-id="47e80-142">Należy także zmienić nazwę certyfikatu usługi, aby być taka sama jak w pełni kwalifikowana nazwa domeny komputera usługi (w `findValue` atrybutu w `defaultCertificate` elementu `serviceCertificate` w obszarze `clientCredentials`).</span><span class="sxs-lookup"><span data-stu-id="47e80-142">You must also change the certificate name of the service to be the same as the fully-qualified domain name of the service computer (in the `findValue` attribute in the `defaultCertificate` element of `serviceCertificate` under `clientCredentials`).</span></span>  
  
9. <span data-ttu-id="47e80-143">Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.</span><span class="sxs-lookup"><span data-stu-id="47e80-143">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
10. <span data-ttu-id="47e80-144">Na komputerze klienckim, należy uruchomić `ImportServiceCert.bat`.</span><span class="sxs-lookup"><span data-stu-id="47e80-144">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="47e80-145">To importuje certyfikatu usługi z pliku Service.cer, do CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="47e80-145">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
11. <span data-ttu-id="47e80-146">Na serwerze, uruchom `ImportClientCert.bat`, to importuje certyfikat klienta z pliku Client.cer do LocalMachine - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="47e80-146">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="47e80-147">Na komputerze usługi Service.exe należy uruchomić z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="47e80-147">On the service computer, launch Service.exe from the command prompt.</span></span>  
  
13. <span data-ttu-id="47e80-148">Na komputerze klienckim należy uruchomić Client.exe w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="47e80-148">On the client computer, launch Client.exe from the command prompt.</span></span> <span data-ttu-id="47e80-149">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="47e80-149">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="47e80-150">Aby wyczyścić zasoby po próbki</span><span class="sxs-lookup"><span data-stu-id="47e80-150">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="47e80-151">Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.</span><span class="sxs-lookup"><span data-stu-id="47e80-151">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="47e80-152">Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania tego przykładu na komputerach.</span><span class="sxs-lookup"><span data-stu-id="47e80-152">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="47e80-153">Po uruchomieniu przykładów Windows Communication Foundation (WCF), które używają certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="47e80-153">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="47e80-154">Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="47e80-154">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>

## <a name="requirements"></a><span data-ttu-id="47e80-155">Wymagania</span><span class="sxs-lookup"><span data-stu-id="47e80-155">Requirements</span></span>
 <span data-ttu-id="47e80-156">Ten przykładowy skrypt wymaga, że usługa MSMQ jest zainstalowana i uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="47e80-156">This sample requires that MSMQ is installed and running.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="47e80-157">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="47e80-157">Demonstrates</span></span>
 <span data-ttu-id="47e80-158">Klient szyfruje wiadomości przy użyciu klucza publicznego usługi i zarejestruje komunikat przy użyciu własnego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="47e80-158">The client encrypts the message using the public key of the service and signs the message using its own certificate.</span></span> <span data-ttu-id="47e80-159">Usługi, odczytywanie wiadomości z kolejki uwierzytelnianie certyfikatu klienta przy użyciu certyfikatu w magazynie zaufanych osób.</span><span class="sxs-lookup"><span data-stu-id="47e80-159">The service reading the message from the queue authenticates the client certificate with the certificate in its trusted people store.</span></span> <span data-ttu-id="47e80-160">Następnie odszyfrowuje komunikat i wysyła komunikat do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="47e80-160">It then decrypts the message and dispatches the message to the service operation.</span></span>

 <span data-ttu-id="47e80-161">Ponieważ komunikat usług Windows Communication Foundation (WCF) jest przenoszone jako ładunek w treści wiadomości usługi MSMQ, treść pozostają zaszyfrowane w magazynie usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="47e80-161">Because the Windows Communication Foundation (WCF) message is carried as a payload in the body of the MSMQ message, the body remains encrypted in the MSMQ store.</span></span> <span data-ttu-id="47e80-162">W ten sposób wiadomości przed ujawnieniem niechciane wiadomości.</span><span class="sxs-lookup"><span data-stu-id="47e80-162">This secures the message from unwanted disclosure of the message.</span></span> <span data-ttu-id="47e80-163">Zwróć uwagę, że usługi MSMQ, sama nie świadomość tego, czy komunikat go prowadzi są szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="47e80-163">Note that MSMQ itself is not aware whether the message it is carrying is encrypted.</span></span>

 <span data-ttu-id="47e80-164">W przykładzie pokazano sposób wzajemnego uwierzytelniania wglądu do wiadomości poziom może być używany z usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="47e80-164">The sample demonstrates how mutual authentication at the message level can be used with MSMQ.</span></span> <span data-ttu-id="47e80-165">Certyfikaty są wymieniane poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="47e80-165">The certificates are exchanged out-of-band.</span></span> <span data-ttu-id="47e80-166">Jest to zawsze w przypadku aplikacji umieszczonych w kolejce, ponieważ usługa i klient nie ma być uruchomiona w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="47e80-166">This is always the case with queued application because the service and the client do not have to be up and running at the same time.</span></span>

## <a name="description"></a><span data-ttu-id="47e80-167">Opis</span><span class="sxs-lookup"><span data-stu-id="47e80-167">Description</span></span>
 <span data-ttu-id="47e80-168">Przykładowy kod klienta i usługi są takie same jak [dokonana transakcja powiązania usługi MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) próbki z jedną różnicą.</span><span class="sxs-lookup"><span data-stu-id="47e80-168">The sample client and service code are the same as the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample with one difference.</span></span> <span data-ttu-id="47e80-169">Kontrakt operacji jest oznaczony za pomocą poziom ochrony, co sugeruje, że wiadomości muszą być podpisane i szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="47e80-169">The operation contract is annotated with protection level, which suggests that the message must be signed and encrypted.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="47e80-170">Aby upewnić się, że wiadomość jest zabezpieczona przy użyciu tokenu wymagany do identyfikowania usługi i klienta, App.config zawiera informacji o poświadczeniach.</span><span class="sxs-lookup"><span data-stu-id="47e80-170">To ensure that the message is secured using the required token to identify the service and client, the App.config contains credential information.</span></span>

 <span data-ttu-id="47e80-171">Konfiguracja klienta Określa certyfikat usługi do uwierzytelniania usługi.</span><span class="sxs-lookup"><span data-stu-id="47e80-171">The client configuration specifies the service certificate to authenticate the service.</span></span> <span data-ttu-id="47e80-172">Użyto jej magazynie jako zaufany magazyn do zależą od ważności usługi.</span><span class="sxs-lookup"><span data-stu-id="47e80-172">It uses its LocalMachine store as the trusted store to rely on the validity of the service.</span></span> <span data-ttu-id="47e80-173">Określa również certyfikat klienta, który jest dołączony komunikat do usługi uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="47e80-173">It also specifies the client certificate that is attached with the message for service authentication of the client.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <system.serviceModel>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                binding="netMsmqBinding"
                bindingConfiguration="messageSecurityBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor"
                behaviorConfiguration="ClientCertificateBehavior" />
    </client>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate"/>
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <!--
        The clientCredentials behavior allows one to define a certificate to present to a service.
        A certificate is used by a client to authenticate itself to the service and provide message integrity.
        This configuration references the "client.com" certificate installed during the setup instructions.
        -->
          <clientCredentials>
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />
            <serviceCertificate>
                <defaultCertificate findValue="localhost" storeLocation="CurrentUser" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>

  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="47e80-174">Należy zauważyć, że tryb zabezpieczeń jest ustawiony na komunikat i ClientCredentialType jest ustawiony na certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="47e80-174">Note that the security mode is set to Message and the ClientCredentialType is set to Certificate.</span></span>

 <span data-ttu-id="47e80-175">Konfiguracja usługi zawiera zachowanie usługi, który określa poświadczenia, które są używane, gdy klient uwierzytelnia się usługi.</span><span class="sxs-lookup"><span data-stu-id="47e80-175">The service configuration includes a service behavior that specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="47e80-176">Nazwa podmiotu certyfikatu serwera jest określona w `findValue` atrybutu w [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="47e80-176">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesMessageSecurity" />
  </appSettings>

  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.OrderProcessorService"
          behaviorConfiguration="PurchaseOrderServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
          </baseAddresses>
        </host>
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                  binding="netMsmqBinding"
                  bindingConfiguration="messageSecurityBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
        <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate" />
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="PurchaseOrderServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <!--
               The serviceCredentials behavior allows one to define a service certificate.
               A service certificate is used by the service to authenticate itself to its clients and to provide message protection.
               This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
            <clientCertificate>
                <certificate findValue="client.com" storeLocation="LocalMachine" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </clientCertificate>
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

 <span data-ttu-id="47e80-177">W przykładzie pokazano kontroli uwierzytelniania za pomocą konfiguracji i jak można uzyskać tożsamości elementu wywołującego z kontekstu zabezpieczeń, jak pokazano w poniższym przykładowym kodzie:</span><span class="sxs-lookup"><span data-stu-id="47e80-177">The sample demonstrates controlling authentication using configuration, and how to obtain the caller’s identity from the security context, as shown in the following sample code:</span></span>

```csharp
// Service class which implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    private string GetCallerIdentity()
    {
        // The client certificate is not mapped to a Windows identity by default.
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information
        // in the certificate that the client used to authenticate itself to the service.
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Console.WriteLine("Client's Identity {0} ", GetCallerIdentity());
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }
  //…
}
```

 <span data-ttu-id="47e80-178">Po uruchomieniu kodu usługi Wyświetla identyfikator klienta.</span><span class="sxs-lookup"><span data-stu-id="47e80-178">When run, the service code displays the client identification.</span></span> <span data-ttu-id="47e80-179">Poniżej przedstawiono przykładowe dane wyjściowe z kodem usługi:</span><span class="sxs-lookup"><span data-stu-id="47e80-179">The following is a sample output from the service code:</span></span>

```
The service is ready.
Press <ENTER> to terminate service.

Client's Identity CN=client.com; ECA6629A3C695D01832D77EEE836E04891DE9D3C
Processing Purchase Order: 6536e097-da96-4773-9da3-77bab4345b5d
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

## <a name="comments"></a><span data-ttu-id="47e80-180">Komentarze</span><span class="sxs-lookup"><span data-stu-id="47e80-180">Comments</span></span>

-   <span data-ttu-id="47e80-181">Tworzenie certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="47e80-181">Creating the client certificate.</span></span>

     <span data-ttu-id="47e80-182">Następujący wiersz w pliku wsadowym tworzy certyfikat klienta.</span><span class="sxs-lookup"><span data-stu-id="47e80-182">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="47e80-183">Podana nazwa klienta jest używany w nazwie podmiotu certyfikatu, utworzony.</span><span class="sxs-lookup"><span data-stu-id="47e80-183">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="47e80-184">Certyfikat jest przechowywany w `My` przechowywać `CurrentUser` lokalizacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="47e80-184">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="47e80-185">Instalowanie certyfikatu klienta do magazynu zaufanych certyfikatów serwera.</span><span class="sxs-lookup"><span data-stu-id="47e80-185">Installing the client certificate into server’s trusted certificate store.</span></span>

     <span data-ttu-id="47e80-186">Następujący wiersz w kopii pliku wsadowego certyfikat klienta do serwera TrustedPeople przechowywać tak, aby istotne zaufania lub decyzji dotyczących zaufania nie mogą być serwera.</span><span class="sxs-lookup"><span data-stu-id="47e80-186">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="47e80-187">Certyfikat zainstalowany w magazynie TrustedPeople, aby być uważany za zaufany przez usługę Windows Communication Foundation (WCF), tryb walidacji certyfikatu klienta musi być równa `PeerOrChainTrust` lub `PeerTrust` wartość.</span><span class="sxs-lookup"><span data-stu-id="47e80-187">For a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust` value.</span></span> <span data-ttu-id="47e80-188">Zobacz poprzedni przykład konfiguracji usługi, aby dowiedzieć się, jak można to zrobić przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="47e80-188">See the previous service configuration sample to learn how this can be done using a configuration file.</span></span>

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

-   <span data-ttu-id="47e80-189">Tworzenie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="47e80-189">Creating the server certificate.</span></span>

     <span data-ttu-id="47e80-190">Następujące wiersze z pliku wsadowego Setup.bat jest utworzenie certyfikatu serwera, który ma być używany:</span><span class="sxs-lookup"><span data-stu-id="47e80-190">The following lines from the Setup.bat batch file create the server certificate to be used:</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="47e80-191">% Zmienna % nazwa_serwera Określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="47e80-191">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="47e80-192">Certyfikat jest przechowywany w magazynie LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="47e80-192">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="47e80-193">Jeśli instalacyjny plik wsadowy jest uruchamiany z nieprawidłowym argumentem usługi (takie jak `setup.bat service`) nazwa_serwera % zawiera w pełni kwalifikowana nazwa domeny komputera. W przeciwnym razie jego wartość domyślna to hosta lokalnego</span><span class="sxs-lookup"><span data-stu-id="47e80-193">If the setup batch file is run with an argument of service (such as, `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.Otherwise it defaults to localhost</span></span>

-   <span data-ttu-id="47e80-194">Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="47e80-194">Installing server certificate into the client’s trusted certificate store.</span></span>

     <span data-ttu-id="47e80-195">Następujący wiersz kopiuje certyfikatu serwera w magazynie zaufanych osób klienta.</span><span class="sxs-lookup"><span data-stu-id="47e80-195">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="47e80-196">Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta.</span><span class="sxs-lookup"><span data-stu-id="47e80-196">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="47e80-197">Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony przez Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="47e80-197">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  <span data-ttu-id="47e80-198">Jeśli używasz spoza USA Wersja programu Microsoft Windows, należy edytować Setup.bat i zastąp nazwę konta "NT AUTHORITY\NETWORK SERVICE" ekwiwalent regionalne w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="47e80-198">If you are using a non-U.S. English edition of Microsoft Windows you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="47e80-199">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="47e80-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="47e80-200">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="47e80-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="47e80-201">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="47e80-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="47e80-202">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="47e80-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
