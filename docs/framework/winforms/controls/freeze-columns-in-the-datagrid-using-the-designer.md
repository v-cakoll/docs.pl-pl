---
title: 'Instrukcje: blokowanie kolumn w kontrolce DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
ms.openlocfilehash: 7ebdf7a1598ac3cd61005ae607e5bfbe7cb49059
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933719"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Instrukcje: blokowanie kolumn w kontrolce DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
Gdy użytkownicy wyświetlają dane w kontrolce <xref:System.Windows.Forms.DataGridView> Windows Forms, czasami muszą odwoływać się do pojedynczej kolumny lub zestawu kolumn często. Na przykład podczas wyświetlania tabeli informacji o kliencie, która zawiera wiele kolumn, warto wyświetlić nazwę klienta przez cały czas, jednocześnie włączając inne kolumny przewijane poza widocznym regionem.

 Aby osiągnąć takie zachowanie, można zablokować kolumny w kontrolce. Po zablokowaniu kolumny wszystkie kolumny po lewej stronie (lub po prawej stronie w skrypcie języka od prawej do lewej) również są zamrożone. Zablokowane kolumny pozostają na miejscu, gdy wszystkie inne kolumny można przewijać. W przypadku włączenia zmiany kolejności kolumn zablokowane kolumny są traktowane jako odrębne dla grupy z odblokowanych kolumn. Użytkownicy mogą zmieniać położenie kolumn w jednej grupie, ale nie mogą przenosić kolumn z jednej grupy do drugiej.

 Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.DataGridView> kontrolkę. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-freeze-a-column-using-the-designer"></a>Aby zablokować kolumnę przy użyciu narzędzia Projektant

1. Kliknij symbol taga inteligentnego (![tag inteligentny](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) w prawym górnym <xref:System.Windows.Forms.DataGridView> rogu kontrolki, a następnie wybierz pozycję **Edytuj kolumny**.

2. Wybierz kolumnę z listy **wybrane kolumny** .

3. W siatce **Właściwości kolumny** Ustaw <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> właściwość na `true`.

    > [!NOTE]
    > Można także zablokować kolumnę podczas dodawania, zaznaczając pole **zablokowane** w oknie dialogowym **Dodaj kolumnę** .

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- [Instrukcje: Dodawanie i usuwanie kolumn w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Włączanie zmiany kolejności kolumn w kontrolce DataGridView Windows Forms przy użyciu narzędzia Projektant](enable-column-reordering-in-the-datagrid-using-the-designer.md)
- [Instrukcje: Wyświetlanie tekstu od prawej do lewej w Windows Forms na potrzeby globalizacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))
- [Instrukcje: Tworzenie projektu aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: Dodawanie formantów do Windows Forms](how-to-add-controls-to-windows-forms.md)
