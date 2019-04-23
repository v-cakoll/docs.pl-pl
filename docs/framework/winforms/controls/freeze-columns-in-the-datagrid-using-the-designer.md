---
title: 'Instrukcje: blokowanie kolumn w kontrolce DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
ms.openlocfilehash: 397a2c5a7879be8c1bef7e04e72cf675f25d0fb8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344315"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Instrukcje: blokowanie kolumn w kontrolce DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Gdy użytkownicy wyświetlają dane wyświetlane w formularzach Windows <xref:System.Windows.Forms.DataGridView> kontrolki, czasami muszą odwoływać się do pojedynczej kolumny lub zestaw kolumn, często. Na przykład podczas wyświetlania spisu informacje o kliencie, który zawiera wiele kolumn jest przydatny do wyświetlania nazwy klientów przez cały czas podczas włączania innych kolumn w celu przewiń poza regionem widoczne.  
  
 Aby uzyskać takie zachowanie, można zablokować kolumn w formancie. Po zablokowaniu kolumny, również są zablokowane wszystkie kolumny po lewej stronie (lub po jego prawej stronie skrypty języka od prawej do lewej). Zamrożone kolumny pozostaną w miejscu, a wszystkie pozostałe kolumny można przewijać. Jeśli zmiany układu kolumn jest włączona, Zablokowane kolumny są traktowane jako różne od kolumny grupy. Użytkownicy mogą zmienić położenie kolumn w każdej grupie, ale kolumna nie może przenieść z jednej grupy do drugiego.  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.DataGridView> kontroli. Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-freeze-a-column-using-the-designer"></a>Aby zablokować kolumnę przy użyciu narzędzia Projektant  
  
1. Kliknij symbol tagu inteligentnego (![symbol tagu inteligentnego](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym rogu <xref:System.Windows.Forms.DataGridView> sterowania, a następnie wybierz **Edytowanie kolumn**.  
  
2. Wybierz kolumnę z **wybrane kolumny** listy.  
  
3. W **właściwości kolumny** siatki, ustaw <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> właściwość `true`.  
  
    > [!NOTE]
    >  Możesz również zablokować kolumnę podczas dodawania go, wybierając **Frozen** pole w **Dodaj kolumnę** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- [Instrukcje: Dodawanie i usuwanie kolumn w formancie DataGridView formularzy Windows przy użyciu narzędzia Projektant](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Włączanie zmiany układu kolumn w formancie DataGridView formularzy Windows przy użyciu narzędzia Projektant](enable-column-reordering-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Wyświetlanie tekstu od prawej do lewej w formularzach Windows Forms dla globalizacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))
- [Instrukcje: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md)
