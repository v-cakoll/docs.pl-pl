---
title: Wiązanie obiektów z kontrolkami DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: d5aa5cb64c7fb2b82d69d6c87134ee901b84f5c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746703"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a>Porady: powiązanie obiektów z formantami DataGridView formularzy systemu Windows
Poniższy przykład kodu ilustruje sposób powiązania kolekcji obiektów z kontrolką <xref:System.Windows.Forms.DataGridView>, tak że każdy obiekt jest wyświetlany jako osobny wiersz. Ten przykład ilustruje również sposób wyświetlania właściwości z typem wyliczenia w <xref:System.Windows.Forms.DataGridViewComboBoxColumn> tak, aby lista rozwijana pola kombi zawierała wartości wyliczenia.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: uzyskiwanie dostępu do obiektów powiązanych z wierszami kontrolki DataGridView formularzy Windows Forms](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
