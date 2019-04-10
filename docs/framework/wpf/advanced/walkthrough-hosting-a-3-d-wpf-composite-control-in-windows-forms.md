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
ms.openlocfilehash: e5b98a33f29759a81ba1cbc1fefbd45c0e5bf736
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330171"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a>Przewodnik: hostowanie kontrolki złożonej 3-D WPF w Windows Forms

W tym instruktażu przedstawiono sposób tworzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] złożonego sterowania, a następnie Hostuj go w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów i formularzy przy użyciu <xref:System.Windows.Forms.Integration.ElementHost> kontroli.

W tym przewodniku zostaną zaimplementowane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> zawiera dwie kontrolki podrzędne. <xref:System.Windows.Controls.UserControl> Wyświetla trójwymiarowej stożek (3-). Renderowanie 3-D obiektów jest o wiele łatwiejsze za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] niż przy użyciu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. W związku z tym, dobrym pomysłem hosta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> klasy w celu utworzenia grafiki 3-w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

Zadania zilustrowane w tym przewodniku obejmują:

-   Tworzenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.

-   Tworząc projekt hosta Windows Forms.

-   Hosting [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

-   Visual Studio 2017

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a>Utworzyć elementu UserControl

1. Tworzenie **Biblioteka kontrolek użytkownika WPF** projektu o nazwie `HostingWpfUserControlInWf`.

2. Otwórz UserControl1.xaml w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

3. Zastąp wygenerowany kod następującym kodem:

     [!code-xaml[HostingWpfUserControlInWf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     Ten kod definiuje <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> zawiera dwie kontrolki podrzędne. Pierwszy formant podrzędny jest <xref:System.Windows.Controls.Label?displayProperty=nameWithType> formantu; druga jest <xref:System.Windows.Controls.Viewport3D> kontrolkę wyświetlającą stożek 3-D.

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a>Utwórz projekt hosta

1. Dodaj **aplikacja WPF (.NET Framework)** projektu o nazwie `WpfUserControlHost` do rozwiązania. Aby uzyskać więcej informacji, zobacz [instruktażu: Mój pierwszy aplikacji klasycznej WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).

2. W **Eksploratora rozwiązań**, Dodaj odwołanie do zestawu WindowsFormsIntegration, która nosi nazwę WindowsFormsIntegration.dll.

3. Dodaj odwołania do następujących [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestawów:

    -   PresentationCore

    -   PresentationFramework

    -   WindowsBase

4. Dodaj odwołanie do `HostingWpfUserControlInWf` projektu.

5. W Eksploratorze rozwiązań ustaw `WpfUserControlHost` projekt jako projekt startowy.

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a>Host UserControl

1. Windows Forms Designer Otwórz formularz Form1.

2. W oknie dialogowym właściwości kliknij **zdarzenia**, a następnie kliknij dwukrotnie <xref:System.Windows.Forms.Form.Load> zdarzenie, aby utworzyć program obsługi zdarzeń.

     Zostanie otwarty Edytor kodu, aby nowo wygenerowane `Form1_Load` programu obsługi zdarzeń.

3. Zastąp kod w Form1.cs z następującym kodem.

     `Form1_Load` Programu obsługi zdarzeń tworzy wystąpienie `UserControl1` i dodaje itto <xref:System.Windows.Forms.Integration.ElementHost> kontrolki zbiór kontrolek podrzędnych. <xref:System.Windows.Forms.Integration.ElementHost> Formant jest dodawany do kolekcji formularza formantów podrzędnych.

     [!code-csharp[HostingWpfUserControlInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4. Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Przewodnik: hostowanie kontrolki złożonej WPF w Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Przewodnik: hostowanie kontrolki złożonej Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Hosting złożonego formantu WPF w Windows Forms próbki](https://go.microsoft.com/fwlink/?LinkID=160001)