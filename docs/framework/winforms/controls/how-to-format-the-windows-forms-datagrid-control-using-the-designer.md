---
title: 'Porady: formatowanie formantu DataGrid formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], DataGrid controls
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: 533b9814-6124-49dc-9fda-085f1502609f
ms.openlocfilehash: e0d703e16ab89243c7f7cf57dc858a0a3889a590
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389024"
---
# <a name="how-to-format-the-windows-forms-datagrid-control-using-the-designer"></a>Porady: formatowanie formantu DataGrid formularzy systemu Windows przy użyciu narzędzia Projektant
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Stosowanie różnych kolorów do różnych części <xref:System.Windows.Forms.DataGrid> kontroli może pomóc w ułatwienia informacje w nim odczytać i zinterpretować. Kolor może być stosowany do wierszy i kolumn. Wiersze i kolumny można również ukryte lub pokazane według uznania.  
  
 Istnieją trzy podstawowe aspekty formatowania <xref:System.Windows.Forms.DataGrid> sterowania:  
  
-   Można ustawić właściwości, aby ustanowić domyślnego stylu, w którym dane są wyświetlane.  
  
-   Z tego podstawowego można następnie dostosować sposób wyświetlania niektórych tabel w czasie wykonywania.  
  
-   Na koniec można zmodyfikować kolumny, które są wyświetlane w siatce danych, a także kolory i inne formatowania, które są wyświetlane.  
  
 Na etapie wstępnym w formatowaniu siatce danych, można ustawić właściwości <xref:System.Windows.Forms.DataGrid> sam. Te opcje kolor i format tworzą podstawowy, z którego można następnie wprowadzić zmiany w zależności od danych w tabelach i wyświetlane kolumny.  
  
 Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.DataGrid> kontroli. Uzyskać informacji o konfigurowaniu taki projekt, zobacz [jak: Tworzenie projektu aplikacji Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). W [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], <xref:System.Windows.Forms.DataGrid> formantu nie znajduje się w **przybornika** domyślnie. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie elementów do przybornika](https://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Ustanowienie domyślnego stylu dla formantu DataGrid  
  
1.  Wybierz <xref:System.Windows.Forms.DataGrid> kontroli.  
  
2.  W **właściwości** okna, ustaw następujące właściwości, zgodnie z potrzebami.  
  
    |Właściwość|Opis|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|`BackColor` Właściwość definiuje kolor wierszach parzystych siatki. Po ustawieniu <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> na inny kolor, co drugi wiersz jest właściwością ten nowy kolor (wiersze, 1, 3, 5 i tak dalej).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Kolor tła wierszy parzystych siatki (wiersze, 0, 2, 4, 6 i tak dalej).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Natomiast <xref:System.Windows.Forms.DataGrid.BackColor%2A> i <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> właściwości określa kolor wierszy w siatce, <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> właściwość określa kolor obszaru spoza obszaru wiersza, która jest widoczna tylko podczas siatki jest przewijane do dolnej lub jeśli istnieją tylko kilka wierszy zawarte w siatce.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Styl obramowania siatki, jeden z <xref:System.Windows.Forms.BorderStyle> wartości wyliczenia.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Kolor tła tytuł okna siatki, które natychmiast pojawi się powyżej siatki.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Czcionka napisów u góry strony siatki.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Kolor tła tytuł okna siatki.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|Czcionka używana do wyświetlania tekstu w siatce.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Kolor czcionki wyświetlanej przez dane w wiersze siatki danych.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Kolor linii siatki w siatce danych.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Styl linii rozdzielających komórek siatki, jeden z <xref:System.Windows.Forms.DataGridLineStyle> wartości wyliczenia.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Kolor tła w nagłówkach wierszy i kolumn.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Czcionka używana w nagłówkach kolumn.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Kolor pierwszego planu nagłówków kolumn siatki, w tym tekst nagłówka kolumny, znak plus (+) i znak minus (-) symbole, rozwijanie i zwijanie wierszy, gdy wiele powiązanych tabel, które są wyświetlane.|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Kolor tekstu wszystkie linki w siatce danych, w tym łącza do tabele podrzędne, Nazwa relacji i tak dalej.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|W tabeli podrzędnej jest to kolor tła wierszy nadrzędnych.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|W tabeli podrzędnej jest to kolor pierwszego planu wierszy nadrzędnych.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Określa, czy nazwy tabel i kolumn są wyświetlane w wierszu nadrzędnym, przez <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> wyliczenia.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Domyślna szerokość (w pikselach) kolumny w siatce. Ustaw tę właściwość przed zresetowaniem <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości (albo oddzielnie, lub za pomocą <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda), lub właściwość nie odniesie żadnego skutku.<br /><br /> Nie można ustawić właściwość na wartość mniejszą niż 0.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Wysokość wiersza (w pikselach) wierszy w siatce. Ustaw tę właściwość przed zresetowaniem <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości (albo oddzielnie, lub za pomocą <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metoda), lub właściwość nie odniesie żadnego skutku.<br /><br /> Nie można ustawić właściwość na wartość mniejszą niż 0.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Szerokość nagłówki wierszy siatki.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Po zaznaczeniu wiersza lub komórki jest to kolor tła.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Po zaznaczeniu wiersza lub komórki jest to kolor pierwszego planu.|  
  
    > [!NOTE]
    >  Podczas dostosowywania kolory kontrolek jest możliwe formant stał się niedostępny z powodu niskiej wyboru (na przykład czerwonego i zielonego). Użyj kolorów, które są dostępne na **kolory systemowe** palety, aby uniknąć tego problemu.  
  
     Poniższa procedura wymaga <xref:System.Windows.Forms.DataGrid> formant powiązany z tabelą danych. Aby uzyskać więcej informacji, zobacz [porady: powiązywanie formantu DataGrid formularzy Windows ze źródłem danych](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-at-design-time"></a>Aby ustawić styl tabel i kolumn w tabeli danych w czasie projektowania  
  
1.  Wybierz <xref:System.Windows.Forms.DataGrid> kontrolkę w formularzu.  
  
2.  W **właściwości** wybierz <xref:System.Windows.Forms.DataGrid.TableStyles%2A> właściwości i kliknij przycisk **wielokropka** (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) przycisku.  
  
3.  W **Edytor kolekcji Element DataGridTableStyle** okno dialogowe, kliknij przycisk **Dodaj** dodać styl tabeli do kolekcji.  
  
     Za pomocą **Edytor kolekcji Element DataGridTableStyle**, można dodawać i Usuń style tabeli, wyświetlania zestawu i właściwości układu oraz zestaw mapowanie nazwy style tabeli.  
  
4.  Ustaw <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> właściwość na nazwę mapowania dla każdego stylu tabeli.  
  
     Nazwa mapowania służy do określania stylu tabeli powinien być używany z tabeli, która.  
  
5.  W **Edytor kolekcji Element DataGridTableStyle**, wybierz opcję <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> właściwości i kliknij przycisk oznaczony wielokropkiem (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton ")).  
  
6.  W **DataGridColumnStyle — Edytor kolekcji** okna dialogowego Dodaj style kolumn do styl tabeli został utworzony.  
  
     Za pomocą **DataGridColumnStyle — Edytor kolekcji**, możesz dodać i usunąć style kolumn, ustaw właściwości wyświetlania i układ i ustaw nazwę mapowania i ciągi formatowania danych kolumny.  
  
    > [!NOTE]
    >  Aby uzyskać więcej informacji na temat formatowania ciągów, zobacz [typy formatowania](../../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.GridTableStylesCollection>  
 <xref:System.Windows.Forms.GridColumnStylesCollection>  
 <xref:System.Windows.Forms.DataGrid>  
 [Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [DataGrid, kontrolka](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
