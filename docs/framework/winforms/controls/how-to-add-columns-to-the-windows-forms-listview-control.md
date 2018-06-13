---
title: 'Porady: dodawanie kolumn do formantu ListView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: 4c284e9d2798a1992e3152a85eca47c8d33bfde8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528292"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a>Porady: dodawanie kolumn do formantu ListView formularzy systemu Windows
W widoku szczegółów <xref:System.Windows.Forms.ListView> formant może wyświetlać wiele kolumn dla każdego elementu listy. Kolumny służy do wyświetlania użytkownikowi kilka typów informacji na temat każdego elementu listy. Na przykład można wyświetlić listę plików, nazwy pliku, typu pliku, rozmiar i datę ostatniej modyfikacji pliku. Aby dowiedzieć się, jak wypełnianie kolumn po ich utworzeniu, zobacz [porady: wyświetlanie podelementów w kolumnach za pomocą formantu ListView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
### <a name="to-add-columns-programmatically"></a>Aby dodać kolumny programowo  
  
1.  Ustawianie formantu <xref:System.Windows.Forms.ListView.View%2A> właściwości <xref:System.Windows.Forms.View.Details>.  
  
2.  Użyj <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> metody widok listy <xref:System.Windows.Forms.ListView.Columns%2A> właściwości.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ListView>  
 [Kontrolka ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [ListView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
