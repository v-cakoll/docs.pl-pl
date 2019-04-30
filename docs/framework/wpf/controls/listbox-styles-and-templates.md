---
title: ListBox — Style i szablony
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ListBox
- templates [WPF], ListBox
- states [WPF], ListBox
- ControlTemplate [WPF], ListBox
- parts [WPF], ListBox
- ListBox [WPF], styles and templates
ms.assetid: fc5764cb-c27b-495b-88d4-d969a8213ccb
ms.openlocfilehash: 441db59a6d04787985245db057074798bed6b3e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766873"
---
# <a name="listbox-styles-and-templates"></a>ListBox — Style i szablony
W tym temacie opisano, style i szablony <xref:System.Windows.Controls.ListBox> kontroli. Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> zapewnienie unikatowego wyglądu kontrolki. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu istniejącego formantu przez stworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="listbox-parts"></a>Części ListBox  
 <xref:System.Windows.Controls.ListBox> Formant nie ma żadnych części o nazwie.  
  
 Po utworzeniu <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ListBox>, szablon może zawierać <xref:System.Windows.Controls.ItemsPresenter> w ramach <xref:System.Windows.Controls.ScrollViewer>. ( <xref:System.Windows.Controls.ItemsPresenter> Wyświetla każdy element na <xref:System.Windows.Controls.ListBox>; <xref:System.Windows.Controls.ScrollViewer> umożliwia przewijanie w kontrolce).  Jeśli <xref:System.Windows.Controls.ItemsPresenter> nie jest bezpośrednie podrzędne <xref:System.Windows.Controls.ScrollViewer>, należy podać <xref:System.Windows.Controls.ItemsPresenter> nazwę, `ItemsPresenter`.  
  
## <a name="listbox-states"></a>Stany ListBox  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.ListBox> kontroli.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Prawidłowe|ValidationStates|Kontrolka jest nieprawidłowy.|  
|InvalidFocused|ValidationStates|Kontrolka nie jest prawidłowy i ma fokus.|  
|InvalidUnfocused|ValidationStates|Kontrolka jest nieprawidłowy i nie ma fokusu.|  
  
## <a name="listboxitem-parts"></a>Części ListBoxItem  
 <xref:System.Windows.Controls.ListBoxItem> Formant nie ma żadnych części o nazwie.  
  
## <a name="listboxitem-states"></a>Stany ListBoxItem  
 Poniższa tabela zawiera listę stanów wizualnych dla <xref:System.Windows.Controls.ListBox> kontroli.  
  
|Nazwa stanu wizualnego|Nazwa element VisualStateGroup|Opis|  
|-|-|-|  
|Normalne|CommonStates|Stan domyślny.|  
|MouseOver|CommonStates|Wskaźnik myszy jest umieszczony nad kontrolką.|  
|Wyłączone|CommonStates|Element jest wyłączony.|  
|Fokus|FocusStates|Element ma fokus.|  
|Po przeniesieniu fokusu|FocusStates|Element nie ma fokusu.|  
|Niezaznaczone|SelectionStates|Nie wybrano elementu.|  
|Wybrane|SelectionStates|Element jest wybrany currentlyplate.|  
|SelectedUnfocused|SelectionStates|Element jest wybrany, ale nie ma fokusu.|  
|Prawidłowe|ValidationStates|Kontrolka używa <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolki jest ustawiony fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma kontrolka nie ma fokusu.|  
  
## <a name="listbox-controltemplate-example"></a>Przykład ControlTemplate ListBox  
 Poniższy przykład pokazuje jak zdefiniować <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.ListBox> i <xref:System.Windows.Controls.ListBoxItem> kontrolki.  
  
 [!code-xaml[ControlTemplateExamples#ListBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listbox.xaml#listbox)]  
  
 W poprzednim przykładzie użyto co najmniej jeden z następujących zasobów.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Aby uzyskać pełny przykład, zobacz [style przykład ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Style i szablony kontrolek](control-styles-and-templates.md)
- [Niestandardowe dostosowywanie kontrolki](control-customization.md)
- [Tworzenie szablonów i stylów](styling-and-templating.md)
- [Dostosowywanie wyglądu istniejącej kontrolki przez tworzenie ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
