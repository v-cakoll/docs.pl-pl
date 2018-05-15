---
title: Przykład technologii serializacji typów ogólnych usług sieci Web
ms.date: 03/30/2017
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
ms.openlocfilehash: 29cfa8f66f4b465d30c85c6944b8f3d94203f489
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="web-services-generics-serialization-technology-sample"></a><span data-ttu-id="17bf7-102">Przykład technologii serializacji typów ogólnych usług sieci Web</span><span class="sxs-lookup"><span data-stu-id="17bf7-102">Web Services Generics Serialization Technology Sample</span></span>
[<span data-ttu-id="17bf7-103">Pobieranie próbki</span><span class="sxs-lookup"><span data-stu-id="17bf7-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 <span data-ttu-id="17bf7-104">W tym przykładzie pokazano, jak i kontrolowanie serializacji typów ogólnych w usługach sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="17bf7-104">This sample shows how to use and control the serialization of generics in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="17bf7-105">Aby samodzielnie tworzyć przykładowy przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="17bf7-105">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="17bf7-106">Otwórz program Visual Studio i wybierz **nowej witryny sieci Web** z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="17bf7-106">Open Visual Studio and select **New Web Site** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="17bf7-107">W **nowej witryny sieci Web** okno dialogowe, wybierz w okienku po lewej stronie odpowiedni język programowania, a następnie w okienku po prawej stronie wybierz **usługi sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="17bf7-107">In the **New Web Site** dialog, select from the left pane your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3.  <span data-ttu-id="17bf7-108">Kliknij przycisk **Przeglądaj** i przejdź do podkatalogu \CS\GenericsService.</span><span class="sxs-lookup"><span data-stu-id="17bf7-108">Click **Browse** and navigate to the \CS\GenericsService subdirectory.</span></span>  
  
4.  <span data-ttu-id="17bf7-109">Wybierz Service.asmx do otwierania tego PLiku w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="17bf7-109">Select Service.asmx to open the file in Visual Studio.</span></span>  
  
5.  <span data-ttu-id="17bf7-110">Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="17bf7-110">On the **Build** menu, click **Build Solution**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17bf7-111">Pierwszych pięć kroków na tej liście są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="17bf7-111">The first five steps in this list are optional.</span></span> <span data-ttu-id="17bf7-112">Środowisko uruchomieniowe programu .NET Framework automatycznie generuje razem usługi pierwszy sieci Web, gdy wymagane są usługi.</span><span class="sxs-lookup"><span data-stu-id="17bf7-112">The .NET Framework runtime will automatically generate the Web service the first time the service is requested.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17bf7-113">Poniższe kroki są wymagane do utworzenia próbki.</span><span class="sxs-lookup"><span data-stu-id="17bf7-113">The following steps are required to build the sample.</span></span>  
  
1.  <span data-ttu-id="17bf7-114">Otwórz [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] i przejdź do podkatalogu \CS.</span><span class="sxs-lookup"><span data-stu-id="17bf7-114">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to the \CS subdirectory.</span></span>  
  
2.  <span data-ttu-id="17bf7-115">Kliknij prawym przyciskiem myszy ikonę podkatalogu GenericsService, a następnie wybierz **udostępnianie i zabezpieczenia**.</span><span class="sxs-lookup"><span data-stu-id="17bf7-115">Right-click the icon for the GenericsService subdirectory, and select **Sharing and Security**.</span></span>  
  
3.  <span data-ttu-id="17bf7-116">W **udostępnianie w sieci Web** wybierz opcję **Udostępnij ten Folder**.</span><span class="sxs-lookup"><span data-stu-id="17bf7-116">In the **Web Sharing** tab, select **Share this Folder**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="17bf7-117">Zanotuj nazwę katalogu wirtualnego, który znajduje się w **aliasy** okienka, ponieważ będą potrzebne do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="17bf7-117">Take note of the virtual directory name that is listed in the **Aliases** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-build-the-sample-using-internet-information-services"></a><span data-ttu-id="17bf7-118">Aby samodzielnie tworzyć przykładowy przy użyciu Internetowych usług informacyjnych</span><span class="sxs-lookup"><span data-stu-id="17bf7-118">To build the sample using Internet Information Services</span></span>  
  
1.  <span data-ttu-id="17bf7-119">Otwórz **Internetowe usługi informacyjne** zarządzania przystawka i rozwiń **witryn sieci Web**.</span><span class="sxs-lookup"><span data-stu-id="17bf7-119">Open the **Internet Information Services** management snap-in and expand **Web Sites**.</span></span>  
  
2.  <span data-ttu-id="17bf7-120">Kliknięcie lewym przyciskiem myszy **domyślna witryna sieci Web**, wybierz pozycję **nowy**, a następnie wybierz **katalog wirtualny?** do utworzenia **Kreatora tworzenia katalogów wirtualnych**.</span><span class="sxs-lookup"><span data-stu-id="17bf7-120">Left-click **Default Web Site**, select **New**, and then select **Virtual Directory?** to create the **Virtual Directory Creation Wizard**.</span></span>  
  
3.  <span data-ttu-id="17bf7-121">Kliknij przycisk **dalej**, wprowadź publicznym aliasem katalogu wirtualnego i kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="17bf7-121">Click **Next**, enter the public alias for your virtual directory, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="17bf7-122">Wprowadź ścieżkę do katalogu, w którym zapisano próbki (zwykle w podkatalogu \CS\GenericsService), a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="17bf7-122">Enter the path to the directory where you saved the sample (normally the \CS\GenericsService subdirectory) and click **Next**.</span></span> <span data-ttu-id="17bf7-123">Kliknij przycisk **dalej** aby zakończyć pracę kreatora.</span><span class="sxs-lookup"><span data-stu-id="17bf7-123">Click **Next** to finish the wizard.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="17bf7-124">Zanotuj nazwę katalogu wirtualnego, który znajduje się w **Alias** okienka, ponieważ będą potrzebne do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="17bf7-124">Take note of the virtual directory name that is listed in the **Alias** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="17bf7-125">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="17bf7-125">To run the sample</span></span>  
  
1.  <span data-ttu-id="17bf7-126">Otwórz okno przeglądarki, a następnie wybierz jego paskiem adresu.</span><span class="sxs-lookup"><span data-stu-id="17bf7-126">Open a browser window and select its address bar.</span></span>  
  
2.  <span data-ttu-id="17bf7-127">Typ  **http://localhost/[wirtualnego directory]/Service.asmx**, gdzie [katalog wirtualny] reprezentuje katalog wirtualny utworzony podczas tworzenia przykładowej.</span><span class="sxs-lookup"><span data-stu-id="17bf7-127">Type **http://localhost/[virtual directory]/Service.asmx**, where [virtual directory] represents the virtual directory you created when you built the sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17bf7-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="17bf7-128">Remarks</span></span>  
 <span data-ttu-id="17bf7-129">Przykład przedstawia domyślnej strony ASP.NET, która zawiera łącza do definicji usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="17bf7-129">The sample displays a default ASP.NET page that contains links to the definition of the Web Service.</span></span> <span data-ttu-id="17bf7-130">Można dostosować wyświetlanie oprócz zmodyfikowanie kodu źródłowego dla usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="17bf7-130">You can customize the display in addition to modifying the source code for the Web service.</span></span> <span data-ttu-id="17bf7-131">Aby uzyskać więcej informacji, zobacz [klientami usługi sieci Web XML budynku](https://msdn.microsoft.com/library/c606f3cb-4111-45b4-ae42-9300420fa16c).</span><span class="sxs-lookup"><span data-stu-id="17bf7-131">For more information, see [Building XML Web Service Clients](https://msdn.microsoft.com/library/c606f3cb-4111-45b4-ae42-9300420fa16c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17bf7-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17bf7-132">See Also</span></span>  
 <xref:System.Collections.Generic>  
 <xref:System.Web.Services>  
 <xref:System.Xml.Serialization>  
 [<span data-ttu-id="17bf7-133">Serializacja</span><span class="sxs-lookup"><span data-stu-id="17bf7-133">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
 [<span data-ttu-id="17bf7-134">Utworzone za pomocą programu ASP.NET i klientami usługi XML sieci Web usług XML sieci Web</span><span class="sxs-lookup"><span data-stu-id="17bf7-134">XML Web Services Created Using ASP.NET and XML Web Service Clients</span></span>](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c)
