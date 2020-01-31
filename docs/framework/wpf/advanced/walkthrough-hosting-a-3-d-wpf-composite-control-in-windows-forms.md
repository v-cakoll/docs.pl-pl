---
title: Kontrolka złożona dla hosta 3W WPF w Windows Forms
titleSuffix: ''
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: aaa726ac90fd75a12054c18be6ec08a1372c1128
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794207"
---
# <a name="walkthrough-host-a-3d-wpf-composite-control-in-windows-forms"></a>Przewodnik: hostowanie złożonego formantu 3D WPF w Windows Forms

W tym instruktażu pokazano, jak można utworzyć formant złożony [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i hostować go w Windows Forms kontrolkach i formularzach za pomocą kontrolki <xref:System.Windows.Forms.Integration.ElementHost>.

W tym instruktażu zaimplementowano <xref:System.Windows.Controls.UserControl> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], który zawiera dwie kontrolki podrzędne. <xref:System.Windows.Controls.UserControl> wyświetla stożkowy wymiar trójwymiarowy (3W). Renderowanie obiektów 3W jest znacznie łatwiejsze dzięki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] niż z Windows Forms. W związku z tym warto hostować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasę <xref:System.Windows.Controls.UserControl> w celu utworzenia grafiki 3D w Windows Forms.

Zadania przedstawione w tym instruktażu obejmują:

- Tworzenie <xref:System.Windows.Controls.UserControl>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

- Tworzenie projektu hosta Windows Forms.

- Hostowanie <xref:System.Windows.Controls.UserControl>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Visual Studio 2017

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a>Tworzenie obiektu UserControl

1. Utwórz projekt **biblioteki formantów użytkownika WPF** o nazwie `HostingWpfUserControlInWf`.

2. Otwórz UserControl1. XAML w projektancie WPF.

3. Zastąp wygenerowany kod następującym kodem:

     [!code-xaml[HostingWpfUserControlInWf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     Ten kod definiuje <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>, który zawiera dwa kontrolki podrzędne. Pierwszy formant podrzędny jest formantem <xref:System.Windows.Controls.Label?displayProperty=nameWithType>; drugim jest formant <xref:System.Windows.Controls.Viewport3D>, który wyświetla stożkowy 3W.

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a>Utwórz projekt hosta

1. Dodaj projekt **aplikacji Windows Forms (.NET Framework)** o nazwie `WpfUserControlHost` do rozwiązania.

2. W **Eksplorator rozwiązań**Dodaj odwołanie do zestawu WindowsFormsIntegration o nazwie WindowsFormsIntegration. dll.

3. Dodaj odwołania do następujących zestawów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:

    - 'Presentationcore

    - Platformie docelowej

    - WindowsBase

4. Dodaj odwołanie do projektu `HostingWpfUserControlInWf`.

5. W Eksplorator rozwiązań Ustaw projekt `WpfUserControlHost` jako projekt startowy.

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a>Hostowanie elementu UserControl

1. W Projektant formularzy systemu Windows otwórz formularz Form1.

2. W okno Właściwości kliknij pozycję **zdarzenia**, a następnie kliknij dwukrotnie zdarzenie <xref:System.Windows.Forms.Form.Load>, aby utworzyć procedurę obsługi zdarzeń.

     Zostanie otwarty Edytor kodu dla nowo wygenerowanego programu obsługi zdarzeń `Form1_Load`.

3. Zastąp kod w Form1.cs następującym kodem.

     Program obsługi zdarzeń `Form1_Load` tworzy wystąpienie `UserControl1` i dodaje je kontrolki podrzędnej formantu <xref:System.Windows.Forms.Integration.ElementHost>. Kontrolka <xref:System.Windows.Forms.Integration.ElementHost> jest dodawana do kolekcji formantów podrzędnych formularza.

     [!code-csharp[HostingWpfUserControlInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4. Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Projektowanie XAML w programie Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Przewodnik: hosting złożonej kontrolki WPF w Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Przewodnik: hosting złożonej kontrolki Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Hostowanie złożonego formantu WPF w Windows Forms przykładzie](https://go.microsoft.com/fwlink/?LinkID=160001)
