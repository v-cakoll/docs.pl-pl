---
title: Ustawianie domyślnych stylów komórek i formatów danych dla formantu DataGridView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
ms.openlocfilehash: ca602fa15e4648550bfa171a9c3abd057e930eca
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731360"
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>Porady: ustawianie domyślnych stylów komórek i formatów danych dla formantu DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant

Formant <xref:System.Windows.Forms.DataGridView> umożliwia określenie domyślnych stylów komórek i formatów danych komórek dla całej kontrolki, dla określonych kolumn, nagłówków wierszy i kolumn, a w przypadku przemiennych wierszy, aby utworzyć efekt księgi. Domyślne style ustawione dla całego formantu są zastępowane przez domyślne style ustawione dla kolumn i przemiennych wierszy. Ponadto style ustawiane w kodzie dla poszczególnych wierszy i komórek przesłaniają domyślne style.

Aby uzyskać więcej informacji na temat stylów komórek, zobacz [style komórek w kontrolce DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md). Aby ustawić style dla przemiennych wierszy, zobacz [How to: Set przemienne style wierszy dla formantu DataGridView Windows Forms przy użyciu narzędzia Projektant](set-alternating-row-styles-for-the-datagrid-using-the-designer.md).

Możesz również ustawić style przy użyciu właściwości <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>, aby wpływać na wszystkie wiersze, które zostaną dodane do kontrolki. Aby uzyskać więcej informacji na temat szablonu wiersza, zobacz [How to: use a Row Template by dostosowywanie wierszy w kontrolce DataGridView Windows Forms](use-the-row-template-to-customize-rows-in-the-datagrid.md).

Poniższe procedury wymagają projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGridView>. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>Aby ustawić domyślne style dla wszystkich komórek w kontrolce

1. Wybierz kontrolkę <xref:System.Windows.Forms.DataGridView> w projektancie.

2. W oknie **Właściwości** kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>lub <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>. Zostanie wyświetlone okno dialogowe **Konstruktor komórek** .

3. Definiowanie stylu przez ustawienie właściwości przy użyciu okienka **podglądu** , aby potwierdzić wybór.

> [!NOTE]
> Jeśli style wizualizacji są włączone, nagłówki wierszy i kolumn (z wyjątkiem <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) są automatycznie wzorowane według bieżącego motywu, zastępując wartości właściwości <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> i <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>.
>
> Można ustawić style komórek dla wielu zaznaczonych <xref:System.Windows.Forms.DataGridView> formantów przy użyciu projektanta, ale tylko wtedy, gdy mają identyczne wartości właściwości styl komórki, które chcesz zmodyfikować. Jeśli wszystkie style komórek różnią się w przypadku tej właściwości, okna dialogowe **Właściwości** **konstruktora komórek** będą puste.

### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>Aby ustawić domyślne style dla komórek w poszczególnych kolumnach

1. Kliknij prawym przyciskiem myszy formant <xref:System.Windows.Forms.DataGridView> w projektancie, a następnie wybierz polecenie **Edytuj kolumny**.

2. Wybierz kolumnę z listy **wybrane kolumny** .

3. W siatce **Właściwości kolumny** kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>. Zostanie wyświetlone okno dialogowe **Konstruktor komórek** .

4. Definiowanie stylu przez ustawienie właściwości przy użyciu okienka **podglądu** , aby potwierdzić wybór.

### <a name="to-format-data-in-cells"></a>Aby sformatować dane w komórkach

1. Użyj jednej z powyższych procedur, aby wyświetlić okno dialogowe **Konstruktor komórek** powiązane z domyślną właściwością stylu komórki.

2. W oknie dialogowym **Konstruktor komórek** kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>. Zostanie wyświetlone okno dialogowe **ciąg formatu** .

3. Wybierz typ formatu, a następnie zmodyfikuj szczegóły typu (na przykład liczbę miejsc dziesiętnych do wyświetlenia), używając pola **przykładowego** , aby potwierdzić wybór.

4. Jeśli powiążesz formant <xref:System.Windows.Forms.DataGridView> ze źródłem danych, które może zawierać wartości null, Wypełnij pole tekstowe **wartość null** . Ta wartość jest wyświetlana, gdy wartość komórki jest równa odwołaniu o wartości null (`Nothing` w Visual Basic) lub <xref:System.DBNull.Value?displayProperty=nameWithType>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: ustawianie przemiennych wierszy dla kontrolki DataGridView formularzy Windows Forms przy użyciu narzędzia Projektant](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)
- [Instrukcje: Tworzenie projektu aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md)
