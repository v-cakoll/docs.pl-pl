---
title: Utwórz zawartość Direct3D9 do hostingu
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
ms.openlocfilehash: 847ee74da5b295c2c9d3824b3df74f94bc98a4db
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727918"
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a><span data-ttu-id="584c8-102">Wskazówki: Tworzenie zawartości Direct3D9 dla hostingu w WPF</span><span class="sxs-lookup"><span data-stu-id="584c8-102">Walkthrough: Creating Direct3D9 Content for Hosting in WPF</span></span>
<span data-ttu-id="584c8-103">W tym instruktażu przedstawiono sposób tworzenia zawartości Direct3D9, która jest odpowiednia do hostingu w aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="584c8-103">This walkthrough shows how to create Direct3D9 content that is suitable for hosting in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="584c8-104">Aby uzyskać więcej informacji na temat hostowania zawartości Direct3D9 w aplikacjach WPF, zobacz [WPF i Direct3D9](wpf-and-direct3d9-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="584c8-104">For more information on hosting Direct3D9 content in WPF applications, see [WPF and Direct3D9 Interoperation](wpf-and-direct3d9-interoperation.md).</span></span>

 <span data-ttu-id="584c8-105">W tym instruktażu wykonasz następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="584c8-105">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="584c8-106">Utwórz projekt Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="584c8-106">Create a Direct3D9 project.</span></span>

- <span data-ttu-id="584c8-107">Skonfiguruj projekt Direct3D9 na potrzeby hostingu w aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="584c8-107">Configure the Direct3D9 project for hosting in a WPF application.</span></span>

 <span data-ttu-id="584c8-108">Po zakończeniu będzie dostępna Biblioteka DLL, która zawiera zawartość Direct3D9 do użycia w aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="584c8-108">When you are finished, you will have a DLL that contains Direct3D9 content for use in a WPF application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="584c8-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="584c8-109">Prerequisites</span></span>
 <span data-ttu-id="584c8-110">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="584c8-110">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="584c8-111">Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="584c8-111">Visual Studio 2010.</span></span>

- <span data-ttu-id="584c8-112">Zestaw DirectX SDK 9 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="584c8-112">DirectX SDK 9 or later.</span></span>

## <a name="creating-the-direct3d9-project"></a><span data-ttu-id="584c8-113">Tworzenie projektu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="584c8-113">Creating the Direct3D9 Project</span></span>
 <span data-ttu-id="584c8-114">Pierwszym krokiem jest utworzenie i skonfigurowanie projektu Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="584c8-114">The first step is to create and configure the Direct3D9 project.</span></span>

#### <a name="to-create-the-direct3d9-project"></a><span data-ttu-id="584c8-115">Aby utworzyć projekt Direct3D9</span><span class="sxs-lookup"><span data-stu-id="584c8-115">To create the Direct3D9 project</span></span>

1. <span data-ttu-id="584c8-116">Utwórz nowy projekt Win32 w C++ nazwanym `D3DContent`.</span><span class="sxs-lookup"><span data-stu-id="584c8-116">Create a new Win32 Project in C++ named `D3DContent`.</span></span>

     <span data-ttu-id="584c8-117">Zostanie otwarty Kreator aplikacji Win32 i zostanie wyświetlony ekran powitalny.</span><span class="sxs-lookup"><span data-stu-id="584c8-117">The Win32 Application Wizard opens and displays the Welcome screen.</span></span>

2. <span data-ttu-id="584c8-118">Kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="584c8-118">Click **Next**.</span></span>

     <span data-ttu-id="584c8-119">Zostanie wyświetlony ekran Ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="584c8-119">The Application Settings screen appears.</span></span>

3. <span data-ttu-id="584c8-120">W sekcji **Typ aplikacji** wybierz opcję **dll** .</span><span class="sxs-lookup"><span data-stu-id="584c8-120">In the **Application type:** section, select the **DLL** option.</span></span>

4. <span data-ttu-id="584c8-121">Kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="584c8-121">Click **Finish**.</span></span>

     <span data-ttu-id="584c8-122">Projekt D3DContent jest generowany.</span><span class="sxs-lookup"><span data-stu-id="584c8-122">The D3DContent project is generated.</span></span>

5. <span data-ttu-id="584c8-123">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt D3DContent i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="584c8-123">In Solution Explorer, right-click the D3DContent project and select **Properties**.</span></span>

     <span data-ttu-id="584c8-124">Zostanie otwarte okno dialogowe **strony właściwości D3DContent** .</span><span class="sxs-lookup"><span data-stu-id="584c8-124">The **D3DContent Property Pages** dialog box opens.</span></span>

6. <span data-ttu-id="584c8-125">Wybierz węzeł **C/C++**  .</span><span class="sxs-lookup"><span data-stu-id="584c8-125">Select the **C/C++** node.</span></span>

7. <span data-ttu-id="584c8-126">W polu **Dodatkowe katalogi dołączane** Określ lokalizację folderu include programu DirectX.</span><span class="sxs-lookup"><span data-stu-id="584c8-126">In the **Additional Include Directories** field, specify the location of the DirectX include folder.</span></span> <span data-ttu-id="584c8-127">Domyślna lokalizacja tego folderu to%ProgramFiles%\Microsoft DirectX SDK (*wersja*) \Include.</span><span class="sxs-lookup"><span data-stu-id="584c8-127">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Include.</span></span>

8. <span data-ttu-id="584c8-128">Kliknij dwukrotnie węzeł **konsolidatora** , aby go rozwinąć.</span><span class="sxs-lookup"><span data-stu-id="584c8-128">Double-click the **Linker** node to expand it.</span></span>

9. <span data-ttu-id="584c8-129">W polu **Dodatkowe katalogi biblioteki** Określ lokalizację folderu biblioteki DirectX.</span><span class="sxs-lookup"><span data-stu-id="584c8-129">In the **Additional Library Directories** field, specify the location of the DirectX libraries folder.</span></span> <span data-ttu-id="584c8-130">Domyślna lokalizacja tego folderu to%ProgramFiles%\Microsoft DirectX SDK (*wersja*) \Lib\x86.</span><span class="sxs-lookup"><span data-stu-id="584c8-130">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Lib\x86.</span></span>

10. <span data-ttu-id="584c8-131">Wybierz węzeł **wejściowy** .</span><span class="sxs-lookup"><span data-stu-id="584c8-131">Select the **Input** node.</span></span>

11. <span data-ttu-id="584c8-132">W polu **dodatkowe zależności** dodaj pliki `d3d9.lib` i `d3dx9.lib`.</span><span class="sxs-lookup"><span data-stu-id="584c8-132">In the **Additional Dependencies** field, add the `d3d9.lib` and `d3dx9.lib` files.</span></span>

12. <span data-ttu-id="584c8-133">W Eksplorator rozwiązań Dodaj nowy plik definicji modułu (. def) o nazwie `D3DContent.def` do projektu.</span><span class="sxs-lookup"><span data-stu-id="584c8-133">In Solution Explorer, add a new module definition file (.def) named `D3DContent.def` to the project.</span></span>

## <a name="creating-the-direct3d9-content"></a><span data-ttu-id="584c8-134">Tworzenie zawartości Direct3D9</span><span class="sxs-lookup"><span data-stu-id="584c8-134">Creating the Direct3D9 Content</span></span>
 <span data-ttu-id="584c8-135">Aby uzyskać najlepszą wydajność, zawartość Direct3D9 musi używać konkretnych ustawień.</span><span class="sxs-lookup"><span data-stu-id="584c8-135">To get the best performance, your Direct3D9 content must use particular settings.</span></span> <span data-ttu-id="584c8-136">Poniższy kod pokazuje, jak utworzyć powierzchnię Direct3D9 o najlepszej charakterystyce wydajności.</span><span class="sxs-lookup"><span data-stu-id="584c8-136">The following code shows how to create a Direct3D9 surface that has the best performance characteristics.</span></span> <span data-ttu-id="584c8-137">Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące wydajności dla współdziałania Direct3D9 i WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span><span class="sxs-lookup"><span data-stu-id="584c8-137">For more information, see [Performance Considerations for Direct3D9 and WPF Interoperability](performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span></span>

#### <a name="to-create-the-direct3d9-content"></a><span data-ttu-id="584c8-138">Aby utworzyć zawartość Direct3D9</span><span class="sxs-lookup"><span data-stu-id="584c8-138">To create the Direct3D9 content</span></span>

1. <span data-ttu-id="584c8-139">Za pomocą Eksplorator rozwiązań Dodaj trzy C++ klasy do projektu o nazwie poniżej.</span><span class="sxs-lookup"><span data-stu-id="584c8-139">Using Solution Explorer, add three C++ classes to the project named the following.</span></span>

     <span data-ttu-id="584c8-140">`CRenderer` (z destruktorem wirtualnym)</span><span class="sxs-lookup"><span data-stu-id="584c8-140">`CRenderer` (with virtual destructor)</span></span>

     `CRendererManager`

     `CTriangleRenderer`

2. <span data-ttu-id="584c8-141">Otwórz program Render. h w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="584c8-141">Open Renderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]

3. <span data-ttu-id="584c8-142">Otwórz program Render. cpp w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="584c8-142">Open Renderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]

4. <span data-ttu-id="584c8-143">Otwórz program Rendermanager. h w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="584c8-143">Open RendererManager.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]

5. <span data-ttu-id="584c8-144">Otwórz program Renderowaniamanager. cpp w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="584c8-144">Open RendererManager.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]

6. <span data-ttu-id="584c8-145">Otwórz TriangleRenderer. h w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="584c8-145">Open TriangleRenderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]

7. <span data-ttu-id="584c8-146">Otwórz TriangleRenderer. cpp w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="584c8-146">Open TriangleRenderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]

8. <span data-ttu-id="584c8-147">Otwórz stdafx. h w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="584c8-147">Open stdafx.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]

9. <span data-ttu-id="584c8-148">Otwórz DllMain. cpp w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="584c8-148">Open dllmain.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]

10. <span data-ttu-id="584c8-149">Otwórz D3DContent. def w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="584c8-149">Open D3DContent.def in the code editor.</span></span>

11. <span data-ttu-id="584c8-150">Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="584c8-150">Replace the automatically generated code with the following code.</span></span>

    ```cpp
    LIBRARY "D3DContent"

    EXPORTS

    SetSize
    SetAlpha
    SetNumDesiredSamples
    SetAdapter

    GetBackBufferNoRef
    Render
    Destroy
    ```

12. <span data-ttu-id="584c8-151">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="584c8-151">Build the project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="584c8-152">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="584c8-152">Next Steps</span></span>

- <span data-ttu-id="584c8-153">Hostowanie zawartości Direct3D9 w aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="584c8-153">Host the Direct3D9 content in a WPF application.</span></span> <span data-ttu-id="584c8-154">Aby uzyskać więcej informacji, zobacz [Przewodnik: hosting zawartości Direct3D9 w WPF](walkthrough-hosting-direct3d9-content-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="584c8-154">For more information, see [Walkthrough: Hosting Direct3D9 Content in WPF](walkthrough-hosting-direct3d9-content-in-wpf.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="584c8-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="584c8-155">See also</span></span>

- <xref:System.Windows.Interop.D3DImage>
- [<span data-ttu-id="584c8-156">Zagadnienia dotyczące współdziałania Direct3D9 i WPF</span><span class="sxs-lookup"><span data-stu-id="584c8-156">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [<span data-ttu-id="584c8-157">Przewodnik: hosting zawartości Direct3D9 w WPF</span><span class="sxs-lookup"><span data-stu-id="584c8-157">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>](walkthrough-hosting-direct3d9-content-in-wpf.md)
