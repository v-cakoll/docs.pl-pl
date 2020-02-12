---
title: Hostowanie kontrolki Windows Forms w WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: 2ed4e153a2513dc99d22a1538399156c138eb9e5
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123834"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a>Wskazówki: hosting formantu Windows Forms w WPF

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia wiele kontrolek z bogatym zestawem funkcji. Czasami jednak może być konieczne użycie formantów Windows Forms na stronach [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Na przykład możesz mieć znaczną inwestycję w istniejące kontrolki Windows Forms lub mieć kontrolkę Windows Forms, która zapewnia unikalne funkcje.

W tym instruktażu pokazano, jak hostować Windows Forms kontrolę <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> na stronie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przy użyciu kodu.

Aby zapoznać się z pełną listą zadań przedstawionych w tym instruktażu, zobacz [Hostowanie formantu Windows Forms w przykładzie WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF).

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.

## <a name="hosting-the-windows-forms-control"></a>Hostowanie kontrolki Windows Forms

### <a name="to-host-the-maskedtextbox-control"></a>Aby hostować formant formantem MaskedTextBox

1. Utwórz projekt aplikacji WPF o nazwie `HostingWfInWpf`.

2. Dodaj odwołania do następujących zestawów.

    - WindowsFormsIntegration

    - System.Windows.Forms

3. Otwórz MainWindow. XAML w projektancie WPF.

4. Nadaj nazwę elementowi <xref:System.Windows.Controls.Grid> `grid1`.

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. W widoku widok Projekt lub XAML wybierz element <xref:System.Windows.Window>.

6. W okno Właściwości kliknij kartę **zdarzenia** .

7. Kliknij dwukrotnie zdarzenie <xref:System.Windows.FrameworkElement.Loaded>.

8. Wstaw poniższy kod, aby obsłużyć zdarzenie <xref:System.Windows.FrameworkElement.Loaded>.

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. W górnej części pliku Dodaj następującą instrukcję `Imports` lub `using`.

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Projektowanie XAML w programie Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Przewodnik: hosting kontrolki Windows Form w WPF z wykorzystaniem XAML](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [Przewodnik: hosting złożonej kontrolki Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Przewodnik: hosting złożonej kontrolki WPF w Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Kontrolki formularzy Windows Forms i równoważne kontrolki WPF](windows-forms-controls-and-equivalent-wpf-controls.md)
- [Hostowanie kontrolki Windows Forms w przykładzie WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF)
