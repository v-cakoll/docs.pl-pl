---
title: Instrukcje instalacji certyfikatu serwera Internetowych usług informacyjnych
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: 1bb9c8bb2fedc846f46f665fbfd00178e5c72975
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044907"
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a><span data-ttu-id="8b15b-102">Instrukcje instalacji certyfikatu serwera Internetowych usług informacyjnych</span><span class="sxs-lookup"><span data-stu-id="8b15b-102">Internet Information Services (IIS) Server Certificate Installation Instructions</span></span>
<span data-ttu-id="8b15b-103">Aby uruchomić przykłady, które bezpiecznie komunikują się z Internet Information Services (IIS), należy utworzyć i zainstalować certyfikat serwera.</span><span class="sxs-lookup"><span data-stu-id="8b15b-103">To run the samples that securely communicate with Internet Information Services (IIS), you must create and install a server certificate.</span></span>  
  
## <a name="step-1-creating-certificates"></a><span data-ttu-id="8b15b-104">Krok 1.</span><span class="sxs-lookup"><span data-stu-id="8b15b-104">Step 1.</span></span> <span data-ttu-id="8b15b-105">Tworzenie certyfikatów</span><span class="sxs-lookup"><span data-stu-id="8b15b-105">Creating Certificates</span></span>  
 <span data-ttu-id="8b15b-106">Aby utworzyć certyfikat dla komputera, Otwórz wiersz polecenia dla deweloperów dla programu Visual Studio z uprawnieniami administratora i uruchom setup. bat, który jest dołączony do każdego z przykładów, które używają bezpiecznej komunikacji z usługami IIS.</span><span class="sxs-lookup"><span data-stu-id="8b15b-106">To create a certificate for your computer, open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat that is included in each of the samples that use secure communication with IIS.</span></span> <span data-ttu-id="8b15b-107">Upewnij się, że ścieżka zawiera folder zawierający Makecert. exe przed uruchomieniem tego pliku wsadowego.</span><span class="sxs-lookup"><span data-stu-id="8b15b-107">Ensure that the path includes the folder that contains Makecert.exe before you run this batch file.</span></span> <span data-ttu-id="8b15b-108">Następujące polecenie służy do tworzenia certyfikatu w Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="8b15b-108">The following command is used to create the certificate in Setup.bat.</span></span>  
  
```  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a><span data-ttu-id="8b15b-109">Krok 2.</span><span class="sxs-lookup"><span data-stu-id="8b15b-109">Step 2.</span></span> <span data-ttu-id="8b15b-110">Instalowanie certyfikatów</span><span class="sxs-lookup"><span data-stu-id="8b15b-110">Installing Certificates</span></span>  
 <span data-ttu-id="8b15b-111">Kroki wymagane do zainstalowania właśnie utworzonych certyfikatów zależą od używanej wersji usług IIS.</span><span class="sxs-lookup"><span data-stu-id="8b15b-111">The steps required to install the certificates you just created depend on which version of IIS you are using.</span></span>  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a><span data-ttu-id="8b15b-112">Aby zainstalować usługi IIS w usługach IIS 5,1 (Windows XP) i IIS 6,0 (Windows Server 2003)</span><span class="sxs-lookup"><span data-stu-id="8b15b-112">To install IIS on IIS 5.1 (Windows XP) and IIS 6.0 (Windows Server 2003)</span></span>  
  
1. <span data-ttu-id="8b15b-113">Otwórz przystawkę MMC Menedżera Internet Information Services.</span><span class="sxs-lookup"><span data-stu-id="8b15b-113">Open the Internet Information Services Manager MMC Snap-In.</span></span>  
  
2. <span data-ttu-id="8b15b-114">Kliknij prawym przyciskiem myszy domyślną witrynę sieci Web i wybierz pozycję **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="8b15b-114">Right-click the default Web site and select **Properties**.</span></span>  
  
3. <span data-ttu-id="8b15b-115">Wybierz kartę **Zabezpieczenia katalogów** .</span><span class="sxs-lookup"><span data-stu-id="8b15b-115">Select the **Directory Security** tab.</span></span>  
  
4. <span data-ttu-id="8b15b-116">Kliknij przycisk **certyfikat serwera** .</span><span class="sxs-lookup"><span data-stu-id="8b15b-116">Click the **Server Certificate** button.</span></span> <span data-ttu-id="8b15b-117">Zostanie uruchomiony Kreator certyfikatu serwera sieci Web.</span><span class="sxs-lookup"><span data-stu-id="8b15b-117">The Web Server Certificate Wizard starts.</span></span>  
  
5. <span data-ttu-id="8b15b-118">Ukończ pracę kreatora.</span><span class="sxs-lookup"><span data-stu-id="8b15b-118">Complete the wizard.</span></span> <span data-ttu-id="8b15b-119">Wybierz opcję przypisania certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="8b15b-119">Select the option to assign a certificate.</span></span> <span data-ttu-id="8b15b-120">Wybierz certyfikat ServiceModelSamples-HTTPS-Server z listy certyfikatów, które są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="8b15b-120">Select the ServiceModelSamples-HTTPS-Server certificate from the list of certificates that are displayed.</span></span>  
  
     <span data-ttu-id="8b15b-121">![Kreator certyfikatów usług IIS](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span><span class="sxs-lookup"><span data-stu-id="8b15b-121">![IIS Certificate Wizard](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span></span>  
  
6. <span data-ttu-id="8b15b-122">Przetestuj dostęp do usługi w przeglądarce przy użyciu adresu `https://localhost/servicemodelsamples/service.svc`https.</span><span class="sxs-lookup"><span data-stu-id="8b15b-122">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a><span data-ttu-id="8b15b-123">Jeśli protokół SSL został wcześniej skonfigurowany przy użyciu programu HttpCfg. exe</span><span class="sxs-lookup"><span data-stu-id="8b15b-123">If SSL was previously configured by using Httpcfg.exe</span></span>  
  
1. <span data-ttu-id="8b15b-124">Użyj Makecert. exe (lub uruchom plik Setup. bat), aby utworzyć certyfikat serwera.</span><span class="sxs-lookup"><span data-stu-id="8b15b-124">Use Makecert.exe (or run Setup.bat) to create the server certificate.</span></span>  
  
2. <span data-ttu-id="8b15b-125">Uruchom Menedżera usług IIS i Zainstaluj certyfikat zgodnie z poprzednimi krokami.</span><span class="sxs-lookup"><span data-stu-id="8b15b-125">Run the IIS manager and install the certificate according to the previous steps.</span></span>  
  
3. <span data-ttu-id="8b15b-126">Dodaj następujący wiersz kodu do programu klienckiego.</span><span class="sxs-lookup"><span data-stu-id="8b15b-126">Add the following line of code to the client program.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8b15b-127">Ten kod jest wymagany tylko w przypadku certyfikatów testowych, takich jak te utworzone przez Makecert. exe.</span><span class="sxs-lookup"><span data-stu-id="8b15b-127">This code is only required for test certificates such as those created by Makecert.exe.</span></span> <span data-ttu-id="8b15b-128">Nie jest to zalecane w przypadku kodu produkcyjnego.</span><span class="sxs-lookup"><span data-stu-id="8b15b-128">It is not recommended for production code.</span></span>  
  
```  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a><span data-ttu-id="8b15b-129">Aby zainstalować usługi IIS w usługach IIS 7,0 (Windows Vista i Windows Server 2008)</span><span class="sxs-lookup"><span data-stu-id="8b15b-129">To install IIS on IIS 7.0 (Windows Vista and Windows Server 2008)</span></span>  
  
1. <span data-ttu-id="8b15b-130">W menu **Start** kliknij polecenie **Uruchom**, a następnie wpisz **inetmgr** , aby otworzyć przystawkę MMC Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="8b15b-130">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="8b15b-131">Kliknij prawym przyciskiem myszy **domyślną witrynę sieci Web** i wybierz pozycję **Edytuj powiązania...**</span><span class="sxs-lookup"><span data-stu-id="8b15b-131">Right-click the **Default Web Site** and select **Edit Bindings…**</span></span>  
  
3. <span data-ttu-id="8b15b-132">Kliknij przycisk **Dodaj** w oknie dialogowym **powiązania witryny** .</span><span class="sxs-lookup"><span data-stu-id="8b15b-132">Click the **Add** button of the **Site Bindings** dialog box.</span></span>  
  
4. <span data-ttu-id="8b15b-133">Z listy rozwijanej **Typ** wybierz pozycję **https** .</span><span class="sxs-lookup"><span data-stu-id="8b15b-133">Select **HTTPS** from the **Type** drop-down list.</span></span>  
  
5. <span data-ttu-id="8b15b-134">Wybierz pozycję **ServiceModelSamples-HTTPS-Server** z listy rozwijanej **certyfikat SSL** i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8b15b-134">Select the **ServiceModelSamples-HTTPS-Server** from the **SSL certificate** drop-down list and click **OK**.</span></span>  
  
6. <span data-ttu-id="8b15b-135">Przetestuj dostęp do usługi w przeglądarce przy użyciu adresu `https://localhost/servicemodelsamples/service.svc`https.</span><span class="sxs-lookup"><span data-stu-id="8b15b-135">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b15b-136">Ponieważ instalowany certyfikat testowy nie jest zaufanym certyfikatem, podczas przeglądania lokalnych adresów sieci Web zabezpieczonych za pomocą tego certyfikatu mogą wystąpić dodatkowe ostrzeżenia dotyczące zabezpieczeń programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="8b15b-136">Because the test certificate you have just installed is not a trusted certificate, you may encounter additional Internet Explorer security warnings when browsing to local Web addresses secured with this certificate.</span></span>  
  
## <a name="removing-certificates"></a><span data-ttu-id="8b15b-137">Usuwanie certyfikatów</span><span class="sxs-lookup"><span data-stu-id="8b15b-137">Removing Certificates</span></span>  
  
- <span data-ttu-id="8b15b-138">Użyj Menedżera Internet Information Services, jak zostało to wcześniej przekazane, ale Usuń certyfikat lub powiązanie zamiast dodawać.</span><span class="sxs-lookup"><span data-stu-id="8b15b-138">Use the Internet Information Services Manager as previously directed, but remove the certificate or binding instead of adding it.</span></span>  
  
- <span data-ttu-id="8b15b-139">Usuń certyfikat komputera za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="8b15b-139">Remove the computer certificate by using the following command.</span></span>  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
