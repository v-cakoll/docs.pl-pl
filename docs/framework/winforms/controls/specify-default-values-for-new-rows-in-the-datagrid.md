---
title: "Porady: określanie wartości domyślnych dla nowych wierszy w formancie DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], default values for new rows
- DataGridView control [Windows Forms], data entry
- rows [Windows Forms], specifying default values
- DataGridView control [Windows Forms], default values for new rows
ms.assetid: 8d127963-d9f8-4e4e-9f7f-beb66688f1f2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 577d5c3bc4b4afef845cd51b62b7d48fcc9d4a7e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a>Porady: określanie wartości domyślnych dla nowych wierszy w formancie DataGridView formularzy systemu Windows
Istnieje możliwość wprowadzania danych wygodniejsze podczas aplikacji wypełnia w domyślnych wartości dla nowo dodanych wierszy. Z <xref:System.Windows.Forms.DataGridView> klasy, możesz wpisać w domyślnej wartości z <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> zdarzeń. To zdarzenie jest wywoływane, gdy użytkownik wprowadzi wiersz dla nowych rekordów. Gdy swój kod obsługi tego zdarzenia, można wypełnić żądaną komórek zawierających wartości wybrane.  
  
 Poniższy przykład kodu pokazuje sposób określania wartości domyślne dla nowych wierszy za pomocą <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> zdarzeń.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.  
  
-   A `NewCustomerId` funkcja generowania unikatowych `CustomerID` wartości.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 [Formantu DataGridView formularzy wprowadzania danych w systemie Windows](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [Używanie wiersza dla nowych rekordów w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
