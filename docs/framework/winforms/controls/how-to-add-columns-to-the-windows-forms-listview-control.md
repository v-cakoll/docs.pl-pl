---
title: Dodawanie kolumn do formantu ListView
description: Dowiedz się, jak dodać kolumny do kontrolki ListView Windows Forms, aby wyświetlić kilka typów informacji na temat każdego elementu listy.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: 7ca4e86ca3a9679876f2525c49596534f175096a
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174565"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a>Porady: dodawanie kolumn do formantu ListView formularzy systemu Windows
W widoku szczegółów <xref:System.Windows.Forms.ListView> kontrolka może wyświetlić wiele kolumn dla każdego elementu listy. Kolumny można używać do wyświetlania użytkownikowi kilku typów informacji na temat każdego elementu listy. Na przykład lista plików może zawierać nazwę pliku, typ pliku, rozmiar i datę ostatniej modyfikacji pliku. Aby uzyskać informacje dotyczące wypełniania kolumn po ich utworzeniu, zobacz [How to: Display SubItems in Columns with Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
### <a name="to-add-columns-programmatically"></a>Aby programowo dodać kolumny  
  
1. Ustaw właściwość kontrolki <xref:System.Windows.Forms.ListView.View%2A> na wartość <xref:System.Windows.Forms.View.Details> .  
  
2. Użyj <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> metody właściwości widoku listy <xref:System.Windows.Forms.ListView.Columns%2A> .  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.ListView>
- [ListView — Formant](listview-control-windows-forms.md)
- [ListView — Informacje o formancie](listview-control-overview-windows-forms.md)
