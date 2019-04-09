---
title: 'Instrukcje: ustawianie domyślnych stylów komórek i formatów danych dla kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
ms.openlocfilehash: 0e5664707d12fd45c73f3585d07660fc732965fb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179897"
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>Instrukcje: ustawianie domyślnych stylów komórek i formatów danych dla kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant
<xref:System.Windows.Forms.DataGridView> Dzięki kontroli Określ domyślnych stylów komórek i formatów danych dla całego kontrolki, w określonych kolumnach, dla nagłówków wierszy i kolumn i przemienne wiersze, aby utworzyć efekt księgi komórki. Domyślne style całego formantu są zastępowane przez domyślne style ustawiony dla kolumn i przemienne wiersze. Ponadto style, które można ustawić w kodzie, dla poszczególnych wierszy i komórek zastępują domyślne style.  
  
 Aby uzyskać więcej informacji na temat style komórki zobacz [style komórki w formancie DataGridView formularzy Windows](cell-styles-in-the-windows-forms-datagridview-control.md). Aby ustawić style wierszy zmiennych, zobacz [jak: Ustawianie przemiennych wierszy dla formantu DataGridView, które przy użyciu narzędzia Projektant formularzy Windows](set-alternating-row-styles-for-the-datagrid-using-the-designer.md).  
  
 Można również ustawić za pomocą stylów <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> właściwości wpływają na wszystkie wiersze, które zostaną dodane do formantu. Aby uzyskać więcej informacji na temat szablonu wiersza zobacz [jak: Użycie szablonu wiersza do dostosowania wierszy w formancie DataGridView formularzy Windows](use-the-row-template-to-customize-rows-in-the-datagrid.md).  
  
 Poniższe procedury wymagają **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.DataGridView> kontroli. Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>Aby Ustawianie domyślnych stylów dla wszystkich komórek w kontrolce  
  
1.  Wybierz <xref:System.Windows.Forms.DataGridView> formantu w projektancie.  
  
2.  W **właściwości** okna, kliknij przycisk oznaczony wielokropkiem (![VisualStudioEllipsesButton — zrzut ekranu](../media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>, lub <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> właściwości. **CellStyle Konstruktor —** pojawi się okno dialogowe.  
  
3.  Zdefiniuj styl przez ustawienie właściwości, za pomocą **(wersja zapoznawcza)** okienko, aby potwierdzić wybór.  
  
> [!NOTE]
>  Po włączeniu funkcji stylów wizualnych nagłówki wierszy i kolumn (z wyjątkiem <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) są automatycznie ich styl, bieżący motyw zastępowanie <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> i <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> wartości właściwości.  
>   
>  Możesz ustawić stylów komórki dla wielu zaznaczonych <xref:System.Windows.Forms.DataGridView> kontrolki przy użyciu projektanta, ale tylko wtedy, jeśli mają identyczne wartości właściwości stylu komórka, którą chcesz zmodyfikować. Jeśli wszystkie style komórki różnią się dla tej właściwości **właściwości** okien **CellStyle Konstruktor —** okno dialogowe będzie pusta.  
  
### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>Aby Ustawianie domyślnych stylów komórek w poszczególnych kolumnach  
  
1.  Kliknij prawym przyciskiem myszy <xref:System.Windows.Forms.DataGridView> formantu w projektancie, a następnie wybierz **Edytowanie kolumn**.  
  
2.  Wybierz kolumnę z **wybrane kolumny** listy.  
  
3.  W **właściwości kolumny** siatki, kliknij przycisk oznaczony wielokropkiem (![VisualStudioEllipsesButton — zrzut ekranu](../media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> właściwości. **CellStyle Konstruktor —** pojawi się okno dialogowe.  
  
4.  Zdefiniuj styl przez ustawienie właściwości, za pomocą **(wersja zapoznawcza)** okienko, aby potwierdzić wybór.  
  
### <a name="to-format-data-in-cells"></a>Aby sformatować dane w komórkach  
  
1.  Użyj jednej z powyższych procedur, aby wyświetlić **CellStyle Konstruktor —** okno dialogowe związane z domyślna właściwość style komórki.  
  
2.  W **CellStyle Konstruktor —** okna dialogowego pole i kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](../media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> Właściwość. **Ciąg formatu** pojawi się okno dialogowe.  
  
3.  Wybierz typ formatu, a następnie zmodyfikować szczegóły tego typu (takie jak liczba miejsc dziesiętnych do wyświetlenia), za pomocą **przykładowe** pole, aby potwierdzić wybór.  
  
4.  Jeśli dokonywane jest wiązanie <xref:System.Windows.Forms.DataGridView> formant ze źródłem danych, który może zawierać wartości null, wypełnij **wartości Null** pola tekstowego. Ta wartość jest wyświetlana, gdy wartość komórki jest odwołanie o wartości null (`Nothing` w języku Visual Basic) lub <xref:System.DBNull.Value?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>
- [Style komórki w formancie DataGridView formularzy systemu Windows](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: ustawianie przemiennych wierszy dla kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)
- [Instrukcje: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: dodawanie kontrolek do formularzy systemu Windows](how-to-add-controls-to-windows-forms.md)
