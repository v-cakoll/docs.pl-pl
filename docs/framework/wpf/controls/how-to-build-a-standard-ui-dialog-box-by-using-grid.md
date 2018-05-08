---
title: Jak tworzyć standardowe okno dialogowe interfejsu użytkownika przy użyciu siatki
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
ms.openlocfilehash: d0b24e320c2a341b069e1c9c3e8b6d5e93076733
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a>Jak tworzyć standardowe okno dialogowe interfejsu użytkownika przy użyciu siatki
W tym przykładzie przedstawiono sposób tworzenia standardowego [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] okno dialogowe przy użyciu <xref:System.Windows.Controls.Grid> elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy okno dialogowe podobne **Uruchom** okno dialogowe w [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] systemu operacyjnego.  
  
 W przykładzie jest tworzony <xref:System.Windows.Controls.Grid> i używa <xref:System.Windows.Controls.ColumnDefinition> i <xref:System.Windows.Controls.RowDefinition> klasy do definiowania pięć kolumn i wierszy cztery.  
  
 W przykładzie następnie dodaje i umieszcza <xref:System.Windows.Controls.Image>, `RunIcon.png`, do reprezentowania obrazu, który można znaleźć w oknie dialogowym. Obraz jest umieszczany w pierwszej kolumnie i wiersza <xref:System.Windows.Controls.Grid> (lewego górnego rogu).  
  
 Następnie w przykładzie dodano <xref:System.Windows.Controls.TextBlock> element do pierwszej kolumny, która obejmuje pozostałych kolumnach pierwszego wiersza. Dodaje innego <xref:System.Windows.Controls.TextBlock> elementu do drugiego wiersza w pierwszej kolumnie do reprezentowania **Otwórz** pola tekstowego. A <xref:System.Windows.Controls.TextBlock> następujące, które reprezentuje obszaru wprowadzania danych.  
  
 Ponadto w przykładzie dodano trzy <xref:System.Windows.Controls.Button> elementy do wiersza końcowego, które reprezentują **OK**, **anulować**, i **Przeglądaj** zdarzenia.  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.GridUnitType>  
 [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/grid-how-to-topics.md)
