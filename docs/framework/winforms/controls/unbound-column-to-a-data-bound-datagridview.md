---
title: 'Porady: dodawanie niepowiązanych kolumn do powiązanego z danymi formantu DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
ms.openlocfilehash: 8ba06457371bab5b81e18a307960a833d1d54199
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a>Porady: dodawanie niepowiązanych kolumn do powiązanego z danymi formantu DataGridView formularzy systemu Windows
Dane wyświetlane w <xref:System.Windows.Forms.DataGridView> kontroli zwykle będą pobierane z określonego rodzaju źródła danych, ale należy wyświetlić kolumny danych, które nie pochodzą ze źródła danych. Tego rodzaju kolumny jest nazywany niepowiązanych kolumn. Niepowiązanych kolumn może mieć wiele form. Często są one używane do zapewniania dostępu do szczegółów wiersza danych.  
  
 Poniższy przykładowy kod przedstawia sposób tworzenia niepowiązanych kolumn z **szczegóły** przyciski, aby wyświetlić tabeli podrzędnej dotyczące określonego wiersza w tabeli nadrzędnej podczas implementowania scenariusza wzorzec/szczegół. Aby odpowiadanie na kliknięcia przycisku, zaimplementuj <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> obsługi zdarzeń, który wyświetla formularz zawierający tabelą podrzędną.  
  
 Brak obsługi dla tego zadania w programie Visual Studio.  Zobacz też [porady: Dodawanie i usuwanie kolumn w Windows Forms DataGridView formantu przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/dyyesckz\(v=vs.110\))  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
