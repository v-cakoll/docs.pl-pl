---
title: Jak implementuj walidację za pomocą formantu DataGrid
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], validation
- validation [WPF], DataGrid
ms.assetid: ec6078a8-1e42-4648-b414-f4348e81bda1
ms.openlocfilehash: 38b4c9cd7679f0d8da9b18fb5bd6bb729d33ed54
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646098"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Jak implementuj walidację za pomocą formantu DataGrid
Formant <xref:System.Windows.Controls.DataGrid> umożliwia wykonywanie sprawdzania poprawności na poziomie komórki i wiersza. Za pomocą sprawdzania poprawności na poziomie komórki można sprawdzić poprawność poszczególnych właściwości obiektu danych powiązanych, gdy użytkownik aktualizuje wartość. Sprawdzanie poprawności na poziomie wiersza umożliwia sprawdzanie poprawności całych obiektów danych, gdy użytkownik zatwierdza zmiany w wierszu. Można również dostarczyć dostosowane wizualne opinie o błędach sprawdzania poprawności <xref:System.Windows.Controls.DataGrid> lub użyć domyślnej wizualnej opinii, która zapewnia formant.  
  
 W poniższych procedurach opisano <xref:System.Windows.Controls.DataGrid> sposób stosowania reguł sprawdzania poprawności do powiązań i dostosowywania wizualnej opinii.  
  
### <a name="to-validate-individual-cell-values"></a>Aby sprawdzić poprawność poszczególnych wartości komórek  
  
- Określ jedną lub więcej reguł sprawdzania poprawności dla powiązania używanego z kolumną. Jest to podobne do sprawdzania poprawności danych w prostych formantach, zgodnie z opisem w [omówieniu powiązania danych](../../../desktop-wpf/data/data-binding-overview.md).  
  
     W poniższym <xref:System.Windows.Controls.DataGrid> przykładzie przedstawiono formant z czterema kolumnami powiązanymi z różnymi właściwościami obiektu biznesowego. Trzy kolumny określają, <xref:System.Windows.Controls.ExceptionValidationRule> ustawiając <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> właściwość `true`na .  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Gdy użytkownik wprowadzi nieprawidłową wartość (taką jak liczba nieokreślona w kolumnie Identyfikator kursu), wokół komórki pojawi się czerwone obramowanie. Tę domyślną opinię zwrotną sprawdzania poprawności można zmienić zgodnie z opisem w poniższej procedurze.  
  
### <a name="to-customize-cell-validation-feedback"></a>Aby dostosować opinię o weryfikacji komórek  
  
- Ustaw <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> właściwość kolumny na styl odpowiedni dla formantu edycji kolumny. Ponieważ formanty edycji są tworzone w <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> czasie wykonywania, nie można użyć dołączonej właściwości, tak jak w przypadku prostych formantów.  
  
     Poniższy przykład aktualizuje poprzedni przykład, dodając styl błędu udostępniony przez trzy kolumny z regułami sprawdzania poprawności. Gdy użytkownik wprowadzi nieprawidłową wartość, styl zmienia kolor tła komórki i dodaje etykietę narzędzia. Należy zwrócić uwagę na użycie wyzwalacza, aby ustalić, czy występuje błąd sprawdzania poprawności. Jest to wymagane, ponieważ obecnie nie ma dedykowanego szablonu błędu dla komórek.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Można zaimplementować bardziej <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> rozbudowane dostosowanie, zastępując używane przez kolumnę.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>Aby sprawdzić poprawność wielu wartości w jednym wierszu  
  
1. Zaimplementuj podklasę, <xref:System.Windows.Controls.ValidationRule> która sprawdza wiele właściwości obiektu danych powiązanych. W <xref:System.Windows.Controls.ValidationRule.Validate%2A> implementacji metody `value` rzutuj <xref:System.Windows.Data.BindingGroup> wartość parametru na wystąpienie. Następnie można uzyskać dostęp do <xref:System.Windows.Data.BindingGroup.Items%2A> obiektu danych za pośrednictwem właściwości.  
  
     Poniższy przykład pokazuje ten proces, `StartDate` aby sprawdzić, `Course` czy wartość `EndDate` właściwości dla obiektu jest wcześniejsza niż jego wartość właściwości.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2. Dodaj regułę sprawdzania <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> poprawności do kolekcji. Właściwość <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> zapewnia bezpośredni <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> dostęp do <xref:System.Windows.Data.BindingGroup> właściwości wystąpienia, które grupuje wszystkie powiązania używane przez formant.  
  
     W poniższym <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> przykładzie ustawia właściwość w języku XAML. Właściwość <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> jest <xref:System.Windows.Controls.ValidationStep.UpdatedValue> ustawiona na tak, że sprawdzanie poprawności występuje tylko po zaktualizowaniu obiektu danych powiązanych.  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Gdy użytkownik określa datę zakończenia wcześniejszą niż data rozpoczęcia, w nagłówku wiersza pojawi się czerwony wykrzyknik (!) . Tę domyślną opinię zwrotną sprawdzania poprawności można zmienić zgodnie z opisem w poniższej procedurze.  
  
### <a name="to-customize-row-validation-feedback"></a>Aby dostosować opinię o weryfikacji wiersza  
  
- Ustaw <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> właściwość. Ta właściwość umożliwia dostosowanie opinii sprawdzania <xref:System.Windows.Controls.DataGrid> poprawności wiersza dla poszczególnych formantów. Można również wpłynąć na wiele formantów <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> przy użyciu niejawnego stylu wiersza, aby ustawić właściwość.  
  
     Poniższy przykład zastępuje domyślną opinię zwrotną sprawdzania poprawności wiersza bardziej widocznym wskaźnikiem. Gdy użytkownik wprowadzi nieprawidłową wartość, w nagłówku wiersza pojawi się czerwone kółko z białym wykrzyknikiem. Dzieje się tak w przypadku błędów sprawdzania poprawności wiersza i komórki. Skojarzony komunikat o błędzie jest wyświetlany w etykietce narzędzia.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera pełną demonstrację sprawdzania poprawności komórek i wierszy. Klasa `Course` zawiera przykładowy obiekt danych, który implementuje <xref:System.ComponentModel.IEditableObject> do obsługi transakcji. Formant współdziała <xref:System.Windows.Controls.DataGrid> z, <xref:System.ComponentModel.IEditableObject> aby umożliwić użytkownikom przywrócić zmiany, naciskając klawisz ESC.  
  
> [!NOTE]
> Jeśli używasz języka Visual Basic, w pierwszym wierszu mainwindow.xaml, zamień na `x:Class="DataGridValidation.MainWindow"` `x:Class="MainWindow"`.  
  
 Aby przetestować sprawdzanie poprawności, spróbuj wykonać następujące czynności:  
  
- W kolumnie Identyfikator kursu wprowadź wartość niekłodiową.  
  
- W kolumnie Data zakończenia wprowadź datę wcześniejszą niż data rozpoczęcia.  
  
- Usuń wartość w identyfikatorze kursu, dacie rozpoczęcia lub dacie zakończenia.  
  
- Aby cofnąć nieprawidłową wartość komórki, umieść kursor z powrotem w komórce i naciśnij klawisz ESC.  
  
- Aby cofnąć zmiany dla całego wiersza, gdy bieżąca komórka jest w trybie edycji, naciśnij dwukrotnie klawisz ESC.  
  
- Po wystąpieniu błędu sprawdzania poprawności przesuń wskaźnik myszy na wskaźnik w nagłówku wiersza, aby wyświetlić skojarzony komunikat o błędzie.  
  
 [!code-csharp[DataGrid_Validation#FullCode](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Controls.DataGrid>
- [DataGrid](datagrid.md)
- [Powiązanie danych](../../../desktop-wpf/data/data-binding-overview.md)
- [Implementowanie sprawdzania poprawności powiązania](../data/how-to-implement-binding-validation.md)
- [Implementowanie logiki sprawdzania poprawności dla obiektów niestandardowych](../data/how-to-implement-validation-logic-on-custom-objects.md)
