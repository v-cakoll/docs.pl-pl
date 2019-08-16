---
title: 'Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
ms.openlocfilehash: d11c4f7e4cdfb597477bb99f38612ed648849f20
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040051"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy systemu Windows przy użyciu narzędzia Projektant

> [!NOTE]
> Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.DataGrid> do <xref:System.Windows.Forms.DataGrid> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.DataGridView> Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Dane można wyświetlić w kontrolce Windows Forms <xref:System.Windows.Forms.DataGrid> w tabelach i kolumnach, tworząc <xref:System.Windows.Forms.DataGridTableStyle> obiekty <xref:System.Windows.Forms.GridTableStylesCollection> i dodając je do obiektu <xref:System.Windows.Forms.DataGrid.TableStyles%2A> , do którego dostęp jest uzyskiwany <xref:System.Windows.Forms.DataGrid> za pomocą właściwości kontrolki. Każdy styl tabeli wyświetla zawartość dowolnej tabeli danych określonej we <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> właściwości. <xref:System.Windows.Forms.DataGridTableStyle> Domyślnie styl tabeli bez określonych stylów kolumn będzie wyświetlał wszystkie kolumny w tej tabeli danych. <xref:System.Windows.Forms.DataGridColumnStyle> Można ograniczyć <xref:System.Windows.Forms.GridColumnStylesCollection>, które kolumny tabeli są wyświetlane przez dodanie obiektów do obiektu, do <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> którego jest dostęp za pośrednictwem właściwości każdego <xref:System.Windows.Forms.DataGridTableStyle>z nich.

Poniższe procedury wymagają projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.DataGrid> kontrolkę. Aby uzyskać informacje na temat sposobu konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md). Domyślnie w programie Visual Studio 2005 <xref:System.Windows.Forms.DataGrid> formant nie znajduje się w **przyborniku**. Aby uzyskać informacje o dodawaniu, [zobacz How to: Dodaj elementy do przybornika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).

### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>Aby dodać tabelę do kontrolki DataGrid w projektancie

1. Aby wyświetlić dane w tabeli, należy najpierw powiązać <xref:System.Windows.Forms.DataGrid> formant z zestawem danych. Aby uzyskać więcej informacji, zobacz [jak: Powiąż formant DataGrid Windows Forms ze źródłem danych przy użyciu narzędzia Projektant](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md).

2. ![](./media/visual-studio-ellipsis-button.png)Wybierz właściwość <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid.TableStyles%2A> kontrolki w okno właściwości, a następnie kliknij przycisk wielokropka (przycisk wielokropka (...) w okno właściwości programu Visual Studio.) obok właściwości, aby wyświetlić **Edytor kolekcji element DataGridTableStyle**.

3. W edytorze kolekcji kliknij przycisk **Dodaj** , aby wstawić styl tabeli.

4. Kliknij przycisk **OK** , aby zamknąć Edytor kolekcji, a następnie otwórz go ponownie, klikając przycisk wielokropka obok <xref:System.Windows.Forms.DataGrid.TableStyles%2A> właściwości.

     Po ponownym otwarciu edytora kolekcji wszystkie tabele danych powiązane z formantem pojawią się na liście <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> rozwijanej właściwości stylu tabeli.

5. W polu **Członkowie** edytora kolekcji kliknij styl tabeli.

6. W polu **Właściwości** edytora kolekcji wybierz <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> wartość tabeli, która ma zostać wyświetlona.

### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>Aby dodać kolumnę do kontrolki DataGrid w projektancie

1. W polu **Członkowie** **edytora kolekcji element DataGridTableStyle**wybierz odpowiedni styl tabeli. W polu **Właściwości** edytora kolekcji wybierz <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> kolekcję, a następnie kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości, aby Wyświetl **Edytor kolekcji DataGridColumnStyle**.

2. W edytorze kolekcji kliknij przycisk **Dodaj** , aby wstawić styl kolumny, lub kliknij strzałkę w dół obok pozycji **Dodaj** , aby określić typ kolumny.

     W polu listy rozwijanej można wybrać <xref:System.Windows.Forms.DataGridTextBoxColumn> lub <xref:System.Windows.Forms.DataGridBoolColumn> typ.

3. Kliknij przycisk OK, aby zamknąć **Edytor kolekcji DataGridColumnStyle**, a następnie otwórz go ponownie, klikając przycisk wielokropka obok <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> właściwości.

     Po ponownym otwarciu edytora kolekcji wszystkie kolumny danych w powiązanej tabeli danych pojawią się na liście <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> rozwijanej właściwości stylu kolumny.

4. W polu **Członkowie** edytora kolekcji kliknij styl kolumny.

5. W polu **Właściwości** edytora kolekcji wybierz <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> wartość dla kolumny, która ma zostać wyświetlona.

## <a name="see-also"></a>Zobacz także

- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
- [Instrukcje: Usuwanie lub ukrywanie kolumn w kontrolce DataGrid Windows Forms](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
