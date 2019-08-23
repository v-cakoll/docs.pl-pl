---
title: 'Instrukcje: Tworzenie standardowego okna dialogowego interfejsu użytkownika przy użyciu siatki'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
ms.openlocfilehash: 68c9653e616388374aad2ad33ac7dab68446241d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923423"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a>Instrukcje: Tworzenie standardowego okna dialogowego interfejsu użytkownika przy użyciu siatki
Ten przykład pokazuje, jak utworzyć standardowe [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] okno dialogowe przy <xref:System.Windows.Controls.Grid> użyciu elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy okno dialogowe, takie jak okno dialogowe **uruchamiania** w systemie operacyjnym Windows.  
  
 Przykład tworzy <xref:System.Windows.Controls.Grid> i <xref:System.Windows.Controls.ColumnDefinition> używa klas i <xref:System.Windows.Controls.RowDefinition> , aby zdefiniować pięć kolumn i cztery wiersze.  
  
 Przykład dodaje i ustawia położenie <xref:System.Windows.Controls.Image>, `RunIcon.png`,,,, aby reprezentować obraz znaleziony w oknie dialogowym. Obraz zostanie umieszczony w pierwszej kolumnie i wierszu <xref:System.Windows.Controls.Grid> (w lewym górnym rogu).  
  
 Następnie przykład dodaje <xref:System.Windows.Controls.TextBlock> element do pierwszej kolumny, który obejmuje pozostałe kolumny pierwszego wiersza. Dodaje kolejny <xref:System.Windows.Controls.TextBlock> element do drugiego wiersza w pierwszej kolumnie, aby reprezentować **otwarte** pole tekstowe. <xref:System.Windows.Controls.TextBlock> Poniżej, który reprezentuje obszar wprowadzania danych.  
  
 Na koniec <xref:System.Windows.Controls.Button> przykład dodaje trzy elementy do ostatniego wiersza, które reprezentują zdarzenia **OK**, **Anuluj**i **Przeglądaj** .  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [Panele — omówienie](panels-overview.md)
- [Tematy z instrukcjami](grid-how-to-topics.md)
