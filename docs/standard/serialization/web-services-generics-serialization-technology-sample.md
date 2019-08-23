---
title: Przykład technologii serializacji danych ogólnych dla usług internetowych
ms.date: 03/30/2017
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
ms.openlocfilehash: 467bfe1fd9eb8a0222385c34cb29a90df00dc937
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960749"
---
# <a name="web-services-generics-serialization-technology-sample"></a><span data-ttu-id="09ab1-102">Przykład technologii serializacji danych ogólnych dla usług internetowych</span><span class="sxs-lookup"><span data-stu-id="09ab1-102">Web Services Generics Serialization Technology Sample</span></span>
[<span data-ttu-id="09ab1-103">Pobierz przykład</span><span class="sxs-lookup"><span data-stu-id="09ab1-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 <span data-ttu-id="09ab1-104">Ten przykład pokazuje, jak używać i kontrolować serializację typów ogólnych w usługach ASP.NET Web Services.</span><span class="sxs-lookup"><span data-stu-id="09ab1-104">This sample shows how to use and control the serialization of generics in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="09ab1-105">Aby skompilować przykład za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="09ab1-105">To build the sample using Visual Studio</span></span>  
  
1. <span data-ttu-id="09ab1-106">Otwórz program Visual Studio i wybierz pozycję **Nowa witryna sieci Web** w menu **plik** .</span><span class="sxs-lookup"><span data-stu-id="09ab1-106">Open Visual Studio and select **New Web Site** from the **File** menu.</span></span>  
  
2. <span data-ttu-id="09ab1-107">W oknie dialogowym **Nowa witryna sieci Web** wybierz w lewym okienku odpowiedni język programowania, a następnie w okienku po prawej stronie wybierz pozycję **usługa sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="09ab1-107">In the **New Web Site** dialog, select from the left pane your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3. <span data-ttu-id="09ab1-108">Kliknij przycisk **Przeglądaj** i przejdź do podkatalogu \CS\GenericsService.</span><span class="sxs-lookup"><span data-stu-id="09ab1-108">Click **Browse** and navigate to the \CS\GenericsService subdirectory.</span></span>  
  
4. <span data-ttu-id="09ab1-109">Wybierz Service.asmx do otwierania tego PLiku w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="09ab1-109">Select Service.asmx to open the file in Visual Studio.</span></span>  
  
5. <span data-ttu-id="09ab1-110">Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="09ab1-110">On the **Build** menu, click **Build Solution**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09ab1-111">Pierwszych pięć kroków na tej liście są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="09ab1-111">The first five steps in this list are optional.</span></span> <span data-ttu-id="09ab1-112">Środowisko uruchomieniowe programu .NET Framework automatycznie generuje razem usługi pierwszy sieci Web, gdy wymagane są usługi.</span><span class="sxs-lookup"><span data-stu-id="09ab1-112">The .NET Framework runtime will automatically generate the Web service the first time the service is requested.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09ab1-113">Poniższe kroki są wymagane do utworzenia przykładu.</span><span class="sxs-lookup"><span data-stu-id="09ab1-113">The following steps are required to build the sample.</span></span>  
  
1. <span data-ttu-id="09ab1-114">Otwórz Eksploratora plików i przejdź do podkatalogu \CS</span><span class="sxs-lookup"><span data-stu-id="09ab1-114">Open File Explorer and navigate to the \CS subdirectory.</span></span>  
  
2. <span data-ttu-id="09ab1-115">Kliknij prawym przyciskiem myszy ikonę podkatalogu GenericsService, a następnie wybierz pozycję **udostępnianie i zabezpieczenia**.</span><span class="sxs-lookup"><span data-stu-id="09ab1-115">Right-click the icon for the GenericsService subdirectory, and select **Sharing and Security**.</span></span>  
  
3. <span data-ttu-id="09ab1-116">Na karcie **udostępnianie w sieci Web** wybierz pozycję **Udostępnij ten folder**.</span><span class="sxs-lookup"><span data-stu-id="09ab1-116">In the **Web Sharing** tab, select **Share this Folder**.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="09ab1-117">Zwróć uwagę na nazwę katalogu wirtualnego, która jest wymieniona w okienku aliasy, ponieważ będzie potrzebna do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="09ab1-117">Take note of the virtual directory name that is listed in the **Aliases** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-build-the-sample-using-internet-information-services"></a><span data-ttu-id="09ab1-118">Aby skompilować przykład za pomocą Internet Information Services</span><span class="sxs-lookup"><span data-stu-id="09ab1-118">To build the sample using Internet Information Services</span></span>  
  
1. <span data-ttu-id="09ab1-119">Otwórz przystawkę Zarządzanie **Internet Information Services** i rozwiń węzeł **witryny sieci Web**.</span><span class="sxs-lookup"><span data-stu-id="09ab1-119">Open the **Internet Information Services** management snap-in and expand **Web Sites**.</span></span>  
  
2. <span data-ttu-id="09ab1-120">Kliknij lewym przyciskiem myszy pozycję **Domyślna witryna sieci Web**, wybierz pozycję **Nowy**, a następnie wybierz pozycję **katalog wirtualny?** aby utworzyć **Kreatora tworzenia katalogów wirtualnych**.</span><span class="sxs-lookup"><span data-stu-id="09ab1-120">Left-click **Default Web Site**, select **New**, and then select **Virtual Directory?** to create the **Virtual Directory Creation Wizard**.</span></span>  
  
3. <span data-ttu-id="09ab1-121">Kliknij przycisk **dalej**, wprowadź publiczny alias katalogu wirtualnego, a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="09ab1-121">Click **Next**, enter the public alias for your virtual directory, and click **Next**.</span></span>  
  
4. <span data-ttu-id="09ab1-122">Wprowadź ścieżkę do katalogu, w którym zapisano przykład (zwykle podkatalog \CS\GenericsService), a następnie kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="09ab1-122">Enter the path to the directory where you saved the sample (normally the \CS\GenericsService subdirectory) and click **Next**.</span></span> <span data-ttu-id="09ab1-123">Kliknij przycisk **dalej** , aby zakończyć pracę kreatora.</span><span class="sxs-lookup"><span data-stu-id="09ab1-123">Click **Next** to finish the wizard.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="09ab1-124">Zwróć uwagę na nazwę katalogu wirtualnego, która jest wymieniona w okienku **alias** , ponieważ będzie potrzebna do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="09ab1-124">Take note of the virtual directory name that is listed in the **Alias** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="09ab1-125">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="09ab1-125">To run the sample</span></span>  
  
1. <span data-ttu-id="09ab1-126">Otwórz okno przeglądarki, a następnie wybierz jego paskiem adresu.</span><span class="sxs-lookup"><span data-stu-id="09ab1-126">Open a browser window and select its address bar.</span></span>  
  
2. <span data-ttu-id="09ab1-127">Typ `http://localhost/[virtual directory]/Service.asmx`, gdzie `[virtual directory]` reprezentuje katalog wirtualny, który został utworzony podczas tworzenia przykładu.</span><span class="sxs-lookup"><span data-stu-id="09ab1-127">Type `http://localhost/[virtual directory]/Service.asmx`, where `[virtual directory]` represents the virtual directory you created when you built the sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09ab1-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09ab1-128">Remarks</span></span>  
 <span data-ttu-id="09ab1-129">Przykład wyświetla domyślną stronę ASP.NET zawierającą linki do definicji usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="09ab1-129">The sample displays a default ASP.NET page that contains links to the definition of the Web Service.</span></span> <span data-ttu-id="09ab1-130">Można dostosować wyświetlanie oprócz modyfikacji kodu źródłowego usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="09ab1-130">You can customize the display in addition to modifying the source code for the Web service.</span></span> <span data-ttu-id="09ab1-131">Aby uzyskać więcej informacji, zobacz [Tworzenie klientów usług sieci Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w3h45ebk(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="09ab1-131">For more information, see [Building XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w3h45ebk(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ab1-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09ab1-132">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Web.Services>
- <xref:System.Xml.Serialization>
- [<span data-ttu-id="09ab1-133">Serializacja</span><span class="sxs-lookup"><span data-stu-id="09ab1-133">Serialization</span></span>](../../../docs/standard/serialization/index.md)
- <span data-ttu-id="09ab1-134">[Usługi sieci Web XML utworzone za pomocą ASP.NET i klientów usług sieci Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="09ab1-134">[XML Web Services Created Using ASP.NET and XML Web Service Clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>
