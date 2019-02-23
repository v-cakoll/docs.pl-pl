---
title: 'Przewodnik: Hosting zawartości Direct3D9 w WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: 8a298bdd9a78279f177b5891bf69d0197ec7c040
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56746710"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a><span data-ttu-id="cdb37-102">Przewodnik: Hosting zawartości Direct3D9 w WPF</span><span class="sxs-lookup"><span data-stu-id="cdb37-102">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>
<span data-ttu-id="cdb37-103">Ten poradnik pokazuje jak do hostowania zawartości Direct3D9 w aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="cdb37-103">This walkthrough shows how to host Direct3D9 content in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 <span data-ttu-id="cdb37-104">W tym przewodniku należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="cdb37-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="cdb37-105">Utwórz projekt WPF do hostowania zawartości Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="cdb37-105">Create a WPF project to host the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="cdb37-106">Importowanie zawartości Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="cdb37-106">Import the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="cdb37-107">Wyświetlanie zawartości Direct3D9 przy użyciu <xref:System.Windows.Interop.D3DImage> klasy.</span><span class="sxs-lookup"><span data-stu-id="cdb37-107">Display the Direct3D9 content by using the <xref:System.Windows.Interop.D3DImage> class.</span></span>  
  
 <span data-ttu-id="cdb37-108">Po zakończeniu będzie wiadomo, jak hostować zawartości Direct3D9 w aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="cdb37-108">When you are finished, you will know how to host Direct3D9 content in a WPF application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cdb37-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="cdb37-109">Prerequisites</span></span>  
 <span data-ttu-id="cdb37-110">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="cdb37-110">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="cdb37-111">Program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cdb37-111">Visual Studio.</span></span>  
  
-   <span data-ttu-id="cdb37-112">DirectX SDK 9 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="cdb37-112">DirectX SDK 9 or later.</span></span>  
  
-   <span data-ttu-id="cdb37-113">Biblioteka DLL, która zawiera zawartości Direct3D9 w formacie zgodnym z WPF.</span><span class="sxs-lookup"><span data-stu-id="cdb37-113">A DLL that contains Direct3D9 content in a WPF-compatible format.</span></span> <span data-ttu-id="cdb37-114">Aby uzyskać więcej informacji, zobacz [WPF i Direct3D9 — współdziałanie](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) i [instruktażu: Tworzenie zawartości Direct3D9 dla hostingu w WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="cdb37-114">For more information, see [WPF and Direct3D9 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) and [Walkthrough: Creating Direct3D9 Content for Hosting in WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span></span>  
  
## <a name="creating-the-wpf-project"></a><span data-ttu-id="cdb37-115">Tworzenie projektu WPF</span><span class="sxs-lookup"><span data-stu-id="cdb37-115">Creating the WPF Project</span></span>  
 <span data-ttu-id="cdb37-116">Pierwszym krokiem jest utworzenie projektu dla aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="cdb37-116">The first step is to create the project for the WPF application.</span></span>  
  
#### <a name="to-create-the-wpf-project"></a><span data-ttu-id="cdb37-117">Aby utworzyć projekt WPF</span><span class="sxs-lookup"><span data-stu-id="cdb37-117">To create the WPF project</span></span>  
  
-   <span data-ttu-id="cdb37-118">Utwórz nowy projekt aplikacji WPF w języku Visual C# o nazwie `D3DHost`.</span><span class="sxs-lookup"><span data-stu-id="cdb37-118">Create a new WPF Application project in Visual C# named `D3DHost`.</span></span> <span data-ttu-id="cdb37-119">Aby uzyskać więcej informacji, zobacz [instruktażu: Mój pierwszy aplikacji klasycznej WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="cdb37-119">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
     <span data-ttu-id="cdb37-120">Otworzy się w pliku MainWindow.xaml [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cdb37-120">MainWindow.xaml opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
## <a name="importing-the-direct3d9-content"></a><span data-ttu-id="cdb37-121">Importowanie zawartości Direct3D9</span><span class="sxs-lookup"><span data-stu-id="cdb37-121">Importing the Direct3D9 Content</span></span>  
 <span data-ttu-id="cdb37-122">Importowanie zawartości Direct3D9 z niezarządzaną biblioteką DLL, przy użyciu `DllImport` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="cdb37-122">You import the Direct3D9 content from an unmanaged DLL by using the `DllImport` attribute.</span></span>  
  
#### <a name="to-import-direct3d9-content"></a><span data-ttu-id="cdb37-123">Aby zaimportować zawartości Direct3D9</span><span class="sxs-lookup"><span data-stu-id="cdb37-123">To import Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="cdb37-124">Otwórz plik MainWindow.xaml.cs w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="cdb37-124">Open MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2.  <span data-ttu-id="cdb37-125">Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="cdb37-125">Replace the automatically generated code with the following code.</span></span>  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a><span data-ttu-id="cdb37-126">Hosting zawartości Direct3D9</span><span class="sxs-lookup"><span data-stu-id="cdb37-126">Hosting the Direct3D9 Content</span></span>  
 <span data-ttu-id="cdb37-127">Na koniec użyj <xref:System.Windows.Interop.D3DImage> klasy do obsługi zawartości Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="cdb37-127">Finally, use the <xref:System.Windows.Interop.D3DImage> class to host the Direct3D9 content.</span></span>  
  
#### <a name="to-host-the-direct3d9-content"></a><span data-ttu-id="cdb37-128">Do hostowania zawartości Direct3D9</span><span class="sxs-lookup"><span data-stu-id="cdb37-128">To host the Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="cdb37-129">W pliku MainWindow.xaml Zastąp automatycznie wygenerowany XAML następujące XAML.</span><span class="sxs-lookup"><span data-stu-id="cdb37-129">In MainWindow.xaml, replace the automatically generated XAML with the following XAML.</span></span>  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  <span data-ttu-id="cdb37-130">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="cdb37-130">Build the project.</span></span>  
  
3.  <span data-ttu-id="cdb37-131">Kopiowanie pliku DLL, która zawiera zawartości Direct3D9 do folderu bin/Debug.</span><span class="sxs-lookup"><span data-stu-id="cdb37-131">Copy the DLL that contains the Direct3D9 content to the bin/Debug folder.</span></span>  
  
4.  <span data-ttu-id="cdb37-132">Naciśnij klawisz F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="cdb37-132">Press F5 to run the project.</span></span>  
  
     <span data-ttu-id="cdb37-133">Zawartości Direct3D9 pojawia się w obrębie aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="cdb37-133">The Direct3D9 content appears within the WPF application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdb37-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cdb37-134">See also</span></span>
- <xref:System.Windows.Interop.D3DImage>
- [<span data-ttu-id="cdb37-135">Zagadnienia dotyczące współdziałania Direct3D9 i WPF</span><span class="sxs-lookup"><span data-stu-id="cdb37-135">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
