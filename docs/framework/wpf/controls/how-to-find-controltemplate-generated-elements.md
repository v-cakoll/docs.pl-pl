---
title: 'Instrukcje: Znajdowanie elementów generowanych przez ControlTemplate'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ControlTemplates [WPF], finding elements
- finding ControlTemplate elements [WPF]
ms.assetid: d7b25447-ceff-4bb4-9be5-fd7c40ef00af
ms.openlocfilehash: a93ec700bc0782439f98aed48f7094a50a3c0ea4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638383"
---
# <a name="how-to-find-controltemplate-generated-elements"></a>Instrukcje: Znajdowanie elementów generowanych przez ControlTemplate
W tym przykładzie pokazano, jak znajdowanie elementów generowanych przez <xref:System.Windows.Controls.ControlTemplate>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano styl, który tworzy prostą <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Button> klasy:  
  
 [!code-xaml[FindGeneratedItems#CT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 Aby znaleźć element w szablonie, po zastosowaniu szablonu, można wywołać <xref:System.Windows.FrameworkTemplate.FindName%2A> metody <xref:System.Windows.Controls.Control.Template%2A>. Poniższy przykład tworzy okno komunikatu, które pokazuje wartość rzeczywista szerokość <xref:System.Windows.Controls.Grid> w szablonie kontrolki:  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## <a name="see-also"></a>Zobacz także
- [Znajdowanie elementów wygenerowanych przez szablon DataTemplate](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
- [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [Zakresy nazw WPF XAML](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)
- [Drzewa w WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
