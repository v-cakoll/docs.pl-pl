---
title: Zabezpieczenia wiązania niestandardowego
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
ms.openlocfilehash: 99fa1e7dea09601de5efff9ef8d8c6a66eae1bac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953773"
---
# <a name="custom-binding-security"></a><span data-ttu-id="5fa60-102">Zabezpieczenia wiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="5fa60-102">Custom Binding Security</span></span>
<span data-ttu-id="5fa60-103">Ten przykład pokazuje, jak skonfigurować zabezpieczenia przy użyciu niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="5fa60-103">This sample demonstrates how to configure security by using a custom binding.</span></span> <span data-ttu-id="5fa60-104">Pokazuje, jak użyć niestandardowego powiązania, aby włączyć zabezpieczenia na poziomie wiadomości razem z bezpiecznym transportem.</span><span class="sxs-lookup"><span data-stu-id="5fa60-104">It shows how to use a custom binding to enable message-level security together with a secure transport.</span></span> <span data-ttu-id="5fa60-105">Jest to przydatne, gdy do przesyłania komunikatów między klientem i usługą jest wymagany bezpieczny transport, a jednocześnie komunikaty muszą być bezpieczne na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5fa60-105">This is useful when a secure transport is required to transmit the messages between client and service and simultaneously the messages must be secure on the message level.</span></span> <span data-ttu-id="5fa60-106">Ta konfiguracja nie jest obsługiwana przez powiązania dostarczone przez system.</span><span class="sxs-lookup"><span data-stu-id="5fa60-106">This configuration is not supported by system-provided bindings.</span></span>

 <span data-ttu-id="5fa60-107">Ten przykład składa się z programu Konsola klienta (EXE) i programu Service Console (EXE).</span><span class="sxs-lookup"><span data-stu-id="5fa60-107">This sample consists of a client console program (EXE) and a service console program (EXE).</span></span> <span data-ttu-id="5fa60-108">Usługa implementuje kontrakt dupleksowy.</span><span class="sxs-lookup"><span data-stu-id="5fa60-108">The service implements a duplex contract.</span></span> <span data-ttu-id="5fa60-109">Kontrakt jest definiowany przez `ICalculatorDuplex` interfejs, który udostępnia operacje matematyczne (Dodawanie, odejmowanie, mnożenie i dzielenie).</span><span class="sxs-lookup"><span data-stu-id="5fa60-109">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="5fa60-110">`ICalculatorDuplex` Interfejs umożliwia klientowi wykonywanie operacji matematycznych, co pozwala obliczyć wynik działania w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="5fa60-110">The `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over a session.</span></span> <span data-ttu-id="5fa60-111">Niezależnie od tego, czy usługa może zwracać wyniki `ICalculatorDuplexCallback` w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="5fa60-111">Independently, the service may return results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="5fa60-112">Kontrakt dupleksowy wymaga sesji, ponieważ należy ustanowić kontekst w celu skorelowania zestawu komunikatów wysyłanych między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="5fa60-112">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span> <span data-ttu-id="5fa60-113">Zdefiniowane jest niestandardowe powiązanie, które obsługuje komunikację dupleksową i jest bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="5fa60-113">A custom binding is defined that supports duplex communication and is secure.</span></span>

> [!NOTE]
> <span data-ttu-id="5fa60-114">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5fa60-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="5fa60-115">Konfiguracja usługi definiuje niestandardowe powiązanie, które obsługuje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="5fa60-115">The service configuration defines a custom binding that supports the following:</span></span>

- <span data-ttu-id="5fa60-116">Komunikacja TCP zabezpieczona przy użyciu protokołu TLS/SSL.</span><span class="sxs-lookup"><span data-stu-id="5fa60-116">TCP communication protected by using the TLS/SSL protocol.</span></span>

- <span data-ttu-id="5fa60-117">Zabezpieczenia komunikatów systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5fa60-117">Windows message security.</span></span>

 <span data-ttu-id="5fa60-118">Konfiguracja powiązania niestandardowego umożliwia bezpieczne transport przez jednoczesne włączenie zabezpieczeń na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5fa60-118">The custom binding configuration enables secure transport by simultaneously enabling the message-level security.</span></span> <span data-ttu-id="5fa60-119">Kolejność elementów powiązania jest istotna dla definiowania niestandardowego powiązania, ponieważ każdy reprezentuje warstwę w stosie kanału (zobacz [powiązania niestandardowe](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="5fa60-119">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="5fa60-120">Niestandardowe powiązanie jest zdefiniowane w plikach konfiguracji usługi i klienta, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="5fa60-120">The custom binding is defined in the service and client configuration files, as shown in the following sample configuration.</span></span>

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

 <span data-ttu-id="5fa60-121">Niestandardowe powiązanie używa certyfikatu usługi do uwierzytelniania usługi na poziomie transportu oraz do ochrony komunikatów podczas przesyłania między klientem i usługą.</span><span class="sxs-lookup"><span data-stu-id="5fa60-121">The custom binding uses a service certificate to authenticate the service on the transport level and to protect the messages during the transmission between client and service.</span></span> <span data-ttu-id="5fa60-122">Jest to realizowane przez `sslStreamSecurity` element Binding.</span><span class="sxs-lookup"><span data-stu-id="5fa60-122">This is accomplished by the `sslStreamSecurity` binding element.</span></span> <span data-ttu-id="5fa60-123">Certyfikat usługi jest konfigurowany przy użyciu zachowania usługi, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="5fa60-123">The service's certificate is configured using a service behavior as shown in the following sample configuration.</span></span>

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

 <span data-ttu-id="5fa60-124">Ponadto niestandardowe powiązanie używa zabezpieczeń komunikatów z typem poświadczeń systemu Windows — jest to domyślny typ poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="5fa60-124">Additionally, the custom binding uses message security with Windows credential type - this is the default credential type.</span></span> <span data-ttu-id="5fa60-125">Jest to realizowane przez `security` element Binding.</span><span class="sxs-lookup"><span data-stu-id="5fa60-125">This is accomplished by the `security` binding element.</span></span> <span data-ttu-id="5fa60-126">Klient i usługa są uwierzytelniani przy użyciu zabezpieczeń na poziomie wiadomości, jeśli jest dostępny mechanizm uwierzytelniania Kerberos.</span><span class="sxs-lookup"><span data-stu-id="5fa60-126">Both client and service are authenticated using message-level security if the Kerberos authentication mechanism is available.</span></span> <span data-ttu-id="5fa60-127">Dzieje się tak, jeśli przykład jest uruchamiany w środowisku Active Directoryowym.</span><span class="sxs-lookup"><span data-stu-id="5fa60-127">This happens if the sample is run in the Active Directory environment.</span></span> <span data-ttu-id="5fa60-128">Jeśli mechanizm uwierzytelniania Kerberos jest niedostępny, jest używane uwierzytelnianie NTLM.</span><span class="sxs-lookup"><span data-stu-id="5fa60-128">If the Kerberos authentication mechanism is not available, NTLM authentication is used.</span></span> <span data-ttu-id="5fa60-129">Protokół NTLM uwierzytelnia klienta w usłudze, ale nie uwierzytelnia usługi dla klienta.</span><span class="sxs-lookup"><span data-stu-id="5fa60-129">NTLM authenticates the client to the service but does not authenticate the service to the client.</span></span> <span data-ttu-id="5fa60-130">Element Binding jest skonfigurowany do użycia `SecureConversation` `authenticationType`, co powoduje utworzenie sesji zabezpieczeń zarówno na kliencie, jak i w usłudze. `security`</span><span class="sxs-lookup"><span data-stu-id="5fa60-130">The `security` binding element is configured to use `SecureConversation` `authenticationType`, which results in the creation of a security session on both the client and the service.</span></span> <span data-ttu-id="5fa60-131">Jest to wymagane, aby umożliwić pracę kontraktu dupleksowego usługi.</span><span class="sxs-lookup"><span data-stu-id="5fa60-131">This is required to enable the service's duplex contract to work.</span></span>

 <span data-ttu-id="5fa60-132">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="5fa60-132">When you run the sample, the operation requests and responses are displayed in the client's console window.</span></span> <span data-ttu-id="5fa60-133">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="5fa60-133">Press ENTER in the client window to shut down the client.</span></span>

```
Press <ENTER> to terminate client.
Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

 <span data-ttu-id="5fa60-134">Po uruchomieniu przykładu komunikaty zwrócone do klienta są wyświetlane w interfejsie wywołania zwrotnego wysyłanego z usługi.</span><span class="sxs-lookup"><span data-stu-id="5fa60-134">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="5fa60-135">Zostanie wyświetlony każdy wynik pośredni, po którym następuje całe równanie po zakończeniu wszystkich operacji.</span><span class="sxs-lookup"><span data-stu-id="5fa60-135">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="5fa60-136">Naciśnij klawisz ENTER, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="5fa60-136">Press ENTER to shut down the client.</span></span>

 <span data-ttu-id="5fa60-137">Dołączony plik Setup. bat umożliwia skonfigurowanie klienta i serwera przy użyciu odpowiedniego certyfikatu usługi do uruchamiania hostowanej aplikacji, która wymaga zabezpieczeń opartych na certyfikatach.</span><span class="sxs-lookup"><span data-stu-id="5fa60-137">The included Setup.bat file enables you to configure the client and server with the relevant service certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="5fa60-138">Ten plik wsadowy należy zmodyfikować, aby mógł działać na różnych komputerach lub działać w nieobsługiwanym przypadku.</span><span class="sxs-lookup"><span data-stu-id="5fa60-138">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="5fa60-139">Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, które mają zastosowanie do tego przykładu, aby można je było modyfikować do uruchamiania w odpowiedniej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="5fa60-139">The following provides a brief overview of the different sections of the batch files that apply to this sample so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="5fa60-140">Tworzenie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="5fa60-140">Creating the server certificate.</span></span>

     <span data-ttu-id="5fa60-141">Poniższe wiersze z pliku Setup. bat umożliwiają utworzenie certyfikatu serwera, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="5fa60-141">The following lines from the Setup.bat file create the server certificate to be used.</span></span> <span data-ttu-id="5fa60-142">`%SERVER_NAME%` Zmienna określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="5fa60-142">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="5fa60-143">Zmień tę zmienną, aby określić własną nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="5fa60-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="5fa60-144">Ten plik wsadowy domyślnie Nazwa serwera to localhost.</span><span class="sxs-lookup"><span data-stu-id="5fa60-144">This batch file defaults the server name to localhost.</span></span>

     <span data-ttu-id="5fa60-145">Certyfikat jest przechowywany w magazynie CurrentUser dla usług hostowanych w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5fa60-145">The certificate is stored in the CurrentUser store for the Web-hosted services.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="5fa60-146">Instalowanie certyfikatu serwera w zaufanym magazynie certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="5fa60-146">Installing the server certificate into the client's trusted certificate store.</span></span>

     <span data-ttu-id="5fa60-147">Poniższe wiersze w pliku Setup. bat kopiują certyfikat serwera do magazynu zaufanych osób klienta.</span><span class="sxs-lookup"><span data-stu-id="5fa60-147">The following lines in the Setup.bat file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="5fa60-148">Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta.</span><span class="sxs-lookup"><span data-stu-id="5fa60-148">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="5fa60-149">Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="5fa60-149">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  <span data-ttu-id="5fa60-150">Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersza polecenia programu Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="5fa60-150">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="5fa60-151">Wymaga, aby zmienna środowiskowa MSSDK wskazywała katalog, w którym zainstalowano zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="5fa60-151">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="5fa60-152">Ta zmienna środowiskowa jest ustawiana automatycznie w wierszu polecenia programu Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="5fa60-152">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5fa60-153">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="5fa60-153">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="5fa60-154">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5fa60-154">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="5fa60-155">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5fa60-155">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="5fa60-156">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5fa60-156">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="5fa60-157">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="5fa60-157">To run the sample on the same computer</span></span>

1. <span data-ttu-id="5fa60-158">Otwórz okno wiersz polecenia dla deweloperów dla programu Visual Studio z uprawnieniami administratora i uruchom setup. bat z przykładowego folderu instalacyjnego.</span><span class="sxs-lookup"><span data-stu-id="5fa60-158">Open a Developer Command Prompt for Visual Studio window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="5fa60-159">Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="5fa60-159">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="5fa60-160">Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersza polecenia programu Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="5fa60-160">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="5fa60-161">Zmienna środowiskowa PATH ustawiona w wierszu polecenia programu Visual Studio 2012 wskazuje katalog zawierający pliki wykonywalne wymagane przez skrypt Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="5fa60-161">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="5fa60-162">Uruchom usługę Service. exe z \service\bin.</span><span class="sxs-lookup"><span data-stu-id="5fa60-162">Launch Service.exe from \service\bin.</span></span>  
  
3. <span data-ttu-id="5fa60-163">Uruchamianie programu Client. exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="5fa60-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="5fa60-164">Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="5fa60-164">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="5fa60-165">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="5fa60-165">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="5fa60-166">Aby uruchomić przykład na wielu komputerach</span><span class="sxs-lookup"><span data-stu-id="5fa60-166">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="5fa60-167">Na komputerze usługi:</span><span class="sxs-lookup"><span data-stu-id="5fa60-167">On the service computer:</span></span>  
  
    1. <span data-ttu-id="5fa60-168">Utwórz katalog wirtualny o nazwie servicemodelsamples na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="5fa60-168">Create a virtual directory named servicemodelsamples on the service computer.</span></span>  
  
    2. <span data-ttu-id="5fa60-169">Skopiuj pliki programu usługi z \Inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="5fa60-169">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="5fa60-170">Upewnij się, że pliki zostały skopiowane do podkatalogu \Bin.</span><span class="sxs-lookup"><span data-stu-id="5fa60-170">Ensure that you copy the files in the \bin subdirectory.</span></span>  
  
    3. <span data-ttu-id="5fa60-171">Skopiuj pliki Setup. bat i Oczyść. bat do komputera usługi.</span><span class="sxs-lookup"><span data-stu-id="5fa60-171">Copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
    4. <span data-ttu-id="5fa60-172">Uruchom następujące polecenie w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora: `Setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="5fa60-172">Run the following command in a Developer Command Prompt for Visual Studio opened with administrator privileges: `Setup.bat service`.</span></span> <span data-ttu-id="5fa60-173">Spowoduje to utworzenie certyfikatu usługi z nazwą podmiotu zgodną z nazwą komputera, na którym uruchomiono plik wsadowy.</span><span class="sxs-lookup"><span data-stu-id="5fa60-173">This creates the service certificate with the subject name matching the name of the computer the batch file was run on.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="5fa60-174">Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersza polecenia programu Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="5fa60-174">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="5fa60-175">Wymaga, aby zmienna środowiskowa Path wskazywała katalog, w którym zainstalowano zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="5fa60-175">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="5fa60-176">Ta zmienna środowiskowa jest ustawiana automatycznie w wierszu polecenia programu Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="5fa60-176">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>

    5. <span data-ttu-id="5fa60-177">Zmień > serviceCertificate w pliku Service. exe. config w taki sposób, aby odzwierciedlał nazwę podmiotu certyfikatu wygenerowanego w poprzednim kroku. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="5fa60-177">Change the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) inside the Service.exe.config file to reflect the subject name of the certificate generated in the previous step.</span></span>

    6. <span data-ttu-id="5fa60-178">Uruchom polecenie Service. exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="5fa60-178">Run Service.exe from a command prompt.</span></span>

2. <span data-ttu-id="5fa60-179">Na komputerze klienckim:</span><span class="sxs-lookup"><span data-stu-id="5fa60-179">On the client computer:</span></span>

    1. <span data-ttu-id="5fa60-180">Skopiuj pliki programu klienckiego z folderu \client\bin\ na komputer kliencki.</span><span class="sxs-lookup"><span data-stu-id="5fa60-180">Copy the client program files from the \client\bin\ folder to the client computer.</span></span> <span data-ttu-id="5fa60-181">Skopiuj również plik Cleanup. bat.</span><span class="sxs-lookup"><span data-stu-id="5fa60-181">Also copy the Cleanup.bat file.</span></span>

    2. <span data-ttu-id="5fa60-182">Uruchom Oczyść. bat, aby usunąć wszystkie stare certyfikaty z poprzednich przykładów.</span><span class="sxs-lookup"><span data-stu-id="5fa60-182">Run Cleanup.bat to remove any old certificates from previous samples.</span></span>

    3. <span data-ttu-id="5fa60-183">Wyeksportuj certyfikat usługi, otwierając wiersz polecenia dla deweloperów dla programu Visual Studio z uprawnieniami administracyjnymi, a następnie uruchamiając następujące polecenie na komputerze usługi ( `%SERVER_NAME%` zastępuje się w pełni kwalifikowaną nazwą komputera, na którym Usługa jest uruchomiona):</span><span class="sxs-lookup"><span data-stu-id="5fa60-183">Export the service's certificate by opening a Developer Command Prompt for Visual Studio with administrative privileges, and running the following command on the service computer (substitute `%SERVER_NAME%` with the fully-qualified name of the computer where the service is running):</span></span>

        ```
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer
        ```

    4. <span data-ttu-id="5fa60-184">Skopiuj% nazwa_serwera%. cer do komputera klienckiego (Zastępuje% nazwa_serwera% w pełni kwalifikowaną nazwą komputera, na którym jest uruchomiona usługa).</span><span class="sxs-lookup"><span data-stu-id="5fa60-184">Copy %SERVER_NAME%.cer to the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running).</span></span>

    5. <span data-ttu-id="5fa60-185">Zaimportuj certyfikat usługi, otwierając wiersz polecenia dla deweloperów dla programu Visual Studio z uprawnieniami administracyjnymi, a następnie uruchamiając następujące polecenie na komputerze klienckim (zamiennie% nazwa_serwera% z w pełni kwalifikowaną nazwą komputera, na którym Usługa jest uruchomiona):</span><span class="sxs-lookup"><span data-stu-id="5fa60-185">Import the service's certificate by opening a Developer Command Prompt for Visual Studio with administrative privileges, and running the following command on the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running):</span></span>

        ```
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople
        ```

         <span data-ttu-id="5fa60-186">Kroki c, d i e nie są konieczne, jeśli certyfikat jest wystawiony przez zaufanego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="5fa60-186">Steps c, d, and e are not necessary if the certificate is issued by a Trusted Issuer.</span></span>

    6. <span data-ttu-id="5fa60-187">Zmodyfikuj plik App. config klienta w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5fa60-187">Modify the client’s App.config file as follows:</span></span>

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

    7. <span data-ttu-id="5fa60-188">Jeśli usługa jest uruchomiona w ramach konta innego niż konto NetworkService lub LocalSystem w środowisku domeny, może być konieczne zmodyfikowanie tożsamości punktu końcowego dla punktu końcowego usługi w pliku App. config klienta w celu ustawienia odpowiedniej nazwy UPN lub nazwy SPN na podstawie na koncie, które jest używane do uruchamiania usługi.</span><span class="sxs-lookup"><span data-stu-id="5fa60-188">If the service is running under an account other than the NetworkService or LocalSystem account in a domain environment, you might need to modify the endpoint identity for the service endpoint inside the client's App.config file to set the appropriate UPN or SPN based on the account that is used to run the service.</span></span> <span data-ttu-id="5fa60-189">Aby uzyskać więcej informacji na temat tożsamości punktów końcowych, zobacz temat [tożsamość usługi i uwierzytelnianie](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) .</span><span class="sxs-lookup"><span data-stu-id="5fa60-189">For more information about endpoint identity, see the [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) topic.</span></span>

    8. <span data-ttu-id="5fa60-190">Uruchom plik Client. exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="5fa60-190">Run Client.exe from a command prompt.</span></span>

### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="5fa60-191">Aby wyczyścić po przykładzie</span><span class="sxs-lookup"><span data-stu-id="5fa60-191">To clean up after the sample</span></span>

- <span data-ttu-id="5fa60-192">Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.</span><span class="sxs-lookup"><span data-stu-id="5fa60-192">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>
