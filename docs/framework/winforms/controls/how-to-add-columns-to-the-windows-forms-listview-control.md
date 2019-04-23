---
title: 'Instrukcje: dodawanie kolumn do kontrolki ListView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: 5c87d43513f2125945145445c61f689cdd9d2aaf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345745"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a>Instrukcje: dodawanie kolumn do kontrolki ListView formularzy systemu Windows
W widoku szczegółów <xref:System.Windows.Forms.ListView> formant może wyświetlić wiele kolumn dla każdego elementu listy. Można użyć kolumny do wyświetlania użytkownikowi kilka rodzajów informacji na temat każdego elementu listy. Na przykład można wyświetlić listę plików, nazwy pliku, typu pliku, rozmiar i Data ostatniej modyfikacji pliku. Aby dowiedzieć się, jak podczas wypełniania kolumn po ich utworzeniu, zobacz [jak: Wyświetlanie podelementów w kolumnach za pomocą Windows formantu ListView formularzy](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
### <a name="to-add-columns-programmatically"></a>Aby programowo dodać kolumny  
  
1. Ustaw dla formantu <xref:System.Windows.Forms.ListView.View%2A> właściwość <xref:System.Windows.Forms.View.Details>.  
  
2. Użyj <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> metoda widok listy <xref:System.Windows.Forms.ListView.Columns%2A> właściwości.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView>
- [Kontrolka ListView](listview-control-windows-forms.md)
- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
