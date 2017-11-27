---
title: "CheckBox — Style i szablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], CheckBox
- templates [WPF], CheckBox
- parts [WPF], CheckBox
- ControlTemplate [WPF], CheckBox
- CheckBox [WPF], styles and templates
- styles [WPF], CheckBox
ms.assetid: bfdaec96-d101-4d3d-864d-c27e6b621d03
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c901d710e96cd111104b9fef2219b157377adc3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="checkbox-styles-and-templates"></a>CheckBox — Style i szablony
W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.CheckBox> formantu. Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="checkbox-parts"></a>Części pola wyboru  
 <xref:System.Windows.Controls.CheckBox> Formant nie ma żadnych części o nazwie.  
  
## <a name="checkbox-states"></a>Stany pola wyboru  
 W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.CheckBox> formantu.  
  
|Nazwa stanu wizualnego|Nazwa VisualStateGroup|Opis|  
|----------------------|---------------------------|-----------------|  
|Normalny|CommonStates|Stan domyślny.|  
|Etykietka wskaźnika myszy|CommonStates|Wskaźnik myszy znajduje się nad formantem.|  
|Naciśnięto|CommonStates|Formant zostanie naciśnięty.|  
|Wyłączone|CommonStates|Kontrolka jest wyłączona.|  
|Fokus|FocusStates|Formant ma fokus.|  
|Bez fokusu|FocusStates|Formant nie ma fokusa.|  
|Zaznaczone|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>jest `true`.|  
|Unchecked|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>jest `false`.|  
|Nieokreślony|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>jest `true`, i <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> jest `null`.|  
|Prawidłowe|ValidationStates|Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.|  
  
## <a name="checkbox-controltemplate-example"></a>Przykład ControlTemplate wyboru  
 Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.CheckBox> formantu.  
  
 [!code-xaml[ControlTemplateExamples#CheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/checkbox.xaml#checkbox)]  
  
 Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Style formantu i szablony](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Dostosowywanie formantu](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Style i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
