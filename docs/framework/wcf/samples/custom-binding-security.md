---
title: "Zabezpieczenia powiązania niestandardowego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
caps.latest.revision: "30"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 94c43586606f42cca120ded59637a998d113d229
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="custom-binding-security"></a><span data-ttu-id="7b424-102">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="7b424-102">Custom Binding Security</span></span>
<span data-ttu-id="7b424-103">W tym przykładzie pokazano, jak skonfigurować zabezpieczenia przy użyciu niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="7b424-103">This sample demonstrates how to configure security by using a custom binding.</span></span> <span data-ttu-id="7b424-104">Widoczny jest sposób umożliwiają niestandardowego powiązania zabezpieczeń na poziomie komunikatu wraz z bezpiecznego transportu.</span><span class="sxs-lookup"><span data-stu-id="7b424-104">It shows how to use a custom binding to enable message-level security together with a secure transport.</span></span> <span data-ttu-id="7b424-105">Jest to przydatne, gdy do przesyłania wiadomości między klientem a usługą jest wymagane bezpieczne transportu i jednocześnie wiadomości musi być bezpieczny na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7b424-105">This is useful when a secure transport is required to transmit the messages between client and service and simultaneously the messages must be secure on the message level.</span></span> <span data-ttu-id="7b424-106">Ta konfiguracja nie jest obsługiwana przez powiązania dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="7b424-106">This configuration is not supported by system-provided bindings.</span></span>  
  
 <span data-ttu-id="7b424-107">W tym przykładzie składa się z konsoli klienta programu (EXE) i usługi konsoli programu (EXE).</span><span class="sxs-lookup"><span data-stu-id="7b424-107">This sample consists of a client console program (EXE) and a service console program (EXE).</span></span> <span data-ttu-id="7b424-108">Usługa implementuje kontraktu dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="7b424-108">The service implements a duplex contract.</span></span> <span data-ttu-id="7b424-109">Kontrakt jest definiowana za pomocą `ICalculatorDuplex` interfejsu, który udostępnia operacji matematycznych (Dodawanie, odjąć mnożenia i dzielenia).</span><span class="sxs-lookup"><span data-stu-id="7b424-109">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="7b424-110">`ICalculatorDuplex` Interfejs umożliwia klientowi wykonywania operacji matematycznych, obliczania wyniku uruchomiona przez sesję.</span><span class="sxs-lookup"><span data-stu-id="7b424-110">The `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over a session.</span></span> <span data-ttu-id="7b424-111">Niezależnie od siebie, usługa może zwrócić wyniki na `ICalculatorDuplexCallback` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7b424-111">Independently, the service may return results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="7b424-112">Kontrakt dupleksowy wymaga elementu session, ponieważ kontekst muszą być ustalane do skorelowania zestaw komunikatów przesyłanych między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="7b424-112">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span> <span data-ttu-id="7b424-113">Powiązania niestandardowego zdefiniowano obsługującego komunikację dupleksową, który jest bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="7b424-113">A custom binding is defined that supports duplex communication and is secure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b424-114">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="7b424-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7b424-115">Konfiguracja usługi definiuje niestandardowego powiązania, który obsługuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="7b424-115">The service configuration defines a custom binding that supports the following:</span></span>  
  
-   <span data-ttu-id="7b424-116">Komunikacja TCP chronione za pomocą protokołu TLS/SSL.</span><span class="sxs-lookup"><span data-stu-id="7b424-116">TCP communication protected by using the TLS/SSL protocol.</span></span>  
  
-   <span data-ttu-id="7b424-117">Zabezpieczenia komunikatów systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="7b424-117">Windows message security.</span></span>  
  
 <span data-ttu-id="7b424-118">Konfiguracja wiązania niestandardowego pozwala bezpiecznego transportu równocześnie umożliwiając zabezpieczeń na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7b424-118">The custom binding configuration enables secure transport by simultaneously enabling the message-level security.</span></span> <span data-ttu-id="7b424-119">Kolejność elementów wiązania jest ważne podczas definiowania niestandardowego powiązania, ponieważ każdy reprezentuje warstwę stosu kanał (zobacz [niestandardowego powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="7b424-119">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="7b424-120">Niestandardowego powiązania jest zdefiniowany w plikach konfiguracji usługi i klienta, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="7b424-120">The custom binding is defined in the service and client configuration files, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="7b424-121">Wiązanie niestandardowe używa certyfikatu usługi do uwierzytelniania usługi na poziomie transportu oraz chronić przed komunikaty podczas transmisji między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="7b424-121">The custom binding uses a service certificate to authenticate the service on the transport level and to protect the messages during the transmission between client and service.</span></span> <span data-ttu-id="7b424-122">Jest to osiągane przez `sslStreamSecurity` element powiązania.</span><span class="sxs-lookup"><span data-stu-id="7b424-122">This is accomplished by the `sslStreamSecurity` binding element.</span></span> <span data-ttu-id="7b424-123">Certyfikat usługi jest skonfigurowany przy użyciu zachowania usługi, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="7b424-123">The service's certificate is configured using a service behavior as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="7b424-124">Ponadto niestandardowego powiązania używa zabezpieczenia komunikatów z typu poświadczeń systemu Windows — jest to domyślny typ poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="7b424-124">Additionally, the custom binding uses message security with Windows credential type - this is the default credential type.</span></span> <span data-ttu-id="7b424-125">Jest to osiągane przez `security` element powiązania.</span><span class="sxs-lookup"><span data-stu-id="7b424-125">This is accomplished by the `security` binding element.</span></span> <span data-ttu-id="7b424-126">Zarówno klient, jak i usługa są uwierzytelniane przy użyciu zabezpieczeń na poziomie komunikatu, jeśli mechanizmu uwierzytelniania Kerberos jest dostępne.</span><span class="sxs-lookup"><span data-stu-id="7b424-126">Both client and service are authenticated using message-level security if the Kerberos authentication mechanism is available.</span></span> <span data-ttu-id="7b424-127">Dzieje się tak, jeśli próbka jest uruchamiany w środowisku usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7b424-127">This happens if the sample is run in the Active Directory environment.</span></span> <span data-ttu-id="7b424-128">Jeśli mechanizm uwierzytelniania Kerberos jest niedostępna, jest używane uwierzytelnianie NTLM.</span><span class="sxs-lookup"><span data-stu-id="7b424-128">If the Kerberos authentication mechanism is not available, NTLM authentication is used.</span></span> <span data-ttu-id="7b424-129">NTLM uwierzytelnia klienta do usługi, ale nie uwierzytelnienia usługi dla klienta.</span><span class="sxs-lookup"><span data-stu-id="7b424-129">NTLM authenticates the client to the service but does not authenticate the service to the client.</span></span> <span data-ttu-id="7b424-130">`security` Element powiązania jest skonfigurowana do używania `SecureConversation``authenticationType`, które powoduje utworzenia sesji zabezpieczeń zarówno klient, jak i usługi.</span><span class="sxs-lookup"><span data-stu-id="7b424-130">The `security` binding element is configured to use `SecureConversation``authenticationType`, which results in the creation of a security session on both the client and the service.</span></span> <span data-ttu-id="7b424-131">Jest to wymagane do włączenia usługi kontraktu dwukierunkowego do pracy.</span><span class="sxs-lookup"><span data-stu-id="7b424-131">This is required to enable the service's duplex contract to work.</span></span>  
  
 <span data-ttu-id="7b424-132">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="7b424-132">When you run the sample, the operation requests and responses are displayed in the client's console window.</span></span> <span data-ttu-id="7b424-133">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="7b424-133">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate client.  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
```  
  
 <span data-ttu-id="7b424-134">Po uruchomieniu próbki, zobacz wiadomości zwracana do klienta na interfejs wywołania zwrotnego wysyłane z usługi.</span><span class="sxs-lookup"><span data-stu-id="7b424-134">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="7b424-135">Zostanie wyświetlona poszczególnych pośrednia wynik, następuje całe równanie po zakończeniu wszystkich operacji.</span><span class="sxs-lookup"><span data-stu-id="7b424-135">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="7b424-136">Naciśnij klawisz ENTER, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="7b424-136">Press ENTER to shut down the client.</span></span>  
  
 <span data-ttu-id="7b424-137">Dołączony pliku Setup.bat umożliwia konfigurowanie klienta i serwera z certyfikatem odpowiedniej usługi uruchamianie hostowanej aplikacji, która wymaga zabezpieczeń oparte na certyfikatach.</span><span class="sxs-lookup"><span data-stu-id="7b424-137">The included Setup.bat file enables you to configure the client and server with the relevant service certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="7b424-138">Ten plik wsadowy muszą zostać zmodyfikowane, aby pracować na komputerach lub do pracy w przypadku z systemem innym niż obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="7b424-138">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="7b424-139">Poniżej przedstawiono krótkie omówienie różnych sekcji pliki wsadowe, które dotyczą tego przykładu tak, aby można modyfikować w prawidłowej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="7b424-139">The following provides a brief overview of the different sections of the batch files that apply to this sample so that they can be modified to run in the appropriate configuration:</span></span>  
  
-   <span data-ttu-id="7b424-140">Tworzenie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="7b424-140">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="7b424-141">Następujące wiersze z pliku pliku Setup.bat utworzenie certyfikatu serwera do użycia.</span><span class="sxs-lookup"><span data-stu-id="7b424-141">The following lines from the Setup.bat file create the server certificate to be used.</span></span> <span data-ttu-id="7b424-142">`%SERVER_NAME%` Zmiennej określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="7b424-142">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="7b424-143">Zmień tę wartość, aby określić nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="7b424-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="7b424-144">Ten plik wsadowy domyślnie nazwę serwera, aby localhost.</span><span class="sxs-lookup"><span data-stu-id="7b424-144">This batch file defaults the server name to localhost.</span></span>  
  
     <span data-ttu-id="7b424-145">Certyfikat jest przechowywany w magazynie CurrentUser usług hostowanych w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7b424-145">The certificate is stored in the CurrentUser store for the Web-hosted services.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="7b424-146">Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="7b424-146">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="7b424-147">Następujące wiersze w pliku Setup.bat kopii pliku certyfikatu serwera do klienta zaufanych osób magazynu.</span><span class="sxs-lookup"><span data-stu-id="7b424-147">The following lines in the Setup.bat file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="7b424-148">Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta.</span><span class="sxs-lookup"><span data-stu-id="7b424-148">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="7b424-149">Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład certyfikat wystawiony przez Microsoft — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="7b424-149">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="7b424-150">Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z programu Visual Studio 2010 wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="7b424-150">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="7b424-151">Wymaga ona, że zmienna środowiskowa MSSDK odwołują się do katalogu, w którym jest zainstalowany zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="7b424-151">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="7b424-152">Ta zmienna środowiskowa jest automatycznie ustawiana w Visual Studio 2010 wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="7b424-152">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7b424-153">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="7b424-153">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7b424-154">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7b424-154">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="7b424-155">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7b424-155">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="7b424-156">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7b424-156">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="7b424-157">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="7b424-157">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="7b424-158">Otwórz okno Wiersz polecenia programu Visual Studio z uprawnieniami administratora i uruchom pliku Setup.bat z folderu instalacyjnego próbki.</span><span class="sxs-lookup"><span data-stu-id="7b424-158">Open a Visual Studio Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="7b424-159">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="7b424-159">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7b424-160">Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="7b424-160">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="7b424-161">Wartość zmiennej środowiskowej PATH w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wskazuje katalog zawierający pliki wykonywalne wymagane przez pliku Setup.bat skryptu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="7b424-161">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="7b424-162">Uruchom Service.exe z \service\bin.</span><span class="sxs-lookup"><span data-stu-id="7b424-162">Launch Service.exe from \service\bin.</span></span>  
  
3.  <span data-ttu-id="7b424-163">Uruchom Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="7b424-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="7b424-164">Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="7b424-164">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="7b424-165">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="7b424-165">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="7b424-166">Aby uruchomić przykład na komputerach</span><span class="sxs-lookup"><span data-stu-id="7b424-166">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="7b424-167">Na komputerze usługi:</span><span class="sxs-lookup"><span data-stu-id="7b424-167">On the service computer:</span></span>  
  
    1.  <span data-ttu-id="7b424-168">Utwórz katalog wirtualny o nazwie servicemodelsamples na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="7b424-168">Create a virtual directory named servicemodelsamples on the service computer.</span></span>  
  
    2.  <span data-ttu-id="7b424-169">Skopiuj pliki programu usługi z \inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="7b424-169">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="7b424-170">Upewnij się, skopiuj pliki w podkatalogu \bin.</span><span class="sxs-lookup"><span data-stu-id="7b424-170">Ensure that you copy the files in the \bin subdirectory.</span></span>  
  
    3.  <span data-ttu-id="7b424-171">Skopiuj pliki pliku Setup.bat i Cleanup.bat komputer usługi.</span><span class="sxs-lookup"><span data-stu-id="7b424-171">Copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
    4.  <span data-ttu-id="7b424-172">Uruchom następujące polecenie w wierszu polecenia programu Visual Studio została otwarta z uprawnieniami administratora: `Setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="7b424-172">Run the following command in a Visual Studio command prompt opened with administrator privileges: `Setup.bat service`.</span></span> <span data-ttu-id="7b424-173">Spowoduje to utworzenie certyfikatu usługi z nazwą podmiotu pasującego do nazwy komputera, na którym uruchomiono plik wsadowy na.</span><span class="sxs-lookup"><span data-stu-id="7b424-173">This creates the service certificate with the subject name matching the name of the computer the batch file was run on.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="7b424-174">Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z programu Visual Studio 2010 wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="7b424-174">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="7b424-175">Wymaga, aby zmiennej środowiskowej path punktu do katalogu, w którym jest zainstalowany zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="7b424-175">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="7b424-176">Ta zmienna środowiskowa jest automatycznie ustawiana w Visual Studio 2010 wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="7b424-176">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>  
  
    5.  <span data-ttu-id="7b424-177">Zmień [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) wewnątrz pliku Service.exe.config w celu odzwierciedlenia nazwy podmiotu certyfikatu generowane w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="7b424-177">Change the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) inside the Service.exe.config file to reflect the subject name of the certificate generated in the previous step.</span></span>  
  
    6.  <span data-ttu-id="7b424-178">Uruchom Service.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="7b424-178">Run Service.exe from a command prompt.</span></span>  
  
2.  <span data-ttu-id="7b424-179">Na komputerze klienckim:</span><span class="sxs-lookup"><span data-stu-id="7b424-179">On the client computer:</span></span>  
  
    1.  <span data-ttu-id="7b424-180">Skopiuj pliki programu klienta z folderu \client\bin\ na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="7b424-180">Copy the client program files from the \client\bin\ folder to the client computer.</span></span> <span data-ttu-id="7b424-181">Również skopiować plik Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="7b424-181">Also copy the Cleanup.bat file.</span></span>  
  
    2.  <span data-ttu-id="7b424-182">Uruchom Cleanup.bat, aby usunąć wszelkie stare certyfikaty z poprzedniej próbki.</span><span class="sxs-lookup"><span data-stu-id="7b424-182">Run Cleanup.bat to remove any old certificates from previous samples.</span></span>  
  
    3.  <span data-ttu-id="7b424-183">Wyeksportuj certyfikat usługi, otwierając wiersz polecenia programu Visual Studio z uprawnieniami administracyjnymi i uruchom następujące polecenie na komputerze usługi (Zastąp `%SERVER_NAME%` z w pełni kwalifikowaną nazwę komputera, na którym usługa jest uruchomiona):</span><span class="sxs-lookup"><span data-stu-id="7b424-183">Export the service's certificate by opening a Visual Studio command prompt with administrative privileges, and running the following command on the service computer (substitute `%SERVER_NAME%` with the fully-qualified name of the computer where the service is running):</span></span>  
  
        ```  
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer  
        ```  
  
    4.  <span data-ttu-id="7b424-184">Skopiuj %SERVER_NAME%.cer na komputerze klienckim (substitute nazwa_serwera % z w pełni kwalifikowaną nazwę komputera, na którym jest uruchomiona usługa).</span><span class="sxs-lookup"><span data-stu-id="7b424-184">Copy %SERVER_NAME%.cer to the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running).</span></span>  
  
    5.  <span data-ttu-id="7b424-185">Zaimportuj certyfikat usługi, otwierając wiersz polecenia programu Visual Studio z uprawnieniami administracyjnymi i uruchom następujące polecenie na komputerze klienckim (substitute nazwa_serwera % z w pełni kwalifikowaną nazwę komputera, na którym usługa jest uruchomiona):</span><span class="sxs-lookup"><span data-stu-id="7b424-185">Import the service's certificate by opening a Visual Studio command prompt with administrative privileges, and running the following command on the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running):</span></span>  
  
        ```  
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople  
        ```  
  
         <span data-ttu-id="7b424-186">Kroki nie są konieczne, jeśli certyfikat został wystawiony przez zaufany wystawcy c, d i e.</span><span class="sxs-lookup"><span data-stu-id="7b424-186">Steps c, d, and e are not necessary if the certificate is issued by a Trusted Issuer.</span></span>  
  
    6.  <span data-ttu-id="7b424-187">Zmodyfikuj plik App.config klienta w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7b424-187">Modify the client’s App.config file as follows:</span></span>  
  
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
  
    7.  <span data-ttu-id="7b424-188">Jeśli usługa jest uruchomiona w ramach konta innego niż Usługa sieciowa lub konta System lokalny w środowisku domeny, może być konieczne zmodyfikowanie tożsamość punktu końcowego dla punktu końcowego usługi w pliku App.config klienta można ustawić odpowiednie nazwy UPN lub nazwy SPN na podstawie konta używanego do uruchamiania usługi.</span><span class="sxs-lookup"><span data-stu-id="7b424-188">If the service is running under an account other than the NetworkService or LocalSystem account in a domain environment, you might need to modify the endpoint identity for the service endpoint inside the client's App.config file to set the appropriate UPN or SPN based on the account that is used to run the service.</span></span> <span data-ttu-id="7b424-189">Aby uzyskać więcej informacji o tożsamości punktu końcowego, zobacz [uwierzytelnianie i tożsamość usługi](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="7b424-189">For more information about endpoint identity, see the [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) topic.</span></span>  
  
    8.  <span data-ttu-id="7b424-190">Uruchom Client.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="7b424-190">Run Client.exe from a command prompt.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="7b424-191">Aby wyczyścić po próbki</span><span class="sxs-lookup"><span data-stu-id="7b424-191">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="7b424-192">Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.</span><span class="sxs-lookup"><span data-stu-id="7b424-192">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b424-193">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b424-193">See Also</span></span>
