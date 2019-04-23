---
title: 'Instrukcje: zmienianie kolejności kolumn w kontrolce DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
ms.openlocfilehash: 90d262e738f092215e88e38e31169d74059e4401
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228799"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a>Instrukcje: zmienianie kolejności kolumn w kontrolce DataGridView formularzy systemu Windows
Kiedy używasz <xref:System.Windows.Forms.DataGridView> do wyświetlania danych ze źródła danych, w kolumnach czasami schematu źródła danych nie są wyświetlane w kolejności, aby je wyświetlić. Można zmienić kolejność wyświetlanych kolumn, używając <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> właściwość <xref:System.Windows.Forms.DataGridViewColumn> klasy.  
  
 Poniższy przykładowy kod powoduje przeniesienie niektórych kolumn generowane automatycznie podczas tworzenia wiązania do tabeli Klienci w bazie danych Northwind. Aby uzyskać więcej informacji o tym, jak powiązać <xref:System.Windows.Forms.DataGridView> sterowania do tabeli bazy danych, zobacz [jak: Powiązywanie danych Windows formantu DataGridView formularzy](how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 Są obsługiwane dla tego zadania w programie Visual Studio.  Zobacz też [jak: Zmienianie kolejności kolumn w formancie DataGridView formularzy Windows za pomocą projektanta](change-the-order-of-columns-in-the-datagrid-using-the-designer.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `customersDataGridView` , jest powiązana z tabelą z nazwami wskazanej kolumny, takie jak `Customers` tabeli w bazie danych Northwind.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, i <xref:System.Xml?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: Powiązanie danych w kontrolce DataGridView formularzy Windows Forms](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
