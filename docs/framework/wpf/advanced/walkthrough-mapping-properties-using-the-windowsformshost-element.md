---
title: 'Wskazówki: mapowanie właściwości z użyciem elementu WindowsFormsHost'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
ms.openlocfilehash: c076937d6431adf1750793d47ece88dc82edf95c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794102"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a>Wskazówki: mapowanie właściwości z użyciem elementu WindowsFormsHost

W tym instruktażu przedstawiono sposób użycia właściwości <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> do mapowania właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do odpowiednich właściwości w hostowanej kontroli Windows Forms.

Zadania przedstawione w tym instruktażu obejmują:

- Tworzenie projektu.

- Definiowanie układu aplikacji.

- Definiowanie nowego mapowania właściwości.

- Usuwanie domyślnego mapowania właściwości.

- Zastępowanie domyślnego mapowania właściwości.

- Rozszerzanie domyślnego mapowania właściwości.

Aby uzyskać pełną listę kodów zadań przedstawionych w tym instruktażu, zobacz [Mapowanie właściwości przy użyciu przykładu elementu WindowsFormsHost](https://go.microsoft.com/fwlink/?LinkID=160019).

Po zakończeniu będzie możliwe mapowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości do odpowiednich właściwości w hostowanej kontrolce Windows Forms.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Visual Studio 2017

## <a name="create-and-set-up-the-project"></a>Tworzenie i Konfigurowanie projektu

1. Utwórz projekt **aplikacji WPF** o nazwie `PropertyMappingWithWfhSample`.

2. W **Eksplorator rozwiązań**Dodaj odwołanie do zestawu WindowsFormsIntegration o nazwie WindowsFormsIntegration. dll.

3. W **Eksplorator rozwiązań**Dodaj odwołania do zestawów System. Drawing i system. Windows. Forms.

## <a name="defining-the-application-layout"></a>Definiowanie układu aplikacji

Aplikacja oparta na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]używa elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> do hostowania kontrolki Windows Forms.

### <a name="to-define-the-application-layout"></a>Aby zdefiniować układ aplikacji

1. Otwórz window1. XAML w projektancie WPF.

2. Zastąp istniejący kod następującym kodem.

     [!code-xaml[PropertyMappingWithWfhSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3. Otwórz Window1.xaml.cs w edytorze kodu.

4. W górnej części pliku Zaimportuj następujące przestrzenie nazw.

     [!code-csharp[PropertyMappingWithWfhSample#20](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a>Definiowanie nowego mapowania właściwości

Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> zawiera kilka domyślnych mapowań właściwości. Dodaj nowe mapowanie właściwości, wywołując metodę <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> w <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.

### <a name="to-define-a-new-property-mapping"></a>Aby zdefiniować nowe mapowanie właściwości

- Skopiuj następujący kod do definicji klasy `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     Metoda `AddClipMapping` dodaje nowe mapowanie dla właściwości <xref:System.Windows.UIElement.Clip%2A>.

     Metoda `OnClipChange` przekształca Właściwość <xref:System.Windows.UIElement.Clip%2A> na Właściwość Windows Forms<xref:System.Windows.Forms.Control.Region%2A>.

     Metoda `Window1_SizeChanged` obsługuje zdarzenie <xref:System.Windows.FrameworkElement.SizeChanged> okna i rozmiary obszaru przycinania w celu dopasowania go do okna aplikacji.

## <a name="removing-a-default-property-mapping"></a>Usuwanie domyślnego mapowania właściwości

Usuń domyślne mapowanie właściwości, wywołując metodę <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> w <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.

### <a name="to-remove-a-default-property-mapping"></a>Aby usunąć domyślne mapowanie właściwości

- Skopiuj następujący kod do definicji klasy `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     Metoda `RemoveCursorMapping` usuwa mapowanie domyślne dla właściwości <xref:System.Windows.FrameworkElement.Cursor%2A>.

## <a name="replacing-a-default-property-mapping"></a>Zastępowanie domyślnego mapowania właściwości

Zastąp domyślne mapowanie właściwości, usuwając mapowanie domyślne i wywołując metodę <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> w <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.

### <a name="to-replace-a-default-property-mapping"></a>Aby zastąpić domyślne mapowanie właściwości

- Skopiuj następujący kod do definicji klasy `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     Metoda `ReplaceFlowDirectionMapping` zastępuje domyślne mapowanie dla właściwości <xref:System.Windows.FrameworkElement.FlowDirection%2A>.

     Metoda `OnFlowDirectionChange` przekształca Właściwość <xref:System.Windows.FrameworkElement.FlowDirection%2A> na Właściwość Windows Forms<xref:System.Windows.Forms.Control.RightToLeft%2A>.

     Metoda `cb_CheckedChanged` obsługuje zdarzenie <xref:System.Windows.Forms.CheckBox.CheckedChanged> w kontrolce <xref:System.Windows.Forms.CheckBox>. Przypisuje Właściwość <xref:System.Windows.FrameworkElement.FlowDirection%2A> na podstawie wartości właściwości <xref:System.Windows.Forms.CheckBox.CheckState%2A>

## <a name="extending-a-default-property-mapping"></a>Rozszerzanie domyślnego mapowania właściwości

Można użyć domyślnego mapowania właściwości, a także poszerzyć go przy użyciu własnego mapowania.

### <a name="to-extend-a-default-property-mapping"></a>Aby zwiększyć domyślne mapowanie właściwości

- Skopiuj następujący kod do definicji klasy `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     Metoda `ExtendBackgroundMapping` dodaje translator właściwości niestandardowych do istniejącego mapowania właściwości <xref:System.Windows.Controls.Control.Background%2A>.

     Metoda `OnBackgroundChange` przypisuje określony obraz do właściwości <xref:System.Windows.Forms.Control.BackgroundImage%2A> kontrolki hostowanej. Metoda `OnBackgroundChange` jest wywoływana po zastosowaniu domyślnego mapowania właściwości.

## <a name="initializing-your-property-mappings"></a>Inicjowanie mapowań właściwości

Skonfiguruj mapowania właściwości, wywołując poprzednio opisane metody w obsłudze zdarzeń <xref:System.Windows.FrameworkElement.Loaded>.

### <a name="to-initialize-your-property-mappings"></a>Aby zainicjować mapowania właściwości

1. Skopiuj następujący kod do definicji klasy `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     Metoda `WindowLoaded` obsługuje zdarzenie <xref:System.Windows.FrameworkElement.Loaded> i wykonuje następujące inicjalizacje.

    - Tworzy kontrolkę<xref:System.Windows.Forms.CheckBox> Windows Forms.

    - Wywołuje metody zdefiniowane wcześniej w przewodniku, aby skonfigurować mapowania właściwości.

    - Przypisuje początkowe wartości do mapowanych właściwości.

2. Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację. Kliknij pole wyboru, aby zobaczyć efekt mapowania <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Po kliknięciu pola wyboru układ zmieni orientację w lewo i w prawo.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Mapowanie właściwości Windows Forms i WPF](windows-forms-and-wpf-property-mapping.md)
- [Projektowanie XAML w programie Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Przewodnik: hosting kontrolki Windows Forms w WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
