---
title: "Porady: zmienianie kolejności kolumn w formancie DataGridView formularzy systemu Windows"
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
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2107da50f3b8a569bc329dbb1ae1722141921e11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a>Porady: zmienianie kolejności kolumn w formancie DataGridView formularzy systemu Windows
Jeśli używasz <xref:System.Windows.Forms.DataGridView> do wyświetlania danych ze źródła danych, w kolumnach czasami schematu źródła danych nie są wyświetlane w kolejności, aby je wyświetlić. Można zmienić kolejność wyświetlanych kolumn za pomocą <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> właściwość <xref:System.Windows.Forms.DataGridViewColumn> klasy.  
  
 Poniższy przykład kodu powoduje przeniesienie niektóre kolumny są generowane automatycznie podczas wiązania z tabeli Klienci w bazie danych Northwind. Aby uzyskać więcej informacji o sposobie wiązania <xref:System.Windows.Forms.DataGridView> sterowania do tabeli bazy danych, zobacz [porady: wiązania danych formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 Brak obsługi dla tego zadania w programie Visual Studio.  Zobacz też [porady: Zmienianie kolejności kolumn w Windows Forms DataGridView formantu przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/hb1dk7ax\(v=vs.110\))  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `customersDataGridView` takich jak, który jest powiązany z tabelą z nazwami wskazanej kolumny `Customers` tabeli w bazie danych Northwind.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, i <xref:System.Xml?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [Wyświetlanie danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Porady: wiązanie danych formularzy systemu Windows formantu DataGridView](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)
