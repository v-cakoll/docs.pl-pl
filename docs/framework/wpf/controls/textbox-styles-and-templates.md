---
title: "TextBox — Style i szablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7f5cfd1c0715c7f9610f85201cd40a3973a2be64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="textbox-styles-and-templates"></a>TextBox — Style i szablony
W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.TextBox> formantu. Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="textbox-parts"></a>Części pola tekstowego  
 W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.TextBox> formantu.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_ContentHost|<xref:System.Windows.FrameworkElement>|Element wizualny, który może zawierać <xref:System.Windows.FrameworkElement>. Tekst <xref:System.Windows.Controls.TextBox> jest wyświetlany w tym elemencie.|  
  
## <a name="textbox-states"></a>Pole tekstowe stanów  
 W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.TextBox> formantu.  
  
|Nazwa stanu wizualnego|Nazwa VisualStateGroup|Opis|  
|----------------------|---------------------------|-----------------|  
|Normalny|CommonStates|Stan domyślny.|  
|Etykietka wskaźnika myszy|CommonStates|Wskaźnik myszy znajduje się nad formantem.|  
|Wyłączone|CommonStates|Kontrolka jest wyłączona.|  
|ReadOnly|CommonStates|Użytkownik nie może zmieniać tekst w <xref:System.Windows.Controls.TextBox>.|  
|Fokus|FocusStates|Formant ma fokus.|  
|Bez fokusu|FocusStates|Formant nie ma fokusa.|  
|Prawidłowe|ValidationStates|Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.|  
  
## <a name="textbox-controltemplate-example"></a>Przykład ControlTemplate pole tekstowe  
 Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.TextBox> formantu.  
  
 [!code-xaml[ControlTemplateExamples#TextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
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
