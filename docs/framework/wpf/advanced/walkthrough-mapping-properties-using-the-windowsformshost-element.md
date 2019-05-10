---
title: 'Przewodnik: mapowanie właściwości przy użyciu kontrolki WindowsFormsHost'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
ms.openlocfilehash: a7c36e8fc150fe3268120ed728f1bed87d24e800
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623587"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a>Przewodnik: mapowanie właściwości przy użyciu kontrolki WindowsFormsHost

W tym instruktażu dowiesz się, jak używać <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> właściwości, aby zamapować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości do odpowiedniej właściwości hostowany [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli.

Zadania zilustrowane w tym przewodniku obejmują:

- Tworzenie projektu.

- Definiowanie układów aplikacji.

- Definiowanie nowego mapowania właściwości.

- Usuwanie mapowania właściwości domyślnej.

- Zastępowanie domyślnego mapowania właściwości.

- Rozszerzanie domyślnego mapowania właściwości.

Lista zadań przedstawione w niniejszym przewodniku kompletny kod znajduje się [Mapowanie właściwości przy użyciu przykładu elementu WindowsFormsHost](https://go.microsoft.com/fwlink/?LinkID=160019).

Po zakończeniu będzie można mapować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości do odpowiedniej właściwości hostowany [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Visual Studio 2017

## <a name="create-and-set-up-the-project"></a>Tworzenie i konfigurowanie projektu

1. Tworzenie **aplikacja WPF** projektu o nazwie `PropertyMappingWithWfhSample`.

2. W **Eksploratora rozwiązań**, Dodaj odwołanie do zestawu WindowsFormsIntegration, która nosi nazwę WindowsFormsIntegration.dll.

3. W **Eksploratora rozwiązań**, dodaj odwołania do zestawów System.Drawing i pozycję System.Windows.Forms.

## <a name="defining-the-application-layout"></a>Definiowanie układu aplikacji

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— Na podstawie aplikacja używa <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu hosta [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli.

### <a name="to-define-the-application-layout"></a>Aby zdefiniować układ aplikacji

1. Otwórz Window1.xaml w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

2. Zastąp istniejący kod następującym kodem.

     [!code-xaml[PropertyMappingWithWfhSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3. Otwórz Window1.xaml.cs w edytorze kodu.

4. W górnej części pliku zaimportuj następujące przestrzenie nazw.

     [!code-csharp[PropertyMappingWithWfhSample#20](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a>Definiowanie nowe mapowanie właściwości

<xref:System.Windows.Forms.Integration.WindowsFormsHost> Elementu udostępnia kilka domyślne mapowania właściwości. Dodaj nowe mapowanie właściwości przez wywołanie metody <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metody <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.

### <a name="to-define-a-new-property-mapping"></a>Aby zdefiniować nowe mapowanie właściwości

- Skopiuj następujący kod do definicji `Window1` klasy.

     [!code-csharp[PropertyMappingWithWfhSample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     `AddClipMapping` Metoda dodaje nowe mapowanie dla <xref:System.Windows.UIElement.Clip%2A> właściwości.

     `OnClipChange` Tłumaczy metoda <xref:System.Windows.UIElement.Clip%2A> właściwości [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.Region%2A> właściwości.

     `Window1_SizeChanged` Obsługiwała okna <xref:System.Windows.FrameworkElement.SizeChanged> zdarzeń i rozmiar obszaru przycinania do rozmiaru okna aplikacji.

## <a name="removing-a-default-property-mapping"></a>Usuwanie mapowania właściwości domyślne

Usuń mapowanie właściwości domyślne przez wywołanie metody <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> metody <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.

### <a name="to-remove-a-default-property-mapping"></a>Aby usunąć mapowanie właściwości domyślne

- Skopiuj następujący kod do definicji `Window1` klasy.

     [!code-csharp[PropertyMappingWithWfhSample#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     `RemoveCursorMapping` Metoda usuwa domyślnego mapowania dla <xref:System.Windows.FrameworkElement.Cursor%2A> właściwości.

## <a name="replacing-a-default-property-mapping"></a>Zastępowanie domyślnego mapowania właściwości

Zastąp domyślne mapowanie właściwości przez usunięcie domyślnego mapowania i wywoływania <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metody <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.

### <a name="to-replace-a-default-property-mapping"></a>Aby zastąpić domyślne mapowanie właściwości

- Skopiuj następujący kod do definicji `Window1` klasy.

     [!code-csharp[PropertyMappingWithWfhSample#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     `ReplaceFlowDirectionMapping` Metoda zastępuje domyślne mapowanie dla <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwości.

     `OnFlowDirectionChange` Tłumaczy metoda <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwości [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.RightToLeft%2A> właściwości.

     `cb_CheckedChanged` Metodę uchwytów <xref:System.Windows.Forms.CheckBox.CheckedChanged> zdarzenie na <xref:System.Windows.Forms.CheckBox> kontroli. Przypisuje <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwości na podstawie wartości z <xref:System.Windows.Forms.CheckBox.CheckState%2A> właściwości

## <a name="extending-a-default-property-mapping"></a>Rozszerzanie domyślne mapowanie właściwości

Możesz użyć domyślnego mapowania właściwości i rozszerzać go za pomocą własnych mapowania.

### <a name="to-extend-a-default-property-mapping"></a>Aby rozszerzyć domyślne mapowanie właściwości

- Skopiuj następujący kod do definicji `Window1` klasy.

     [!code-csharp[PropertyMappingWithWfhSample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     `ExtendBackgroundMapping` Metoda dodaje translator właściwości niestandardowych do istniejących <xref:System.Windows.Controls.Control.Background%2A> mapowania właściwości.

     `OnBackgroundChange` Metoda przypisuje określonego obrazu do obsługiwanego formantu <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwości. `OnBackgroundChange` Metoda jest wywoływana po zastosowaniu do domyślnego mapowania właściwości.

## <a name="initializing-your-property-mappings"></a>Inicjowanie mapowań właściwości

Konfigurowanie mapowań właściwości przez wywołanie metody opisany wcześniej w <xref:System.Windows.FrameworkElement.Loaded> programu obsługi zdarzeń.

### <a name="to-initialize-your-property-mappings"></a>Aby zainicjować mapowań właściwości

1. Skopiuj następujący kod do definicji `Window1` klasy.

     [!code-csharp[PropertyMappingWithWfhSample#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     `WindowLoaded` Metodę uchwytów <xref:System.Windows.FrameworkElement.Loaded> zdarzeń i wykonuje następujące inicjowanie.

    - Tworzy [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.CheckBox> kontroli.

    - Wywołuje metody, które są zdefiniowane we wcześniejszej części przewodnika do skonfigurowania mapowania właściwości.

    - Przypisuje wartości początkowe, aby mapowanych właściwości.

2. Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację. Kliknij pole wyboru, aby zobaczyć efekt <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapowania. Po kliknięciu pola wyboru, układ odwraca orientacji lewa prawa.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Mapowanie właściwości Windows Forms i WPF](windows-forms-and-wpf-property-mapping.md)
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Przewodnik: Hosting kontrolki Windows Forms w WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)