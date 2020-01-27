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
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a>Wskazówki: Tworzenie zawartości Direct3D9 dla hostingu w WPF
W tym instruktażu przedstawiono sposób tworzenia zawartości Direct3D9, która jest odpowiednia do hostingu w aplikacji Windows Presentation Foundation (WPF). Aby uzyskać więcej informacji na temat hostowania zawartości Direct3D9 w aplikacjach WPF, zobacz [WPF i Direct3D9](wpf-and-direct3d9-interoperation.md).

 W tym instruktażu wykonasz następujące zadania:

- Utwórz projekt Direct3D9.

- Skonfiguruj projekt Direct3D9 na potrzeby hostingu w aplikacji WPF.

 Po zakończeniu będzie dostępna Biblioteka DLL, która zawiera zawartość Direct3D9 do użycia w aplikacji WPF.

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Visual Studio 2010.

- Zestaw DirectX SDK 9 lub nowszy.

## <a name="creating-the-direct3d9-project"></a>Tworzenie projektu Direct3D9
 Pierwszym krokiem jest utworzenie i skonfigurowanie projektu Direct3D9.

#### <a name="to-create-the-direct3d9-project"></a>Aby utworzyć projekt Direct3D9

1. Utwórz nowy projekt Win32 w C++ nazwanym `D3DContent`.

     Zostanie otwarty Kreator aplikacji Win32 i zostanie wyświetlony ekran powitalny.

2. Kliknij przycisk **Dalej**.

     Zostanie wyświetlony ekran Ustawienia aplikacji.

3. W sekcji **Typ aplikacji** wybierz opcję **dll** .

4. Kliknij przycisk **Zakończ**.

     Projekt D3DContent jest generowany.

5. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt D3DContent i wybierz polecenie **Właściwości**.

     Zostanie otwarte okno dialogowe **strony właściwości D3DContent** .

6. Wybierz węzeł **C/C++**  .

7. W polu **Dodatkowe katalogi dołączane** Określ lokalizację folderu include programu DirectX. Domyślna lokalizacja tego folderu to%ProgramFiles%\Microsoft DirectX SDK (*wersja*) \Include.

8. Kliknij dwukrotnie węzeł **konsolidatora** , aby go rozwinąć.

9. W polu **Dodatkowe katalogi biblioteki** Określ lokalizację folderu biblioteki DirectX. Domyślna lokalizacja tego folderu to%ProgramFiles%\Microsoft DirectX SDK (*wersja*) \Lib\x86.

10. Wybierz węzeł **wejściowy** .

11. W polu **dodatkowe zależności** dodaj pliki `d3d9.lib` i `d3dx9.lib`.

12. W Eksplorator rozwiązań Dodaj nowy plik definicji modułu (. def) o nazwie `D3DContent.def` do projektu.

## <a name="creating-the-direct3d9-content"></a>Tworzenie zawartości Direct3D9
 Aby uzyskać najlepszą wydajność, zawartość Direct3D9 musi używać konkretnych ustawień. Poniższy kod pokazuje, jak utworzyć powierzchnię Direct3D9 o najlepszej charakterystyce wydajności. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące wydajności dla współdziałania Direct3D9 i WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md).

#### <a name="to-create-the-direct3d9-content"></a>Aby utworzyć zawartość Direct3D9

1. Za pomocą Eksplorator rozwiązań Dodaj trzy C++ klasy do projektu o nazwie poniżej.

     `CRenderer` (z destruktorem wirtualnym)

     `CRendererManager`

     `CTriangleRenderer`

2. Otwórz program Render. h w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]

3. Otwórz program Render. cpp w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]

4. Otwórz program Rendermanager. h w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]

5. Otwórz program Renderowaniamanager. cpp w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]

6. Otwórz TriangleRenderer. h w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]

7. Otwórz TriangleRenderer. cpp w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]

8. Otwórz stdafx. h w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.

     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]

9. Otwórz DllMain. cpp w edytorze kodu i Zastąp automatycznie wygenerowany kod następującym kodem.

     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]

10. Otwórz D3DContent. def w edytorze kodu.

11. Zastąp automatycznie wygenerowany kod następującym kodem.

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

12. Skompiluj projekt.

## <a name="next-steps"></a>Następne kroki

- Hostowanie zawartości Direct3D9 w aplikacji WPF. Aby uzyskać więcej informacji, zobacz [Przewodnik: hosting zawartości Direct3D9 w WPF](walkthrough-hosting-direct3d9-content-in-wpf.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Interop.D3DImage>
- [Zagadnienia dotyczące współdziałania Direct3D9 i WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [Przewodnik: hosting zawartości Direct3D9 w WPF](walkthrough-hosting-direct3d9-content-in-wpf.md)
