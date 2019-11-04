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
ms.openlocfilehash: f9265e3f7b287e1e8c264e89325f7c9649eebe2c
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459133"
---
# <a name="how-to-find-datatemplate-generated-elements"></a>Porady: znajdowanie elementów generowanych przez DataTemplate
Ten przykład pokazuje, jak znaleźć elementy, które są generowane przez <xref:System.Windows.DataTemplate>.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie istnieje <xref:System.Windows.Controls.ListBox>, która jest powiązana z niektórymi [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] danymi:  
  
 [!code-xaml[FindGeneratedItems#LB](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 <xref:System.Windows.Controls.ListBox> używa następujących <xref:System.Windows.DataTemplate>:  
  
 [!code-xaml[FindGeneratedItems#DT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 Jeśli chcesz pobrać <xref:System.Windows.Controls.TextBlock> element wygenerowany przez <xref:System.Windows.DataTemplate> niektórych <xref:System.Windows.Controls.ListBoxItem>, należy uzyskać <xref:System.Windows.Controls.ListBoxItem>, znaleźć <xref:System.Windows.Controls.ContentPresenter> w tym <xref:System.Windows.Controls.ListBoxItem>, a następnie wywołać <xref:System.Windows.FrameworkTemplate.FindName%2A> na <xref:System.Windows.DataTemplate>, który jest ustawiony na <xref:System.Windows.Controls.ContentPresenter>. Poniższy przykład pokazuje, jak wykonać te kroki. W celach demonstracyjnych ten przykład tworzy okno komunikatu, które pokazuje zawartość tekstową bloku tekstu wygenerowanego <xref:System.Windows.DataTemplate>.  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 Poniżej przedstawiono implementację `FindVisualChild`, która używa metod <xref:System.Windows.Media.VisualTreeHelper>:  
  
 [!code-csharp[FindGeneratedItems#FVC](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: znajdowanie elementów generowanych przez ControlTemplate](../controls/how-to-find-controltemplate-generated-elements.md)
- [Powiązanie danych — omówienie](data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Zakresy nazw WPF XAML](../advanced/wpf-xaml-namescopes.md)
- [Drzewa w WPF](../advanced/trees-in-wpf.md)
