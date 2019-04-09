---
title: 'Instrukcje: znajdowanie elementów generowanych przez element ControlTemplate'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ControlTemplates [WPF], finding elements
- finding ControlTemplate elements [WPF]
ms.assetid: d7b25447-ceff-4bb4-9be5-fd7c40ef00af
ms.openlocfilehash: 426f6c93433711ac72fe67eff2ee3006aa4d9166
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092131"
---
# <a name="how-to-find-controltemplate-generated-elements"></a>Instrukcje: znajdowanie elementów generowanych przez element ControlTemplate
W tym przykładzie pokazano, jak znajdowanie elementów generowanych przez <xref:System.Windows.Controls.ControlTemplate>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano styl, który tworzy prostą <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Button> klasy:  
  
 [!code-xaml[FindGeneratedItems#CT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 Aby znaleźć element w szablonie, po zastosowaniu szablonu, można wywołać <xref:System.Windows.FrameworkTemplate.FindName%2A> metody <xref:System.Windows.Controls.Control.Template%2A>. Poniższy przykład tworzy okno komunikatu, które pokazuje wartość rzeczywista szerokość <xref:System.Windows.Controls.Grid> w szablonie kontrolki:  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## <a name="see-also"></a>Zobacz także

- [Znajdowanie elementów wygenerowanych przez szablon DataTemplate](../data/how-to-find-datatemplate-generated-elements.md)
- [Tworzenie szablonów i stylów](styling-and-templating.md)
- [Zakresy nazw WPF XAML](../advanced/wpf-xaml-namescopes.md)
- [Drzewa w WPF](../advanced/trees-in-wpf.md)
