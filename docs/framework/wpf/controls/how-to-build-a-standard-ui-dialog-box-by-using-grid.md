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
ms.openlocfilehash: 57edaa173b85bc06c6859b08d3edec281e1b8942
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372870"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a>Instrukcje: Twórz standardowe okno dialogowe interfejsu użytkownika przy użyciu siatki
W tym przykładzie przedstawiono sposób tworzenia standardowego [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] okno dialogowe, za pomocą <xref:System.Windows.Controls.Grid> elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy okno dialogowe, takich jak **Uruchom** okno dialogowe w [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] systemu operacyjnego.  
  
 W przykładzie jest tworzony <xref:System.Windows.Controls.Grid> i używa <xref:System.Windows.Controls.ColumnDefinition> i <xref:System.Windows.Controls.RowDefinition> klasy zdefiniowanie pięciu kolumn i cztery wiersze.  
  
 Przykład następnie dodaje i umieszcza <xref:System.Windows.Controls.Image>, `RunIcon.png`, do reprezentowania obraz, który znajduje się w oknie dialogowym. Obraz jest umieszczany w pierwszej kolumnie, a wiersz <xref:System.Windows.Controls.Grid> (lewy górny róg).  
  
 Następnie w przykładzie dodano <xref:System.Windows.Controls.TextBlock> element do pierwszej kolumny, która obejmuje pozostałych kolumnach pierwszego wiersza. Dodaje, kolejny <xref:System.Windows.Controls.TextBlock> elementu do drugiego wiersza w pierwszej kolumnie do reprezentowania **Otwórz** pola tekstowego. A <xref:System.Windows.Controls.TextBlock> poniżej, które reprezentuje obszaru wprowadzania danych.  
  
 Ponadto w przykładzie dodano trzy <xref:System.Windows.Controls.Button> elementów w ostatnim wierszu, które reprezentują **OK**, **anulować**, i **Przeglądaj** zdarzenia.  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [Panele — omówienie](panels-overview.md)
- [Tematy z instrukcjami](grid-how-to-topics.md)
