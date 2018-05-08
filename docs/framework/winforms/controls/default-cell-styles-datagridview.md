---
title: 'Porady: ustawianie domyślnych stylów komórek i formatów danych dla formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
ms.openlocfilehash: 47e15afe71ed3497b634e965c96badcee2fe3ed4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>Porady: ustawianie domyślnych stylów komórek i formatów danych dla formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
<xref:System.Windows.Forms.DataGridView> Kontroli pozwala określić domyślnych stylów komórek i formatów danych dla całego formantu dla określonych kolumn, dla nagłówków wierszy i kolumn i naprzemiennych wierszach utworzyć efekt księgi komórki. Domyślne style całego formantu są zastępowane przez domyślne style ustawione dla przemiennych wierszy i kolumn. Ponadto style, które można ustawić w kodzie dla poszczególnych wierszy i komórek zastępują domyślne style.  
  
 Aby uzyskać więcej informacji na temat style komórki, zobacz [style komórki w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md). Aby ustawić style wierszy zmiennych, zobacz [porady: Ustawianie zmiennych style wierszy dla systemu Windows Forms DataGridView formantu przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md).  
  
 Można również ustawić za pomocą stylów <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> właściwość wpływ na wszystkie wiersze, które zostaną dodane do formantu. Aby uzyskać więcej informacji o szablonie wiersza, zobacz [porady: użycie szablonu wiersza do dostosowania wierszy w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md).  
  
 Wykonanie poniższych procedur wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.DataGridView> formantu. Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>Aby ustawić domyślne style dla wszystkich komórek w formancie  
  
1.  Wybierz <xref:System.Windows.Forms.DataGridView> kontroli w projektancie.  
  
2.  W **właściwości** okna, kliknij przycisk oznaczony wielokropkiem (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>, lub <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> właściwości. **Konstruktora elementu CellStyle** zostanie wyświetlone okno dialogowe.  
  
3.  Zdefiniuj styl przez ustawienie właściwości, za pomocą **Podgląd** okienko, aby uzgodnić wybrane opcje.  
  
> [!NOTE]
>  Jeżeli style wizualne są włączone, nagłówki wierszy i kolumn (z wyjątkiem <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) są automatycznie wstawiony przez bieżący motyw zastępowanie <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> i <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> wartości właściwości.  
>   
>  Można ustawić stylów komórki dla wielu zaznaczonych <xref:System.Windows.Forms.DataGridView> steruje przy użyciu projektanta, ale tylko wtedy, gdy mają identyczne wartości właściwości stylu komórki, który chcesz zmodyfikować. Jeśli wszystkie style komórki są różne dla tej właściwości **właściwości** systemu windows z **konstruktora elementu CellStyle** okno dialogowe będzie puste.  
  
### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>Aby ustawić domyślnych stylów komórek w poszczególnych kolumn  
  
1.  Kliknij prawym przyciskiem myszy <xref:System.Windows.Forms.DataGridView> kontroli w Projektancie i wybierz **Edytowanie kolumn**.  
  
2.  Wybierz kolumny z **wybrane kolumny** listy.  
  
3.  W **właściwości kolumny** siatki, kliknij przycisk oznaczony wielokropkiem (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> właściwości. **Konstruktora elementu CellStyle** zostanie wyświetlone okno dialogowe.  
  
4.  Zdefiniuj styl przez ustawienie właściwości, za pomocą **Podgląd** okienko, aby uzgodnić wybrane opcje.  
  
### <a name="to-format-data-in-cells"></a>Aby sformatować dane w komórkach  
  
1.  Użyj jednej z powyższych procedur do wyświetlenia **konstruktora elementu CellStyle** okno dialogowe związane z domyślnej właściwości stylu komórki.  
  
2.  W **konstruktora elementu CellStyle** oknie dialogowym kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> Właściwość. **Ciąg formatu** zostanie wyświetlone okno dialogowe.  
  
3.  Wybierz typ formatu, a następnie zmodyfikuj szczegóły typu (np. liczbę miejsc dziesiętnych do wyświetlenia), za pomocą **próbki** pole, aby uzgodnić wybrane opcje.  
  
4.  Są wiązane <xref:System.Windows.Forms.DataGridView> formantu ze źródłem danych, która może zawierać wartości null, wypełnij **wartości Null** pola tekstowego. Ta wartość jest wyświetlana, gdy wartość komórki jest odwołanie o wartości null (`Nothing` w języku Visual Basic) lub <xref:System.DBNull.Value?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>  
 [Style komórki w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Instrukcje: ustawianie przemiennych wierszy dla kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 [Porady: Tworzenie projektu aplikacji systemu Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
