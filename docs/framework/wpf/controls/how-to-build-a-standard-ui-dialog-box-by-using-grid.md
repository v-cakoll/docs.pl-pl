---
title: 'Instrukcje: Twórz standardowe okno dialogowe interfejsu użytkownika przy użyciu siatki'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
ms.openlocfilehash: 893b3f7fda3314b158f7c67392a0913e30a92c09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650525"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a>Instrukcje: Twórz standardowe okno dialogowe interfejsu użytkownika przy użyciu siatki
W tym przykładzie przedstawiono sposób tworzenia standardowego [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] okno dialogowe, za pomocą <xref:System.Windows.Controls.Grid> elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy okno dialogowe, takich jak **Uruchom** okno dialogowe w [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] systemu operacyjnego.  
  
 W przykładzie jest tworzony <xref:System.Windows.Controls.Grid> i używa <xref:System.Windows.Controls.ColumnDefinition> i <xref:System.Windows.Controls.RowDefinition> klasy zdefiniowanie pięciu kolumn i cztery wiersze.  
  
 Przykład następnie dodaje i umieszcza <xref:System.Windows.Controls.Image>, `RunIcon.png`, do reprezentowania obraz, który znajduje się w oknie dialogowym. Obraz jest umieszczany w pierwszej kolumnie, a wiersz <xref:System.Windows.Controls.Grid> (lewy górny róg).  
  
 Następnie w przykładzie dodano <xref:System.Windows.Controls.TextBlock> element do pierwszej kolumny, która obejmuje pozostałych kolumnach pierwszego wiersza. Dodaje, kolejny <xref:System.Windows.Controls.TextBlock> elementu do drugiego wiersza w pierwszej kolumnie do reprezentowania **Otwórz** pola tekstowego. A <xref:System.Windows.Controls.TextBlock> poniżej, które reprezentuje obszaru wprowadzania danych.  
  
 Ponadto w przykładzie dodano trzy <xref:System.Windows.Controls.Button> elementów w ostatnim wierszu, które reprezentują **OK**, **anulować**, i **Przeglądaj** zdarzenia.  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)
- [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/grid-how-to-topics.md)
