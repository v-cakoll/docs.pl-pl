---
title: "Jak utworzyć siatkę złożoną"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- calendar [WPF], creating
- monthly calendar [WPF], creating
- Grid control [WPF], creating [WPF], complex grid
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2c0008a7379feefd9b3fe719f85b3205a72fb51d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-complex-grid"></a>Jak utworzyć siatkę złożoną
Ten przykład przedstawia sposób użycia <xref:System.Windows.Controls.Grid> do tworzenia układu, która wygląda jak kalendarza miesięcznego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano osiem wierszy i kolumn osiem przy użyciu <xref:System.Windows.Controls.RowDefinition> i <xref:System.Windows.Controls.ColumnDefinition> klasy. Używa <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=nameWithType> i <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=nameWithType> dołączone właściwości, wraz z <xref:System.Windows.Shapes.Rectangle> elementów, które wypełnienia tła różnych kolumn i wierszy. Ten projekt jest możliwa, ponieważ w każdej komórki w może istnieć więcej niż jeden element <xref:System.Windows.Controls.Grid>, zasady różnicę między <xref:System.Windows.Controls.Grid> i <xref:System.Windows.Documents.Table>.  
  
 W przykładzie użyto pionowy gradientów do <xref:System.Windows.Shapes.Shape.Fill%2A> kolumn i wierszy w celu ulepszania wizualną prezentację i czytelność kalendarza. Styl <xref:System.Windows.Controls.TextBlock> elementy reprezentują dat i dni tygodnia. <xref:System.Windows.Controls.TextBlock>elementy są bezwzględnego w komórkach ich przy użyciu <xref:System.Windows.FrameworkElement.Margin%2A> właściwości i wyrównanie właściwości, które są zdefiniowane w stylu dla aplikacji.  
  
 [!code-xaml[GridComplex#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Documents.TableCell>  
 [Malowanie pełnych kolorów i gradientów — omówienie](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Omówienie paneli](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Przegląd tabeli](../../../../docs/framework/wpf/advanced/table-overview.md)
