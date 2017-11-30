---
title: "Porady: znajdowanie elementów generowanych przez ControlTemplate"
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
- ControlTemplates [WPF], finding elements
- finding ControlTemplate elements [WPF]
ms.assetid: d7b25447-ceff-4bb4-9be5-fd7c40ef00af
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f81069873930af57e1f6ab2f3e0408b4d53f38b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-controltemplate-generated-elements"></a>Porady: znajdowanie elementów generowanych przez ControlTemplate
W tym przykładzie pokazano, jak znaleźć elementy, które są generowane przez <xref:System.Windows.Controls.ControlTemplate>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono styl, który tworzy prosty <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Button> klasy:  
  
 [!code-xaml[FindGeneratedItems#CT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 Aby znaleźć element w szablonie, po zastosowaniu szablon, należy wywołać <xref:System.Windows.FrameworkTemplate.FindName%2A> metody <xref:System.Windows.Controls.Control.Template%2A>. Poniższy przykład tworzy okno komunikatu pokazujący wartość rzeczywista szerokość <xref:System.Windows.Controls.Grid> w kontroli szablonu:  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## <a name="see-also"></a>Zobacz też  
 [Znajdź elementy generowane DataTemplate](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)  
 [Style i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Namescopes WPF XAML](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)  
 [Drzewa na platformie WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
