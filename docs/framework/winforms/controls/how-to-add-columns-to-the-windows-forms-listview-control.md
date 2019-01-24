---
title: 'Instrukcje: Dodawanie kolumn do formantu ListView formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: eed032ec0bacd50666c30979b33362dabf00d565
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700198"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a>Instrukcje: Dodawanie kolumn do formantu ListView formularzy Windows
W widoku szczegółów <xref:System.Windows.Forms.ListView> formant może wyświetlić wiele kolumn dla każdego elementu listy. Można użyć kolumny do wyświetlania użytkownikowi kilka rodzajów informacji na temat każdego elementu listy. Na przykład można wyświetlić listę plików, nazwy pliku, typu pliku, rozmiar i Data ostatniej modyfikacji pliku. Aby dowiedzieć się, jak podczas wypełniania kolumn po ich utworzeniu, zobacz [jak: Wyświetlanie podelementów w kolumnach za pomocą Windows formantu ListView formularzy](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
### <a name="to-add-columns-programmatically"></a>Aby programowo dodać kolumny  
  
1.  Ustaw dla formantu <xref:System.Windows.Forms.ListView.View%2A> właściwość <xref:System.Windows.Forms.View.Details>.  
  
2.  Użyj <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> metoda widok listy <xref:System.Windows.Forms.ListView.Columns%2A> właściwości.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ListView>
- [Kontrolka ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
- [ListView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
