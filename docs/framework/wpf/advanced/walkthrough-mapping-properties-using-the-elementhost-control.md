---
title: 'Przewodnik: mapowanie właściwości przy użyciu kontrolki ElementHost'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
ms.openlocfilehash: 360f19e558f97e1807b329ad18e429fa893bbf86
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300921"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a>Przewodnik: mapowanie właściwości przy użyciu kontrolki ElementHost

W tym instruktażu dowiesz się, jak używać <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> właściwości, aby zamapować [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] właściwości do odpowiedniej właściwości hostowany [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementu.

Zadania zilustrowane w tym przewodniku obejmują:

-   Tworzenie projektu.

-   Definiowanie nowego mapowania właściwości.

-   Usuwanie mapowania właściwości domyślnej.

-   Rozszerzanie domyślnego mapowania właściwości.

Lista zadań przedstawione w niniejszym przewodniku kompletny kod znajduje się [Mapowanie właściwości przy użyciu przykładu formantu ElementHost](https://go.microsoft.com/fwlink/?LinkID=160018).

Po zakończeniu będzie można mapować [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] właściwości do odpowiadającego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości hostowanego elementu.

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

-   Visual Studio 2017

## <a name="creating-the-project"></a>Tworzenie projektu

### <a name="to-create-the-project"></a>Aby utworzyć projekt

1. Tworzenie **Windows Forms App** projektu o nazwie `PropertyMappingWithElementHost`.

2. W **Eksploratora rozwiązań**, dodaj odwołania do następujących [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestawów.

    -   PresentationCore

    -   PresentationFramework

    -   WindowsBase

    -   WindowsFormsIntegration

3. Skopiuj poniższy kod w górnej części `Form1` pliku kodu.

     [!code-csharp[PropertyMappingWithElementHost#10](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]

4. Otwórz `Form1` w programie Windows Forms Designer. Kliknij dwukrotnie formularz, aby dodać moduł obsługi zdarzenia <xref:System.Windows.Forms.Form.Load> zdarzeń.

5. Wróć do projektanta Windows Forms i Dodaj program obsługi zdarzeń w formularzu <xref:System.Windows.Forms.Control.Resize> zdarzeń. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie obsługi zdarzeń za pomocą projektanta](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).

6. Zadeklaruj <xref:System.Windows.Forms.Integration.ElementHost> pole `Form1` klasy.

     [!code-csharp[PropertyMappingWithElementHost#16](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]

## <a name="defining-new-property-mappings"></a>Definiowanie nowego mapowania właściwości

<xref:System.Windows.Forms.Integration.ElementHost> Control oferuje kilka domyślnego mapowania właściwości. Dodaj nowe mapowanie właściwości przez wywołanie metody <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metody <xref:System.Windows.Forms.Integration.ElementHost> formantu <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.

### <a name="to-define-new-property-mappings"></a>Aby zdefiniować nowe mapowanie właściwości

1. Skopiuj następujący kod do definicji `Form1` klasy.

     [!code-csharp[PropertyMappingWithElementHost#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]

     `AddMarginMapping` Metoda dodaje nowe mapowanie dla <xref:System.Windows.Forms.Control.Margin%2A> właściwości.

     `OnMarginChange` Tłumaczy metoda <xref:System.Windows.Forms.Control.Margin%2A> właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> właściwości.

2. Skopiuj następujący kod do definicji `Form1` klasy.

     [!code-csharp[PropertyMappingWithElementHost#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]

     `AddRegionMapping` Metoda dodaje nowe mapowanie dla <xref:System.Windows.Forms.Control.Region%2A> właściwości.

     `OnRegionChange` Tłumaczy metoda <xref:System.Windows.Forms.Control.Region%2A> właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> właściwości.

     `Form1_Resize` Obsługiwała formularza <xref:System.Windows.Forms.Control.Resize> zdarzeń i rozmiar obszaru przycinania, aby dopasować element hostowany.

## <a name="removing-a-default-property-mapping"></a>Usuwanie mapowania właściwości domyślne

Usuń mapowanie właściwości domyślne przez wywołanie metody <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> metody <xref:System.Windows.Forms.Integration.ElementHost> formantu <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.

### <a name="to-remove-a-default-property-mapping"></a>Aby usunąć mapowanie właściwości domyślne

-   Skopiuj następujący kod do definicji `Form1` klasy.

     [!code-csharp[PropertyMappingWithElementHost#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]

     `RemoveCursorMapping` Metoda usuwa domyślnego mapowania dla <xref:System.Windows.Forms.Control.Cursor%2A> właściwości.

## <a name="extending-a-default-property-mapping"></a>Rozszerzanie domyślne mapowanie właściwości

Możesz użyć domyślnego mapowania właściwości i rozszerzać go za pomocą własnych mapowania.

### <a name="to-extend-a-default-property-mapping"></a>Aby rozszerzyć domyślne mapowanie właściwości

-   Skopiuj następujący kod do definicji `Form1` klasy.

     [!code-csharp[PropertyMappingWithElementHost#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]

     `ExtendBackColorMapping` Metoda dodaje translator właściwości niestandardowych do istniejących <xref:System.Windows.Forms.Control.BackColor%2A> mapowania właściwości.

     `OnBackColorChange` Metoda przypisuje określonego obrazu do obsługiwanego formantu <xref:System.Windows.Controls.Control.Background%2A> właściwości. `OnBackColorChange` Metoda jest wywoływana po zastosowaniu do domyślnego mapowania właściwości.

## <a name="initialize-your-property-mappings"></a>Inicjowanie mapowań właściwości

1. Skopiuj następujący kod do definicji `Form1` klasy.

     [!code-csharp[PropertyMappingWithElementHost#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]

     `Form1_Load` Metodę uchwytów <xref:System.Windows.Forms.Form.Load> zdarzeń i wykonuje następujące inicjowanie.

    -   Tworzy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> elementu.

    -   Wywołuje metody, które są zdefiniowane we wcześniejszej części przewodnika do skonfigurowania mapowania właściwości.

    -   Przypisuje wartości początkowe, aby mapowanych właściwości.

2. Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Mapowanie właściwości Windows Forms i WPF](windows-forms-and-wpf-property-mapping.md)
- [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Przewodnik: Hosting złożonego formantu WPF w formularzach Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)