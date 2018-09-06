---
title: 'Wskazówki: hosing zawartości Direct3D9 w WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: 5e7edfbeb9a3cddcdcd81d9c87e5e85bfc947339
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785017"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a>Wskazówki: hosing zawartości Direct3D9 w WPF
Ten poradnik pokazuje jak do hostowania zawartości Direct3D9 w aplikacji Windows Presentation Foundation (WPF).  
  
 W tym przewodniku należy wykonać następujące zadania:  
  
-   Utwórz projekt WPF do hostowania zawartości Direct3D9.  
  
-   Importowanie zawartości Direct3D9.  
  
-   Wyświetlanie zawartości Direct3D9 przy użyciu <xref:System.Windows.Interop.D3DImage> klasy.  
  
 Po zakończeniu będzie wiadomo, jak hostować zawartości Direct3D9 w aplikacji WPF.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   DirectX SDK 9 lub nowszy.  
  
-   Biblioteka DLL, która zawiera zawartości Direct3D9 w formacie zgodnym z WPF. Aby uzyskać więcej informacji, zobacz [WPF i Direct3D9 — współdziałanie](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) i [wskazówki: tworzenie zawartości Direct3D9 dla hostingu w WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
## <a name="creating-the-wpf-project"></a>Tworzenie projektu WPF  
 Pierwszym krokiem jest utworzenie projektu dla aplikacji WPF.  
  
#### <a name="to-create-the-wpf-project"></a>Aby utworzyć projekt WPF  
  
-   Utwórz nowy projekt aplikacji WPF w języku Visual C# o nazwie `D3DHost`. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie nowego projektu aplikacji WPF](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
     Otworzy się w pliku MainWindow.xaml [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
## <a name="importing-the-direct3d9-content"></a>Importowanie zawartości Direct3D9  
 Importowanie zawartości Direct3D9 z niezarządzaną biblioteką DLL, przy użyciu `DllImport` atrybutu.  
  
#### <a name="to-import-direct3d9-content"></a>Aby zaimportować zawartości Direct3D9  
  
1.  Otwórz plik MainWindow.xaml.cs w edytorze kodu.  
  
2.  Zastąp automatycznie wygenerowany kod następującym kodem.  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a>Hosting zawartości Direct3D9  
 Na koniec użyj <xref:System.Windows.Interop.D3DImage> klasy do obsługi zawartości Direct3D9.  
  
#### <a name="to-host-the-direct3d9-content"></a>Do hostowania zawartości Direct3D9  
  
1.  W pliku MainWindow.xaml Zastąp automatycznie wygenerowany XAML następujące XAML.  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  Skompiluj projekt.  
  
3.  Kopiowanie pliku DLL, która zawiera zawartości Direct3D9 do folderu bin/Debug.  
  
4.  Naciśnij klawisz F5, aby uruchomić projekt.  
  
     Zawartości Direct3D9 pojawia się w obrębie aplikacji WPF.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Interop.D3DImage>  
 [Zagadnienia dotyczące współdziałania Direct3D9 i WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
