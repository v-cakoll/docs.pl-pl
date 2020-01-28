---
title: Dodawanie niepowiązanej kolumny do kontrolki DataGridView powiązanej z danymi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
ms.openlocfilehash: 807bbc121f33c35d70068571e76637c078ecb3da
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747063"
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a>Porady: dodawanie niepowiązanych kolumn do powiązanego z danymi formantu DataGridView formularzy systemu Windows
Dane wyświetlane w formancie <xref:System.Windows.Forms.DataGridView> zwykle pochodzą ze źródła danych pewnego rodzaju, ale może być konieczne wyświetlenie kolumny danych, które nie pochodzą ze źródła danych. Ten rodzaj kolumny nosi nazwę kolumny niepowiązanej. Kolumny niepowiązane mogą przyjmować wiele form. Często są one używane do zapewnienia dostępu do szczegółów wiersza danych.  
  
 Poniższy przykład kodu demonstruje sposób tworzenia niepowiązanej kolumny **szczegółów** , aby wyświetlić tabelę podrzędną powiązaną z określonym wierszem w tabeli nadrzędnej podczas implementowania scenariusza wzorzec/szczegóły. Aby reagować na kliknięcia przycisku, zaimplementuj procedurę obsługi zdarzeń <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>, która wyświetla formularz zawierający tabelę podrzędną.  
  
 To zadanie jest obsługiwane w programie Visual Studio.  Zobacz również [instrukcje: Dodawanie i usuwanie kolumn w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](add-and-remove-columns-in-the-datagrid-using-the-designer.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.  
  
- Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)
