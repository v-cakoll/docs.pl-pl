---
title: Przykład technologii serializacji typów ogólnych usług sieci Web
ms.date: 03/30/2017
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
ms.openlocfilehash: b233ed4374231c7e7ff2b6617a63c4e4c94612c2
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46479549"
---
# <a name="web-services-generics-serialization-technology-sample"></a><span data-ttu-id="aff9b-102">Przykład technologii serializacji typów ogólnych usług sieci Web</span><span class="sxs-lookup"><span data-stu-id="aff9b-102">Web Services Generics Serialization Technology Sample</span></span>
[<span data-ttu-id="aff9b-103">Pobierz przykładowe</span><span class="sxs-lookup"><span data-stu-id="aff9b-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 <span data-ttu-id="aff9b-104">W tym przykładzie przedstawiono sposób użycia i sterować serializacji rodzajowych w usługach sieci Web programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="aff9b-104">This sample shows how to use and control the serialization of generics in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="aff9b-105">Aby skompilować przykład za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="aff9b-105">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="aff9b-106">Otwórz program Visual Studio i wybierz **nową witrynę sieci Web** z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="aff9b-106">Open Visual Studio and select **New Web Site** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="aff9b-107">W **nową witrynę sieci Web** okno dialogowe, wybierz w okienku po lewej stronie język programowania, a następnie w okienku po prawej stronie wybierz **usługi sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="aff9b-107">In the **New Web Site** dialog, select from the left pane your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3.  <span data-ttu-id="aff9b-108">Kliknij przycisk **Przeglądaj** i przejdź do podkatalogu \CS\GenericsService.</span><span class="sxs-lookup"><span data-stu-id="aff9b-108">Click **Browse** and navigate to the \CS\GenericsService subdirectory.</span></span>  
  
4.  <span data-ttu-id="aff9b-109">Wybierz Service.asmx do otwierania tego PLiku w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aff9b-109">Select Service.asmx to open the file in Visual Studio.</span></span>  
  
5.  <span data-ttu-id="aff9b-110">Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="aff9b-110">On the **Build** menu, click **Build Solution**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aff9b-111">Pierwszych pięć kroków na tej liście są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="aff9b-111">The first five steps in this list are optional.</span></span> <span data-ttu-id="aff9b-112">Środowisko uruchomieniowe programu .NET Framework automatycznie generuje razem usługi pierwszy sieci Web, gdy wymagane są usługi.</span><span class="sxs-lookup"><span data-stu-id="aff9b-112">The .NET Framework runtime will automatically generate the Web service the first time the service is requested.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aff9b-113">Poniższe kroki są wymagane do utworzenia przykładu.</span><span class="sxs-lookup"><span data-stu-id="aff9b-113">The following steps are required to build the sample.</span></span>  
  
1.  <span data-ttu-id="aff9b-114">Otwórz [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] i przejdź do podkatalogu \CS.</span><span class="sxs-lookup"><span data-stu-id="aff9b-114">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to the \CS subdirectory.</span></span>  
  
2.  <span data-ttu-id="aff9b-115">Kliknij prawym przyciskiem myszy ikonę podkatalogu GenericsService, a następnie wybierz pozycję **udostępnianie i zabezpieczenia**.</span><span class="sxs-lookup"><span data-stu-id="aff9b-115">Right-click the icon for the GenericsService subdirectory, and select **Sharing and Security**.</span></span>  
  
3.  <span data-ttu-id="aff9b-116">W **udostępnianie w sieci Web** zaznacz **Udostępnij ten Folder**.</span><span class="sxs-lookup"><span data-stu-id="aff9b-116">In the **Web Sharing** tab, select **Share this Folder**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="aff9b-117">Zwróć uwagę na nazwy katalogu wirtualnego, który znajduje się w **aliasy** okienka, ponieważ będzie potrzebny do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="aff9b-117">Take note of the virtual directory name that is listed in the **Aliases** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-build-the-sample-using-internet-information-services"></a><span data-ttu-id="aff9b-118">Aby skompilować przykład za pomocą Internetowych usług informacyjnych</span><span class="sxs-lookup"><span data-stu-id="aff9b-118">To build the sample using Internet Information Services</span></span>  
  
1.  <span data-ttu-id="aff9b-119">Otwórz **Internetowe usługi informacyjne** zarządzania przystawki i rozwiń **witryn sieci Web**.</span><span class="sxs-lookup"><span data-stu-id="aff9b-119">Open the **Internet Information Services** management snap-in and expand **Web Sites**.</span></span>  
  
2.  <span data-ttu-id="aff9b-120">Kliknięcie lewym przyciskiem myszy **domyślna witryna sieci Web**, wybierz opcję **nowy**, a następnie wybierz pozycję **katalog wirtualny?** utworzyć **Kreatora tworzenia katalogów wirtualnych**.</span><span class="sxs-lookup"><span data-stu-id="aff9b-120">Left-click **Default Web Site**, select **New**, and then select **Virtual Directory?** to create the **Virtual Directory Creation Wizard**.</span></span>  
  
3.  <span data-ttu-id="aff9b-121">Kliknij przycisk **dalej**, wprowadź alias publicznego dla katalogu wirtualnego, a kliknij **dalej**.</span><span class="sxs-lookup"><span data-stu-id="aff9b-121">Click **Next**, enter the public alias for your virtual directory, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="aff9b-122">Wprowadź ścieżkę do katalogu, w którym zapisywane próbce (zwykle podkatalogu \CS\GenericsService), a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="aff9b-122">Enter the path to the directory where you saved the sample (normally the \CS\GenericsService subdirectory) and click **Next**.</span></span> <span data-ttu-id="aff9b-123">Kliknij przycisk **dalej** aby zakończyć działanie kreatora.</span><span class="sxs-lookup"><span data-stu-id="aff9b-123">Click **Next** to finish the wizard.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="aff9b-124">Zwróć uwagę na nazwy katalogu wirtualnego, który znajduje się w **Alias** okienka, ponieważ będzie potrzebny do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="aff9b-124">Take note of the virtual directory name that is listed in the **Alias** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="aff9b-125">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="aff9b-125">To run the sample</span></span>  
  
1.  <span data-ttu-id="aff9b-126">Otwórz okno przeglądarki, a następnie wybierz jego paskiem adresu.</span><span class="sxs-lookup"><span data-stu-id="aff9b-126">Open a browser window and select its address bar.</span></span>  
  
2.  <span data-ttu-id="aff9b-127">Typ `http://localhost/[virtual directory]/Service.asmx`, gdzie `[virtual directory]` reprezentuje katalog wirtualny utworzony podczas tworzenia przykładu.</span><span class="sxs-lookup"><span data-stu-id="aff9b-127">Type `http://localhost/[virtual directory]/Service.asmx`, where `[virtual directory]` represents the virtual directory you created when you built the sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aff9b-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aff9b-128">Remarks</span></span>  
 <span data-ttu-id="aff9b-129">Przykład przedstawia domyślna strona programu ASP.NET, który zawiera łącza do definicji usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="aff9b-129">The sample displays a default ASP.NET page that contains links to the definition of the Web Service.</span></span> <span data-ttu-id="aff9b-130">Można dostosować wyświetlanie Oprócz modyfikowania kodu źródłowego dla usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="aff9b-130">You can customize the display in addition to modifying the source code for the Web service.</span></span> <span data-ttu-id="aff9b-131">Aby uzyskać więcej informacji, zobacz [klientów usługi sieci Web XML budynku](https://msdn.microsoft.com/library/c606f3cb-4111-45b4-ae42-9300420fa16c).</span><span class="sxs-lookup"><span data-stu-id="aff9b-131">For more information, see [Building XML Web Service Clients](https://msdn.microsoft.com/library/c606f3cb-4111-45b4-ae42-9300420fa16c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aff9b-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aff9b-132">See also</span></span>

- <xref:System.Collections.Generic>  
- <xref:System.Web.Services>  
- <xref:System.Xml.Serialization>  
- [<span data-ttu-id="aff9b-133">Serializacja</span><span class="sxs-lookup"><span data-stu-id="aff9b-133">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
- [<span data-ttu-id="aff9b-134">Usługi sieci Web XML utworzone za pomocą platformy ASP.NET i klientów usługi sieci Web XML</span><span class="sxs-lookup"><span data-stu-id="aff9b-134">XML Web Services Created Using ASP.NET and XML Web Service Clients</span></span>](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c)
