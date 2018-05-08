---
title: Jak utworzyć siatkę złożoną
ms.date: 03/30/2017
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
ms.openlocfilehash: 49bf9781d56b93fd4529f3c9b62deb171e69155f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-complex-grid"></a>Jak utworzyć siatkę złożoną
Ten przykład przedstawia sposób użycia <xref:System.Windows.Controls.Grid> do tworzenia układu, która wygląda jak kalendarza miesięcznego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano osiem wierszy i kolumn osiem przy użyciu <xref:System.Windows.Controls.RowDefinition> i <xref:System.Windows.Controls.ColumnDefinition> klasy. Używa <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> i <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> dołączone właściwości, wraz z <xref:System.Windows.Shapes.Rectangle> elementów, które wypełnienia tła różnych kolumn i wierszy. Ten projekt jest możliwa, ponieważ w każdej komórki w może istnieć więcej niż jeden element <xref:System.Windows.Controls.Grid>, zasady różnicę między <xref:System.Windows.Controls.Grid> i <xref:System.Windows.Documents.Table>.  
  
 W przykładzie użyto pionowy gradientów do <xref:System.Windows.Shapes.Shape.Fill%2A> kolumn i wierszy w celu ulepszania wizualną prezentację i czytelność kalendarza. Styl <xref:System.Windows.Controls.TextBlock> elementy reprezentują dat i dni tygodnia. <xref:System.Windows.Controls.TextBlock> elementy są bezwzględnego w komórkach ich przy użyciu <xref:System.Windows.FrameworkElement.Margin%2A> właściwości i wyrównanie właściwości, które są zdefiniowane w stylu dla aplikacji.  
  
 [!code-xaml[GridComplex#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Documents.TableCell>  
 [Malowanie jednolitymi kolorami i gradientami — przegląd](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Przegląd tabeli](../../../../docs/framework/wpf/advanced/table-overview.md)
