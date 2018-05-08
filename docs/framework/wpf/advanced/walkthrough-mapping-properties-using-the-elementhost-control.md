---
title: 'Wskazówki: mapowanie właściwości z użyciem formantu ElementHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
ms.openlocfilehash: b5af1f45a0d01761358e83c890544ec1a11836e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a>Wskazówki: mapowanie właściwości z użyciem formantu ElementHost
Ten przewodnik przedstawia sposób użycia <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> właściwości do mapowania [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] właściwości do odpowiedniej właściwości hostowany [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementu.  
  
 Zadania przedstawione w tym przewodniku obejmują:  
  
-   Tworzenie projektu.  
  
-   Definiowanie nowego mapowania właściwości.  
  
-   Usuwanie mapowania właściwości domyślnej.  
  
-   Rozszerzanie domyślne mapowanie właściwości.  
  
 Kompletny kod lista zadań przedstawione w tym przewodniku, zobacz [mapowania właściwości przy użyciu przykładowych formantu ElementHost](http://go.microsoft.com/fwlink/?LinkID=160018).  
  
 Gdy skończysz, będzie można mapować [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] właściwości do odpowiadającego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości w elemencie hostowanej.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Utwórz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] projekt aplikacji o nazwie `PropertyMappingWithElementHost`. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  W Eksploratorze rozwiązań, dodaj odwołania do następujących [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zestawów.  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   WindowsFormsIntegration  
  
3.  Skopiuj następujący kod w górnej części `Form1` pliku kodu.  
  
     [!code-csharp[PropertyMappingWithElementHost#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]  
  
4.  Otwórz `Form1` w narzędziu Projektant dla formularzy systemu Windows. Kliknij dwukrotnie formularza, aby dodać obsługę zdarzeń dla <xref:System.Windows.Forms.Form.Load> zdarzeń.  
  
5.  Powrót do projektanta formularzy systemu Windows i Dodaj program obsługi zdarzeń w formularzu <xref:System.Windows.Forms.Control.Resize> zdarzeń. Aby uzyskać więcej informacji, zobacz [porady: tworzenie zdarzeń obsługi przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).  
  
6.  Deklarowanie <xref:System.Windows.Forms.Integration.ElementHost> w `Form1` klasy.  
  
     [!code-csharp[PropertyMappingWithElementHost#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]  
  
## <a name="defining-new-property-mappings"></a>Definiowanie nowych mapowań właściwości  
 <xref:System.Windows.Forms.Integration.ElementHost> Kontrola zapewnia kilka domyślnego mapowania właściwości. Dodaj nowe mapowanie właściwości przez wywołanie metody <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metoda <xref:System.Windows.Forms.Integration.ElementHost> formantu <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.  
  
#### <a name="to-define-new-property-mappings"></a>Aby zdefiniować nowe mapowanie właściwości  
  
1.  Skopiuj następujący kod do definicji `Form1` klasy.  
  
     [!code-csharp[PropertyMappingWithElementHost#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]  
  
     `AddMarginMapping` Metoda dodaje nowe mapowanie dla <xref:System.Windows.Forms.Control.Margin%2A> właściwości.  
  
     `OnMarginChange` Tłumaczy — metoda <xref:System.Windows.Forms.Control.Margin%2A> właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> właściwości.  
  
2.  Skopiuj następujący kod do definicji `Form1` klasy.  
  
     [!code-csharp[PropertyMappingWithElementHost#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]  
  
     `AddRegionMapping` Metoda dodaje nowe mapowanie dla <xref:System.Windows.Forms.Control.Region%2A> właściwości.  
  
     `OnRegionChange` Tłumaczy — metoda <xref:System.Windows.Forms.Control.Region%2A> właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> właściwości.  
  
     `Form1_Resize` Metoda obsługuje formularza <xref:System.Windows.Forms.Control.Resize> zdarzeń i rozmiar obszaru przycinania w celu dopasowania elementu hostowanej.  
  
## <a name="removing-a-default-property-mapping"></a>Usuwanie mapowania właściwości domyślne  
 Usuń domyślne mapowanie właściwości przez wywołanie metody <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> metoda <xref:System.Windows.Forms.Integration.ElementHost> formantu <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.  
  
#### <a name="to-remove-a-default-property-mapping"></a>Aby usunąć domyślne mapowanie właściwości  
  
-   Skopiuj następujący kod do definicji `Form1` klasy.  
  
     [!code-csharp[PropertyMappingWithElementHost#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]  
  
     `RemoveCursorMapping` Metoda usuwa domyślnego mapowania dla <xref:System.Windows.Forms.Control.Cursor%2A> właściwości.  
  
## <a name="extending-a-default-property-mapping"></a>Rozszerzanie domyślne mapowanie właściwości  
 Można użyć domyślnego mapowania właściwości i rozszerzać go z własnych mapowania.  
  
#### <a name="to-extend-a-default-property-mapping"></a>Aby rozszerzyć domyślne mapowanie właściwości  
  
-   Skopiuj następujący kod do definicji `Form1` klasy.  
  
     [!code-csharp[PropertyMappingWithElementHost#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]  
  
     `ExtendBackColorMapping` Metoda dodaje translatora właściwości niestandardowych do istniejącej <xref:System.Windows.Forms.Control.BackColor%2A> mapowania właściwości.  
  
     `OnBackColorChange` — Metoda przypisuje określony obraz sterowania hostowanej <xref:System.Windows.Controls.Control.Background%2A> właściwości. `OnBackColorChange` Metoda jest wywoływana po zastosowaniu domyślne mapowanie właściwości.  
  
## <a name="initializing-your-property-mappings"></a>Inicjowanie mapowań właściwości  
  
#### <a name="to-initialize-your-property-mappings"></a>Aby zainicjować mapowań właściwości  
  
1.  Skopiuj następujący kod do definicji `Form1` klasy.  
  
     [!code-csharp[PropertyMappingWithElementHost#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]  
  
     `Form1_Load` Dojścia metody <xref:System.Windows.Forms.Form.Load> zdarzeń i wykonuje następujące inicjowania.  
  
    -   Tworzy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> elementu.  
  
    -   Wywołuje metody zdefiniowanych we wcześniejszej części przewodnika, aby skonfigurować mapowań właściwości.  
  
    -   Przypisuje wartości początkowej do mapowanej właściwości.  
  
2.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Mapowanie właściwości Windows Forms i WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [Projektant WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Przewodnik: hosting złożonej kontrolki WPF w Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
