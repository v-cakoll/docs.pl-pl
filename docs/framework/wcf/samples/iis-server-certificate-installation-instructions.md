---
title: Instrukcje instalacji certyfikatu serwera Internetowych usług informacyjnych
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: 8d0b80930424f0d8529f2b035a8e1167f361f99a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303948"
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a><span data-ttu-id="9e4a3-102">Instrukcje instalacji certyfikatu serwera Internetowych usług informacyjnych</span><span class="sxs-lookup"><span data-stu-id="9e4a3-102">Internet Information Services (IIS) Server Certificate Installation Instructions</span></span>
<span data-ttu-id="9e4a3-103">Aby uruchomić przykłady, które bezpiecznego komunikowania się za pomocą programu Internet Information Services (IIS), możesz utworzyć i zainstalować certyfikat serwera.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-103">To run the samples that securely communicate with Internet Information Services (IIS), you must create and install a server certificate.</span></span>  
  
## <a name="step-1-creating-certificates"></a><span data-ttu-id="9e4a3-104">Krok 1.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-104">Step 1.</span></span> <span data-ttu-id="9e4a3-105">Tworzenie certyfikatów</span><span class="sxs-lookup"><span data-stu-id="9e4a3-105">Creating Certificates</span></span>  
 <span data-ttu-id="9e4a3-106">Aby utworzyć certyfikat dla tego komputera, otwórz wiersz polecenia dla deweloperów programu Visual Studio z uprawnieniami administratora i uruchom Setup.bat, który znajduje się w każdym z przykładów, które bezpiecznej komunikacji za pomocą usług IIS.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-106">To create a certificate for your computer, open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat that is included in each of the samples that use secure communication with IIS.</span></span> <span data-ttu-id="9e4a3-107">Upewnij się, że ścieżka zawiera folder, który zawiera Makecert.exe, przed uruchomieniem tego pliku wsadowego.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-107">Ensure that the path includes the folder that contains Makecert.exe before you run this batch file.</span></span> <span data-ttu-id="9e4a3-108">Następujące polecenie służy do utworzenia certyfikatu w Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-108">The following command is used to create the certificate in Setup.bat.</span></span>  
  
```  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a><span data-ttu-id="9e4a3-109">Krok 2.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-109">Step 2.</span></span> <span data-ttu-id="9e4a3-110">Instalowanie certyfikatów</span><span class="sxs-lookup"><span data-stu-id="9e4a3-110">Installing Certificates</span></span>  
 <span data-ttu-id="9e4a3-111">Kroki wymagane do zainstalowania certyfikatów, który został utworzony, zależą od tego, która wersja usług IIS, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-111">The steps required to install the certificates you just created depend on which version of IIS you are using.</span></span>  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a><span data-ttu-id="9e4a3-112">Aby zainstalować usługi IIS 5.1 usług IIS (Windows XP) i usług IIS 6.0 (Windows Server 2003)</span><span class="sxs-lookup"><span data-stu-id="9e4a3-112">To install IIS on IIS 5.1 (Windows XP) and IIS 6.0 (Windows Server 2003)</span></span>  
  
1. <span data-ttu-id="9e4a3-113">Otwórz Internet Information Services Manager przystawki MMC w.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-113">Open the Internet Information Services Manager MMC Snap-In.</span></span>  
  
2. <span data-ttu-id="9e4a3-114">Kliknij prawym przyciskiem myszy domyślna witryna sieci Web, a następnie wybierz pozycję **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-114">Right-click the default Web site and select **Properties**.</span></span>  
  
3. <span data-ttu-id="9e4a3-115">Wybierz **zabezpieczeń katalogu** kartę.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-115">Select the **Directory Security** tab.</span></span>  
  
4. <span data-ttu-id="9e4a3-116">Kliknij przycisk **certyfikatu serwera** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-116">Click the **Server Certificate** button.</span></span> <span data-ttu-id="9e4a3-117">Zostanie uruchomiony Kreator certyfikatu serwera sieci Web.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-117">The Web Server Certificate Wizard starts.</span></span>  
  
5. <span data-ttu-id="9e4a3-118">Ukończ pracę kreatora.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-118">Complete the wizard.</span></span> <span data-ttu-id="9e4a3-119">Wybierz opcję, aby przypisać certyfikat.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-119">Select the option to assign a certificate.</span></span> <span data-ttu-id="9e4a3-120">Wybierz certyfikat ServiceModelSamples HTTPS serwera z listy certyfikatów, które są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-120">Select the ServiceModelSamples-HTTPS-Server certificate from the list of certificates that are displayed.</span></span>  
  
     <span data-ttu-id="9e4a3-121">![Kreator certyfikatów usług IIS](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span><span class="sxs-lookup"><span data-stu-id="9e4a3-121">![IIS Certificate Wizard](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span></span>  
  
6. <span data-ttu-id="9e4a3-122">Testowanie dostępu do usługi w przeglądarce, korzystając z adresu HTTPS `https://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-122">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a><span data-ttu-id="9e4a3-123">Jeśli uprzednio skonfigurowane połączenie SSL przy użyciu Httpcfg.exe</span><span class="sxs-lookup"><span data-stu-id="9e4a3-123">If SSL was previously configured by using Httpcfg.exe</span></span>  
  
1. <span data-ttu-id="9e4a3-124">Użyj Makecert.exe (lub wykonywania Setup.bat), można utworzyć certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-124">Use Makecert.exe (or run Setup.bat) to create the server certificate.</span></span>  
  
2. <span data-ttu-id="9e4a3-125">Uruchom Menedżera usług IIS i instalowania certyfikatu zgodnie z poprzednich kroków.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-125">Run the IIS manager and install the certificate according to the previous steps.</span></span>  
  
3. <span data-ttu-id="9e4a3-126">Dodaj następujący wiersz kodu do programu klienta.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-126">Add the following line of code to the client program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9e4a3-127">Ten kod jest wymagana tylko w przypadku testowania certyfikaty, takich jak te utworzone przez Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-127">This code is only required for test certificates such as those created by Makecert.exe.</span></span> <span data-ttu-id="9e4a3-128">Nie jest zalecane dla kodu produkcyjnego.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-128">It is not recommended for production code.</span></span>  
  
```  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a><span data-ttu-id="9e4a3-129">Aby zainstalować usługi IIS przez usługi IIS 7.0 (Windows Vista i Windows Server 2008)</span><span class="sxs-lookup"><span data-stu-id="9e4a3-129">To install IIS on IIS 7.0 (Windows Vista and Windows Server 2008)</span></span>  
  
1. <span data-ttu-id="9e4a3-130">Z **Start** menu, kliknij przycisk **Uruchom**, a następnie wpisz **inetmgr** aby otworzyć przystawkę MMC usług Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="9e4a3-130">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="9e4a3-131">Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** i wybierz **Edytuj powiązania...**</span><span class="sxs-lookup"><span data-stu-id="9e4a3-131">Right-click the **Default Web Site** and select **Edit Bindings…**</span></span>  
  
3. <span data-ttu-id="9e4a3-132">Kliknij przycisk **Dodaj** przycisku **powiązania witryny** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-132">Click the **Add** button of the **Site Bindings** dialog box.</span></span>  
  
4. <span data-ttu-id="9e4a3-133">Wybierz **HTTPS** z **typu** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-133">Select **HTTPS** from the **Type** drop-down list.</span></span>  
  
5. <span data-ttu-id="9e4a3-134">Wybierz **ServiceModelSamples HTTPS serwera** z **certyfikat SSL** listy rozwijanej i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-134">Select the **ServiceModelSamples-HTTPS-Server** from the **SSL certificate** drop-down list and click **OK**.</span></span>  
  
6. <span data-ttu-id="9e4a3-135">Testowanie dostępu do usługi w przeglądarce, korzystając z adresu HTTPS `https://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-135">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e4a3-136">Ponieważ certyfikat testowy, który właśnie zainstalowałeś nie jest zaufany certyfikat, mogą wystąpić dodatkowe ostrzeżenia dotyczące zabezpieczeń programu Internet Explorer podczas przeglądania do lokalnego adresy sieci Web zabezpieczony za pomocą tego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-136">Because the test certificate you have just installed is not a trusted certificate, you may encounter additional Internet Explorer security warnings when browsing to local Web addresses secured with this certificate.</span></span>  
  
## <a name="removing-certificates"></a><span data-ttu-id="9e4a3-137">Usuwanie certyfikatów</span><span class="sxs-lookup"><span data-stu-id="9e4a3-137">Removing Certificates</span></span>  
  
-   <span data-ttu-id="9e4a3-138">Użyj Menedżera internetowych usług informacyjnych, zgodnie z wcześniej skierowany, ale usunąć certyfikat lub powiązanie zamiast dodawania go.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-138">Use the Internet Information Services Manager as previously directed, but remove the certificate or binding instead of adding it.</span></span>  
  
-   <span data-ttu-id="9e4a3-139">Usuwanie certyfikatu komputera za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="9e4a3-139">Remove the computer certificate by using the following command.</span></span>  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
