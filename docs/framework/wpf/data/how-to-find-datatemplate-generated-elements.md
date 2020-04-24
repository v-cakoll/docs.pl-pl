---
title: 'Porady: znajdowanie elementów generowanych przez DataTemplate'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- finding DataTemplate elements [WPF]
- DataTemplate [WPF]
ms.assetid: bfcd564e-5e9e-451e-8641-a9b5c3cfac90
ms.openlocfilehash: 3b222880aa4eda32502e3dcece2fa5c0b57b7a51
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646435"
---
# <a name="how-to-find-datatemplate-generated-elements"></a>Porady: znajdowanie elementów generowanych przez DataTemplate
W tym przykładzie pokazano, jak <xref:System.Windows.DataTemplate>znaleźć elementy, które są generowane przez .  
  
## <a name="example"></a>Przykład  
 W tym przykładzie <xref:System.Windows.Controls.ListBox> istnieje, że jest powiązany z niektórych danych XML:  
  
 [!code-xaml[FindGeneratedItems#LB](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 Używa <xref:System.Windows.Controls.ListBox> następujących elementów: <xref:System.Windows.DataTemplate>  
  
 [!code-xaml[FindGeneratedItems#DT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 Jeśli chcesz pobrać <xref:System.Windows.Controls.TextBlock> element generowany przez <xref:System.Windows.DataTemplate> określony <xref:System.Windows.Controls.ListBoxItem>, musisz uzyskać <xref:System.Windows.Controls.ListBoxItem>, znaleźć <xref:System.Windows.Controls.ContentPresenter> w <xref:System.Windows.Controls.ListBoxItem>tym , <xref:System.Windows.FrameworkTemplate.FindName%2A> a <xref:System.Windows.DataTemplate> następnie wywołać, który jest ustawiony na tym <xref:System.Windows.Controls.ContentPresenter>. W poniższym przykładzie pokazano, jak wykonać te kroki. Do celów demonstracyjnych w tym przykładzie tworzy okno <xref:System.Windows.DataTemplate>komunikatu, który pokazuje zawartość tekstową bloku tekstu generowane.  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 Poniżej przedstawiono `FindVisualChild`implementację , <xref:System.Windows.Media.VisualTreeHelper> która wykorzystuje metody:  
  
 [!code-csharp[FindGeneratedItems#FVC](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: znajdowanie elementów generowanych przez ControlTemplate](../controls/how-to-find-controltemplate-generated-elements.md)
- [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md)
- [— Tematy porad](data-binding-how-to-topics.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Zakresy nazw WPF XAML](../advanced/wpf-xaml-namescopes.md)
- [Drzewa w WPF](../advanced/trees-in-wpf.md)
