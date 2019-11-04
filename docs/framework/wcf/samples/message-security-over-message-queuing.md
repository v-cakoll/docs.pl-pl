---
title: Zabezpieczenia komunikatów w ramach kolejkowania komunikatów
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: d27ee01636e37ac8f09c4f7dc497f14bfac1b0f1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424127"
---
# <a name="message-security-over-message-queuing"></a><span data-ttu-id="003e6-102">Zabezpieczenia komunikatów w ramach kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="003e6-102">Message Security over Message Queuing</span></span>
<span data-ttu-id="003e6-103">Ten przykład pokazuje, jak zaimplementować aplikację, która korzysta z protokołu WS-Security z uwierzytelnianiem za pomocą certyfikatu X. 509v3 na potrzeby klienta i wymaga uwierzytelniania serwera przy użyciu certyfikatu X. 509v3 serwera za pośrednictwem usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="003e6-103">This sample demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span> <span data-ttu-id="003e6-104">Zabezpieczenia komunikatów są czasami bardziej pożądane, aby zapewnić, że komunikaty w magazynie usługi MSMQ pozostają zaszyfrowane, a aplikacja może wykonać własne uwierzytelnianie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="003e6-104">Message security is sometimes more desirable to ensure that the messages in the MSMQ store stay encrypted and the application can perform its own authentication of the message.</span></span>

 <span data-ttu-id="003e6-105">Ten przykład jest oparty na przykładowym [wiązaniem usługi MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) .</span><span class="sxs-lookup"><span data-stu-id="003e6-105">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="003e6-106">Komunikaty są szyfrowane i podpisane.</span><span class="sxs-lookup"><span data-stu-id="003e6-106">The messages are encrypted and signed.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="003e6-107">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="003e6-107">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="003e6-108">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="003e6-108">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="003e6-109">Jeśli usługa jest uruchamiana po raz pierwszy, sprawdzi, czy kolejka jest obecna.</span><span class="sxs-lookup"><span data-stu-id="003e6-109">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="003e6-110">Jeśli kolejka nie istnieje, usługa utworzy ją.</span><span class="sxs-lookup"><span data-stu-id="003e6-110">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="003e6-111">Aby utworzyć kolejkę, można najpierw uruchomić tę usługę lub utworzyć ją za pośrednictwem Menedżera kolejki usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="003e6-111">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="003e6-112">Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="003e6-112">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="003e6-113">Otwórz Menedżer serwera w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="003e6-113">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="003e6-114">Rozwiń kartę **funkcje** .</span><span class="sxs-lookup"><span data-stu-id="003e6-114">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="003e6-115">Kliknij prawym przyciskiem myszy pozycję **prywatne kolejki komunikatów**, a następnie wybierz kolejno pozycje **Nowa**i **prywatne**.</span><span class="sxs-lookup"><span data-stu-id="003e6-115">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="003e6-116">Zaznacz pole **transakcyjne** .</span><span class="sxs-lookup"><span data-stu-id="003e6-116">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="003e6-117">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="003e6-117">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="003e6-118">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="003e6-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="003e6-119">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="003e6-119">To run the sample on the same computer</span></span>

1. <span data-ttu-id="003e6-120">Upewnij się, że ścieżka zawiera folder zawierający Makecert. exe i FindPrivateKey. exe.</span><span class="sxs-lookup"><span data-stu-id="003e6-120">Ensure that the path includes the folder that contains Makecert.exe and FindPrivateKey.exe.</span></span>

2. <span data-ttu-id="003e6-121">Uruchom setup. bat z przykładowego folderu instalacyjnego.</span><span class="sxs-lookup"><span data-stu-id="003e6-121">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="003e6-122">Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="003e6-122">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="003e6-123">Upewnij się, że certyfikaty są usuwane przez uruchomienie Oczyść. bat po zakończeniu z przykładem.</span><span class="sxs-lookup"><span data-stu-id="003e6-123">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="003e6-124">Inne przykłady zabezpieczeń używają tych samych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="003e6-124">Other security samples use the same certificates.</span></span>  
  
3. <span data-ttu-id="003e6-125">Uruchom usługę Service. exe z \service\bin.</span><span class="sxs-lookup"><span data-stu-id="003e6-125">Launch Service.exe from \service\bin.</span></span>  
  
4. <span data-ttu-id="003e6-126">Uruchamianie programu Client. exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="003e6-126">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="003e6-127">Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="003e6-127">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="003e6-128">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="003e6-128">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="003e6-129">Aby uruchomić przykład na wielu komputerach</span><span class="sxs-lookup"><span data-stu-id="003e6-129">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="003e6-130">Skopiuj pliki Setup. bat, Oczyść. bat i ImportClientCert. bat do komputera usługi.</span><span class="sxs-lookup"><span data-stu-id="003e6-130">Copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
2. <span data-ttu-id="003e6-131">Utwórz katalog na komputerze klienckim dla plików binarnych klienta.</span><span class="sxs-lookup"><span data-stu-id="003e6-131">Create a directory on the client computer for the client binaries.</span></span>  
  
3. <span data-ttu-id="003e6-132">Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="003e6-132">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="003e6-133">Skopiuj również do klienta pliki Setup. bat, Oczyść. bat i ImportServiceCert. bat.</span><span class="sxs-lookup"><span data-stu-id="003e6-133">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
4. <span data-ttu-id="003e6-134">Na serwerze programu Uruchom `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="003e6-134">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="003e6-135">Uruchomienie `setup.bat` z argumentem `service` tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service. cer.</span><span class="sxs-lookup"><span data-stu-id="003e6-135">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
5. <span data-ttu-id="003e6-136">Edytuj plik Service. exe. config usługi, aby odzwierciedlić nową nazwę certyfikatu (w atrybucie `findValue` w [\<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), która jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="003e6-136">Edit service's service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
6. <span data-ttu-id="003e6-137">Skopiuj plik. cer usługi z katalogu usługi do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="003e6-137">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
7. <span data-ttu-id="003e6-138">Na kliencie Uruchom `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="003e6-138">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="003e6-139">Uruchomienie `setup.bat` z argumentem `client` tworzy certyfikat klienta o nazwie client.com i eksportuje certyfikat klienta do pliku o nazwie Client. cer.</span><span class="sxs-lookup"><span data-stu-id="003e6-139">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
8. <span data-ttu-id="003e6-140">W pliku Client. exe. config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi.</span><span class="sxs-lookup"><span data-stu-id="003e6-140">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="003e6-141">Aby to zrobić, Zastąp wartość localhost nazwą FQDN serwera.</span><span class="sxs-lookup"><span data-stu-id="003e6-141">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  <span data-ttu-id="003e6-142">Należy również zmienić nazwę certyfikatu usługi tak samo jak w pełni kwalifikowana nazwa domeny komputera usługi (w atrybucie `findValue` w elemencie `defaultCertificate` `serviceCertificate` w `clientCredentials`).</span><span class="sxs-lookup"><span data-stu-id="003e6-142">You must also change the certificate name of the service to be the same as the fully-qualified domain name of the service computer (in the `findValue` attribute in the `defaultCertificate` element of `serviceCertificate` under `clientCredentials`).</span></span>  
  
9. <span data-ttu-id="003e6-143">Skopiuj plik. cer programu Client z katalogu Client do katalogu usługi na serwerze programu.</span><span class="sxs-lookup"><span data-stu-id="003e6-143">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
10. <span data-ttu-id="003e6-144">Na kliencie Uruchom `ImportServiceCert.bat`.</span><span class="sxs-lookup"><span data-stu-id="003e6-144">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="003e6-145">Spowoduje to zaimportowanie certyfikatu usługi z pliku CER usługi do magazynu CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="003e6-145">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
11. <span data-ttu-id="003e6-146">Na serwerze programu Uruchom `ImportClientCert.bat`, czyli importuje certyfikat klienta z pliku Client. cer do magazynu LocalMachine-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="003e6-146">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="003e6-147">Na komputerze usługi Uruchom polecenie Service. exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="003e6-147">On the service computer, launch Service.exe from the command prompt.</span></span>  
  
13. <span data-ttu-id="003e6-148">Na komputerze klienckim uruchom program Client. exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="003e6-148">On the client computer, launch Client.exe from the command prompt.</span></span> <span data-ttu-id="003e6-149">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="003e6-149">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="003e6-150">Aby wyczyścić po przykładzie</span><span class="sxs-lookup"><span data-stu-id="003e6-150">To clean up after the sample</span></span>  
  
- <span data-ttu-id="003e6-151">Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.</span><span class="sxs-lookup"><span data-stu-id="003e6-151">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="003e6-152">Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania tego przykładu między komputerami.</span><span class="sxs-lookup"><span data-stu-id="003e6-152">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="003e6-153">W przypadku uruchamiania przykładów programu Windows Communication Foundation (WCF), które używają certyfikatów między komputerami, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w magazynie CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="003e6-153">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="003e6-154">Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="003e6-154">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>

## <a name="requirements"></a><span data-ttu-id="003e6-155">Wymagania</span><span class="sxs-lookup"><span data-stu-id="003e6-155">Requirements</span></span>
 <span data-ttu-id="003e6-156">Ten przykład wymaga, aby usługa MSMQ była zainstalowana i uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="003e6-156">This sample requires that MSMQ is installed and running.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="003e6-157">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="003e6-157">Demonstrates</span></span>
 <span data-ttu-id="003e6-158">Klient szyfruje komunikat przy użyciu klucza publicznego usługi i podpisuje komunikat przy użyciu własnego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="003e6-158">The client encrypts the message using the public key of the service and signs the message using its own certificate.</span></span> <span data-ttu-id="003e6-159">Usługa odczytująca komunikat z kolejki uwierzytelnia certyfikat klienta przy użyciu certyfikatu w magazynie zaufanych osób.</span><span class="sxs-lookup"><span data-stu-id="003e6-159">The service reading the message from the queue authenticates the client certificate with the certificate in its trusted people store.</span></span> <span data-ttu-id="003e6-160">Następnie odszyfrowuje komunikat i wysyła komunikat do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="003e6-160">It then decrypts the message and dispatches the message to the service operation.</span></span>

 <span data-ttu-id="003e6-161">Ponieważ komunikat Windows Communication Foundation (WCF) jest przenoszony jako ładunek w treści wiadomości MSMQ, treść pozostaje zaszyfrowana w magazynie usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="003e6-161">Because the Windows Communication Foundation (WCF) message is carried as a payload in the body of the MSMQ message, the body remains encrypted in the MSMQ store.</span></span> <span data-ttu-id="003e6-162">Dzięki temu wiadomość jest zabezpieczona przed niechcianym ujawnieniem wiadomości.</span><span class="sxs-lookup"><span data-stu-id="003e6-162">This secures the message from unwanted disclosure of the message.</span></span> <span data-ttu-id="003e6-163">Należy zauważyć, że sama usługa MSMQ nie ma informacji o tym, czy komunikat, który jest na nim przenoszony, jest szyfrowany.</span><span class="sxs-lookup"><span data-stu-id="003e6-163">Note that MSMQ itself is not aware whether the message it is carrying is encrypted.</span></span>

 <span data-ttu-id="003e6-164">W przykładzie pokazano, jak uwierzytelnianie obustronne na poziomie komunikatu może być używane z usługą MSMQ.</span><span class="sxs-lookup"><span data-stu-id="003e6-164">The sample demonstrates how mutual authentication at the message level can be used with MSMQ.</span></span> <span data-ttu-id="003e6-165">Certyfikaty są wymieniane poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="003e6-165">The certificates are exchanged out-of-band.</span></span> <span data-ttu-id="003e6-166">Jest to zawsze przypadek z aplikacją umieszczoną w kolejce, ponieważ usługa i klient nie muszą działać w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="003e6-166">This is always the case with queued application because the service and the client do not have to be up and running at the same time.</span></span>

## <a name="description"></a><span data-ttu-id="003e6-167">Opis</span><span class="sxs-lookup"><span data-stu-id="003e6-167">Description</span></span>
 <span data-ttu-id="003e6-168">Przykładowy klient i kod usługi są takie same jak [transakcyjne powiązanie MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) przykładowe z jedną różnicą.</span><span class="sxs-lookup"><span data-stu-id="003e6-168">The sample client and service code are the same as the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample with one difference.</span></span> <span data-ttu-id="003e6-169">Umowa operacji ma adnotację z poziomem ochrony, która sugeruje, że komunikat musi być podpisany i szyfrowany.</span><span class="sxs-lookup"><span data-stu-id="003e6-169">The operation contract is annotated with protection level, which suggests that the message must be signed and encrypted.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="003e6-170">Aby upewnić się, że komunikat jest zabezpieczony przy użyciu wymaganego tokenu do identyfikacji usługi i klienta, plik App. config zawiera informacje o poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="003e6-170">To ensure that the message is secured using the required token to identify the service and client, the App.config contains credential information.</span></span>

 <span data-ttu-id="003e6-171">Konfiguracja klienta określa certyfikat usługi do uwierzytelniania usługi.</span><span class="sxs-lookup"><span data-stu-id="003e6-171">The client configuration specifies the service certificate to authenticate the service.</span></span> <span data-ttu-id="003e6-172">Używa magazynu LocalMachine jako zaufanego magazynu, aby polegać na ważności usługi.</span><span class="sxs-lookup"><span data-stu-id="003e6-172">It uses its LocalMachine store as the trusted store to rely on the validity of the service.</span></span> <span data-ttu-id="003e6-173">Określa również certyfikat klienta, który jest dołączony do wiadomości w celu uwierzytelnienia usługi klienta.</span><span class="sxs-lookup"><span data-stu-id="003e6-173">It also specifies the client certificate that is attached with the message for service authentication of the client.</span></span>

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

 <span data-ttu-id="003e6-174">Należy pamiętać, że tryb zabezpieczeń jest ustawiony na komunikat, a obiekt ClientCredentialtype jest ustawiony na wartość Certificate.</span><span class="sxs-lookup"><span data-stu-id="003e6-174">Note that the security mode is set to Message and the ClientCredentialType is set to Certificate.</span></span>

 <span data-ttu-id="003e6-175">Konfiguracja usługi obejmuje zachowanie usługi, które określa poświadczenia usługi, które są używane podczas uwierzytelniania usługi przez klienta.</span><span class="sxs-lookup"><span data-stu-id="003e6-175">The service configuration includes a service behavior that specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="003e6-176">Nazwa podmiotu certyfikatu serwera jest określona w atrybucie `findValue` w [\<ServiceCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="003e6-176">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

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

 <span data-ttu-id="003e6-177">Przykład demonstruje kontrolę uwierzytelniania przy użyciu konfiguracji i sposób uzyskiwania tożsamości obiektu wywołującego z kontekstu zabezpieczeń, jak pokazano w poniższym przykładowym kodzie:</span><span class="sxs-lookup"><span data-stu-id="003e6-177">The sample demonstrates controlling authentication using configuration, and how to obtain the caller’s identity from the security context, as shown in the following sample code:</span></span>

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

 <span data-ttu-id="003e6-178">Po uruchomieniu kod usługi wyświetla identyfikację klienta.</span><span class="sxs-lookup"><span data-stu-id="003e6-178">When run, the service code displays the client identification.</span></span> <span data-ttu-id="003e6-179">Poniżej przedstawiono przykładowe dane wyjściowe z kodu usługi:</span><span class="sxs-lookup"><span data-stu-id="003e6-179">The following is a sample output from the service code:</span></span>

```console
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

## <a name="comments"></a><span data-ttu-id="003e6-180">Komentarze</span><span class="sxs-lookup"><span data-stu-id="003e6-180">Comments</span></span>

- <span data-ttu-id="003e6-181">Tworzenie certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="003e6-181">Creating the client certificate.</span></span>

     <span data-ttu-id="003e6-182">Następujący wiersz w pliku wsadowym tworzy certyfikat klienta.</span><span class="sxs-lookup"><span data-stu-id="003e6-182">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="003e6-183">Określona nazwa klienta jest używana w nazwie podmiotu utworzonego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="003e6-183">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="003e6-184">Certyfikat jest przechowywany w magazynie `My` w lokalizacji magazynu `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="003e6-184">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="003e6-185">Instalowanie certyfikatu klienta w zaufanym magazynie certyfikatów na serwerze.</span><span class="sxs-lookup"><span data-stu-id="003e6-185">Installing the client certificate into server’s trusted certificate store.</span></span>

     <span data-ttu-id="003e6-186">Następujący wiersz w pliku wsadowym kopiuje certyfikat klienta do magazynu TrustedPeople serwera, dzięki czemu serwer może podejmować odpowiednie decyzje zaufania lub braku zaufania.</span><span class="sxs-lookup"><span data-stu-id="003e6-186">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="003e6-187">Aby certyfikat zainstalowany w magazynie TrustedPeople był zaufany przez usługę Windows Communication Foundation (WCF), tryb walidacji certyfikatu klienta musi być ustawiony na wartość `PeerOrChainTrust` lub `PeerTrust`.</span><span class="sxs-lookup"><span data-stu-id="003e6-187">For a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust` value.</span></span> <span data-ttu-id="003e6-188">Zobacz poprzedni przykład konfiguracji usługi, aby dowiedzieć się, jak można to zrobić za pomocą pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="003e6-188">See the previous service configuration sample to learn how this can be done using a configuration file.</span></span>

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

- <span data-ttu-id="003e6-189">Tworzenie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="003e6-189">Creating the server certificate.</span></span>

     <span data-ttu-id="003e6-190">Następujące wiersze z pliku wsadowego Setup. bat tworzą certyfikat serwera do użycia:</span><span class="sxs-lookup"><span data-stu-id="003e6-190">The following lines from the Setup.bat batch file create the server certificate to be used:</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="003e6-191">Zmienna% nazwa_serwera% określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="003e6-191">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="003e6-192">Certyfikat jest przechowywany w magazynie LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="003e6-192">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="003e6-193">Jeśli plik wsadowy instalacji jest uruchamiany z argumentem usługi (np. `setup.bat service`),% nazwa_serwera% zawiera w pełni kwalifikowaną nazwę domeny komputera. W przeciwnym razie wartość domyślna to localhost</span><span class="sxs-lookup"><span data-stu-id="003e6-193">If the setup batch file is run with an argument of service (such as, `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.Otherwise it defaults to localhost</span></span>

- <span data-ttu-id="003e6-194">Instalowanie certyfikatu serwera w zaufanym magazynie certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="003e6-194">Installing server certificate into the client’s trusted certificate store.</span></span>

     <span data-ttu-id="003e6-195">Poniższy wiersz zawiera kopię certyfikatu serwera w magazynie zaufanych osób klienta.</span><span class="sxs-lookup"><span data-stu-id="003e6-195">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="003e6-196">Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta.</span><span class="sxs-lookup"><span data-stu-id="003e6-196">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="003e6-197">Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="003e6-197">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > <span data-ttu-id="003e6-198">Jeśli używasz wersji innej niż U. S. w języku angielskim firmy Microsoft Windows, musisz edytować plik Setup. bat i zamienić nazwę konta "NT AUTHORITY\NETWORK SERVICE" na swój odpowiednik regionalny.</span><span class="sxs-lookup"><span data-stu-id="003e6-198">If you are using a non-U.S. English edition of Microsoft Windows you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="003e6-199">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="003e6-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="003e6-200">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="003e6-200">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="003e6-201">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="003e6-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="003e6-202">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="003e6-202">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
