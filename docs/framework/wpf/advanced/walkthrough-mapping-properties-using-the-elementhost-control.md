---
title: 'Wskazówki: mapowanie właściwości z użyciem formantu ElementHost'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
ms.openlocfilehash: 7d1cf353f7e6c4b87c13598e7e6029960cd0f715
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197817"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a>Wskazówki: mapowanie właściwości z użyciem formantu ElementHost

W tym instruktażu przedstawiono sposób użycia właściwości <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> do mapowania właściwości [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] na odpowiednie właściwości w hostowanym elemencie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

Zadania przedstawione w tym instruktażu obejmują:

- Tworzenie projektu.

- Definiowanie nowego mapowania właściwości.

- Usuwanie domyślnego mapowania właściwości.

- Rozszerzanie domyślnego mapowania właściwości.

Aby uzyskać pełną listę kodów zadań przedstawionych w tym instruktażu, zobacz [Mapowanie właściwości przy użyciu przykładu kontrolki ElementHost](https://go.microsoft.com/fwlink/?LinkID=160018).

Po zakończeniu będzie możliwe mapowanie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] właściwości do odpowiednich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości w hostowanym elemencie.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Visual Studio 2017

## <a name="creating-the-project"></a>Tworzenie projektu

### <a name="to-create-the-project"></a>Aby utworzyć projekt

1. Utwórz projekt **aplikacji Windows Forms** o nazwie `PropertyMappingWithElementHost`.

2. W **Eksplorator rozwiązań**Dodaj odwołania do następujących zestawów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

    - 'Presentationcore

    - Platformie docelowej

    - 'Windowsbase

    - WindowsFormsIntegration

3. Skopiuj poniższy kod do góry pliku kodu `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#10](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]

4. Otwórz `Form1` w Projektant formularzy systemu Windows. Kliknij dwukrotnie formularz, aby dodać program obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.Form.Load>.

5. Wróć do Projektant formularzy systemu Windows i Dodaj procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.Control.Resize> formularza. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie obsługi zdarzeń przy użyciu projektanta](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).

6. Zadeklaruj pole <xref:System.Windows.Forms.Integration.ElementHost> w klasie `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#16](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]

## <a name="defining-new-property-mappings"></a>Definiowanie nowych mapowań właściwości

Formant <xref:System.Windows.Forms.Integration.ElementHost> zawiera kilka domyślnych mapowań właściwości. Aby dodać nowe mapowanie właściwości, należy wywołać metodę <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> na <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>kontrolce <xref:System.Windows.Forms.Integration.ElementHost>.

### <a name="to-define-new-property-mappings"></a>Aby zdefiniować nowe mapowania właściwości

1. Skopiuj następujący kod do definicji klasy `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]

     Metoda `AddMarginMapping` dodaje nowe mapowanie dla właściwości <xref:System.Windows.Forms.Control.Margin%2A>.

     Metoda `OnMarginChange` przekształca Właściwość <xref:System.Windows.Forms.Control.Margin%2A> na Właściwość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A>.

2. Skopiuj następujący kod do definicji klasy `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]

     Metoda `AddRegionMapping` dodaje nowe mapowanie dla właściwości <xref:System.Windows.Forms.Control.Region%2A>.

     Metoda `OnRegionChange` przekształca Właściwość <xref:System.Windows.Forms.Control.Region%2A> na Właściwość [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A>.

     Metoda `Form1_Resize` obsługuje zdarzenie <xref:System.Windows.Forms.Control.Resize> formularza i rozmiary obszaru przycinania w celu dopasowania go do hostowanego elementu.

## <a name="removing-a-default-property-mapping"></a>Usuwanie domyślnego mapowania właściwości

Usuń domyślne mapowanie właściwości, wywołując metodę <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> na <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>kontroli <xref:System.Windows.Forms.Integration.ElementHost>.

### <a name="to-remove-a-default-property-mapping"></a>Aby usunąć domyślne mapowanie właściwości

- Skopiuj następujący kod do definicji klasy `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]

     Metoda `RemoveCursorMapping` usuwa mapowanie domyślne dla właściwości <xref:System.Windows.Forms.Control.Cursor%2A>.

## <a name="extending-a-default-property-mapping"></a>Rozszerzanie domyślnego mapowania właściwości

Można użyć domyślnego mapowania właściwości, a także poszerzyć go przy użyciu własnego mapowania.

### <a name="to-extend-a-default-property-mapping"></a>Aby zwiększyć domyślne mapowanie właściwości

- Skopiuj następujący kod do definicji klasy `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]

     Metoda `ExtendBackColorMapping` dodaje translator właściwości niestandardowych do istniejącego mapowania właściwości <xref:System.Windows.Forms.Control.BackColor%2A>.

     Metoda `OnBackColorChange` przypisuje określony obraz do właściwości <xref:System.Windows.Controls.Control.Background%2A> kontrolki hostowanej. Metoda `OnBackColorChange` jest wywoływana po zastosowaniu domyślnego mapowania właściwości.

## <a name="initialize-your-property-mappings"></a>Inicjuj mapowania właściwości

1. Skopiuj następujący kod do definicji klasy `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]

     Metoda `Form1_Load` obsługuje zdarzenie <xref:System.Windows.Forms.Form.Load> i wykonuje następujące inicjalizacje.

    - Tworzy element <xref:System.Windows.Controls.Button> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

    - Wywołuje metody zdefiniowane wcześniej w przewodniku, aby skonfigurować mapowania właściwości.

    - Przypisuje początkowe wartości do mapowanych właściwości.

2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Mapowanie właściwości Windows Forms i WPF](windows-forms-and-wpf-property-mapping.md)
- [Projektowanie XAML w programie Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Przewodnik: hosting złożonej kontrolki WPF w Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
