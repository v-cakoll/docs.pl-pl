---
title: 'Przewodnik: tworzenie zawartości Direct3D9 na potrzeby hostingu w WPF'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
ms.openlocfilehash: 160395b84ef7ca447d162ceff34752113a1d59a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62031203"
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a><span data-ttu-id="60b63-102">Przewodnik: tworzenie zawartości Direct3D9 na potrzeby hostingu w WPF</span><span class="sxs-lookup"><span data-stu-id="60b63-102">Walkthrough: Creating Direct3D9 Content for Hosting in WPF</span></span>
<span data-ttu-id="60b63-103">W tym instruktażu przedstawiono sposób tworzenia zawartości Direct3D9, który jest odpowiedni dla hostingu w aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="60b63-103">This walkthrough shows how to create Direct3D9 content that is suitable for hosting in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="60b63-104">Aby uzyskać więcej informacji na temat hosting zawartości Direct3D9 w aplikacjach WPF, zobacz [WPF i Direct3D9 — współdziałanie](wpf-and-direct3d9-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="60b63-104">For more information on hosting Direct3D9 content in WPF applications, see [WPF and Direct3D9 Interoperation](wpf-and-direct3d9-interoperation.md).</span></span>

 <span data-ttu-id="60b63-105">W tym przewodniku należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="60b63-105">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="60b63-106">Utwórz projekt Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="60b63-106">Create a Direct3D9 project.</span></span>

- <span data-ttu-id="60b63-107">Konfigurowanie projektu Direct3D9 dla hostingu w aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="60b63-107">Configure the Direct3D9 project for hosting in a WPF application.</span></span>

 <span data-ttu-id="60b63-108">Gdy skończysz, masz biblioteki DLL, która zawiera zawartości Direct3D9 do użycia w aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="60b63-108">When you are finished, you will have a DLL that contains Direct3D9 content for use in a WPF application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="60b63-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="60b63-109">Prerequisites</span></span>
 <span data-ttu-id="60b63-110">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="60b63-110">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="60b63-111">Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="60b63-111">Visual Studio 2010.</span></span>

- <span data-ttu-id="60b63-112">DirectX SDK 9 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="60b63-112">DirectX SDK 9 or later.</span></span>

## <a name="creating-the-direct3d9-project"></a><span data-ttu-id="60b63-113">Tworzenie projektu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="60b63-113">Creating the Direct3D9 Project</span></span>
 <span data-ttu-id="60b63-114">Pierwszym krokiem jest utworzenie i skonfigurowanie projektu Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="60b63-114">The first step is to create and configure the Direct3D9 project.</span></span>

#### <a name="to-create-the-direct3d9-project"></a><span data-ttu-id="60b63-115">Aby utworzyć projekt Direct3D9</span><span class="sxs-lookup"><span data-stu-id="60b63-115">To create the Direct3D9 project</span></span>

1. <span data-ttu-id="60b63-116">Utwórz nowy projekt systemu Win32 w języku C++ o nazwie `D3DContent`.</span><span class="sxs-lookup"><span data-stu-id="60b63-116">Create a new Win32 Project in C++ named `D3DContent`.</span></span>

     <span data-ttu-id="60b63-117">Kreator aplikacji Win32 otwiera i wyświetla ekran powitalny.</span><span class="sxs-lookup"><span data-stu-id="60b63-117">The Win32 Application Wizard opens and displays the Welcome screen.</span></span>

2. <span data-ttu-id="60b63-118">Kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="60b63-118">Click **Next**.</span></span>

     <span data-ttu-id="60b63-119">Zostanie wyświetlony ekran ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="60b63-119">The Application Settings screen appears.</span></span>

3. <span data-ttu-id="60b63-120">W **typu aplikacji:** zaznacz **DLL** opcji.</span><span class="sxs-lookup"><span data-stu-id="60b63-120">In the **Application type:** section, select the **DLL** option.</span></span>

4. <span data-ttu-id="60b63-121">Kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="60b63-121">Click **Finish**.</span></span>

     <span data-ttu-id="60b63-122">Projekt D3DContent jest generowany.</span><span class="sxs-lookup"><span data-stu-id="60b63-122">The D3DContent project is generated.</span></span>

5. <span data-ttu-id="60b63-123">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt D3DContent, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="60b63-123">In Solution Explorer, right-click the D3DContent project and select **Properties**.</span></span>

     <span data-ttu-id="60b63-124">**Stron właściwości D3DContent** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="60b63-124">The **D3DContent Property Pages** dialog box opens.</span></span>

6. <span data-ttu-id="60b63-125">Wybierz **C/C++** węzła.</span><span class="sxs-lookup"><span data-stu-id="60b63-125">Select the **C/C++** node.</span></span>

7. <span data-ttu-id="60b63-126">W **dodatkowe katalogi dołączenia** Określ lokalizację DirectX folderem.</span><span class="sxs-lookup"><span data-stu-id="60b63-126">In the **Additional Include Directories** field, specify the location of the DirectX include folder.</span></span> <span data-ttu-id="60b63-127">Domyślna lokalizacja dla tego folderu to %ProgramFiles%\Microsoft zestawu SDK programu DirectX (*wersji*) \Include.</span><span class="sxs-lookup"><span data-stu-id="60b63-127">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Include.</span></span>

8. <span data-ttu-id="60b63-128">Kliknij dwukrotnie **konsolidatora** węzeł, aby ją rozwinąć.</span><span class="sxs-lookup"><span data-stu-id="60b63-128">Double-click the **Linker** node to expand it.</span></span>

9. <span data-ttu-id="60b63-129">W **dodatkowe katalogi bibliotek** Określ lokalizację folderu biblioteki DirectX.</span><span class="sxs-lookup"><span data-stu-id="60b63-129">In the **Additional Library Directories** field, specify the location of the DirectX libraries folder.</span></span> <span data-ttu-id="60b63-130">Domyślna lokalizacja dla tego folderu to %ProgramFiles%\Microsoft zestawu SDK programu DirectX (*wersji*) \Lib\x86.</span><span class="sxs-lookup"><span data-stu-id="60b63-130">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Lib\x86.</span></span>

10. <span data-ttu-id="60b63-131">Wybierz **dane wejściowe** węzła.</span><span class="sxs-lookup"><span data-stu-id="60b63-131">Select the **Input** node.</span></span>

11. <span data-ttu-id="60b63-132">W **dodatkowe zależności** pola, Dodaj `d3d9.lib` i `d3dx9.lib` plików.</span><span class="sxs-lookup"><span data-stu-id="60b63-132">In the **Additional Dependencies** field, add the `d3d9.lib` and `d3dx9.lib` files.</span></span>

12. <span data-ttu-id="60b63-133">W oknie Eksploratora rozwiązań Dodaj nowy plik definicji modułu (.def) o nazwie `D3DContent.def` do projektu.</span><span class="sxs-lookup"><span data-stu-id="60b63-133">In Solution Explorer, add a new module definition file (.def) named `D3DContent.def` to the project.</span></span>

## <a name="creating-the-direct3d9-content"></a><span data-ttu-id="60b63-134">Tworzenie zawartości Direct3D9</span><span class="sxs-lookup"><span data-stu-id="60b63-134">Creating the Direct3D9 Content</span></span>
 <span data-ttu-id="60b63-135">Aby uzyskać najlepszą wydajność, zawartości Direct3D9 użyć określonego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="60b63-135">To get the best performance, your Direct3D9 content must use particular settings.</span></span> <span data-ttu-id="60b63-136">Poniższy kod przedstawia sposób tworzenia powierzchni Direct3D9, która ma najlepsze cechy wydajności.</span><span class="sxs-lookup"><span data-stu-id="60b63-136">The following code shows how to create a Direct3D9 surface that has the best performance characteristics.</span></span> <span data-ttu-id="60b63-137">Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące współdziałania Direct3D9 i WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span><span class="sxs-lookup"><span data-stu-id="60b63-137">For more information, see [Performance Considerations for Direct3D9 and WPF Interoperability](performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span></span>

#### <a name="to-create-the-direct3d9-content"></a><span data-ttu-id="60b63-138">Aby utworzyć zawartości Direct3D9</span><span class="sxs-lookup"><span data-stu-id="60b63-138">To create the Direct3D9 content</span></span>

1. <span data-ttu-id="60b63-139">Za pomocą Eksploratora rozwiązań, Dodaj trzy klasy języka C++ do projektu o nazwie poniżej.</span><span class="sxs-lookup"><span data-stu-id="60b63-139">Using Solution Explorer, add three C++ classes to the project named the following.</span></span>

     <span data-ttu-id="60b63-140">`CRenderer` (z destruktor wirtualny)</span><span class="sxs-lookup"><span data-stu-id="60b63-140">`CRenderer` (with virtual destructor)</span></span>

     `CRendererManager`

     `CTriangleRenderer`

2. <span data-ttu-id="60b63-141">Otwórz Renderer.h w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="60b63-141">Open Renderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]

3. <span data-ttu-id="60b63-142">Otwórz Renderer.cpp w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="60b63-142">Open Renderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]

4. <span data-ttu-id="60b63-143">Otwórz RendererManager.h w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="60b63-143">Open RendererManager.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]

5. <span data-ttu-id="60b63-144">Otwórz RendererManager.cpp w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="60b63-144">Open RendererManager.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]

6. <span data-ttu-id="60b63-145">Otwórz TriangleRenderer.h w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="60b63-145">Open TriangleRenderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]

7. <span data-ttu-id="60b63-146">Otwórz TriangleRenderer.cpp w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="60b63-146">Open TriangleRenderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]

8. <span data-ttu-id="60b63-147">Otwórz w edytorze kodu w pliku stdafx.h i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="60b63-147">Open stdafx.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]

9. <span data-ttu-id="60b63-148">Otwórz dllmain.cpp w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="60b63-148">Open dllmain.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]

10. <span data-ttu-id="60b63-149">Otwórz D3DContent.def w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="60b63-149">Open D3DContent.def in the code editor.</span></span>

11. <span data-ttu-id="60b63-150">Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="60b63-150">Replace the automatically generated code with the following code.</span></span>

    ```
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

12. <span data-ttu-id="60b63-151">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="60b63-151">Build the project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="60b63-152">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="60b63-152">Next Steps</span></span>

- <span data-ttu-id="60b63-153">Hostowanie zawartości Direct3D9 w aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="60b63-153">Host the Direct3D9 content in a WPF application.</span></span> <span data-ttu-id="60b63-154">Aby uzyskać więcej informacji, zobacz [instruktażu: Hosting zawartości Direct3D9 w WPF](walkthrough-hosting-direct3d9-content-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="60b63-154">For more information, see [Walkthrough: Hosting Direct3D9 Content in WPF](walkthrough-hosting-direct3d9-content-in-wpf.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="60b63-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60b63-155">See also</span></span>

- <xref:System.Windows.Interop.D3DImage>
- [<span data-ttu-id="60b63-156">Zagadnienia dotyczące współdziałania Direct3D9 i WPF</span><span class="sxs-lookup"><span data-stu-id="60b63-156">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [<span data-ttu-id="60b63-157">Przewodnik: Hosting zawartości Direct3D9 w WPF</span><span class="sxs-lookup"><span data-stu-id="60b63-157">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>](walkthrough-hosting-direct3d9-content-in-wpf.md)
