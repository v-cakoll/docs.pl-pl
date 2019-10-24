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
ms.openlocfilehash: b3a85f5f9e51dae50a40058b8f07f92976da66f2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "69666162"
---
# <a name="how-to-format-the-windows-forms-datagrid-control-using-the-designer"></a>Porady: formatowanie formantu DataGrid formularzy systemu Windows przy użyciu narzędzia Projektant

> [!NOTE]
> Formant <xref:System.Windows.Forms.DataGridView> zamienia i dodaje funkcje do kontrolki <xref:System.Windows.Forms.DataGrid>; Niemniej jednak kontrolka <xref:System.Windows.Forms.DataGrid> jest zachowywana na potrzeby zgodności z poprzednimi wersjami i w przyszłości. Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Zastosowanie różnych kolorów do różnych części formantu <xref:System.Windows.Forms.DataGrid> może pomóc w ułatwieniu odczytywania i interpretowania informacji. Kolor można zastosować do wierszy i kolumn. Wiersze i kolumny można także ukryć lub pokazać według własnego uznania.

Istnieją trzy podstawowe aspekty formatowania kontrolki <xref:System.Windows.Forms.DataGrid>:

- Można ustawić właściwości, aby określić domyślny styl, w którym są wyświetlane dane.

- Z tej bazy można następnie dostosować sposób wyświetlania niektórych tabel w czasie wykonywania.

- Na koniec można modyfikować, które kolumny są wyświetlane w siatce danych, a także kolory i inne wyświetlane formatowanie.

Jako pierwszy krok formatowania siatki danych można ustawić właściwości <xref:System.Windows.Forms.DataGrid> samego siebie. Opcje tego koloru i formatu stanowią podstawę, z której można wprowadzać zmiany w zależności od wyświetlanych tabel i kolumn danych.

Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGrid>. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md). W programie Visual Studio 2005 formant <xref:System.Windows.Forms.DataGrid> nie jest domyślnie w **przyborniku** . Aby uzyskać więcej informacji, zobacz [jak: dodać elementy do przybornika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).

### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Aby określić styl domyślny dla kontrolki DataGrid

1. Wybierz kontrolkę <xref:System.Windows.Forms.DataGrid>.

2. W oknie **Właściwości** ustaw następujące właściwości, zgodnie z potrzebami.

    |Właściwość|Opis|
    |--------------|-----------------|
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|Właściwość `BackColor` definiuje kolor wierszy z parzystymi numerami siatki. Po ustawieniu właściwości <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> na inny kolor, każdy inny wiersz jest ustawiany na ten nowy kolor (wiersze 1, 3, 5 itd.).|
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Kolor tła wierszy z parzystymi numerami siatki (wiersze 0, 2, 4, 6 itd.).|
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Natomiast właściwości <xref:System.Windows.Forms.DataGrid.BackColor%2A> i <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> określają kolor wierszy w siatce, właściwość <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> określa kolor obszaru poza obszarem wiersza, co jest widoczne tylko wtedy, gdy siatka jest przewijana do dołu lub w siatki.|
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Styl obramowania siatki, jedna z wartości <xref:System.Windows.Forms.BorderStyle> wyliczeniowych.|
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Kolor tła podpisu okna siatki, który pojawia się bezpośrednio nad siatką.|
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Czcionka napisu w górnej części siatki.|
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Kolor tła podpisu okna siatki.|
    |<xref:System.Windows.Forms.Control.Font%2A>|Czcionka używana do wyświetlania tekstu w siatce.|
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Kolor czcionki wyświetlanej przez dane w wierszach siatki danych.|
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Kolor linii siatki siatki danych.|
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Styl linii oddzielających komórki siatki, jedną z <xref:System.Windows.Forms.DataGridLineStyle> wartości wyliczenia.|
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Kolor tła nagłówków wierszy i kolumn.|
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Czcionka używana w nagłówkach kolumn.|
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Kolor pierwszego planu nagłówka kolumny siatki, włącznie z tekstem nagłówka kolumny i symbolami plus (+) i znakiem minus (-), które rozszerzają i zwijają wiersze po wyświetleniu wielu powiązanych tabel.|
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Kolor tekstu wszystkich łączy w siatce danych, w tym linki do tabel podrzędnych, nazwy relacji i tak dalej.|
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|W tabeli podrzędnej jest to kolor tła wierszy nadrzędnych.|
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|W tabeli podrzędnej jest to kolor pierwszego planu wierszy nadrzędnych.|
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Określa, czy nazwy tabel i kolumn są wyświetlane w wierszu nadrzędnym, za pomocą wyliczenia <xref:System.Windows.Forms.DataGridParentRowsLabelStyle>.|
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Domyślna szerokość (w pikselach) kolumn w siatce. Ustaw tę właściwość przed zresetowaniem <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości (oddzielnie albo za pomocą metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>) lub właściwość nie będzie mieć żadnego efektu.<br /><br /> Właściwość nie może być ustawiona na wartość mniejszą niż 0.|
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Wysokość wiersza (w pikselach) wierszy w siatce. Ustaw tę właściwość przed zresetowaniem <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości (oddzielnie albo za pomocą metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>) lub właściwość nie będzie mieć żadnego efektu.<br /><br /> Właściwość nie może być ustawiona na wartość mniejszą niż 0.|
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Szerokość nagłówków wierszy siatki.|
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Po wybraniu wiersza lub komórki jest to kolor tła.|
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Po wybraniu wiersza lub komórki jest to kolor pierwszego planu.|

    > [!NOTE]
    > Gdy dostosowujesz kolory formantów, istnieje możliwość, że kontrolka jest niedostępna ze względu na niewłaściwy wybór koloru (na przykład czerwony i zielony). Użyj kolorów dostępnych na palecie **kolorów systemu** , aby uniknąć tego problemu.

    Poniższa procedura wymaga, aby formant <xref:System.Windows.Forms.DataGrid> powiązany z tabelą danych. Aby uzyskać więcej informacji, zobacz [jak: powiązać formant DataGrid Windows Forms ze źródłem danych](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).

### <a name="to-set-the-table-and-column-style-of-a-data-table-at-design-time"></a>Aby ustawić styl tabeli i kolumny tabeli danych w czasie projektowania

1. Wybierz kontrolkę <xref:System.Windows.Forms.DataGrid> w formularzu.

2. W oknie **Właściwości** wybierz właściwość <xref:System.Windows.Forms.DataGrid.TableStyles%2A> i kliknij przycisk **wielokropka** (![The przycisk wielokropka (...) w okno Właściwości przycisku Visual Studio. ](./media/visual-studio-ellipsis-button.png)).

3. W oknie dialogowym **Edytor kolekcji element DataGridTableStyle** kliknij przycisk **Dodaj** , aby dodać styl tabeli do kolekcji.

     Za pomocą **edytora kolekcji element DataGridTableStyle**można dodawać i usuwać Style tabeli, ustawiać właściwości wyświetlania i układu oraz określać nazwę mapowania dla stylów tabeli.

4. Ustaw właściwość <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> na nazwę mapowania dla każdego stylu tabeli.

     Nazwa mapowania służy do określenia stylu tabeli, który ma być używany z tą tabelą.

5. W **edytorze kolekcji element DataGridTableStyle**wybierz właściwość <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> i kliknij przycisk wielokropka (![The przycisk wielokropka (...) w okno właściwości programu Visual Studio. ](./media/visual-studio-ellipsis-button.png)).

6. W oknie dialogowym **Edytor kolekcji DataGridColumnStyle** Dodaj Style kolumn do utworzonego stylu tabeli.

     Za pomocą **edytora kolekcji DataGridColumnStyle**można dodawać i usuwać Style kolumn, ustawiać właściwości wyświetlania i układu oraz ustawiać nazwę mapowania i ciągi formatowania dla kolumn danych.

    > [!NOTE]
    > Aby uzyskać więcej informacji na temat formatowania ciągów, zobacz [Typy formatowania](../../../standard/base-types/formatting-types.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
