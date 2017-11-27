---
title: "Porady: określanie kolumn jako tylko do odczytu w formancie DataGridView formularzy systemu Windows"
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
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f3fb80b5baeafff53781cb1ff430ad05dd93f2ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a>Porady: określanie kolumn jako tylko do odczytu w formancie DataGridView formularzy systemu Windows
Nie wszystkie dane są przeznaczone do edycji. W <xref:System.Windows.Forms.DataGridView> kontrolować kolumny <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> właściwości wartość określa, czy użytkownicy mogą edytować komórki w tej kolumnie. Aby uzyskać informacje o sposobie tworzenia kontrolki całkowicie tylko do odczytu, zobacz [porady: Zapobiegaj dodawaniu i usuwaniu rzędów do formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md).  
  
 Brak obsługi dla tego zadania w programie Visual Studio.  Zobacz też [jak: utworzyć tylko do odczytu w kolumnach w Windows Forms DataGridView formantu przy użyciu projektanta](http://msdn.microsoft.com/library/xd4k3c7e\(v=vs.110\)).  
  
### <a name="to-make-a-column-read-only-programmatically"></a>Aby kolumnę tylko do odczytu programowo  
  
-   Ustaw <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> właściwości `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` z kolumny o nazwie `CompanyName`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 [Wierszy i kolumn podstawowe funkcje komórek w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [Porady: Zapobieganie dodawaniu i usuwaniu w oknach formantu DataGridView formularzy](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)
