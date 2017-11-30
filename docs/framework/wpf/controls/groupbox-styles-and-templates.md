---
title: "GroupBox — Style i szablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8a39e09812c54df533fdac27b5bfcaedd3fb93ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="groupbox-styles-and-templates"></a>GroupBox — Style i szablony
<a name="introduction"></a>W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.GroupBox> formantu. Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
<a name="groupbox_parts"></a>   
## <a name="groupbox-parts"></a>GroupBox — elementy  
 <xref:System.Windows.Controls.GroupBox> Formant nie ma żadnych części o nazwie.  
  
<a name="groupbox_states"></a>   
## <a name="groupbox-states"></a>GroupBox — Stany  
 W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.GroupBox> formantu.  
  
|Nazwa stanu wizualnego|Nazwa VisualStateGroup|Opis|  
|-|-|-|  
|Prawidłowe|ValidationStates|Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.|  
  
<a name="groupbox_controltemplate_example"></a>   
## <a name="groupbox-controltemplate-example"></a>Przykład ControlTemplate GroupBox  
 Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.GroupBox> formantu.  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <xref:System.Windows.Controls.ControlTemplate> Korzysta z co najmniej jeden z następujących zasobów.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Style formantu i szablony](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Dostosowywanie formantu](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Style i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
