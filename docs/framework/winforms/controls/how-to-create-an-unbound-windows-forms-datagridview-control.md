---
title: 'Instrukcje: utworzenie niezwiązanej kontrolki DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
ms.assetid: b5d4b47d-9a28-4d88-9dba-0a3c90fba71d
ms.openlocfilehash: c488d0221080454a82e4c80f89964df0ee62f068
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591648"
---
# <a name="how-to-create-an-unbound-windows-forms-datagridview-control"></a>Instrukcje: utworzenie niezwiązanej kontrolki DataGridView formularzy systemu Windows
Poniższy przykład kodu pokazuje, jak wypełnić <xref:System.Windows.Forms.DataGridView> kontroli programowo bez powiązania go ze źródłem danych. Jest to przydatne, jeśli masz niewielką ilość danych, które mają być wyświetlane w formacie tabeli.  
  
 Aby uzyskać pełne wyjaśnienie ten przykład kodu, zobacz [instruktażu: Tworzenie Windows niezwiązanego formantu DataGridView formularzy](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [Przewodnik: Tworzenie Windows niezwiązanego formantu DataGridView formularzy](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)
