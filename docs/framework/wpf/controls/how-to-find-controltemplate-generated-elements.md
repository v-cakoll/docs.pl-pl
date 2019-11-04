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
ms.openlocfilehash: 232ee7d2859059591c9beff753f45781598a8127
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460709"
---
# <a name="how-to-find-controltemplate-generated-elements"></a>Porady: znajdowanie elementów generowanych przez ControlTemplate
Ten przykład pokazuje, jak znaleźć elementy, które są generowane przez <xref:System.Windows.Controls.ControlTemplate>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono styl, który tworzy prostą <xref:System.Windows.Controls.ControlTemplate> dla klasy <xref:System.Windows.Controls.Button>:  
  
 [!code-xaml[FindGeneratedItems#CT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 Aby znaleźć element w szablonie po zastosowaniu szablonu, można wywołać metodę <xref:System.Windows.FrameworkTemplate.FindName%2A> <xref:System.Windows.Controls.Control.Template%2A>. Poniższy przykład tworzy okno komunikatu, które pokazuje rzeczywistą wartość szerokości <xref:System.Windows.Controls.Grid> w szablonie kontrolki:  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## <a name="see-also"></a>Zobacz także

- [Znajdowanie elementów wygenerowanych przez szablon DataTemplate](../data/how-to-find-datatemplate-generated-elements.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Zakresy nazw WPF XAML](../advanced/wpf-xaml-namescopes.md)
- [Drzewa w WPF](../advanced/trees-in-wpf.md)
