---
title: 'Porady: blokowanie kolumn w formancie DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
ms.openlocfilehash: d03355dbf7f8b9025e7d86e9930c6b96567b6b7d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420020"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Porady: blokowanie kolumn w formancie DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Gdy użytkownicy wyświetlają dane wyświetlane w formularzach Windows <xref:System.Windows.Forms.DataGridView> kontrolki, czasami muszą odwoływać się do pojedynczej kolumny lub zestaw kolumn, często. Na przykład podczas wyświetlania spisu informacje o kliencie, który zawiera wiele kolumn jest przydatny do wyświetlania nazwy klientów przez cały czas podczas włączania innych kolumn w celu przewiń poza regionem widoczne.  
  
 Aby uzyskać takie zachowanie, można zablokować kolumn w formancie. Po zablokowaniu kolumny, również są zablokowane wszystkie kolumny po lewej stronie (lub po jego prawej stronie skrypty języka od prawej do lewej). Zamrożone kolumny pozostaną w miejscu, a wszystkie pozostałe kolumny można przewijać. Jeśli zmiany układu kolumn jest włączona, Zablokowane kolumny są traktowane jako różne od kolumny grupy. Użytkownicy mogą zmienić położenie kolumn w każdej grupie, ale kolumna nie może przenieść z jednej grupy do drugiego.  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.DataGridView> kontroli. Uzyskać informacji o konfigurowaniu taki projekt, zobacz [jak: Tworzenie projektu aplikacji Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-freeze-a-column-using-the-designer"></a>Aby zablokować kolumnę przy użyciu narzędzia Projektant  
  
1.  Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> sterowania, a następnie wybierz **Edytowanie kolumn**.  
  
2.  Wybierz kolumnę z **wybrane kolumny** listy.  
  
3.  W **właściwości kolumny** siatki, ustaw <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> właściwość `true`.  
  
    > [!NOTE]
    >  Możesz również zablokować kolumnę podczas dodawania go, wybierając **Frozen** pole w **Dodaj kolumnę** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>  
 [Instrukcje: dodawanie i usuwanie kolumn do kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [Instrukcje: włączanie zmiany układu kolumn w kontrolce DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 [Porady: wyświetlanie tekstu od prawej do lewej w formularzach Windows Forms dla globalizacji](https://msdn.microsoft.com/library/f0663385-2354-4c65-8676-706422283b14)  
 [Porady: Tworzenie projektu aplikacji Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
