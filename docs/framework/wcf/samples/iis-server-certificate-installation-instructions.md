---
title: Instrukcje instalacji certyfikatu serwera Internetowych usług informacyjnych
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: 46d1acf758dd50b881527a16570a1e4a45933958
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a><span data-ttu-id="d3763-102">Instrukcje instalacji certyfikatu serwera Internetowych usług informacyjnych</span><span class="sxs-lookup"><span data-stu-id="d3763-102">Internet Information Services (IIS) Server Certificate Installation Instructions</span></span>
<span data-ttu-id="d3763-103">Aby uruchomić przykłady, które bezpiecznego komunikowania się z programu Internet Information Services (IIS), należy utworzyć i instalowania certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="d3763-103">To run the samples that securely communicate with Internet Information Services (IIS), you must create and install a server certificate.</span></span>  
  
## <a name="step-1-creating-certificates"></a><span data-ttu-id="d3763-104">Krok 1.</span><span class="sxs-lookup"><span data-stu-id="d3763-104">Step 1.</span></span> <span data-ttu-id="d3763-105">Tworzenie certyfikatów</span><span class="sxs-lookup"><span data-stu-id="d3763-105">Creating Certificates</span></span>  
 <span data-ttu-id="d3763-106">Aby utworzyć certyfikat komputera, otwórz wiersz polecenia programu Visual Studio z uprawnieniami administratora i uruchom pliku Setup.bat, który znajduje się w każdym przykłady, które bezpiecznej komunikacji za pomocą usług IIS.</span><span class="sxs-lookup"><span data-stu-id="d3763-106">To create a certificate for your computer, open a Visual Studio command prompt with administrator privileges and run the Setup.bat that is included in each of the samples that use secure communication with IIS.</span></span> <span data-ttu-id="d3763-107">Upewnij się, że ścieżka zawiera folder zawierający Makecert.exe przed uruchomieniem tego pliku wsadowego.</span><span class="sxs-lookup"><span data-stu-id="d3763-107">Ensure that the path includes the folder that contains Makecert.exe before you run this batch file.</span></span> <span data-ttu-id="d3763-108">Następujące polecenie służy do utworzenia certyfikatu w pliku Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="d3763-108">The following command is used to create the certificate in Setup.bat.</span></span>  
  
```  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a><span data-ttu-id="d3763-109">Krok 2.</span><span class="sxs-lookup"><span data-stu-id="d3763-109">Step 2.</span></span> <span data-ttu-id="d3763-110">Instalowanie certyfikatów</span><span class="sxs-lookup"><span data-stu-id="d3763-110">Installing Certificates</span></span>  
 <span data-ttu-id="d3763-111">Kroki wymagane do zainstalowania certyfikatów utworzonego zależą od tego, używając wersji programu IIS.</span><span class="sxs-lookup"><span data-stu-id="d3763-111">The steps required to install the certificates you just created depend on which version of IIS you are using.</span></span>  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a><span data-ttu-id="d3763-112">Aby zainstalować usługi IIS w wersji 5.1 usług IIS (z systemem Windows XP) i usług IIS 6.0 (Windows Server 2003)</span><span class="sxs-lookup"><span data-stu-id="d3763-112">To install IIS on IIS 5.1 (Windows XP) and IIS 6.0 (Windows Server 2003)</span></span>  
  
1.  <span data-ttu-id="d3763-113">Otwórz Internet Information Services przystawki programu MMC Menedżer.</span><span class="sxs-lookup"><span data-stu-id="d3763-113">Open the Internet Information Services Manager MMC Snap-In.</span></span>  
  
2.  <span data-ttu-id="d3763-114">Kliknij prawym przyciskiem myszy domyślnej witryny sieci Web i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d3763-114">Right-click the default Web site and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="d3763-115">Wybierz **zabezpieczenia katalogu** kartę.</span><span class="sxs-lookup"><span data-stu-id="d3763-115">Select the **Directory Security** tab.</span></span>  
  
4.  <span data-ttu-id="d3763-116">Kliknij przycisk **certyfikatu serwera** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d3763-116">Click the **Server Certificate** button.</span></span> <span data-ttu-id="d3763-117">Zostanie uruchomiony Kreator certyfikatu serwera sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d3763-117">The Web Server Certificate Wizard starts.</span></span>  
  
5.  <span data-ttu-id="d3763-118">Ukończ pracę kreatora.</span><span class="sxs-lookup"><span data-stu-id="d3763-118">Complete the wizard.</span></span> <span data-ttu-id="d3763-119">Wybierz opcję, aby przypisać certyfikat.</span><span class="sxs-lookup"><span data-stu-id="d3763-119">Select the option to assign a certificate.</span></span> <span data-ttu-id="d3763-120">Wybierz certyfikat serwera ServiceModelSamples-HTTPS z listy certyfikatów, które są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="d3763-120">Select the ServiceModelSamples-HTTPS-Server certificate from the list of certificates that are displayed.</span></span>  
  
     <span data-ttu-id="d3763-121">![Kreator certyfikatów usług IIS](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span><span class="sxs-lookup"><span data-stu-id="d3763-121">![IIS Certificate Wizard](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span></span>  
  
6.  <span data-ttu-id="d3763-122">Testowanie dostępu do usługi w przeglądarce przy użyciu adresu HTTPS https://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="d3763-122">Test access to the service in a browser by using the HTTPS address https://localhost/servicemodelsamples/service.svc.</span></span>  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a><span data-ttu-id="d3763-123">Jeśli protokół SSL został uprzednio skonfigurowany przy użyciu Httpcfg.exe</span><span class="sxs-lookup"><span data-stu-id="d3763-123">If SSL was previously configured by using Httpcfg.exe</span></span>  
  
1.  <span data-ttu-id="d3763-124">Użyj Makecert.exe (lub wykonywania pliku Setup.bat) można utworzyć certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="d3763-124">Use Makecert.exe (or run Setup.bat) to create the server certificate.</span></span>  
  
2.  <span data-ttu-id="d3763-125">Uruchom Menedżera usług IIS i instalowania certyfikatu zgodnie z poprzednich kroków.</span><span class="sxs-lookup"><span data-stu-id="d3763-125">Run the IIS manager and install the certificate according to the previous steps.</span></span>  
  
3.  <span data-ttu-id="d3763-126">Dodaj następujący wiersz kodu do programu klienta.</span><span class="sxs-lookup"><span data-stu-id="d3763-126">Add the following line of code to the client program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d3763-127">Ten kod jest wymagana tylko dla certyfikaty, takich jak te utworzone przez Makecert.exe testów.</span><span class="sxs-lookup"><span data-stu-id="d3763-127">This code is only required for test certificates such as those created by Makecert.exe.</span></span> <span data-ttu-id="d3763-128">Nie jest zalecane dla kodu produkcyjnego.</span><span class="sxs-lookup"><span data-stu-id="d3763-128">It is not recommended for production code.</span></span>  
  
```  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a><span data-ttu-id="d3763-129">Aby zainstalować usługi IIS w programie IIS 7.0 (system Windows Vista i Windows Server 2008)</span><span class="sxs-lookup"><span data-stu-id="d3763-129">To install IIS on IIS 7.0 (Windows Vista and Windows Server 2008)</span></span>  
  
1.  <span data-ttu-id="d3763-130">Z **Start** menu, kliknij przycisk **Uruchom**, wpisz **inetmgr** do otwierania przystawki MMC usług Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="d3763-130">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="d3763-131">Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** i wybierz **Edytuj powiązania...**</span><span class="sxs-lookup"><span data-stu-id="d3763-131">Right-click the **Default Web Site** and select **Edit Bindings…**</span></span>  
  
3.  <span data-ttu-id="d3763-132">Kliknij przycisk **Dodaj** przycisku **powiązania witryny** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="d3763-132">Click the **Add** button of the **Site Bindings** dialog box.</span></span>  
  
4.  <span data-ttu-id="d3763-133">Wybierz **HTTPS** z **typu** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="d3763-133">Select **HTTPS** from the **Type** drop-down list.</span></span>  
  
5.  <span data-ttu-id="d3763-134">Wybierz **ServiceModelSamples HTTPS serwera** z **certyfikat SSL** listy rozwijanej i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="d3763-134">Select the **ServiceModelSamples-HTTPS-Server** from the **SSL certificate** drop-down list and click **OK**.</span></span>  
  
6.  <span data-ttu-id="d3763-135">Testowanie dostępu do usługi w przeglądarce przy użyciu adresu HTTPS https://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="d3763-135">Test access to the service in a browser by using the HTTPS address https://localhost/servicemodelsamples/service.svc.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3763-136">Ponieważ certyfikat testowy, który został właśnie zainstalowany, nie jest zaufany certyfikat, mogą wystąpić dodatkowe ostrzeżenia dotyczące zabezpieczeń programu Internet Explorer podczas przeglądania do lokalnego adresy sieci Web zabezpieczone przy użyciu tego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d3763-136">Because the test certificate you have just installed is not a trusted certificate, you may encounter additional Internet Explorer security warnings when browsing to local Web addresses secured with this certificate.</span></span>  
  
## <a name="removing-certificates"></a><span data-ttu-id="d3763-137">Usuwanie certyfikatów</span><span class="sxs-lookup"><span data-stu-id="d3763-137">Removing Certificates</span></span>  
  
-   <span data-ttu-id="d3763-138">Zgodnie z wcześniej skierowany, ale usunąć certyfikat lub powiązanie zamiast opcji dodawania go, użyj Menedżera internetowych usług informacyjnych.</span><span class="sxs-lookup"><span data-stu-id="d3763-138">Use the Internet Information Services Manager as previously directed, but remove the certificate or binding instead of adding it.</span></span>  
  
-   <span data-ttu-id="d3763-139">Usuń certyfikat komputera za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="d3763-139">Remove the computer certificate by using the following command.</span></span>  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
