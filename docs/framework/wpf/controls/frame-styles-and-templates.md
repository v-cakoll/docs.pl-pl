---
title: Style i szablony klatek
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], Frame
- templates [WPF], Frame
- ControlTemplate [WPF], Frame
- Frame [WPF], styles and templates
- states [WPF], Frame
- styles [WPF], Frame
ms.assetid: a01c32e2-c951-46a0-a82f-2614ca241f0b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d1b69ffb0eff114252383e682d6c200d88503a80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="frame-styles-and-templates"></a>Style i szablony klatek
W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.Frame> formantu. Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="frame-parts"></a>Części ramki  
 W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.Frame> formantu.  
  
|Część|Typ|Opis|  
|-|-|-|  
|PART_FrameCP|<xref:System.Windows.Controls.ContentPresenter>|Obszar zawartości.|  
  
## <a name="frame-states"></a>Stany ramek  
 W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Frame> formantu.  
  
|Nazwa stanu wizualnego|Nazwa VisualStateGroup|Opis|  
|-|-|-|  
|Prawidłowe|ValidationStates|Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.|  
  
## <a name="frame-controltemplate-example"></a>Przykład ControlTemplate ramki  
 Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Frame> formantu.  
  
 [!code-xaml[ControlTemplateExamples#Frame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
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
