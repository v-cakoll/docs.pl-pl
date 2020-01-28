---
title: Dodawanie tabel i kolumn do kontrolki DataGrid przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
ms.openlocfilehash: fed7465fbe665b1945161653616e3a21640e0b2a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746262"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>Porady: dodawanie tabel i kolumn do formantu DataGrid formularzy systemu Windows przy użyciu narzędzia Projektant

> [!NOTE]
> Formant <xref:System.Windows.Forms.DataGridView> zamienia i dodaje funkcje do kontrolki <xref:System.Windows.Forms.DataGrid>; Niemniej jednak kontrolka <xref:System.Windows.Forms.DataGrid> jest zachowywana na potrzeby zgodności z poprzednimi wersjami i w przyszłości. Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Dane można wyświetlić w kontrolce <xref:System.Windows.Forms.DataGrid> Windows Forms w tabelach i kolumnach, tworząc <xref:System.Windows.Forms.DataGridTableStyle> obiekty i dodając je do obiektu <xref:System.Windows.Forms.GridTableStylesCollection>, do którego dostęp jest uzyskiwany za pomocą właściwości <xref:System.Windows.Forms.DataGrid> formantu <xref:System.Windows.Forms.DataGrid.TableStyles%2A>. Każdy styl tabeli wyświetla zawartość dowolnej tabeli danych określonej we właściwości <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> <xref:System.Windows.Forms.DataGridTableStyle>. Domyślnie styl tabeli bez określonych stylów kolumn będzie wyświetlał wszystkie kolumny w tej tabeli danych. Można określić, które kolumny tabeli mają być wyświetlane przez dodanie <xref:System.Windows.Forms.DataGridColumnStyle> obiektów do <xref:System.Windows.Forms.GridColumnStylesCollection>, do których dostęp odbywa się za pośrednictwem właściwości <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> każdego <xref:System.Windows.Forms.DataGridTableStyle>.

Poniższe procedury wymagają projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGrid>. Aby uzyskać informacje na temat sposobu konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md). Domyślnie w programie Visual Studio 2005 formant <xref:System.Windows.Forms.DataGrid> nie znajduje się w **przyborniku**. Aby uzyskać informacje o dodawaniu, zobacz [jak: dodać elementy do przybornika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).

### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>Aby dodać tabelę do kontrolki DataGrid w projektancie

1. Aby wyświetlić dane w tabeli, należy najpierw powiązać formant <xref:System.Windows.Forms.DataGrid> z zestawem danych. Aby uzyskać więcej informacji, zobacz [jak: powiązać formant DataGrid Windows Forms ze źródłem danych przy użyciu narzędzia Projektant](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md).

2. Wybierz właściwość <xref:System.Windows.Forms.DataGrid.TableStyles%2A> kontrolki <xref:System.Windows.Forms.DataGrid> w okno Właściwości, a następnie kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno Właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości, aby wyświetlić **Edytor kolekcji element DataGridTableStyle**.

3. W edytorze kolekcji kliknij przycisk **Dodaj** , aby wstawić styl tabeli.

4. Kliknij przycisk **OK** , aby zamknąć Edytor kolekcji, a następnie otwórz go ponownie, klikając przycisk wielokropka obok właściwości <xref:System.Windows.Forms.DataGrid.TableStyles%2A>.

     Po ponownym otwarciu edytora kolekcji wszystkie tabele danych powiązane z formantem pojawią się na liście rozwijanej właściwości <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> stylu tabeli.

5. W polu **Członkowie** edytora kolekcji kliknij styl tabeli.

6. W polu **Właściwości** edytora kolekcji wybierz wartość <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> dla tabeli, która ma być wyświetlana.

### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>Aby dodać kolumnę do kontrolki DataGrid w projektancie

1. W polu **Członkowie** **edytora kolekcji element DataGridTableStyle**wybierz odpowiedni styl tabeli. W polu **Właściwości** edytora kolekcji wybierz kolekcję <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>, a następnie kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości, aby wyświetlić **Edytor kolekcji DataGridColumnStyle**.

2. W edytorze kolekcji kliknij przycisk **Dodaj** , aby wstawić styl kolumny, lub kliknij strzałkę w dół obok pozycji **Dodaj** , aby określić typ kolumny.

     W polu listy rozwijanej można wybrać typ <xref:System.Windows.Forms.DataGridTextBoxColumn> lub <xref:System.Windows.Forms.DataGridBoolColumn>.

3. Kliknij przycisk OK, aby zamknąć **Edytor kolekcji DataGridColumnStyle**, a następnie otwórz go ponownie, klikając przycisk wielokropka obok właściwości <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>.

     Po ponownym otwarciu edytora kolekcji wszystkie kolumny danych w powiązanej tabeli danych pojawią się na liście rozwijanej właściwości <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> stylu kolumny.

4. W polu **Członkowie** edytora kolekcji kliknij styl kolumny.

5. W polu **Właściwości** edytora kolekcji wybierz wartość <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> dla kolumny, która ma zostać wyświetlona.

## <a name="see-also"></a>Zobacz także

- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
- [Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
