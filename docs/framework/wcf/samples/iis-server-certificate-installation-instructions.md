---
title: Instrukcje instalacji certyfikatu serwera Internetowych usług informacyjnych
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: 301a10c615a13a42e1a6e1b89d2724476ca4fbae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594663"
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a><span data-ttu-id="88bf2-102">Instrukcje instalacji certyfikatu serwera Internetowych usług informacyjnych</span><span class="sxs-lookup"><span data-stu-id="88bf2-102">Internet Information Services (IIS) Server Certificate Installation Instructions</span></span>
<span data-ttu-id="88bf2-103">Aby uruchomić przykłady, które bezpiecznie komunikują się z Internet Information Services (IIS), należy utworzyć i zainstalować certyfikat serwera.</span><span class="sxs-lookup"><span data-stu-id="88bf2-103">To run the samples that securely communicate with Internet Information Services (IIS), you must create and install a server certificate.</span></span>  
  
## <a name="step-1-creating-certificates"></a><span data-ttu-id="88bf2-104">Krok 1.</span><span class="sxs-lookup"><span data-stu-id="88bf2-104">Step 1.</span></span> <span data-ttu-id="88bf2-105">Tworzenie certyfikatów</span><span class="sxs-lookup"><span data-stu-id="88bf2-105">Creating Certificates</span></span>  
 <span data-ttu-id="88bf2-106">Aby utworzyć certyfikat dla komputera, Otwórz wiersz polecenia dla deweloperów dla programu Visual Studio z uprawnieniami administratora i uruchom setup. bat, który jest dołączony do każdego z przykładów, które używają bezpiecznej komunikacji z usługami IIS.</span><span class="sxs-lookup"><span data-stu-id="88bf2-106">To create a certificate for your computer, open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat that is included in each of the samples that use secure communication with IIS.</span></span> <span data-ttu-id="88bf2-107">Upewnij się, że ścieżka zawiera folder zawierający Makecert. exe przed uruchomieniem tego pliku wsadowego.</span><span class="sxs-lookup"><span data-stu-id="88bf2-107">Ensure that the path includes the folder that contains Makecert.exe before you run this batch file.</span></span> <span data-ttu-id="88bf2-108">Następujące polecenie służy do tworzenia certyfikatu w Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="88bf2-108">The following command is used to create the certificate in Setup.bat.</span></span>  
  
```console  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a><span data-ttu-id="88bf2-109">Krok 2.</span><span class="sxs-lookup"><span data-stu-id="88bf2-109">Step 2.</span></span> <span data-ttu-id="88bf2-110">Instalowanie certyfikatów</span><span class="sxs-lookup"><span data-stu-id="88bf2-110">Installing Certificates</span></span>  
 <span data-ttu-id="88bf2-111">Kroki wymagane do zainstalowania właśnie utworzonych certyfikatów zależą od używanej wersji usług IIS.</span><span class="sxs-lookup"><span data-stu-id="88bf2-111">The steps required to install the certificates you just created depend on which version of IIS you are using.</span></span>  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a><span data-ttu-id="88bf2-112">Aby zainstalować usługi IIS w usługach IIS 5,1 (Windows XP) i IIS 6,0 (Windows Server 2003)</span><span class="sxs-lookup"><span data-stu-id="88bf2-112">To install IIS on IIS 5.1 (Windows XP) and IIS 6.0 (Windows Server 2003)</span></span>  
  
1. <span data-ttu-id="88bf2-113">Otwórz przystawkę MMC Menedżera Internet Information Services.</span><span class="sxs-lookup"><span data-stu-id="88bf2-113">Open the Internet Information Services Manager MMC Snap-In.</span></span>  
  
2. <span data-ttu-id="88bf2-114">Kliknij prawym przyciskiem myszy domyślną witrynę sieci Web i wybierz pozycję **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="88bf2-114">Right-click the default Web site and select **Properties**.</span></span>  
  
3. <span data-ttu-id="88bf2-115">Wybierz kartę **Zabezpieczenia katalogów** .</span><span class="sxs-lookup"><span data-stu-id="88bf2-115">Select the **Directory Security** tab.</span></span>  
  
4. <span data-ttu-id="88bf2-116">Kliknij przycisk **certyfikat serwera** .</span><span class="sxs-lookup"><span data-stu-id="88bf2-116">Click the **Server Certificate** button.</span></span> <span data-ttu-id="88bf2-117">Zostanie uruchomiony Kreator certyfikatu serwera sieci Web.</span><span class="sxs-lookup"><span data-stu-id="88bf2-117">The Web Server Certificate Wizard starts.</span></span>  
  
5. <span data-ttu-id="88bf2-118">Wykonaj kroki kreatora.</span><span class="sxs-lookup"><span data-stu-id="88bf2-118">Complete the wizard.</span></span> <span data-ttu-id="88bf2-119">Wybierz opcję przypisania certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="88bf2-119">Select the option to assign a certificate.</span></span> <span data-ttu-id="88bf2-120">Wybierz certyfikat ServiceModelSamples-HTTPS-Server z listy certyfikatów, które są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="88bf2-120">Select the ServiceModelSamples-HTTPS-Server certificate from the list of certificates that are displayed.</span></span>  
  
     <span data-ttu-id="88bf2-121">![Kreator certyfikatów usług IIS](media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span><span class="sxs-lookup"><span data-stu-id="88bf2-121">![IIS Certificate Wizard](media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span></span>  
  
6. <span data-ttu-id="88bf2-122">Przetestuj dostęp do usługi w przeglądarce przy użyciu adresu HTTPS `https://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="88bf2-122">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a><span data-ttu-id="88bf2-123">Jeśli protokół SSL został wcześniej skonfigurowany przy użyciu programu HttpCfg. exe</span><span class="sxs-lookup"><span data-stu-id="88bf2-123">If SSL was previously configured by using Httpcfg.exe</span></span>  
  
1. <span data-ttu-id="88bf2-124">Użyj Makecert. exe (lub uruchom plik Setup. bat), aby utworzyć certyfikat serwera.</span><span class="sxs-lookup"><span data-stu-id="88bf2-124">Use Makecert.exe (or run Setup.bat) to create the server certificate.</span></span>  
  
2. <span data-ttu-id="88bf2-125">Uruchom Menedżera usług IIS i Zainstaluj certyfikat zgodnie z poprzednimi krokami.</span><span class="sxs-lookup"><span data-stu-id="88bf2-125">Run the IIS manager and install the certificate according to the previous steps.</span></span>  
  
3. <span data-ttu-id="88bf2-126">Dodaj następujący wiersz kodu do programu klienckiego.</span><span class="sxs-lookup"><span data-stu-id="88bf2-126">Add the following line of code to the client program.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="88bf2-127">Ten kod jest wymagany tylko w przypadku certyfikatów testowych, takich jak te utworzone przez Makecert. exe.</span><span class="sxs-lookup"><span data-stu-id="88bf2-127">This code is only required for test certificates such as those created by Makecert.exe.</span></span> <span data-ttu-id="88bf2-128">Nie jest to zalecane w przypadku kodu produkcyjnego.</span><span class="sxs-lookup"><span data-stu-id="88bf2-128">It is not recommended for production code.</span></span>  
  
```csharp  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a><span data-ttu-id="88bf2-129">Aby zainstalować usługi IIS w usługach IIS 7,0 (Windows Vista i Windows Server 2008)</span><span class="sxs-lookup"><span data-stu-id="88bf2-129">To install IIS on IIS 7.0 (Windows Vista and Windows Server 2008)</span></span>  
  
1. <span data-ttu-id="88bf2-130">W menu **Start** kliknij polecenie **Uruchom**, a następnie wpisz **inetmgr** , aby otworzyć przystawkę MMC Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="88bf2-130">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="88bf2-131">Kliknij prawym przyciskiem myszy **domyślną witrynę sieci Web** i wybierz pozycję **Edytuj powiązania...**</span><span class="sxs-lookup"><span data-stu-id="88bf2-131">Right-click the **Default Web Site** and select **Edit Bindings…**</span></span>  
  
3. <span data-ttu-id="88bf2-132">Kliknij przycisk **Dodaj** w oknie dialogowym **powiązania witryny** .</span><span class="sxs-lookup"><span data-stu-id="88bf2-132">Click the **Add** button of the **Site Bindings** dialog box.</span></span>  
  
4. <span data-ttu-id="88bf2-133">Z listy rozwijanej **Typ** wybierz pozycję **https** .</span><span class="sxs-lookup"><span data-stu-id="88bf2-133">Select **HTTPS** from the **Type** drop-down list.</span></span>  
  
5. <span data-ttu-id="88bf2-134">Wybierz pozycję **ServiceModelSamples-HTTPS-Server** z listy rozwijanej **certyfikat SSL** i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="88bf2-134">Select the **ServiceModelSamples-HTTPS-Server** from the **SSL certificate** drop-down list and click **OK**.</span></span>  
  
6. <span data-ttu-id="88bf2-135">Przetestuj dostęp do usługi w przeglądarce przy użyciu adresu HTTPS `https://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="88bf2-135">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="88bf2-136">Ponieważ instalowany certyfikat testowy nie jest zaufanym certyfikatem, podczas przeglądania lokalnych adresów sieci Web zabezpieczonych za pomocą tego certyfikatu mogą wystąpić dodatkowe ostrzeżenia dotyczące zabezpieczeń programu Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="88bf2-136">Because the test certificate you have just installed is not a trusted certificate, you may encounter additional Internet Explorer security warnings when browsing to local Web addresses secured with this certificate.</span></span>  
  
## <a name="removing-certificates"></a><span data-ttu-id="88bf2-137">Usuwanie certyfikatów</span><span class="sxs-lookup"><span data-stu-id="88bf2-137">Removing Certificates</span></span>  
  
- <span data-ttu-id="88bf2-138">Użyj Menedżera Internet Information Services, jak zostało to wcześniej przekazane, ale Usuń certyfikat lub powiązanie zamiast dodawać.</span><span class="sxs-lookup"><span data-stu-id="88bf2-138">Use the Internet Information Services Manager as previously directed, but remove the certificate or binding instead of adding it.</span></span>  
  
- <span data-ttu-id="88bf2-139">Usuń certyfikat komputera za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="88bf2-139">Remove the computer certificate by using the following command.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
