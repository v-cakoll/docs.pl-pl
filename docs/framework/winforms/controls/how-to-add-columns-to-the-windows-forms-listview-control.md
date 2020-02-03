---
title: Dodawanie kolumn do formantu ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: dd438ffbadddfc37ec9eb15e59a908bb58472a45
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744585"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a>Porady: dodawanie kolumn do formantu ListView formularzy systemu Windows
W widoku Szczegóły formant <xref:System.Windows.Forms.ListView> może wyświetlać wiele kolumn dla każdego elementu listy. Kolumny można używać do wyświetlania użytkownikowi kilku typów informacji na temat każdego elementu listy. Na przykład lista plików może zawierać nazwę pliku, typ pliku, rozmiar i datę ostatniej modyfikacji pliku. Aby uzyskać informacje dotyczące wypełniania kolumn po ich utworzeniu, zobacz [How to: Display SubItems in Columns with Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
### <a name="to-add-columns-programmatically"></a>Aby programowo dodać kolumny  
  
1. Ustaw właściwość <xref:System.Windows.Forms.ListView.View%2A> formantu na <xref:System.Windows.Forms.View.Details>.  
  
2. Użyj metody <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> właściwości <xref:System.Windows.Forms.ListView.Columns%2A> widoku listy.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView>
- [Kontrolka ListView](listview-control-windows-forms.md)
- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
