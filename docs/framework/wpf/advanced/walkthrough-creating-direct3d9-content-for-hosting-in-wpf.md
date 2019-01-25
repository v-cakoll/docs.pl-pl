---
title: 'Przewodnik: Tworzenie zawartości Direct3D9 dla hostingu w WPF'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
ms.openlocfilehash: 8e598b557381bf82b42ea87e2f020ebba4450929
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520298"
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a>Przewodnik: Tworzenie zawartości Direct3D9 dla hostingu w WPF
W tym instruktażu przedstawiono sposób tworzenia zawartości Direct3D9, który jest odpowiedni dla hostingu w aplikacji Windows Presentation Foundation (WPF). Aby uzyskać więcej informacji na temat hosting zawartości Direct3D9 w aplikacjach WPF, zobacz [WPF i Direct3D9 — współdziałanie](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).

 W tym przewodniku należy wykonać następujące zadania:

-   Utwórz projekt Direct3D9.

-   Konfigurowanie projektu Direct3D9 dla hostingu w aplikacji WPF.

 Gdy skończysz, masz biblioteki DLL, która zawiera zawartości Direct3D9 do użycia w aplikacji WPF.

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

-   Visual Studio 2010.

-   DirectX SDK 9 lub nowszy.

## <a name="creating-the-direct3d9-project"></a>Tworzenie projektu Direct3D9
 Pierwszym krokiem jest utworzenie i skonfigurowanie projektu Direct3D9.

#### <a name="to-create-the-direct3d9-project"></a>Aby utworzyć projekt Direct3D9

1.  Utwórz nowy projekt systemu Win32 w języku C++ o nazwie `D3DContent`.

     Kreator aplikacji Win32 otwiera i wyświetla ekran powitalny.

2.  Kliknij przycisk **Dalej**.

     Zostanie wyświetlony ekran ustawień aplikacji.

3.  W **typu aplikacji:** zaznacz **DLL** opcji.

4.  Kliknij przycisk **Zakończ**.

     Projekt D3DContent jest generowany.

5.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt D3DContent, a następnie wybierz **właściwości**.

     **Stron właściwości D3DContent** zostanie otwarte okno dialogowe.

6.  Wybierz **C/C++** węzła.

7.  W **dodatkowe katalogi dołączenia** Określ lokalizację DirectX folderem. Domyślna lokalizacja dla tego folderu to %ProgramFiles%\Microsoft zestawu SDK programu DirectX (*wersji*) \Include.

8.  Kliknij dwukrotnie **konsolidatora** węzeł, aby ją rozwinąć.

9. W **dodatkowe katalogi bibliotek** Określ lokalizację folderu biblioteki DirectX. Domyślna lokalizacja dla tego folderu to %ProgramFiles%\Microsoft zestawu SDK programu DirectX (*wersji*) \Lib\x86.

10. Wybierz **dane wejściowe** węzła.

11. W **dodatkowe zależności** pola, Dodaj `d3d9.lib` i `d3dx9.lib` plików.

12. W oknie Eksploratora rozwiązań Dodaj nowy plik definicji modułu (.def) o nazwie `D3DContent.def` do projektu.

## <a name="creating-the-direct3d9-content"></a>Tworzenie zawartości Direct3D9
 Aby uzyskać najlepszą wydajność, zawartości Direct3D9 użyć określonego ustawienia. Poniższy kod przedstawia sposób tworzenia powierzchni Direct3D9, która ma najlepsze cechy wydajności. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące współdziałania Direct3D9 i WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).

#### <a name="to-create-the-direct3d9-content"></a>Aby utworzyć zawartości Direct3D9

1.  Za pomocą Eksploratora rozwiązań, Dodaj trzy klasy języka C++ do projektu o nazwie poniżej.

     `CRenderer` (z destruktor wirtualny)

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

8.  Otwórz w edytorze kodu w pliku stdafx.h i Zastąp automatycznie wygenerowany kod następującym kodem.

     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]

9. Otwórz dllmain.cpp w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.

     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]

10. Otwórz D3DContent.def w edytorze kodu.

11. Zastąp automatycznie wygenerowany kod następującym kodem.

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

-   Hostowanie zawartości Direct3D9 w aplikacji WPF. Aby uzyskać więcej informacji, zobacz [instruktażu: Hosting zawartości Direct3D9 w WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Interop.D3DImage>
- [Zagadnienia dotyczące współdziałania Direct3D9 i WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [Przewodnik: Hosting zawartości Direct3D9 w WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
