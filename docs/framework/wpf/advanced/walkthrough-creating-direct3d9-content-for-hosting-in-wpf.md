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
ms.workload: dotnet
ms.openlocfilehash: f1a5d70807541a0a3faf6bc99a3ced42827efd72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a>Wskazówki: Tworzenie zawartości Direct3D9 dla hostingu w WPF
W tym przewodniku przedstawiono sposób tworzenia Direct3D9 zawartość, która jest odpowiednia dla hostowanie w aplikacji Windows Presentation Foundation (WPF). Aby uzyskać więcej informacji dotyczących obsługi Direct3D9 zawartości w aplikacjach WPF, zobacz [WPF i współdziałanie Direct3D9](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).  
  
 W tym przewodniku należy wykonać następujące zadania:  
  
-   Utwórz projekt Direct3D9.  
  
-   Konfigurowanie projektu Direct3D9 do umieszczenia w aplikacji WPF.  
  
 Gdy skończysz, konieczne będzie bibliotekę DLL, która zawiera Direct3D9 zawartości do użycia w aplikacji WPF.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].,  
  
-   Później 9or zestawu SDK programu DirectX.  
  
## <a name="creating-the-direct3d9-project"></a>Tworzenie projektu Direct3D9  
 Pierwszym krokiem jest tworzenie i konfigurowanie projektu Direct3D9.  
  
#### <a name="to-create-the-direct3d9-project"></a>Aby utworzyć projekt Direct3D9  
  
1.  Utwórz nowy projekt Win32 w języku C++ o nazwie `D3DContent`.  
  
     Kreator aplikacji Win32 otwiera i wyświetla ekran powitalny.  
  
2.  Kliknij przycisk **Dalej**.  
  
     Zostanie wyświetlony ekran Ustawienia aplikacji.  
  
3.  W **typu aplikacji:** zaznacz **DLL** opcji.  
  
4.  Kliknij przycisk **Zakończ**.  
  
     Projekt D3DContent jest generowany.  
  
5.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt D3DContent i wybierz **właściwości**.  
  
     **Strony właściwości D3DContent** zostanie otwarte okno dialogowe.  
  
6.  Wybierz **C/C++** węzła.  
  
7.  W **dodatkowe katalogi dołączenia** Określ lokalizację DirectX zawierają folder. Domyślna lokalizacja dla tego folderu to %ProgramFiles%\Microsoft zestawu SDK programu DirectX (*wersji*) \Include.  
  
8.  Kliknij dwukrotnie **konsolidatora** węzeł, aby go rozwinąć.  
  
9. W **dodatkowe katalogi bibliotek** Określ lokalizację folderu biblioteki DirectX. Domyślna lokalizacja dla tego folderu to %ProgramFiles%\Microsoft zestawu SDK programu DirectX (*wersji*) \Lib\x86.  
  
10. Wybierz **dane wejściowe** węzła.  
  
11. W **dodatkowe zależności** pól, Dodaj `d3d9.lib` i `d3dx9.lib` plików.  
  
12. W Eksploratorze rozwiązań, Dodaj nowy plik definicji modułu (.def) o nazwie `D3DContent.def` do projektu.  
  
## <a name="creating-the-direct3d9-content"></a>Tworzenie zawartości Direct3D9  
 Aby uzyskać najlepszą wydajność, zawartość Direct3D9 korzystać określone ustawienia. Poniższy kod przedstawia sposób tworzenia powierzchni Direct3D9 cechach najlepszą wydajność. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące wydajności Direct3D9 i współdziałanie WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
#### <a name="to-create-the-direct3d9-content"></a>Aby utworzyć Direct3D9 zawartości  
  
1.  W Eksploratorze rozwiązań Dodaj trzech klas C++ do projektu o nazwie poniżej.  
  
     `CRenderer`(z destruktor wirtualny)  
  
     `CRendererManager`  
  
     `CTriangleRenderer`  
  
2.  Otwórz Renderer.h w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]  
  
3.  Otwórz Renderer.cpp w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]  
  
4.  Otwórz RendererManager.h w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]  
  
5.  Otwórz RendererManager.cpp w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]  
  
6.  Otwórz TriangleRenderer.h w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]  
  
7.  Otwórz TriangleRenderer.cpp w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]  
  
8.  Otwórz stdafx.h w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]  
  
9. Otwórz dllmain.cpp w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]  
  
10. Otwórz D3DContent.def w edytorze kodu.  
  
11. Zastąp następujący kod automatycznie wygenerowanego kodu.  
  
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
  
12. Skompiluj projekt.  
  
## <a name="next-steps"></a>Następne kroki  
  
-   Hostowanie zawartości Direct3D9 w aplikacji WPF. Aby uzyskać więcej informacji, zobacz [wskazówki: Obsługa zawartości Direct3D9 na platformie WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Interop.D3DImage>  
 [Zagadnienia dotyczące współdziałania Direct3D9 i WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)  
 [Przewodnik: hosting zawartości Direct3D9 w WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
