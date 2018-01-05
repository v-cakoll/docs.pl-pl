---
title: "Porady: blokowanie kolumn w formancie DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 049dd4952dc8af2c0f56567d8f2f53f5be5928ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Porady: blokowanie kolumn w formancie DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Gdy użytkownicy wyświetlać dane wyświetlane w formularzach systemu Windows <xref:System.Windows.Forms.DataGridView> kontroli, czasami muszą odwoływać się do jednej kolumny lub zestaw kolumn często. Na przykład podczas wyświetlania informacji klienta, który zawiera wiele kolumn tabeli, jest przydatne w przypadku można wyświetlić nazwę klienta przez cały czas podczas włączania obsługi innych kolumn przewinięcia poza region widoczny.  
  
 Aby osiągnąć ten problem, można zablokować kolumn w formancie. Po zablokowaniu kolumny zablokowanych również wszystkich kolumn po lewej stronie (lub po jego prawej stronie skrypty języka od prawej do lewej). Zablokowane kolumny pozostają bez zmian, gdy mogą być przewijane w innych kolumn. Jeśli włączono zmiany układu kolumn zablokowane kolumny są traktowane jako grupę różne od kolumny. Użytkownicy można zmienić kolumny w każdej grupie, ale nie może przenieść kolumny z jednej grupy, do drugiego.  
  
 Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.DataGridView> formantu. Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-freeze-a-column-using-the-designer"></a>Aby zablokować kolumnę przy użyciu narzędzia Projektant  
  
1.  Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> kontroli, a następnie wybierz **Edytowanie kolumn**.  
  
2.  Wybierz kolumny z **wybrane kolumny** listy.  
  
3.  W **właściwości kolumny** siatki, ustaw <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> właściwości `true`.  
  
    > [!NOTE]
    >  Możesz również zablokować kolumnę podczas dodawania go, wybierając **zablokowane** polu **Dodaj kolumnę** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>  
 [Instrukcje: dodawanie i usuwanie kolumn do kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [Instrukcje: włączanie zmiany układu kolumn w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 [Porady: wyświetlanie tekstu od prawej do lewej w formularzach systemu Windows dla globalizacji](http://msdn.microsoft.com/en-us/f0663385-2354-4c65-8676-706422283b14)  
 [Porady: Tworzenie projektu aplikacji systemu Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
