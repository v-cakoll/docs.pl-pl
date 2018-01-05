---
title: "Wskazówki: mapowanie właściwości z użyciem elementu WindowsFormsHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 612d4a78f2f18824e5859604dc40e66b99e68586
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a>Wskazówki: mapowanie właściwości z użyciem elementu WindowsFormsHost
Ten przewodnik przedstawia sposób użycia <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> właściwości do mapowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości do odpowiedniej właściwości hostowany [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu.  
  
 Zadania przedstawione w tym przewodniku obejmują:  
  
-   Tworzenie projektu.  
  
-   Definiowanie układu aplikacji.  
  
-   Definiowanie nowego mapowania właściwości.  
  
-   Usuwanie mapowania właściwości domyślnej.  
  
-   Zastępowanie domyślnego mapowania właściwości.  
  
-   Rozszerzanie domyślne mapowanie właściwości.  
  
 Kompletny kod lista zadań przedstawione w tym przewodniku, zobacz [mapowania właściwości za pomocą przykład elementu WindowsFormsHost](http://go.microsoft.com/fwlink/?LinkID=160019).  
  
 Gdy skończysz, będzie można mapować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości do odpowiedniej właściwości hostowany [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].,  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
  
#### <a name="to-create-and-set-up-the-project"></a>Tworzenie i konfigurowanie projektu  
  
1.  Utwórz projekt aplikacji WPF o nazwie `PropertyMappingWithWfhSample`.  
  
2.  W Eksploratorze rozwiązań Dodaj odwołanie do zestawu WindowsFormsIntegration, o nazwie WindowsFormsIntegration.dll.  
  
3.  W Eksploratorze rozwiązań Dodaj odwołania do zestawów System.Drawing i System.Windows.Forms.  
  
## <a name="defining-the-application-layout"></a>Definiowanie układ aplikacji  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— Na podstawie aplikacja używa <xref:System.Windows.Forms.Integration.WindowsFormsHost> element do hosta [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantu.  
  
#### <a name="to-define-the-application-layout"></a>Aby zdefiniować układ aplikacji  
  
1.  Otwórz Window1.xaml w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
2.  Zastąp istniejący kod następującym kodem.  
  
     [!code-xaml[PropertyMappingWithWfhSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]  
  
3.  Otwórz Window1.xaml.cs w edytorze kodu.  
  
4.  W górnej części pliku należy zaimportować następujących przestrzeni nazw.  
  
     [!code-csharp[PropertyMappingWithWfhSample#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]  
  
## <a name="defining-a-new-property-mapping"></a>Definiowanie nowe mapowanie właściwości  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element udostępnia kilka domyślnego mapowania właściwości. Dodaj nowe mapowanie właściwości przez wywołanie metody <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metoda <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.  
  
#### <a name="to-define-a-new-property-mapping"></a>Aby zdefiniować nowe mapowanie właściwości  
  
-   Skopiuj następujący kod do definicji `Window1` klasy.  
  
     [!code-csharp[PropertyMappingWithWfhSample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]  
  
     `AddClipMapping` Metoda dodaje nowe mapowanie dla <xref:System.Windows.UIElement.Clip%2A> właściwości.  
  
     `OnClipChange` Tłumaczy — metoda <xref:System.Windows.UIElement.Clip%2A> właściwości [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.Region%2A> właściwości.  
  
     `Window1_SizeChanged` Metoda obsługuje okna <xref:System.Windows.FrameworkElement.SizeChanged> zdarzeń i rozmiar obszaru przycinania w celu dopasowania do okna aplikacji.  
  
## <a name="removing-a-default-property-mapping"></a>Usuwanie mapowania właściwości domyślne  
 Usuń domyślne mapowanie właściwości przez wywołanie metody <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> metoda <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.  
  
#### <a name="to-remove-a-default-property-mapping"></a>Aby usunąć domyślne mapowanie właściwości  
  
-   Skopiuj następujący kod do definicji `Window1` klasy.  
  
     [!code-csharp[PropertyMappingWithWfhSample#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]  
  
     `RemoveCursorMapping` Metoda usuwa domyślnego mapowania dla <xref:System.Windows.FrameworkElement.Cursor%2A> właściwości.  
  
## <a name="replacing-a-default-property-mapping"></a>Zastępowanie domyślnego mapowania właściwości  
 Zastąp domyślne mapowanie właściwości przez usunięcie domyślnego mapowania i wywoływania <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metoda <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.  
  
#### <a name="to-replace-a-default-property-mapping"></a>Aby zastąpić domyślne mapowanie właściwości  
  
-   Skopiuj następujący kod do definicji `Window1` klasy.  
  
     [!code-csharp[PropertyMappingWithWfhSample#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]  
  
     `ReplaceFlowDirectionMapping` Metoda zastępuje domyślne mapowanie dla <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwości.  
  
     `OnFlowDirectionChange` Tłumaczy — metoda <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwości [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.RightToLeft%2A> właściwości.  
  
     `cb_CheckedChanged` Dojścia metody <xref:System.Windows.Forms.CheckBox.CheckedChanged> zdarzenia w <xref:System.Windows.Forms.CheckBox> formantu. Przypisuje <xref:System.Windows.FrameworkElement.FlowDirection%2A> na podstawie właściwości na wartość <xref:System.Windows.Forms.CheckBox.CheckState%2A> właściwości  
  
## <a name="extending-a-default-property-mapping"></a>Rozszerzanie domyślne mapowanie właściwości  
 Można użyć domyślnego mapowania właściwości i rozszerzać go z własnych mapowania.  
  
#### <a name="to-extend-a-default-property-mapping"></a>Aby rozszerzyć domyślne mapowanie właściwości  
  
-   Skopiuj następujący kod do definicji `Window1` klasy.  
  
     [!code-csharp[PropertyMappingWithWfhSample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]  
  
     `ExtendBackgroundMapping` Metoda dodaje translatora właściwości niestandardowych do istniejącej <xref:System.Windows.Controls.Control.Background%2A> mapowania właściwości.  
  
     `OnBackgroundChange` — Metoda przypisuje określony obraz sterowania hostowanej <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwości. `OnBackgroundChange` Metoda jest wywoływana po zastosowaniu domyślne mapowanie właściwości.  
  
## <a name="initializing-your-property-mappings"></a>Inicjowanie mapowań właściwości  
 Konfigurowanie mapowań właściwości przez wywołanie metody opisany wcześniej w <xref:System.Windows.FrameworkElement.Loaded> obsługi zdarzeń.  
  
#### <a name="to-initialize-your-property-mappings"></a>Aby zainicjować mapowań właściwości  
  
1.  Skopiuj następujący kod do definicji `Window1` klasy.  
  
     [!code-csharp[PropertyMappingWithWfhSample#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]  
  
     `WindowLoaded` Dojścia metody <xref:System.Windows.FrameworkElement.Loaded> zdarzeń i wykonuje następujące inicjowania.  
  
    -   Tworzy [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.CheckBox> formantu.  
  
    -   Wywołuje metody zdefiniowanych we wcześniejszej części przewodnika, aby skonfigurować mapowań właściwości.  
  
    -   Przypisuje wartości początkowej do mapowanej właściwości.  
  
2.  Naciśnij klawisz F5, aby skompilować i uruchomić aplikację. Kliknij pole wyboru, aby zobaczyć efekt <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapowania. Po kliknięciu pola wyboru układ odwraca orientacji od lewej do prawej.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Mapowanie właściwości Windows Forms i WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [Projektant WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Przewodnik: hosting kontrolki Windows Forms w WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
