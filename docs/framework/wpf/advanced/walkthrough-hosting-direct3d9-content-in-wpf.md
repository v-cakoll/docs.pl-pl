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
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a>Przewodnik: hostowanie zawartości Direct3D9 w WPF

W tym instruktażu pokazano, jak hostować zawartość Direct3D9 w aplikacji Windows Presentation Foundation (WPF).

W tym instruktażu wykonasz następujące zadania:

- Utwórz projekt WPF do hostowania zawartości Direct3D9.

- Zaimportuj zawartość Direct3D9.

- Wyświetl zawartość Direct3D9 przy użyciu <xref:System.Windows.Interop.D3DImage> klasy.

 Po zakończeniu dowiesz się, jak hostować zawartość Direct3D9 w aplikacji WPF.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Program Visual Studio.

- Zestaw DirectX SDK 9 lub nowszy.

- Biblioteka DLL, która zawiera zawartość Direct3D9 w formacie zgodnym z WPF. Aby uzyskać więcej informacji, zobacz [WPF i Direct3D9 — międzyoperacyjność](wpf-and-direct3d9-interoperation.md) i [Przewodnik: Tworzenie zawartości Direct3D9 do hostingu w WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).

## <a name="creating-the-wpf-project"></a>Tworzenie projektu WPF

Pierwszym krokiem jest utworzenie projektu dla aplikacji WPF.

### <a name="to-create-the-wpf-project"></a>Aby utworzyć projekt WPF

Utwórz nowy projekt aplikacji WPF w wizualizacji C# o `D3DHost`nazwie. Aby uzyskać więcej informacji, [zobacz Przewodnik: Moja pierwsza aplikacja](../getting-started/walkthrough-my-first-wpf-desktop-application.md)klasyczna WPF.

MainWindow. XAML zostanie otwarty w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

## <a name="importing-the-direct3d9-content"></a>Importowanie zawartości Direct3D9

Zawartość Direct3D9 można zaimportować z niezarządzanej biblioteki DLL przy użyciu `DllImport` atrybutu.

### <a name="to-import-direct3d9-content"></a>Aby zaimportować zawartość Direct3D9

1. Otwórz MainWindow.xaml.cs w edytorze kodu.

2. Zastąp automatycznie wygenerowany kod następującym kodem.

    [!code-csharp[System.Windows.Interop.D3DImage#1](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]

## <a name="hosting-the-direct3d9-content"></a>Hosting zawartości Direct3D9

Na koniec Użyj <xref:System.Windows.Interop.D3DImage> klasy do hostowania zawartości Direct3D9.

### <a name="to-host-the-direct3d9-content"></a>Aby hostować zawartość Direct3D9

1. W MainWindow. XAML Zastąp automatycznie wygenerowany kod XAML następującym XAML.

    [!code-xaml[System.Windows.Interop.D3DImage#10](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]

2. Skompiluj projekt.

3. Skopiuj plik DLL zawierający zawartość Direct3D9 do folderu bin/debug.

4. Naciśnij klawisz F5, aby uruchomić projekt.

    Zawartość Direct3D9 pojawia się w aplikacji WPF.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Interop.D3DImage>
- [Zagadnienia dotyczące współdziałania Direct3D9 i WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
