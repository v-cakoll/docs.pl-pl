---
title: 'Porady: znajdowanie elementów generowanych przez ControlTemplate'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ControlTemplates [WPF], finding elements
- finding ControlTemplate elements [WPF]
ms.assetid: d7b25447-ceff-4bb4-9be5-fd7c40ef00af
ms.openlocfilehash: 3d3032326a0cedc01b4a7ec8e6546044353d6b4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
 [Znajdowanie elementów wygenerowanych przez szablon DataTemplate](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)  
 [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Zakresy nazw WPF XAML](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)  
 [Drzewa w WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
