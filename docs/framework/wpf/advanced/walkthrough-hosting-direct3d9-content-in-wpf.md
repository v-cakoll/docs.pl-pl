---
title: 'Przewodnik: hostowanie zawartości Direct3D9 w WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: 2c31c044aa50a74255a61da1675037ab3d09f615
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053450"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a><span data-ttu-id="58275-102">Przewodnik: hostowanie zawartości Direct3D9 w WPF</span><span class="sxs-lookup"><span data-stu-id="58275-102">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>

<span data-ttu-id="58275-103">W tym instruktażu pokazano, jak hostować zawartość Direct3D9 w aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="58275-103">This walkthrough shows how to host Direct3D9 content in a Windows Presentation Foundation (WPF) application.</span></span>

<span data-ttu-id="58275-104">W tym instruktażu wykonasz następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="58275-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="58275-105">Utwórz projekt WPF do hostowania zawartości Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="58275-105">Create a WPF project to host the Direct3D9 content.</span></span>

- <span data-ttu-id="58275-106">Zaimportuj zawartość Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="58275-106">Import the Direct3D9 content.</span></span>

- <span data-ttu-id="58275-107">Wyświetl zawartość Direct3D9 przy użyciu <xref:System.Windows.Interop.D3DImage> klasy.</span><span class="sxs-lookup"><span data-stu-id="58275-107">Display the Direct3D9 content by using the <xref:System.Windows.Interop.D3DImage> class.</span></span>

 <span data-ttu-id="58275-108">Po zakończeniu dowiesz się, jak hostować zawartość Direct3D9 w aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="58275-108">When you are finished, you will know how to host Direct3D9 content in a WPF application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="58275-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="58275-109">Prerequisites</span></span>

<span data-ttu-id="58275-110">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="58275-110">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="58275-111">Program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="58275-111">Visual Studio.</span></span>

- <span data-ttu-id="58275-112">Zestaw DirectX SDK 9 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="58275-112">DirectX SDK 9 or later.</span></span>

- <span data-ttu-id="58275-113">Biblioteka DLL, która zawiera zawartość Direct3D9 w formacie zgodnym z WPF.</span><span class="sxs-lookup"><span data-stu-id="58275-113">A DLL that contains Direct3D9 content in a WPF-compatible format.</span></span> <span data-ttu-id="58275-114">Aby uzyskać więcej informacji, zobacz [WPF i Direct3D9 — międzyoperacyjność](wpf-and-direct3d9-interoperation.md) i [Przewodnik: Tworzenie zawartości Direct3D9 do hostingu w WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="58275-114">For more information, see [WPF and Direct3D9 Interoperation](wpf-and-direct3d9-interoperation.md) and [Walkthrough: Creating Direct3D9 Content for Hosting in WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span></span>

## <a name="creating-the-wpf-project"></a><span data-ttu-id="58275-115">Tworzenie projektu WPF</span><span class="sxs-lookup"><span data-stu-id="58275-115">Creating the WPF Project</span></span>

<span data-ttu-id="58275-116">Pierwszym krokiem jest utworzenie projektu dla aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="58275-116">The first step is to create the project for the WPF application.</span></span>

### <a name="to-create-the-wpf-project"></a><span data-ttu-id="58275-117">Aby utworzyć projekt WPF</span><span class="sxs-lookup"><span data-stu-id="58275-117">To create the WPF project</span></span>

<span data-ttu-id="58275-118">Utwórz nowy projekt aplikacji WPF w wizualizacji C# o `D3DHost`nazwie.</span><span class="sxs-lookup"><span data-stu-id="58275-118">Create a new WPF Application project in Visual C# named `D3DHost`.</span></span> <span data-ttu-id="58275-119">Aby uzyskać więcej informacji, [zobacz Przewodnik: Moja pierwsza aplikacja](../getting-started/walkthrough-my-first-wpf-desktop-application.md)klasyczna WPF.</span><span class="sxs-lookup"><span data-stu-id="58275-119">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

<span data-ttu-id="58275-120">MainWindow. XAML zostanie otwarty w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="58275-120">MainWindow.xaml opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

## <a name="importing-the-direct3d9-content"></a><span data-ttu-id="58275-121">Importowanie zawartości Direct3D9</span><span class="sxs-lookup"><span data-stu-id="58275-121">Importing the Direct3D9 Content</span></span>

<span data-ttu-id="58275-122">Zawartość Direct3D9 można zaimportować z niezarządzanej biblioteki DLL przy użyciu `DllImport` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="58275-122">You import the Direct3D9 content from an unmanaged DLL by using the `DllImport` attribute.</span></span>

### <a name="to-import-direct3d9-content"></a><span data-ttu-id="58275-123">Aby zaimportować zawartość Direct3D9</span><span class="sxs-lookup"><span data-stu-id="58275-123">To import Direct3D9 content</span></span>

1. <span data-ttu-id="58275-124">Otwórz MainWindow.xaml.cs w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="58275-124">Open MainWindow.xaml.cs in the Code Editor.</span></span>

2. <span data-ttu-id="58275-125">Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="58275-125">Replace the automatically generated code with the following code.</span></span>

    [!code-csharp[System.Windows.Interop.D3DImage#1](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]

## <a name="hosting-the-direct3d9-content"></a><span data-ttu-id="58275-126">Hosting zawartości Direct3D9</span><span class="sxs-lookup"><span data-stu-id="58275-126">Hosting the Direct3D9 Content</span></span>

<span data-ttu-id="58275-127">Na koniec Użyj <xref:System.Windows.Interop.D3DImage> klasy do hostowania zawartości Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="58275-127">Finally, use the <xref:System.Windows.Interop.D3DImage> class to host the Direct3D9 content.</span></span>

### <a name="to-host-the-direct3d9-content"></a><span data-ttu-id="58275-128">Aby hostować zawartość Direct3D9</span><span class="sxs-lookup"><span data-stu-id="58275-128">To host the Direct3D9 content</span></span>

1. <span data-ttu-id="58275-129">W MainWindow. XAML Zastąp automatycznie wygenerowany kod XAML następującym XAML.</span><span class="sxs-lookup"><span data-stu-id="58275-129">In MainWindow.xaml, replace the automatically generated XAML with the following XAML.</span></span>

    [!code-xaml[System.Windows.Interop.D3DImage#10](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]

2. <span data-ttu-id="58275-130">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="58275-130">Build the project.</span></span>

3. <span data-ttu-id="58275-131">Skopiuj plik DLL zawierający zawartość Direct3D9 do folderu bin/debug.</span><span class="sxs-lookup"><span data-stu-id="58275-131">Copy the DLL that contains the Direct3D9 content to the bin/Debug folder.</span></span>

4. <span data-ttu-id="58275-132">Naciśnij klawisz F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="58275-132">Press F5 to run the project.</span></span>

    <span data-ttu-id="58275-133">Zawartość Direct3D9 pojawia się w aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="58275-133">The Direct3D9 content appears within the WPF application.</span></span>

## <a name="see-also"></a><span data-ttu-id="58275-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58275-134">See also</span></span>

- <xref:System.Windows.Interop.D3DImage>
- [<span data-ttu-id="58275-135">Zagadnienia dotyczące współdziałania Direct3D9 i WPF</span><span class="sxs-lookup"><span data-stu-id="58275-135">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
