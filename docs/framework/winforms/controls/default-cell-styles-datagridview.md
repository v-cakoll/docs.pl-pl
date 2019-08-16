---
title: 'Instrukcje: ustawianie domyślnych stylów komórek i formatów danych dla kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
ms.openlocfilehash: 53faf31c8dd3be1606c491e95594c4aae5aedf98
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039669"
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>Instrukcje: ustawianie domyślnych stylów komórek i formatów danych dla kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant

<xref:System.Windows.Forms.DataGridView> Kontrolka umożliwia określenie domyślnych stylów komórek i formatów danych komórek dla całej kontrolki, dla określonych kolumn, nagłówków wierszy i kolumn, a w przypadku przemiennych wierszy, aby utworzyć efekt księgi. Domyślne style ustawione dla całego formantu są zastępowane przez domyślne style ustawione dla kolumn i przemiennych wierszy. Ponadto style ustawiane w kodzie dla poszczególnych wierszy i komórek przesłaniają domyślne style.

Aby uzyskać więcej informacji na temat stylów komórek, zobacz [style komórek w kontrolce DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md). Aby ustawić style dla przemiennych wierszy, [zobacz How to: Ustaw style przemiennych wierszy dla kontrolki DataGridView Windows Forms przy użyciu](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)narzędzia Projektant.

Możesz również ustawić style przy użyciu <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> właściwości, aby wpływać na wszystkie wiersze, które zostaną dodane do kontrolki. Aby uzyskać więcej informacji na temat szablonu wiersza, [zobacz How to: Użyj szablonu wiersza do dostosowania wierszy w kontrolce](use-the-row-template-to-customize-rows-in-the-datagrid.md)DataGridView Windows Forms.

Poniższe procedury wymagają projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.DataGridView> kontrolkę. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).


### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>Aby ustawić domyślne style dla wszystkich komórek w kontrolce

1. <xref:System.Windows.Forms.DataGridView> Wybierz kontrolkę w projektancie.

2. W oknie **Właściwości** ![kliknij przycisk wielokropka (przycisk wielokropka (...) w okno właściwości programu Visual Studio. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>](./media/visual-studio-ellipsis-button.png)) obok właściwości, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>, lub <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> . Zostanie wyświetlone okno dialogowe **Konstruktor komórek** .

3. Definiowanie stylu przez ustawienie właściwości przy użyciu okienka **podglądu** , aby potwierdzić wybór.

> [!NOTE]
> Jeśli style wizualizacji są włączone, nagłówki wierszy i kolumn (z wyjątkiem <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) są automatycznie wzorowane przez bieżący motyw, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> zastępując wartości właściwości i <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> .
>
> Można ustawić style komórek dla wielu zaznaczonych <xref:System.Windows.Forms.DataGridView> kontrolek przy użyciu projektanta, ale tylko wtedy, gdy mają identyczne wartości właściwości styl komórki, które chcesz zmodyfikować. Jeśli wszystkie style komórek różnią się w przypadku tej właściwości, okna dialogowe **Właściwości** **konstruktora komórek** będą puste.

### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>Aby ustawić domyślne style dla komórek w poszczególnych kolumnach

1. Kliknij prawym przyciskiem <xref:System.Windows.Forms.DataGridView> myszy formant w projektancie, a następnie wybierz polecenie **Edytuj kolumny**.

2. Wybierz kolumnę z listy **wybrane kolumny** .

3. W siatce **Właściwości kolumny** kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> właściwości. Zostanie wyświetlone okno dialogowe **Konstruktor komórek** .

4. Definiowanie stylu przez ustawienie właściwości przy użyciu okienka **podglądu** , aby potwierdzić wybór.

### <a name="to-format-data-in-cells"></a>Aby sformatować dane w komórkach

1. Użyj jednej z powyższych procedur, aby wyświetlić okno dialogowe **Konstruktor komórek** powiązane z domyślną właściwością stylu komórki.

2. W oknie dialogowym **Konstruktor komórek** kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> właściwości. Zostanie wyświetlone okno dialogowe **ciąg formatu** .

3. Wybierz typ formatu, a następnie zmodyfikuj szczegóły typu (na przykład liczbę miejsc dziesiętnych do wyświetlenia), używając pola przykładowego, aby potwierdzić wybór.

4. Jeśli powiążesz <xref:System.Windows.Forms.DataGridView> formant ze źródłem danych, które prawdopodobnie zawiera wartości null, Wypełnij pole tekstowe **wartość null** . Ta wartość jest wyświetlana, gdy wartość komórki jest równa odwołaniu o wartości`Nothing` null (w Visual Basic <xref:System.DBNull.Value?displayProperty=nameWithType>) lub.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: Ustawianie stylów wierszy przemiennych dla Windows Forms formantu DataGridView przy użyciu narzędzia Projektant](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)
- [Instrukcje: Tworzenie projektu aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: Dodawanie formantów do Windows Forms](how-to-add-controls-to-windows-forms.md)
