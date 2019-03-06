---
title: 'Przewodnik: Hosting zawartości Direct3D9 w WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: e588118e995694ea899b73d238e00f63e92feea4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352051"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a>Przewodnik: Hosting zawartości Direct3D9 w WPF
Ten poradnik pokazuje jak do hostowania zawartości Direct3D9 w aplikacji Windows Presentation Foundation (WPF).  
  
 W tym przewodniku należy wykonać następujące zadania:  
  
-   Utwórz projekt WPF do hostowania zawartości Direct3D9.  
  
-   Importowanie zawartości Direct3D9.  
  
-   Wyświetlanie zawartości Direct3D9 przy użyciu <xref:System.Windows.Interop.D3DImage> klasy.  
  
 Po zakończeniu będzie wiadomo, jak hostować zawartości Direct3D9 w aplikacji WPF.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Program Visual Studio.  
  
-   DirectX SDK 9 lub nowszy.  
  
-   Biblioteka DLL, która zawiera zawartości Direct3D9 w formacie zgodnym z WPF. Aby uzyskać więcej informacji, zobacz [WPF i Direct3D9 — współdziałanie](wpf-and-direct3d9-interoperation.md) i [instruktażu: Tworzenie zawartości Direct3D9 dla hostingu w WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
## <a name="creating-the-wpf-project"></a>Tworzenie projektu WPF  
 Pierwszym krokiem jest utworzenie projektu dla aplikacji WPF.  
  
#### <a name="to-create-the-wpf-project"></a>Aby utworzyć projekt WPF  
  
-   Utwórz nowy projekt aplikacji WPF w języku Visual C# o nazwie `D3DHost`. Aby uzyskać więcej informacji, zobacz [instruktażu: Mój pierwszy aplikacji klasycznej WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
     Otworzy się w pliku MainWindow.xaml [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
## <a name="importing-the-direct3d9-content"></a>Importowanie zawartości Direct3D9  
 Importowanie zawartości Direct3D9 z niezarządzaną biblioteką DLL, przy użyciu `DllImport` atrybutu.  
  
#### <a name="to-import-direct3d9-content"></a>Aby zaimportować zawartości Direct3D9  
  
1.  Otwórz plik MainWindow.xaml.cs w edytorze kodu.  
  
2.  Zastąp automatycznie wygenerowany kod następującym kodem.  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a>Hosting zawartości Direct3D9  
 Na koniec użyj <xref:System.Windows.Interop.D3DImage> klasy do obsługi zawartości Direct3D9.  
  
#### <a name="to-host-the-direct3d9-content"></a>Do hostowania zawartości Direct3D9  
  
1.  W pliku MainWindow.xaml Zastąp automatycznie wygenerowany XAML następujące XAML.  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  Skompiluj projekt.  
  
3.  Kopiowanie pliku DLL, która zawiera zawartości Direct3D9 do folderu bin/Debug.  
  
4.  Naciśnij klawisz F5, aby uruchomić projekt.  
  
     Zawartości Direct3D9 pojawia się w obrębie aplikacji WPF.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Interop.D3DImage>
- [Zagadnienia dotyczące współdziałania Direct3D9 i WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
