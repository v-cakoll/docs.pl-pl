---
title: "ListBox — Style i szablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], ListBox
- templates [WPF], ListBox
- states [WPF], ListBox
- ControlTemplate [WPF], ListBox
- parts [WPF], ListBox
- ListBox [WPF], styles and templates
ms.assetid: fc5764cb-c27b-495b-88d4-d969a8213ccb
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edf8c50424a9694c4e00f5bf319d3122999bda85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="listbox-styles-and-templates"></a>ListBox — Style i szablony
W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.ListBox> formantu. Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="listbox-parts"></a>Części ListBox  
 <xref:System.Windows.Controls.ListBox> Formant nie ma żadnych części o nazwie.  
  
 Po utworzeniu <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ListBox>, szablon może zawierać <xref:System.Windows.Controls.ItemsPresenter> w <xref:System.Windows.Controls.ScrollViewer>. ( <xref:System.Windows.Controls.ItemsPresenter> Wyświetla każdy element <xref:System.Windows.Controls.ListBox>; <xref:System.Windows.Controls.ScrollViewer> włącza przewijanie w kontrolce).  Jeśli <xref:System.Windows.Controls.ItemsPresenter> nie jest bezpośrednim elementem podrzędnym elementu <xref:System.Windows.Controls.ScrollViewer>, musisz podać <xref:System.Windows.Controls.ItemsPresenter> nazwę, `ItemsPresenter`.  
  
## <a name="listbox-states"></a>Stany ListBox  
 W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.ListBox> formantu.  
  
|Nazwa stanu wizualnego|Nazwa VisualStateGroup|Opis|  
|-|-|-|  
|Prawidłowe|ValidationStates|Formant jest nieprawidłowy.|  
|InvalidFocused|ValidationStates|Formant nie jest prawidłowy i ma fokus.|  
|InvalidUnfocused|ValidationStates|Formant jest nieprawidłowy i nie ma fokusa.|  
  
## <a name="listboxitem-parts"></a>Części ListBoxItem  
 <xref:System.Windows.Controls.ListBoxItem> Formant nie ma żadnych części o nazwie.  
  
## <a name="listboxitem-states"></a>Stany ListBoxItem  
 W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.ListBox> formantu.  
  
|Nazwa stanu wizualnego|Nazwa VisualStateGroup|Opis|  
|-|-|-|  
|Normalny|CommonStates|Stan domyślny.|  
|Etykietka wskaźnika myszy|CommonStates|Wskaźnik myszy znajduje się nad formantem.|  
|Wyłączone|CommonStates|Element jest wyłączona.|  
|Fokus|FocusStates|Element ma fokus.|  
|Bez fokusu|FocusStates|Element nie ma fokusa.|  
|Niezaznaczony|SelectionStates|Nie wybrano elementu.|  
|Wybrane|SelectionStates|Element jest wybrany currentlyplate.|  
|SelectedUnfocused|SelectionStates|Element jest wybrany, ale nie ma fokusa.|  
|Prawidłowe|ValidationStates|Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.|  
  
## <a name="listbox-controltemplate-example"></a>Przykład ControlTemplate ListBox  
 Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.ListBoxItem> kontrolki.  
  
 [!code-xaml[ControlTemplateExamples#ListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listbox.xaml#listbox)]  
  
 Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Style i szablony kontrolek](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Niestandardowe dostosowywanie kontrolki](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
