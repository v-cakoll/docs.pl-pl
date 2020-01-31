---
title: Uzyskiwanie dostępu do obiektów powiązanych z wierszami kontrolki DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 0b9a4becb78ae817141728467c1e9ea5b693476d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743165"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a>Porady: uzyskiwanie dostępu do obiektów powiązanych z wierszami formantu DataGridView formularzy systemu Windows
Czasami warto wyświetlić tabelę informacji przechowywanych w kolekcji obiektów biznesowych. Po powiązaniu formantu <xref:System.Windows.Forms.DataGridView> z taką kolekcją Każda właściwość publiczna jest wyświetlana we własnej kolumnie, chyba że właściwość została oznaczona jako nieumożliwia przeglądania z <xref:System.ComponentModel.BrowsableAttribute>. Na przykład kolekcja obiektów `Customer` powinna zawierać kolumny, takie jak **Nazwa** i **adres**.  
  
 Jeśli te obiekty zawierają dodatkowe informacje i kod, do których chcesz uzyskać dostęp, możesz dotrzeć do niego za poorednictwem obiektów wierszy. W poniższym przykładzie kodu użytkownicy mogą wybrać wiele wierszy i kliknąć przycisk, aby wysłać fakturę do każdego z odpowiednich klientów.  
  
### <a name="to-access-row-bound-objects"></a>Aby uzyskać dostęp do obiektów powiązanych z wierszem  
  
- Użyj właściwości <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a>Przykład  
 Pełny przykład kodu zawiera prostą implementację `Customer` i wiąże <xref:System.Windows.Forms.DataGridView> z <xref:System.Collections.ArrayList> zawierającą kilka `Customer` obiektów. Procedura obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> <xref:System.Windows.Forms.Button?displayProperty=nameWithType> musi uzyskiwać dostęp do obiektów `Customer` za pomocą wierszy, ponieważ kolekcja klienta nie jest dostępna poza programem obsługi zdarzeń <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: wiązanie obiektów z kontrolkami DataGridView formularzy Windows Forms](how-to-bind-objects-to-windows-forms-datagridview-controls.md)
