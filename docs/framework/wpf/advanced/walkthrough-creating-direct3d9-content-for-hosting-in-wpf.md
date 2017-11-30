---
title: "Wskazówki: Tworzenie zawartości Direct3D9 dla hostingu w WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 750e5c42158a87c04a7fb0f2a83f126a698bb93f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a><span data-ttu-id="4ff64-102">Wskazówki: Tworzenie zawartości Direct3D9 dla hostingu w WPF</span><span class="sxs-lookup"><span data-stu-id="4ff64-102">Walkthrough: Creating Direct3D9 Content for Hosting in WPF</span></span>
<span data-ttu-id="4ff64-103">W tym przewodniku przedstawiono sposób tworzenia Direct3D9 zawartość, która jest odpowiednia dla hostowanie w aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="4ff64-103">This walkthrough shows how to create Direct3D9 content that is suitable for hosting in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="4ff64-104">Aby uzyskać więcej informacji dotyczących obsługi Direct3D9 zawartości w aplikacjach WPF, zobacz [WPF i współdziałanie Direct3D9](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="4ff64-104">For more information on hosting Direct3D9 content in WPF applications, see [WPF and Direct3D9 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).</span></span>  
  
 <span data-ttu-id="4ff64-105">W tym przewodniku należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="4ff64-105">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="4ff64-106">Utwórz projekt Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="4ff64-106">Create a Direct3D9 project.</span></span>  
  
-   <span data-ttu-id="4ff64-107">Konfigurowanie projektu Direct3D9 do umieszczenia w aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="4ff64-107">Configure the Direct3D9 project for hosting in a WPF application.</span></span>  
  
 <span data-ttu-id="4ff64-108">Gdy skończysz, konieczne będzie bibliotekę DLL, która zawiera Direct3D9 zawartości do użycia w aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="4ff64-108">When you are finished, you will have a DLL that contains Direct3D9 content for use in a WPF application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4ff64-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="4ff64-109">Prerequisites</span></span>  
 <span data-ttu-id="4ff64-110">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="4ff64-110">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="4ff64-111">.</span><span class="sxs-lookup"><span data-stu-id="4ff64-111">.</span></span>  
  
-   <span data-ttu-id="4ff64-112">Później 9or zestawu SDK programu DirectX.</span><span class="sxs-lookup"><span data-stu-id="4ff64-112">DirectX SDK 9or later.</span></span>  
  
## <a name="creating-the-direct3d9-project"></a><span data-ttu-id="4ff64-113">Tworzenie projektu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="4ff64-113">Creating the Direct3D9 Project</span></span>  
 <span data-ttu-id="4ff64-114">Pierwszym krokiem jest tworzenie i konfigurowanie projektu Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="4ff64-114">The first step is to create and configure the Direct3D9 project.</span></span>  
  
#### <a name="to-create-the-direct3d9-project"></a><span data-ttu-id="4ff64-115">Aby utworzyć projekt Direct3D9</span><span class="sxs-lookup"><span data-stu-id="4ff64-115">To create the Direct3D9 project</span></span>  
  
1.  <span data-ttu-id="4ff64-116">Utwórz nowy projekt Win32 w języku C++ o nazwie `D3DContent`.</span><span class="sxs-lookup"><span data-stu-id="4ff64-116">Create a new Win32 Project in C++ named `D3DContent`.</span></span>  
  
     <span data-ttu-id="4ff64-117">Kreator aplikacji Win32 otwiera i wyświetla ekran powitalny.</span><span class="sxs-lookup"><span data-stu-id="4ff64-117">The Win32 Application Wizard opens and displays the Welcome screen.</span></span>  
  
2.  <span data-ttu-id="4ff64-118">Kliknij przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="4ff64-118">Click **Next**.</span></span>  
  
     <span data-ttu-id="4ff64-119">Zostanie wyświetlony ekran Ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4ff64-119">The Application Settings screen appears.</span></span>  
  
3.  <span data-ttu-id="4ff64-120">W **typu aplikacji:** zaznacz **DLL** opcji.</span><span class="sxs-lookup"><span data-stu-id="4ff64-120">In the **Application type:** section, select the **DLL** option.</span></span>  
  
4.  <span data-ttu-id="4ff64-121">Kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="4ff64-121">Click **Finish**.</span></span>  
  
     <span data-ttu-id="4ff64-122">Projekt D3DContent jest generowany.</span><span class="sxs-lookup"><span data-stu-id="4ff64-122">The D3DContent project is generated.</span></span>  
  
5.  <span data-ttu-id="4ff64-123">W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt D3DContent i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="4ff64-123">In Solution Explorer, right-click the D3DContent project and select **Properties**.</span></span>  
  
     <span data-ttu-id="4ff64-124">**Strony właściwości D3DContent** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="4ff64-124">The **D3DContent Property Pages** dialog box opens.</span></span>  
  
6.  <span data-ttu-id="4ff64-125">Wybierz **C/C++** węzła.</span><span class="sxs-lookup"><span data-stu-id="4ff64-125">Select the **C/C++** node.</span></span>  
  
7.  <span data-ttu-id="4ff64-126">W **dodatkowe katalogi dołączenia** Określ lokalizację DirectX zawierają folder.</span><span class="sxs-lookup"><span data-stu-id="4ff64-126">In the **Additional Include Directories** field, specify the location of the DirectX include folder.</span></span> <span data-ttu-id="4ff64-127">Domyślna lokalizacja dla tego folderu to %ProgramFiles%\Microsoft zestawu SDK programu DirectX (*wersji*) \Include.</span><span class="sxs-lookup"><span data-stu-id="4ff64-127">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Include.</span></span>  
  
8.  <span data-ttu-id="4ff64-128">Kliknij dwukrotnie **konsolidatora** węzeł, aby go rozwinąć.</span><span class="sxs-lookup"><span data-stu-id="4ff64-128">Double-click the **Linker** node to expand it.</span></span>  
  
9. <span data-ttu-id="4ff64-129">W **dodatkowe katalogi bibliotek** Określ lokalizację folderu biblioteki DirectX.</span><span class="sxs-lookup"><span data-stu-id="4ff64-129">In the **Additional Library Directories** field, specify the location of the DirectX libraries folder.</span></span> <span data-ttu-id="4ff64-130">Domyślna lokalizacja dla tego folderu to %ProgramFiles%\Microsoft zestawu SDK programu DirectX (*wersji*) \Lib\x86.</span><span class="sxs-lookup"><span data-stu-id="4ff64-130">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Lib\x86.</span></span>  
  
10. <span data-ttu-id="4ff64-131">Wybierz **dane wejściowe** węzła.</span><span class="sxs-lookup"><span data-stu-id="4ff64-131">Select the **Input** node.</span></span>  
  
11. <span data-ttu-id="4ff64-132">W **dodatkowe zależności** pól, Dodaj `d3d9.lib` i `d3dx9.lib` plików.</span><span class="sxs-lookup"><span data-stu-id="4ff64-132">In the **Additional Dependencies** field, add the `d3d9.lib` and `d3dx9.lib` files.</span></span>  
  
12. <span data-ttu-id="4ff64-133">W Eksploratorze rozwiązań, Dodaj nowy plik definicji modułu (.def) o nazwie `D3DContent.def` do projektu.</span><span class="sxs-lookup"><span data-stu-id="4ff64-133">In Solution Explorer, add a new module definition file (.def) named `D3DContent.def` to the project.</span></span>  
  
## <a name="creating-the-direct3d9-content"></a><span data-ttu-id="4ff64-134">Tworzenie zawartości Direct3D9</span><span class="sxs-lookup"><span data-stu-id="4ff64-134">Creating the Direct3D9 Content</span></span>  
 <span data-ttu-id="4ff64-135">Aby uzyskać najlepszą wydajność, zawartość Direct3D9 korzystać określone ustawienia.</span><span class="sxs-lookup"><span data-stu-id="4ff64-135">To get the best performance, your Direct3D9 content must use particular settings.</span></span> <span data-ttu-id="4ff64-136">Poniższy kod przedstawia sposób tworzenia powierzchni Direct3D9 cechach najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="4ff64-136">The following code shows how to create a Direct3D9 surface that has the best performance characteristics.</span></span> <span data-ttu-id="4ff64-137">Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące wydajności Direct3D9 i współdziałanie WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span><span class="sxs-lookup"><span data-stu-id="4ff64-137">For more information, see [Performance Considerations for Direct3D9 and WPF Interoperability](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span></span>  
  
#### <a name="to-create-the-direct3d9-content"></a><span data-ttu-id="4ff64-138">Aby utworzyć Direct3D9 zawartości</span><span class="sxs-lookup"><span data-stu-id="4ff64-138">To create the Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="4ff64-139">W Eksploratorze rozwiązań Dodaj trzech klas C++ do projektu o nazwie poniżej.</span><span class="sxs-lookup"><span data-stu-id="4ff64-139">Using Solution Explorer, add three C++ classes to the project named the following.</span></span>  
  
     <span data-ttu-id="4ff64-140">`CRenderer`(z destruktor wirtualny)</span><span class="sxs-lookup"><span data-stu-id="4ff64-140">`CRenderer` (with virtual destructor)</span></span>  
  
     `CRendererManager`  
  
     `CTriangleRenderer`  
  
2.  <span data-ttu-id="4ff64-141">Otwórz Renderer.h w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="4ff64-141">Open Renderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]  
  
3.  <span data-ttu-id="4ff64-142">Otwórz Renderer.cpp w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="4ff64-142">Open Renderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]  
  
4.  <span data-ttu-id="4ff64-143">Otwórz RendererManager.h w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="4ff64-143">Open RendererManager.h in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]  
  
5.  <span data-ttu-id="4ff64-144">Otwórz RendererManager.cpp w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="4ff64-144">Open RendererManager.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]  
  
6.  <span data-ttu-id="4ff64-145">Otwórz TriangleRenderer.h w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="4ff64-145">Open TriangleRenderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]  
  
7.  <span data-ttu-id="4ff64-146">Otwórz TriangleRenderer.cpp w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="4ff64-146">Open TriangleRenderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]  
  
8.  <span data-ttu-id="4ff64-147">Otwórz stdafx.h w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="4ff64-147">Open stdafx.h in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]  
  
9. <span data-ttu-id="4ff64-148">Otwórz dllmain.cpp w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="4ff64-148">Open dllmain.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]  
  
10. <span data-ttu-id="4ff64-149">Otwórz D3DContent.def w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="4ff64-149">Open D3DContent.def in the code editor.</span></span>  
  
11. <span data-ttu-id="4ff64-150">Zastąp następujący kod automatycznie wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="4ff64-150">Replace the automatically generated code with the following code.</span></span>  
  
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
  
12. <span data-ttu-id="4ff64-151">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="4ff64-151">Build the project.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4ff64-152">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="4ff64-152">Next Steps</span></span>  
  
-   <span data-ttu-id="4ff64-153">Hostowanie zawartości Direct3D9 w aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="4ff64-153">Host the Direct3D9 content in a WPF application.</span></span> <span data-ttu-id="4ff64-154">Aby uzyskać więcej informacji, zobacz [wskazówki: Obsługa zawartości Direct3D9 na platformie WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="4ff64-154">For more information, see [Walkthrough: Hosting Direct3D9 Content in WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ff64-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ff64-155">See Also</span></span>  
 <xref:System.Windows.Interop.D3DImage>  
 [<span data-ttu-id="4ff64-156">Zagadnienia dotyczące wydajności Direct3D9 i współdziałanie z WPF</span><span class="sxs-lookup"><span data-stu-id="4ff64-156">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)  
 [<span data-ttu-id="4ff64-157">Wskazówki: Obsługa Direct3D9 zawartości na platformie WPF</span><span class="sxs-lookup"><span data-stu-id="4ff64-157">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
