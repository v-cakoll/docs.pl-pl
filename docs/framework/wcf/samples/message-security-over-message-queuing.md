---
title: Zabezpieczenia komunikatów w ramach kolejkowania komunikatów
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: 2048b27f15787c70abda65ae582849276469c763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144438"
---
# <a name="message-security-over-message-queuing"></a><span data-ttu-id="4375e-102">Zabezpieczenia komunikatów w ramach kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="4375e-102">Message Security over Message Queuing</span></span>
<span data-ttu-id="4375e-103">W tym przykładzie pokazano, jak zaimplementować aplikację, która używa usługi WS-Security z uwierzytelnianiem certyfikatu X.509v3 dla klienta i wymaga uwierzytelnienia serwera przy użyciu certyfikatu X.509v3 serwera za pośrednictwem usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4375e-103">This sample demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span> <span data-ttu-id="4375e-104">Zabezpieczenia wiadomości jest czasami bardziej pożądane, aby upewnić się, że wiadomości w magazynie USŁUGI MSMQ pozostają zaszyfrowane i aplikacja może wykonać własne uwierzytelnianie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4375e-104">Message security is sometimes more desirable to ensure that the messages in the MSMQ store stay encrypted and the application can perform its own authentication of the message.</span></span>

 <span data-ttu-id="4375e-105">Ten przykład jest oparty na próbce [wiązania transacted MSMQ.](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)</span><span class="sxs-lookup"><span data-stu-id="4375e-105">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="4375e-106">Wiadomości są szyfrowane i podpisane.</span><span class="sxs-lookup"><span data-stu-id="4375e-106">The messages are encrypted and signed.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4375e-107">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="4375e-107">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="4375e-108">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4375e-108">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="4375e-109">Jeśli usługa jest uruchamiana jako pierwsza, sprawdzi, czy kolejka jest obecna.</span><span class="sxs-lookup"><span data-stu-id="4375e-109">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="4375e-110">Jeśli kolejka nie jest obecny, usługa utworzy jeden.</span><span class="sxs-lookup"><span data-stu-id="4375e-110">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="4375e-111">Usługę można uruchomić najpierw, aby utworzyć kolejkę, lub utworzyć ją za pośrednictwem Menedżera kolejek usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4375e-111">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="4375e-112">Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="4375e-112">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="4375e-113">Otwórz Menedżera serwera w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="4375e-113">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="4375e-114">Rozwiń kartę **Funkcje.**</span><span class="sxs-lookup"><span data-stu-id="4375e-114">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="4375e-115">Kliknij prawym przyciskiem myszy **pozycję Kolejki wiadomości prywatnych**i wybierz polecenie **Nowa**, **Kolejka prywatna**.</span><span class="sxs-lookup"><span data-stu-id="4375e-115">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="4375e-116">Zaznacz pole **Transakcyjne.**</span><span class="sxs-lookup"><span data-stu-id="4375e-116">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="4375e-117">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="4375e-117">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="4375e-118">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4375e-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="4375e-119">Aby uruchomić próbkę na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="4375e-119">To run the sample on the same computer</span></span>

1. <span data-ttu-id="4375e-120">Upewnij się, że ścieżka zawiera folder zawierający pliki Makecert.exe i FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="4375e-120">Ensure that the path includes the folder that contains Makecert.exe and FindPrivateKey.exe.</span></span>

2. <span data-ttu-id="4375e-121">Uruchom plik Setup.bat z przykładowego folderu instalacyjnego.</span><span class="sxs-lookup"><span data-stu-id="4375e-121">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="4375e-122">Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia próbki.</span><span class="sxs-lookup"><span data-stu-id="4375e-122">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4375e-123">Upewnij się, że certyfikaty zostały ściął certyfikaty, uruchamiając Cleanup.bat po zakończeniu z próbką.</span><span class="sxs-lookup"><span data-stu-id="4375e-123">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="4375e-124">Inne przykłady zabezpieczeń używają tych samych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="4375e-124">Other security samples use the same certificates.</span></span>  
  
3. <span data-ttu-id="4375e-125">Uruchom program Service.exe z \service\bin.</span><span class="sxs-lookup"><span data-stu-id="4375e-125">Launch Service.exe from \service\bin.</span></span>  
  
4. <span data-ttu-id="4375e-126">Uruchom program Client.exe z pliku \client\bin.</span><span class="sxs-lookup"><span data-stu-id="4375e-126">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="4375e-127">Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="4375e-127">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="4375e-128">Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="4375e-128">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="4375e-129">Aby uruchomić próbkę na różnych komputerach</span><span class="sxs-lookup"><span data-stu-id="4375e-129">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="4375e-130">Skopiuj pliki Setup.bat, Cleanup.bat i ImportClientCert.bat na komputer usługi.</span><span class="sxs-lookup"><span data-stu-id="4375e-130">Copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
2. <span data-ttu-id="4375e-131">Utwórz katalog na komputerze klienckim dla plików binarnych klienta.</span><span class="sxs-lookup"><span data-stu-id="4375e-131">Create a directory on the client computer for the client binaries.</span></span>  
  
3. <span data-ttu-id="4375e-132">Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="4375e-132">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="4375e-133">Skopiuj również pliki Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="4375e-133">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
4. <span data-ttu-id="4375e-134">Na serwerze `setup.bat service`uruchom program .</span><span class="sxs-lookup"><span data-stu-id="4375e-134">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="4375e-135">Uruchomiony `setup.bat` z `service` argumentem tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service.cer.</span><span class="sxs-lookup"><span data-stu-id="4375e-135">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
5. <span data-ttu-id="4375e-136">Edytuj service's service.exe.config, aby odzwierciedlić nową nazwę certyfikatu (w `findValue` atrybucie w [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), która jest taka sama jak w pełni kwalifikowana nazwa domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="4375e-136">Edit service's service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
6. <span data-ttu-id="4375e-137">Skopiuj plik Service.cer z katalogu usługi do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="4375e-137">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
7. <span data-ttu-id="4375e-138">Na kliencie `setup.bat client`uruchom program .</span><span class="sxs-lookup"><span data-stu-id="4375e-138">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="4375e-139">Uruchamianie `setup.bat` `client` z argumentem tworzy certyfikat klienta o nazwie client.com i eksportuje certyfikat klienta do pliku o nazwie Client.cer.</span><span class="sxs-lookup"><span data-stu-id="4375e-139">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
8. <span data-ttu-id="4375e-140">W pliku Client.exe.config na komputerze klienckim zmień wartość adresu punktu końcowego, aby dopasować go do nowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="4375e-140">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="4375e-141">W tym celu można zastąpić hosta lokalnego w pełni kwalifikowaną nazwą domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="4375e-141">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  <span data-ttu-id="4375e-142">Należy również zmienić nazwę certyfikatu usługi tak, aby była taka sama jak w `findValue` pełni kwalifikowana nazwa domeny komputera usługowego (w atrybucie w `defaultCertificate` elemencie `serviceCertificate` under `clientCredentials`).</span><span class="sxs-lookup"><span data-stu-id="4375e-142">You must also change the certificate name of the service to be the same as the fully-qualified domain name of the service computer (in the `findValue` attribute in the `defaultCertificate` element of `serviceCertificate` under `clientCredentials`).</span></span>  
  
9. <span data-ttu-id="4375e-143">Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.</span><span class="sxs-lookup"><span data-stu-id="4375e-143">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
10. <span data-ttu-id="4375e-144">Na kliencie `ImportServiceCert.bat`uruchom program .</span><span class="sxs-lookup"><span data-stu-id="4375e-144">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="4375e-145">Spowoduje to zaimportować certyfikat usługi z pliku Service.cer do magazynu CurrentUser — TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="4375e-145">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
11. <span data-ttu-id="4375e-146">Na serwerze `ImportClientCert.bat`uruchom program Uruchom program Ta importuje certyfikat klienta z pliku Client.cer do magazynu LocalMachine — TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="4375e-146">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="4375e-147">Na komputerze z usługami uruchom program Service.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="4375e-147">On the service computer, launch Service.exe from the command prompt.</span></span>  
  
13. <span data-ttu-id="4375e-148">Na komputerze klienckim uruchom program Client.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="4375e-148">On the client computer, launch Client.exe from the command prompt.</span></span> <span data-ttu-id="4375e-149">Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="4375e-149">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="4375e-150">Aby oczyścić po próbce</span><span class="sxs-lookup"><span data-stu-id="4375e-150">To clean up after the sample</span></span>  
  
- <span data-ttu-id="4375e-151">Uruchom Cleanup.bat w folderze przykłady po zakończeniu uruchamiania próbki.</span><span class="sxs-lookup"><span data-stu-id="4375e-151">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4375e-152">Ten skrypt nie usuwa certyfikatów usługi na kliencie podczas uruchamiania tego przykładu na komputerach.</span><span class="sxs-lookup"><span data-stu-id="4375e-152">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="4375e-153">Jeśli uruchomiono przykłady Programu Windows Communication Foundation (WCF), które używają certyfikatów na różnych komputerach, należy wyczyścić certyfikaty usług, które zostały zainstalowane w magazynie CurrentUser — TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="4375e-153">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="4375e-154">Aby to zrobić, należy `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` użyć następującego polecenia: Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="4375e-154">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>

## <a name="requirements"></a><span data-ttu-id="4375e-155">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4375e-155">Requirements</span></span>
 <span data-ttu-id="4375e-156">Ten przykład wymaga zainstalowania i uruchomienia usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4375e-156">This sample requires that MSMQ is installed and running.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="4375e-157">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="4375e-157">Demonstrates</span></span>
 <span data-ttu-id="4375e-158">Klient szyfruje wiadomość przy użyciu klucza publicznego usługi i podpisuje wiadomość przy użyciu własnego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="4375e-158">The client encrypts the message using the public key of the service and signs the message using its own certificate.</span></span> <span data-ttu-id="4375e-159">Usługa odczytywania wiadomości z kolejki uwierzytelnia certyfikat klienta z certyfikatem w magazynie zaufanych osób.</span><span class="sxs-lookup"><span data-stu-id="4375e-159">The service reading the message from the queue authenticates the client certificate with the certificate in its trusted people store.</span></span> <span data-ttu-id="4375e-160">Następnie odszyfrowuje komunikat i wysyła komunikat do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="4375e-160">It then decrypts the message and dispatches the message to the service operation.</span></span>

 <span data-ttu-id="4375e-161">Ponieważ komunikat Fundacji Komunikacji systemu Windows (WCF) jest przenoszony jako ładunek w treści wiadomości MSMQ, treść pozostaje zaszyfrowana w magazynie usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4375e-161">Because the Windows Communication Foundation (WCF) message is carried as a payload in the body of the MSMQ message, the body remains encrypted in the MSMQ store.</span></span> <span data-ttu-id="4375e-162">Zabezpiecza to wiadomość przed niechcianym ujawnieniem wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4375e-162">This secures the message from unwanted disclosure of the message.</span></span> <span data-ttu-id="4375e-163">Należy zauważyć, że sam program MSMQ nie wie, czy wiadomość, którą nosi, jest szyfrowana.</span><span class="sxs-lookup"><span data-stu-id="4375e-163">Note that MSMQ itself is not aware whether the message it is carrying is encrypted.</span></span>

 <span data-ttu-id="4375e-164">W przykładzie pokazano, jak wzajemne uwierzytelnianie na poziomie wiadomości może być używane z usługą MSMQ.</span><span class="sxs-lookup"><span data-stu-id="4375e-164">The sample demonstrates how mutual authentication at the message level can be used with MSMQ.</span></span> <span data-ttu-id="4375e-165">Certyfikaty są wymieniane poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="4375e-165">The certificates are exchanged out-of-band.</span></span> <span data-ttu-id="4375e-166">Jest to zawsze w przypadku aplikacji w kolejce, ponieważ usługa i klient nie muszą być uruchomione w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="4375e-166">This is always the case with queued application because the service and the client do not have to be up and running at the same time.</span></span>

## <a name="description"></a><span data-ttu-id="4375e-167">Opis</span><span class="sxs-lookup"><span data-stu-id="4375e-167">Description</span></span>
 <span data-ttu-id="4375e-168">Przykładowy kod klienta i usługi są takie same jak próbka [powiązania usługi Transacted MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) z jedną różnicą.</span><span class="sxs-lookup"><span data-stu-id="4375e-168">The sample client and service code are the same as the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample with one difference.</span></span> <span data-ttu-id="4375e-169">Kontrakt operacyjny jest adnotacjami o poziomie ochrony, co sugeruje, że wiadomość musi być podpisana i zaszyfrowana.</span><span class="sxs-lookup"><span data-stu-id="4375e-169">The operation contract is annotated with protection level, which suggests that the message must be signed and encrypted.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="4375e-170">Aby upewnić się, że wiadomość jest zabezpieczona przy użyciu tokenu wymaganego do identyfikowania usługi i klienta, App.config zawiera informacje o poświadczeniach.</span><span class="sxs-lookup"><span data-stu-id="4375e-170">To ensure that the message is secured using the required token to identify the service and client, the App.config contains credential information.</span></span>

 <span data-ttu-id="4375e-171">Konfiguracja klienta określa certyfikat usługi do uwierzytelniania usługi.</span><span class="sxs-lookup"><span data-stu-id="4375e-171">The client configuration specifies the service certificate to authenticate the service.</span></span> <span data-ttu-id="4375e-172">Używa magazynu LocalMachine jako zaufanego magazynu, aby polegać na ważności usługi.</span><span class="sxs-lookup"><span data-stu-id="4375e-172">It uses its LocalMachine store as the trusted store to rely on the validity of the service.</span></span> <span data-ttu-id="4375e-173">Określa również certyfikat klienta, który jest dołączony do komunikatu do uwierzytelniania usługi klienta.</span><span class="sxs-lookup"><span data-stu-id="4375e-173">It also specifies the client certificate that is attached with the message for service authentication of the client.</span></span>

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

 <span data-ttu-id="4375e-174">Należy zauważyć, że tryb zabezpieczeń jest ustawiony na Message i ClientCredentialType jest ustawiona na certyfikat.</span><span class="sxs-lookup"><span data-stu-id="4375e-174">Note that the security mode is set to Message and the ClientCredentialType is set to Certificate.</span></span>

 <span data-ttu-id="4375e-175">Konfiguracja usługi zawiera zachowanie usługi, które określa poświadczenia usługi, które są używane, gdy klient uwierzytelnia usługę.</span><span class="sxs-lookup"><span data-stu-id="4375e-175">The service configuration includes a service behavior that specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="4375e-176">Nazwa podmiotu certyfikatu serwera `findValue` jest określona w atrybucie w [ \<>serviceCredentials ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="4375e-176">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

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

 <span data-ttu-id="4375e-177">W przykładzie pokazano kontrolowanie uwierzytelniania przy użyciu konfiguracji i jak uzyskać tożsamość wywołującego z kontekstu zabezpieczeń, jak pokazano w poniższym przykładowym kodzie:</span><span class="sxs-lookup"><span data-stu-id="4375e-177">The sample demonstrates controlling authentication using configuration, and how to obtain the caller’s identity from the security context, as shown in the following sample code:</span></span>

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

 <span data-ttu-id="4375e-178">Po uruchomieniu kod usługi wyświetla identyfikację klienta.</span><span class="sxs-lookup"><span data-stu-id="4375e-178">When run, the service code displays the client identification.</span></span> <span data-ttu-id="4375e-179">Poniżej przedstawiono przykładowe dane wyjściowe z kodu usługi:</span><span class="sxs-lookup"><span data-stu-id="4375e-179">The following is a sample output from the service code:</span></span>

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

## <a name="comments"></a><span data-ttu-id="4375e-180">Komentarze</span><span class="sxs-lookup"><span data-stu-id="4375e-180">Comments</span></span>

- <span data-ttu-id="4375e-181">Tworzenie certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="4375e-181">Creating the client certificate.</span></span>

     <span data-ttu-id="4375e-182">Następujący wiersz w pliku wsadowym tworzy certyfikat klienta.</span><span class="sxs-lookup"><span data-stu-id="4375e-182">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="4375e-183">Określona nazwa klienta jest używana w nazwie podmiotu utworzonego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="4375e-183">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="4375e-184">Certyfikat jest przechowywany `My` w `CurrentUser` magazynie w lokalizacji sklepu.</span><span class="sxs-lookup"><span data-stu-id="4375e-184">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="4375e-185">Instalowanie certyfikatu klienta w magazynie zaufanych certyfikatów serwera.</span><span class="sxs-lookup"><span data-stu-id="4375e-185">Installing the client certificate into server’s trusted certificate store.</span></span>

     <span data-ttu-id="4375e-186">Poniższy wiersz w pliku wsadowym kopiuje certyfikat klienta do magazynu TrustedPeople serwera, dzięki czemu serwer może podejmować odpowiednie decyzje dotyczące zaufania lub braku zaufania.</span><span class="sxs-lookup"><span data-stu-id="4375e-186">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="4375e-187">Aby certyfikat zainstalowany w magazynie TrustedPeople był zaufany przez usługę Windows Communication Foundation (WCF), `PeerOrChainTrust` należy `PeerTrust` ustawić lub wartość trybu sprawdzania poprawności certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="4375e-187">For a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust` value.</span></span> <span data-ttu-id="4375e-188">Zobacz przykład poprzedniej konfiguracji usługi, aby dowiedzieć się, jak można to zrobić za pomocą pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="4375e-188">See the previous service configuration sample to learn how this can be done using a configuration file.</span></span>

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

- <span data-ttu-id="4375e-189">Tworzenie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="4375e-189">Creating the server certificate.</span></span>

     <span data-ttu-id="4375e-190">Następujące wiersze z pliku wsadowego Setup.bat tworzą certyfikat serwera, który ma być używany:</span><span class="sxs-lookup"><span data-stu-id="4375e-190">The following lines from the Setup.bat batch file create the server certificate to be used:</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="4375e-191">Zmienna %SERVER_NAME% określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="4375e-191">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="4375e-192">Certyfikat jest przechowywany w magazynie LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="4375e-192">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="4375e-193">Jeśli plik wsadowy instalatora jest uruchamiany `setup.bat service`z argumentem usługi (na przykład ) %SERVER_NAME% zawiera w pełni kwalifikowaną nazwę domeny komputera. W przeciwnym razie domyślnie host localhost</span><span class="sxs-lookup"><span data-stu-id="4375e-193">If the setup batch file is run with an argument of service (such as, `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.Otherwise it defaults to localhost</span></span>

- <span data-ttu-id="4375e-194">Instalowanie certyfikatu serwera w magazynie zaufanych certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="4375e-194">Installing server certificate into the client’s trusted certificate store.</span></span>

     <span data-ttu-id="4375e-195">Poniższy wiersz kopiuje certyfikat serwera do magazynu zaufanych osób klienta.</span><span class="sxs-lookup"><span data-stu-id="4375e-195">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="4375e-196">Ten krok jest wymagany, ponieważ certyfikaty generowane przez plik Makecert.exe nie są niejawnie zaufane przez system kliencki.</span><span class="sxs-lookup"><span data-stu-id="4375e-196">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="4375e-197">Jeśli masz już certyfikat zakorzeniony w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten etap wypełniania magazynu certyfikatów klienta certyfikatem serwera nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="4375e-197">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > <span data-ttu-id="4375e-198">Jeśli używasz wersji systemu Microsoft Windows w wersji innej niż amerykańska, musisz edytować plik Setup.bat i zastąpić nazwę konta "NT AUTHORITY\NETWORK SERVICE" regionalnym odpowiednikiem.</span><span class="sxs-lookup"><span data-stu-id="4375e-198">If you are using a non-U.S. English edition of Microsoft Windows you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4375e-199">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="4375e-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4375e-200">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="4375e-200">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4375e-201">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="4375e-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4375e-202">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4375e-202">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
