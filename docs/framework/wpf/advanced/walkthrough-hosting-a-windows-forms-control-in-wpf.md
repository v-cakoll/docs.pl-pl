---
title: Hostowanie kontrolki Windows Forms w WPF
description: Dowiedz się, jak hostować Windows Forms formantów w Windows Presentation Foundation, które już udostępniają wiele kontrolek z bogatym zestawem funkcji.
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: ec67cf9fabaa5b7aadbb2a3c21ebf8dd828ee20f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164977"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a>Przewodnik: hostowanie kontrolki Windows Forms w WPF

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]oferuje wiele kontrolek z bogatym zestawem funkcji. Czasami jednak może być konieczne użycie formantów Windows Forms na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stronach. Na przykład możesz mieć znaczną inwestycję w istniejące kontrolki Windows Forms lub mieć kontrolkę Windows Forms, która zapewnia unikalne funkcje.

W tym instruktażu pokazano, jak hostować <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> formant Windows Forms na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stronie przy użyciu kodu.

Aby zapoznać się z pełną listą zadań przedstawionych w tym instruktażu, zobacz [Hostowanie formantu Windows Forms w przykładzie WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF).

## <a name="prerequisites"></a>Wymagania wstępne

Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.

## <a name="hosting-the-windows-forms-control"></a>Hostowanie kontrolki Windows Forms

### <a name="to-host-the-maskedtextbox-control"></a>Aby hostować formant formantem MaskedTextBox

1. Utwórz projekt aplikacji WPF o nazwie `HostingWfInWpf` .

2. Dodaj odwołania do następujących zestawów.

    - WindowsFormsIntegration

    - System. Windows. Forms

3. Otwórz MainWindow. XAML w projektancie WPF.

4. Nadaj nazwę <xref:System.Windows.Controls.Grid> element `grid1` .

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. W widoku widok Projekt lub XAML wybierz <xref:System.Windows.Window> element.

6. W okno Właściwości kliknij kartę **zdarzenia** .

7. Kliknij dwukrotnie <xref:System.Windows.FrameworkElement.Loaded> zdarzenie.

8. Wstaw następujący kod, aby obsłużyć <xref:System.Windows.FrameworkElement.Loaded> zdarzenie.

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. W górnej części pliku Dodaj następującą `Imports` `using` instrukcję lub.

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. Naciśnij klawisz **F5**, aby skompilować i uruchomić aplikację.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Projektowanie XAML w programie Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Przewodnik: hostowanie kontrolki Windows Forms w WPF z wykorzystaniem języka XAML](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [Przewodnik: hostowanie kontrolki złożonej Windows Forms w WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Przewodnik: hostowanie kontrolki złożonej WPF w Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Kontrolki Windows Forms i ekwiwalentne kontrolki WPF](windows-forms-controls-and-equivalent-wpf-controls.md)
- [Hostowanie kontrolki Windows Forms w przykładzie WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF)
