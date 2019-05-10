---
title: Zabezpieczenia wiązania niestandardowego
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
ms.openlocfilehash: 71bc3d463330b893e8b415892a9bdcc2dae88a2b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616042"
---
# <a name="custom-binding-security"></a><span data-ttu-id="d35b7-102">Zabezpieczenia wiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="d35b7-102">Custom Binding Security</span></span>
<span data-ttu-id="d35b7-103">Niniejszy przykład pokazuje sposób konfigurowania zabezpieczeń przy użyciu niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="d35b7-103">This sample demonstrates how to configure security by using a custom binding.</span></span> <span data-ttu-id="d35b7-104">Widoczny jest sposób użyć niestandardowego powiązania, aby włączyć zabezpieczenia na poziomie komunikatu wraz z bezpiecznym transportem.</span><span class="sxs-lookup"><span data-stu-id="d35b7-104">It shows how to use a custom binding to enable message-level security together with a secure transport.</span></span> <span data-ttu-id="d35b7-105">Jest to przydatne, gdy bezpiecznym transportem jest wymagana do przesyłania komunikatów między klientem a usługą i jednocześnie komunikaty muszą być bezpieczne na poziomie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="d35b7-105">This is useful when a secure transport is required to transmit the messages between client and service and simultaneously the messages must be secure on the message level.</span></span> <span data-ttu-id="d35b7-106">Ta konfiguracja nie jest obsługiwana przez powiązania dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="d35b7-106">This configuration is not supported by system-provided bindings.</span></span>

 <span data-ttu-id="d35b7-107">W tym przykładzie składa się z konsoli klienta programu (EXE) i program konsoli usługi (EXE).</span><span class="sxs-lookup"><span data-stu-id="d35b7-107">This sample consists of a client console program (EXE) and a service console program (EXE).</span></span> <span data-ttu-id="d35b7-108">Usługa implementuje kontraktu dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="d35b7-108">The service implements a duplex contract.</span></span> <span data-ttu-id="d35b7-109">Kontrakt jest definiowany przez `ICalculatorDuplex` interfejs, który udostępnia operacje matematyczne (dodawania, odejmowania, mnożenia i dzielenia).</span><span class="sxs-lookup"><span data-stu-id="d35b7-109">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="d35b7-110">`ICalculatorDuplex` Interfejs umożliwia klientowi do wykonywania operacji matematycznych obliczania wyniku uruchomionych w sesji.</span><span class="sxs-lookup"><span data-stu-id="d35b7-110">The `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over a session.</span></span> <span data-ttu-id="d35b7-111">Niezależnie od siebie, usługa może zwrócić wyniki na `ICalculatorDuplexCallback` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d35b7-111">Independently, the service may return results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="d35b7-112">Kontrakt dupleksowy wymaga elementu session, ponieważ kontekst muszą być ustalane do skorelowania zestaw komunikatów przesyłanych między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="d35b7-112">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span> <span data-ttu-id="d35b7-113">Powiązanie niestandardowe zdefiniowano obsługującego komunikację dupleksową, która jest bezpieczna.</span><span class="sxs-lookup"><span data-stu-id="d35b7-113">A custom binding is defined that supports duplex communication and is secure.</span></span>

> [!NOTE]
>  <span data-ttu-id="d35b7-114">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="d35b7-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="d35b7-115">Konfiguracja usługi definiuje niestandardowego powiązania, który obsługuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="d35b7-115">The service configuration defines a custom binding that supports the following:</span></span>

- <span data-ttu-id="d35b7-116">Komunikację TCP chronionych z użyciem protokołu TLS/SSL.</span><span class="sxs-lookup"><span data-stu-id="d35b7-116">TCP communication protected by using the TLS/SSL protocol.</span></span>

- <span data-ttu-id="d35b7-117">Zabezpieczenia komunikatów Windows.</span><span class="sxs-lookup"><span data-stu-id="d35b7-117">Windows message security.</span></span>

 <span data-ttu-id="d35b7-118">Konfiguracja powiązania niestandardowego pozwala bezpiecznym transportem, jednocześnie umożliwiając zabezpieczenia na poziomie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="d35b7-118">The custom binding configuration enables secure transport by simultaneously enabling the message-level security.</span></span> <span data-ttu-id="d35b7-119">Określanie kolejności elementów wiązania jest ważny w celu definiowania niestandardowego powiązania, ponieważ każdy z nich reprezentuje warstwę w stosie kanału (zobacz [powiązań niestandardowych](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="d35b7-119">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="d35b7-120">Powiązania niestandardowego jest zdefiniowany w plikach konfiguracji usługi i klienta, jak pokazano w poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="d35b7-120">The custom binding is defined in the service and client configuration files, as shown in the following sample configuration.</span></span>

```xml
<bindings>
  <!-- Configure a custom binding. -->
  <customBinding>
    <binding name="Binding1">
      <security authenticationMode="SecureConversation"
                 requireSecurityContextCancellation="true">
      </security>
      <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>
      <sslStreamSecurity requireClientCertificate="false"/>
      <tcpTransport/>
    </binding>
  </customBinding>
</bindings>
```

 <span data-ttu-id="d35b7-121">Niestandardowego powiązania z certyfikatem usługi do uwierzytelniania usługi na poziomie transportu i do ochrony komunikatów podczas transmisji między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="d35b7-121">The custom binding uses a service certificate to authenticate the service on the transport level and to protect the messages during the transmission between client and service.</span></span> <span data-ttu-id="d35b7-122">Jest to osiągane przez `sslStreamSecurity` element powiązania.</span><span class="sxs-lookup"><span data-stu-id="d35b7-122">This is accomplished by the `sslStreamSecurity` binding element.</span></span> <span data-ttu-id="d35b7-123">Certyfikat usługi jest skonfigurowany za pomocą zachowanie usługi, jak pokazano w poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="d35b7-123">The service's certificate is configured using a service behavior as shown in the following sample configuration.</span></span>

```xml
<behaviors>
    <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
        <serviceMetadata />
        <serviceDebug includeExceptionDetailInFaults="False" />
        <serviceCredentials>
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>
        </serviceCredentials>
    </behavior>
    </serviceBehaviors>
</behaviors>
```

 <span data-ttu-id="d35b7-124">Ponadto niestandardowego powiązania za pomocą zabezpieczeń wiadomości typ poświadczeń Windows — jest to domyślny typ poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="d35b7-124">Additionally, the custom binding uses message security with Windows credential type - this is the default credential type.</span></span> <span data-ttu-id="d35b7-125">Jest to osiągane przez `security` element powiązania.</span><span class="sxs-lookup"><span data-stu-id="d35b7-125">This is accomplished by the `security` binding element.</span></span> <span data-ttu-id="d35b7-126">Zarówno klient, jak i usługi są uwierzytelniane przy użyciu zabezpieczeń na poziomie komunikatu, jeśli mechanizm uwierzytelniania Kerberos jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="d35b7-126">Both client and service are authenticated using message-level security if the Kerberos authentication mechanism is available.</span></span> <span data-ttu-id="d35b7-127">Dzieje się tak, jeśli na przykład jest uruchamiany w środowisku usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d35b7-127">This happens if the sample is run in the Active Directory environment.</span></span> <span data-ttu-id="d35b7-128">Jeśli mechanizm uwierzytelniania Kerberos jest niedostępny, zostanie użyte uwierzytelnianie NTLM.</span><span class="sxs-lookup"><span data-stu-id="d35b7-128">If the Kerberos authentication mechanism is not available, NTLM authentication is used.</span></span> <span data-ttu-id="d35b7-129">NTLM uwierzytelnia klienta do usługi, ale nie uwierzytelnia usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="d35b7-129">NTLM authenticates the client to the service but does not authenticate the service to the client.</span></span> <span data-ttu-id="d35b7-130">`security` Element powiązania jest skonfigurowany do używania `SecureConversation` `authenticationType`, co powoduje, że w przypadku tworzenia sesji zabezpieczeń zarówno klient, jak i usługi.</span><span class="sxs-lookup"><span data-stu-id="d35b7-130">The `security` binding element is configured to use `SecureConversation` `authenticationType`, which results in the creation of a security session on both the client and the service.</span></span> <span data-ttu-id="d35b7-131">Jest to wymagane do włączenia usługi kontraktu dwukierunkowego do pracy.</span><span class="sxs-lookup"><span data-stu-id="d35b7-131">This is required to enable the service's duplex contract to work.</span></span>

 <span data-ttu-id="d35b7-132">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="d35b7-132">When you run the sample, the operation requests and responses are displayed in the client's console window.</span></span> <span data-ttu-id="d35b7-133">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="d35b7-133">Press ENTER in the client window to shut down the client.</span></span>

```
Press <ENTER> to terminate client.
Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

 <span data-ttu-id="d35b7-134">Po uruchomieniu przykładu, zobacz komunikaty zwracane do klienta na interfejs wywołania zwrotnego wysyłane z usługi.</span><span class="sxs-lookup"><span data-stu-id="d35b7-134">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="d35b7-135">Jest wyświetlany wynik każdego pośrednich następuje całe równanie po ukończeniu wszystkich operacji.</span><span class="sxs-lookup"><span data-stu-id="d35b7-135">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="d35b7-136">Naciśnij klawisz ENTER, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="d35b7-136">Press ENTER to shut down the client.</span></span>

 <span data-ttu-id="d35b7-137">Dołączony plik Setup.bat umożliwia konfigurowanie klienta i serwera przy użyciu certyfikatu odpowiednie usługi uruchamianie hostowanej aplikacji, która wymaga zabezpieczeń oparte na certyfikatach.</span><span class="sxs-lookup"><span data-stu-id="d35b7-137">The included Setup.bat file enables you to configure the client and server with the relevant service certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="d35b7-138">Ten plik wsadowy muszą zostać zmodyfikowane, działają na różnych komputerach lub działać w przypadku innych obsługiwanych.</span><span class="sxs-lookup"><span data-stu-id="d35b7-138">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="d35b7-139">Poniżej zawiera krótkie omówienie różnych sekcji plików wsadowych, które dotyczą tego przykładu tak, aby ich można modyfikować, aby uruchomić w prawidłowej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="d35b7-139">The following provides a brief overview of the different sections of the batch files that apply to this sample so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="d35b7-140">Tworzenie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="d35b7-140">Creating the server certificate.</span></span>

     <span data-ttu-id="d35b7-141">Następujące wiersze z pliku Setup.bat jest utworzenie certyfikatu serwera, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="d35b7-141">The following lines from the Setup.bat file create the server certificate to be used.</span></span> <span data-ttu-id="d35b7-142">`%SERVER_NAME%` Zmienna Określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="d35b7-142">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="d35b7-143">Zmieniać tej zmiennej do określenia nazwy serwera.</span><span class="sxs-lookup"><span data-stu-id="d35b7-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="d35b7-144">Ten plik wsadowy wartością domyślną jest nazwa serwera, na hoście lokalnym.</span><span class="sxs-lookup"><span data-stu-id="d35b7-144">This batch file defaults the server name to localhost.</span></span>

     <span data-ttu-id="d35b7-145">Certyfikat jest przechowywany w magazynie CurrentUser usług hostowanych w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d35b7-145">The certificate is stored in the CurrentUser store for the Web-hosted services.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="d35b7-146">Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="d35b7-146">Installing the server certificate into the client's trusted certificate store.</span></span>

     <span data-ttu-id="d35b7-147">Przechowywać następujące wiersze w Setup.bat jest kopiowanie plików certyfikatu serwera do klienta zaufanych osób.</span><span class="sxs-lookup"><span data-stu-id="d35b7-147">The following lines in the Setup.bat file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="d35b7-148">Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta.</span><span class="sxs-lookup"><span data-stu-id="d35b7-148">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="d35b7-149">Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony przez Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="d35b7-149">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  <span data-ttu-id="d35b7-150">Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z programu Visual Studio 2010 wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="d35b7-150">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="d35b7-151">Wymaga to, że zmienna środowiskowa MSSDK odwołują się do katalogu, w którym jest zainstalowany zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="d35b7-151">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="d35b7-152">Ta zmienna środowiskowa jest automatycznie ustawiana w ramach programu Visual Studio 2010 wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="d35b7-152">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d35b7-153">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="d35b7-153">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="d35b7-154">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d35b7-154">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="d35b7-155">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d35b7-155">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="d35b7-156">Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d35b7-156">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="d35b7-157">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="d35b7-157">To run the sample on the same computer</span></span>

1. <span data-ttu-id="d35b7-158">Otwórz wiersz polecenia dewelopera dla okna programu Visual Studio z uprawnieniami administratora i uruchom Setup.bat jest z poziomu folderu instalacji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="d35b7-158">Open a Developer Command Prompt for Visual Studio window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="d35b7-159">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="d35b7-159">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="d35b7-160">Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z programu Visual Studio 2012 wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="d35b7-160">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="d35b7-161">Ustaw w Visual Studio 2012 Command Prompt punkty do katalogu, który zawiera pliki wykonywalne wymagane przez skrypt Setup.bat jest zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="d35b7-161">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="d35b7-162">Uruchom Service.exe z \service\bin.</span><span class="sxs-lookup"><span data-stu-id="d35b7-162">Launch Service.exe from \service\bin.</span></span>  
  
3. <span data-ttu-id="d35b7-163">Uruchom Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="d35b7-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="d35b7-164">Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.</span><span class="sxs-lookup"><span data-stu-id="d35b7-164">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="d35b7-165">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="d35b7-165">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="d35b7-166">Do uruchomienia przykładu na komputerach</span><span class="sxs-lookup"><span data-stu-id="d35b7-166">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="d35b7-167">Na komputerze usługi:</span><span class="sxs-lookup"><span data-stu-id="d35b7-167">On the service computer:</span></span>  
  
    1. <span data-ttu-id="d35b7-168">Utwórz katalog wirtualny o nazwie servicemodelsamples na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="d35b7-168">Create a virtual directory named servicemodelsamples on the service computer.</span></span>  
  
    2. <span data-ttu-id="d35b7-169">Skopiuj pliki programu usługi z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="d35b7-169">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="d35b7-170">Upewnij się, skopiuj pliki w podkatalogu \bin.</span><span class="sxs-lookup"><span data-stu-id="d35b7-170">Ensure that you copy the files in the \bin subdirectory.</span></span>  
  
    3. <span data-ttu-id="d35b7-171">Skopiuj pliki Setup.bat i Cleanup.bat komputer usługi.</span><span class="sxs-lookup"><span data-stu-id="d35b7-171">Copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
    4. <span data-ttu-id="d35b7-172">Uruchom następujące polecenie w wierszu polecenia dewelopera dla programu Visual Studio otwartych z uprawnieniami administratora: `Setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="d35b7-172">Run the following command in a Developer Command Prompt for Visual Studio opened with administrator privileges: `Setup.bat service`.</span></span> <span data-ttu-id="d35b7-173">Spowoduje to utworzenie certyfikatu usługi o nazwie podmiotu, pasujące do nazwy komputera, na którym uruchomiono plik wsadowy na.</span><span class="sxs-lookup"><span data-stu-id="d35b7-173">This creates the service certificate with the subject name matching the name of the computer the batch file was run on.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="d35b7-174">Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z programu Visual Studio 2010 wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="d35b7-174">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="d35b7-175">Wymaga to, że zmiennej środowiskowej path odwołują się do katalogu, w którym jest zainstalowany zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="d35b7-175">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="d35b7-176">Ta zmienna środowiskowa jest automatycznie ustawiana w ramach programu Visual Studio 2010 wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="d35b7-176">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>

    5. <span data-ttu-id="d35b7-177">Zmiana [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) wewnątrz pliku Service.exe.config, aby odzwierciedlić nazwę podmiotu certyfikatu, wygenerowany w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="d35b7-177">Change the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) inside the Service.exe.config file to reflect the subject name of the certificate generated in the previous step.</span></span>

    6. <span data-ttu-id="d35b7-178">Uruchom Service.exe z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="d35b7-178">Run Service.exe from a command prompt.</span></span>

2. <span data-ttu-id="d35b7-179">Na komputerze klienckim:</span><span class="sxs-lookup"><span data-stu-id="d35b7-179">On the client computer:</span></span>

    1. <span data-ttu-id="d35b7-180">Skopiuj pliki programu klienta z folderu \client\bin\ na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="d35b7-180">Copy the client program files from the \client\bin\ folder to the client computer.</span></span> <span data-ttu-id="d35b7-181">Również skopiować plik Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="d35b7-181">Also copy the Cleanup.bat file.</span></span>

    2. <span data-ttu-id="d35b7-182">Uruchom Cleanup.bat, aby usunąć wszelkie stare certyfikaty z poprzednich przykładów.</span><span class="sxs-lookup"><span data-stu-id="d35b7-182">Run Cleanup.bat to remove any old certificates from previous samples.</span></span>

    3. <span data-ttu-id="d35b7-183">Eksportowanie certyfikatu usługi otworzyć wiersz polecenia dla deweloperów programu Visual Studio z uprawnieniami administracyjnymi, a następnie uruchamiając następujące polecenie na komputerze usługi (Zastąp `%SERVER_NAME%` z w pełni kwalifikowaną nazwę komputera, na którym Usługa jest uruchomiona):</span><span class="sxs-lookup"><span data-stu-id="d35b7-183">Export the service's certificate by opening a Developer Command Prompt for Visual Studio with administrative privileges, and running the following command on the service computer (substitute `%SERVER_NAME%` with the fully-qualified name of the computer where the service is running):</span></span>

        ```
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer
        ```

    4. <span data-ttu-id="d35b7-184">Skopiuj %SERVER_NAME%.cer komputer kliencki (Zastąp nazwa_serwera % z w pełni kwalifikowaną nazwę komputera, na którym jest uruchomiona usługa).</span><span class="sxs-lookup"><span data-stu-id="d35b7-184">Copy %SERVER_NAME%.cer to the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running).</span></span>

    5. <span data-ttu-id="d35b7-185">Zaimportuj certyfikat usługi otworzyć wiersz polecenia dla deweloperów programu Visual Studio z uprawnieniami administracyjnymi, a następnie uruchamiając następujące polecenie na komputerze klienckim (Zastąp % nazwa_serwera % z w pełni kwalifikowaną nazwę komputera, na którym Usługa jest uruchomiona):</span><span class="sxs-lookup"><span data-stu-id="d35b7-185">Import the service's certificate by opening a Developer Command Prompt for Visual Studio with administrative privileges, and running the following command on the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running):</span></span>

        ```
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople
        ```

         <span data-ttu-id="d35b7-186">Kroki nie są konieczne, jeśli certyfikat został wystawiony przez zaufanego wystawcy c, d i e.</span><span class="sxs-lookup"><span data-stu-id="d35b7-186">Steps c, d, and e are not necessary if the certificate is issued by a Trusted Issuer.</span></span>

    6. <span data-ttu-id="d35b7-187">Zmodyfikuj plik App.config klienta w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d35b7-187">Modify the client’s App.config file as follows:</span></span>

        ```xml
        <client>
            <endpoint name="default"
                address="net.tcp://ReplaceThisWithServiceMachineName:8000/ServiceModelSamples/Service"
                binding="customBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex"
        behaviorConfiguration="CalculatorClientBehavior" />
        </client>
        ```

    7. <span data-ttu-id="d35b7-188">Jeśli usługa jest uruchomiona w ramach konta innego niż Usługa sieciowa lub konta System lokalny w środowisku domeny, może być konieczne zmodyfikowanie tożsamość punktu końcowego dla punktu końcowego usługi w pliku App.config klienta można ustawić odpowiednie nazwy UPN lub nazwy SPN na podstawie na koncie, które jest używane do uruchamiania usługi.</span><span class="sxs-lookup"><span data-stu-id="d35b7-188">If the service is running under an account other than the NetworkService or LocalSystem account in a domain environment, you might need to modify the endpoint identity for the service endpoint inside the client's App.config file to set the appropriate UPN or SPN based on the account that is used to run the service.</span></span> <span data-ttu-id="d35b7-189">Aby uzyskać więcej informacji o tożsamości punktu końcowego, zobacz [uwierzytelnianie i tożsamość usług](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="d35b7-189">For more information about endpoint identity, see the [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) topic.</span></span>

    8. <span data-ttu-id="d35b7-190">Uruchom Client.exe z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="d35b7-190">Run Client.exe from a command prompt.</span></span>

### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="d35b7-191">Aby wyczyścić zasoby po próbki</span><span class="sxs-lookup"><span data-stu-id="d35b7-191">To clean up after the sample</span></span>

- <span data-ttu-id="d35b7-192">Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.</span><span class="sxs-lookup"><span data-stu-id="d35b7-192">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>
