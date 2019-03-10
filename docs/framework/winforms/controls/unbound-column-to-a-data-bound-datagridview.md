---
title: 'Instrukcje: Dodawanie niepowiązanych kolumn do formantu DataGridView formularzy Windows powiązane z danymi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
ms.openlocfilehash: d7f96aa8d11cee9427a9e51f8e79fc55adc79355
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712019"
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a>Instrukcje: Dodawanie niepowiązanych kolumn do formantu DataGridView formularzy Windows powiązane z danymi
Dane wyświetlane w <xref:System.Windows.Forms.DataGridView> kontroli zwykle będą pochodzić z określonego rodzaju źródła danych, ale możesz chcieć wyświetlić kolumny danych, która nie pochodzi ze źródła danych. Tego rodzaju kolumny jest nazywany niepowiązanych kolumn. Niepowiązanych kolumn może mieć wiele form. Służą one często, aby zapewnić dostęp do szczegółów wiersza danych.  
  
 Poniższy przykład kodu demonstruje sposób tworzenia niepowiązanych kolumn z **szczegóły** przycisków, aby wyświetlić tabeli podrzędnej związane z określonego wiersza w tabeli nadrzędnej, gdy implementować scenariusza wzorzec/szczegół. Aby reagować na kliknięcia przycisku, zaimplementować <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> program obsługi zdarzeń, który wyświetla formularz zawierający tabeli podrzędnej.  
  
 Są obsługiwane dla tego zadania w programie Visual Studio.  Zobacz też [jak: Dodawanie i usuwanie kolumn w Windows Forms formantu DataGridView za pomocą projektanta](add-and-remove-columns-in-the-datagrid-using-the-designer.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.  
  
-   Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.DataGridView>
- [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)
