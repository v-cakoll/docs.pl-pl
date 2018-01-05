---
title: "Porady: wyświetlanie obrazów w komórkach formantu DataGridView formularzy systemu Windows"
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
- cells [Windows Forms], displaying images
- data grids [Windows Forms], displaying in grids
- DataGridView control [Windows Forms], displaying images
- data grids [Windows Forms], displaying images in cells
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 56c8558f34c895567c3eebfbb5a89612c4b56224
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a>Porady: wyświetlanie obrazów w komórkach formantu DataGridView formularzy systemu Windows
Obraz lub grafikę to jedna z wartości, które można wyświetlić w wierszu danych. Często te grafiki formę pracownika zdjęcie lub logo firmy.  
  
 Dołączanie obrazów jest proste, podczas wyświetlania danych w ramach <xref:System.Windows.Forms.DataGridView> formantu. <xref:System.Windows.Forms.DataGridView> Kontroli natywnie obsługuje dowolny format obrazu obsługiwany przez <xref:System.Drawing.Image> klasy, a także OLE obraz format używany przez niektóre bazy danych.  
  
 Jeśli <xref:System.Windows.Forms.DataGridView> formantu źródła danych zawiera kolumnę obrazów, będą one wyświetlane automatycznie przez <xref:System.Windows.Forms.DataGridView> formantu.  
  
 Poniższy przykład kodu pokazuje, jak wyodrębnić ikony z zasobu osadzonego i przekształcić ją w mapy bitowej do wyświetlenia w każdej komórce kolumny obrazu. Na przykład innego zamienia wartości tekstowej komórek odpowiednich obrazów, zobacz [porady: dostosowywanie formatowania danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.  
  
-   Zasobów osadzonych ikona o nazwie `tree.ico`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, i <xref:System.Drawing?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 [Podstawowe funkcje komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [Instrukcje: dostosowywanie formatowania danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
