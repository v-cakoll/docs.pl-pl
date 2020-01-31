---
title: Powiązywanie formantu DataGrid ze źródłem danych przy użyciu narzędzia Projektant
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
ms.openlocfilehash: cc0a74eca40e34f06b065980d25d922b919b0c3c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744088"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>Porady: powiązywanie formantu DataGrid formularzy systemu Windows ze źródłem danych przy użyciu narzędzia Projektant

> [!NOTE]
> Formant <xref:System.Windows.Forms.DataGridView> zamienia i dodaje funkcje do kontrolki <xref:System.Windows.Forms.DataGrid>; Niemniej jednak kontrolka <xref:System.Windows.Forms.DataGrid> jest zachowywana na potrzeby zgodności z poprzednimi wersjami i w przyszłości. Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

 Kontrolka <xref:System.Windows.Forms.DataGrid> Windows Forms jest przeznaczona specjalnie do wyświetlania informacji ze źródła danych. Formant można powiązać w czasie projektowania przez ustawienie właściwości <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> lub w czasie wykonywania przez wywołanie metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>. Mimo że można wyświetlać dane z różnych źródeł danych, najbardziej typowe źródła to zestawy danych i ich widoki.

 Jeśli źródło danych jest dostępne w czasie projektowania — na przykład, jeśli formularz zawiera wystąpienie zestawu danych lub widok danych — można powiązać siatkę ze źródłem danych w czasie projektowania. Następnie możesz wyświetlić podgląd danych, które będą wyglądały jak w siatce.

 Możesz również programowo powiązać siatkę w czasie wykonywania. Jest to przydatne, gdy chcesz ustawić źródło danych na podstawie informacji uzyskanych w czasie wykonywania. Na przykład aplikacja może pozwolić, aby użytkownik określił nazwę tabeli do wyświetlenia. Jest to również konieczne w sytuacjach, gdy źródło danych nie istnieje w czasie projektowania. Obejmuje to źródła danych, takie jak tablice, kolekcje, niewpisane zestawy danych i czytniki danych.

 Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.DataGrid>. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md). W programie Visual Studio 2005 formant <xref:System.Windows.Forms.DataGrid> nie jest domyślnie w **przyborniku** . Aby uzyskać informacje o dodawaniu, zobacz [jak: dodać elementy do przybornika](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)). Ponadto w programie Visual Studio 2005 można użyć okna **źródła danych** dla powiązania danych czasu projektowania. Aby uzyskać więcej informacji [, zobacz Powiązywanie kontrolek z danymi w programie Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).

## <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>Do danych — powiązywanie formantu DataGrid z pojedynczą tabelą w projektancie

1. Ustaw właściwość <xref:System.Windows.Forms.DataGrid.DataSource%2A> kontrolki na obiekt zawierający elementy danych, do których chcesz utworzyć powiązanie.

2. Jeśli źródłem danych jest zestaw danych, ustaw właściwość <xref:System.Windows.Forms.DataGrid.DataMember%2A> na nazwę tabeli, z którą ma zostać utworzone powiązanie.

3. Jeśli źródłem danych jest zestaw danych lub widok danych oparty na tabeli zestawu danych, Dodaj kod do formularza, aby wypełnić zestaw danych.

     Dokładny kod, którego używasz, zależy od tego, gdzie zestaw danych pobiera dane. Jeśli zestaw danych jest wypełniany bezpośrednio z bazy danych, zazwyczaj wywoływana jest metoda `Fill` adaptera danych, tak jak w poniższym przykładzie kodu, który wypełnia zestaw danych o nazwie `DsCategories1`:

    ```vb
    sqlDataAdapter1.Fill(DsCategories1)
    ```

    ```csharp
    sqlDataAdapter1.Fill(DsCategories1);
    ```

    ```cpp
    sqlDataAdapter1->Fill(dsCategories1);
    ```

4. Obowiązkowe Dodaj odpowiednie style tabeli i Style kolumn do siatki.

     Jeśli nie ma żadnych stylów tabeli, zostanie wyświetlona tabela, ale z minimalnym formatowaniem i wszystkimi kolumnami widocznymi.

## <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a>Do danych — powiązywanie formantu DataGrid z wieloma tabelami w zestawie danych w projektancie

1. Ustaw właściwość <xref:System.Windows.Forms.DataGrid.DataSource%2A> kontrolki na obiekt zawierający elementy danych, do których chcesz utworzyć powiązanie.

2. Jeśli zestaw danych zawiera powiązane tabele (czyli jeśli zawiera obiekt relacji), ustaw właściwość <xref:System.Windows.Forms.DataGrid.DataMember%2A> na nazwę tabeli nadrzędnej.

3. Napisz kod, aby wypełnić zestaw danych.

## <a name="see-also"></a>Zobacz także

- [DataGrid, kontrolka — omówienie](datagrid-control-overview-windows-forms.md)
- [Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
- [Wiązanie danych formularzy Windows Forms](../windows-forms-data-binding.md)
- [Uzyskiwanie dostępu do danych w programie Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)
