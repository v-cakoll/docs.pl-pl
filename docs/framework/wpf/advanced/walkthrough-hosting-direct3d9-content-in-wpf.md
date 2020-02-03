---
title: Hostowanie zawartości Direct3D9 w WPF
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: e65b0c59268b44abed289e54181bf0bda9355664
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742610"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a><span data-ttu-id="efc1b-102">Wskazówki: hosing zawartości Direct3D9 w WPF</span><span class="sxs-lookup"><span data-stu-id="efc1b-102">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>

<span data-ttu-id="efc1b-103">W tym instruktażu pokazano, jak hostować zawartość Direct3D9 w aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="efc1b-103">This walkthrough shows how to host Direct3D9 content in a Windows Presentation Foundation (WPF) application.</span></span>

<span data-ttu-id="efc1b-104">W tym instruktażu wykonasz następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="efc1b-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="efc1b-105">Utwórz projekt WPF do hostowania zawartości Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="efc1b-105">Create a WPF project to host the Direct3D9 content.</span></span>

- <span data-ttu-id="efc1b-106">Zaimportuj zawartość Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="efc1b-106">Import the Direct3D9 content.</span></span>

- <span data-ttu-id="efc1b-107">Wyświetl zawartość Direct3D9 przy użyciu klasy <xref:System.Windows.Interop.D3DImage>.</span><span class="sxs-lookup"><span data-stu-id="efc1b-107">Display the Direct3D9 content by using the <xref:System.Windows.Interop.D3DImage> class.</span></span>

 <span data-ttu-id="efc1b-108">Po zakończeniu dowiesz się, jak hostować zawartość Direct3D9 w aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="efc1b-108">When you are finished, you will know how to host Direct3D9 content in a WPF application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="efc1b-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="efc1b-109">Prerequisites</span></span>

<span data-ttu-id="efc1b-110">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="efc1b-110">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="efc1b-111">Program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="efc1b-111">Visual Studio.</span></span>

- <span data-ttu-id="efc1b-112">Zestaw DirectX SDK 9 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="efc1b-112">DirectX SDK 9 or later.</span></span>

- <span data-ttu-id="efc1b-113">Biblioteka DLL, która zawiera zawartość Direct3D9 w formacie zgodnym z WPF.</span><span class="sxs-lookup"><span data-stu-id="efc1b-113">A DLL that contains Direct3D9 content in a WPF-compatible format.</span></span> <span data-ttu-id="efc1b-114">Aby uzyskać więcej informacji, zobacz [WPF i Direct3D9 — współdziałanie](wpf-and-direct3d9-interoperation.md) i [Przewodnik: Tworzenie zawartości Direct3D9 do hostingu w WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="efc1b-114">For more information, see [WPF and Direct3D9 Interoperation](wpf-and-direct3d9-interoperation.md) and [Walkthrough: Creating Direct3D9 Content for Hosting in WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span></span>

## <a name="creating-the-wpf-project"></a><span data-ttu-id="efc1b-115">Tworzenie projektu WPF</span><span class="sxs-lookup"><span data-stu-id="efc1b-115">Creating the WPF Project</span></span>

<span data-ttu-id="efc1b-116">Pierwszym krokiem jest utworzenie projektu dla aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="efc1b-116">The first step is to create the project for the WPF application.</span></span>

### <a name="to-create-the-wpf-project"></a><span data-ttu-id="efc1b-117">Aby utworzyć projekt WPF</span><span class="sxs-lookup"><span data-stu-id="efc1b-117">To create the WPF project</span></span>

<span data-ttu-id="efc1b-118">Utwórz nowy projekt aplikacji WPF w wizualizacji C# o nazwie `D3DHost`.</span><span class="sxs-lookup"><span data-stu-id="efc1b-118">Create a new WPF Application project in Visual C# named `D3DHost`.</span></span> <span data-ttu-id="efc1b-119">Aby uzyskać więcej informacji, zobacz [Przewodnik: moja pierwsza aplikacja klasyczna WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="efc1b-119">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

<span data-ttu-id="efc1b-120">MainWindow. XAML zostanie otwarty w projektancie WPF.</span><span class="sxs-lookup"><span data-stu-id="efc1b-120">MainWindow.xaml opens in the WPF Designer.</span></span>

## <a name="importing-the-direct3d9-content"></a><span data-ttu-id="efc1b-121">Importowanie zawartości Direct3D9</span><span class="sxs-lookup"><span data-stu-id="efc1b-121">Importing the Direct3D9 Content</span></span>

<span data-ttu-id="efc1b-122">Zawartość Direct3D9 można zaimportować z niezarządzanej biblioteki DLL przy użyciu atrybutu `DllImport`.</span><span class="sxs-lookup"><span data-stu-id="efc1b-122">You import the Direct3D9 content from an unmanaged DLL by using the `DllImport` attribute.</span></span>

### <a name="to-import-direct3d9-content"></a><span data-ttu-id="efc1b-123">Aby zaimportować zawartość Direct3D9</span><span class="sxs-lookup"><span data-stu-id="efc1b-123">To import Direct3D9 content</span></span>

1. <span data-ttu-id="efc1b-124">Otwórz MainWindow.xaml.cs w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="efc1b-124">Open MainWindow.xaml.cs in the Code Editor.</span></span>

2. <span data-ttu-id="efc1b-125">Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="efc1b-125">Replace the automatically generated code with the following code.</span></span>

    [!code-csharp[System.Windows.Interop.D3DImage#1](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]

## <a name="hosting-the-direct3d9-content"></a><span data-ttu-id="efc1b-126">Hosting zawartości Direct3D9</span><span class="sxs-lookup"><span data-stu-id="efc1b-126">Hosting the Direct3D9 Content</span></span>

<span data-ttu-id="efc1b-127">Na koniec użyj klasy <xref:System.Windows.Interop.D3DImage>, aby hostować zawartość Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="efc1b-127">Finally, use the <xref:System.Windows.Interop.D3DImage> class to host the Direct3D9 content.</span></span>

### <a name="to-host-the-direct3d9-content"></a><span data-ttu-id="efc1b-128">Aby hostować zawartość Direct3D9</span><span class="sxs-lookup"><span data-stu-id="efc1b-128">To host the Direct3D9 content</span></span>

1. <span data-ttu-id="efc1b-129">W MainWindow. XAML Zastąp automatycznie wygenerowany kod XAML następującym XAML.</span><span class="sxs-lookup"><span data-stu-id="efc1b-129">In MainWindow.xaml, replace the automatically generated XAML with the following XAML.</span></span>

    [!code-xaml[System.Windows.Interop.D3DImage#10](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]

2. <span data-ttu-id="efc1b-130">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="efc1b-130">Build the project.</span></span>

3. <span data-ttu-id="efc1b-131">Skopiuj plik DLL zawierający zawartość Direct3D9 do folderu bin/debug.</span><span class="sxs-lookup"><span data-stu-id="efc1b-131">Copy the DLL that contains the Direct3D9 content to the bin/Debug folder.</span></span>

4. <span data-ttu-id="efc1b-132">Naciśnij klawisz F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="efc1b-132">Press F5 to run the project.</span></span>

    <span data-ttu-id="efc1b-133">Zawartość Direct3D9 pojawia się w aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="efc1b-133">The Direct3D9 content appears within the WPF application.</span></span>

## <a name="see-also"></a><span data-ttu-id="efc1b-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efc1b-134">See also</span></span>

- <xref:System.Windows.Interop.D3DImage>
- [<span data-ttu-id="efc1b-135">Zagadnienia dotyczące współdziałania Direct3D9 i WPF</span><span class="sxs-lookup"><span data-stu-id="efc1b-135">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
