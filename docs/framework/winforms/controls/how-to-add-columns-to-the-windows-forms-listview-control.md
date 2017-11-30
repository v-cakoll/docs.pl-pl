---
title: 'Porady: dodawanie kolumn do formantu ListView formularzy systemu Windows'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8df87e62e8c19ee6e30ffdbc2a4e473b444f538
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [ListView — formant](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Informacje o formancie ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
