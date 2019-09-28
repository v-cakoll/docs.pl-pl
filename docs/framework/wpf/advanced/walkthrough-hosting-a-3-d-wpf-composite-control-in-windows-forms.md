---
title: 'Przewodnik: hostowanie kontrolki złożonej 3-D WPF w Windows Forms'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: a35f2b4062edb18914c55046a69dcd9b8825d778
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353844"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a>Przewodnik: hostowanie kontrolki złożonej 3-D WPF w Windows Forms

W tym instruktażu pokazano, jak utworzyć formant złożony [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i hostować go w kontrolkach i formularzach [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] przy użyciu kontrolki <xref:System.Windows.Forms.Integration.ElementHost>.

W tym instruktażu zostanie zaimplementowana [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>, która zawiera dwie kontrolki podrzędne. @No__t-0 wyświetla stożek trójwymiarowy (3-D). Renderowanie obiektów 3-D jest znacznie łatwiejsze dzięki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] niż [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. W związku z tym warto hostować klasę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> w celu utworzenia grafiki trójwymiarowej w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

Zadania przedstawione w tym instruktażu obejmują:

- Tworzenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.

- Tworzenie projektu hosta Windows Forms.

- Hostowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Visual Studio 2017

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a>Tworzenie obiektu UserControl

1. Utwórz projekt **biblioteki formantów użytkownika WPF** o nazwie `HostingWpfUserControlInWf`.

2. Otwórz UserControl1. XAML w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

3. Zastąp wygenerowany kod następującym kodem:

     [!code-xaml[HostingWpfUserControlInWf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     Ten kod definiuje <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>, która zawiera dwie kontrolki podrzędne. Pierwszy formant podrzędny jest kontrolką <xref:System.Windows.Controls.Label?displayProperty=nameWithType>; drugim jest formant <xref:System.Windows.Controls.Viewport3D>, który wyświetla stożkowy 3-D.

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

     Obsługa zdarzeń `Form1_Load` tworzy wystąpienie `UserControl1` i dodaje je kontrolki podrzędnej formantu <xref:System.Windows.Forms.Integration.ElementHost>. Kontrolka <xref:System.Windows.Forms.Integration.ElementHost> jest dodawana do kolekcji formantów podrzędnych formularza.

     [!code-csharp[HostingWpfUserControlInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4. Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Przewodnik: Hostowanie złożonego formantu WPF w Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Przewodnik: Hostowanie złożonego formantu Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Hostowanie złożonego formantu WPF w Windows Forms przykładzie](https://go.microsoft.com/fwlink/?LinkID=160001)
