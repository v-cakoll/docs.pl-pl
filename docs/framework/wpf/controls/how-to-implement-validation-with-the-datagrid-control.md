---
title: 'Instrukcje: implementowanie weryfikowania za pomocą kontrolki DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], validation
- validation [WPF], DataGrid
ms.assetid: ec6078a8-1e42-4648-b414-f4348e81bda1
ms.openlocfilehash: 8ae651b3085b39673a51cf8d5f65e9bfb9da87d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962040"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Instrukcje: implementowanie weryfikowania za pomocą kontrolki DataGrid
<xref:System.Windows.Controls.DataGrid> Kontrolka umożliwia wykonywanie walidacji zarówno na poziomie komórki, jak i w wierszu. Walidacja na poziomie komórki polega na sprawdzeniu poprawności poszczególnych właściwości powiązanego obiektu danych, gdy użytkownik aktualizuje wartość. Za pomocą walidacji na poziomie wierszy można sprawdzać poprawność wszystkich obiektów danych, gdy użytkownik zatwierdzi zmiany w wierszu. Możesz również dostarczyć dostosowaną wizualną opinię na temat błędów walidacji lub użyć domyślnej wizualizacji, <xref:System.Windows.Controls.DataGrid> którą zapewnia formant.  
  
 Poniższe procedury opisują sposób stosowania reguł walidacji do <xref:System.Windows.Controls.DataGrid> powiązań i dostosowywania wizualizacji wizualnej.  
  
### <a name="to-validate-individual-cell-values"></a>Aby sprawdzić poprawność wartości poszczególnych komórek  
  
- Określ co najmniej jedną regułę walidacji dla powiązania używanego z kolumną. Jest to podobne do sprawdzania poprawności danych w prostych kontrolkach, zgodnie z opisem w temacie [powiązanie danych — omówienie](../data/data-binding-overview.md).  
  
     Poniższy przykład pokazuje <xref:System.Windows.Controls.DataGrid> kontrolkę z czterema kolumnami związanymi z różnymi właściwościami obiektu biznesowego. Trzy kolumny określają <xref:System.Windows.Controls.ExceptionValidationRule> przez <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> ustawienie właściwości na `true`.  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Gdy użytkownik wprowadzi nieprawidłową wartość (na przykład niebędącą liczbą całkowitą w kolumnie Identyfikator kursu), wokół komórki pojawia się czerwone obramowanie. Możesz zmienić te domyślne informacje zwrotne, zgodnie z opisem w poniższej procedurze.  
  
### <a name="to-customize-cell-validation-feedback"></a>Aby dostosować opinię na temat walidacji komórki  
  
- Ustaw <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> właściwość kolumny na styl odpowiedni dla kontrolki edycji kolumny. Ponieważ kontrolki edycji są tworzone w czasie wykonywania, nie można użyć <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> dołączonej właściwości, tak jak w przypadku formantów prostych.  
  
     Poniższy przykład aktualizuje poprzedni przykład, dodając styl błędu współużytkowany przez trzy kolumny z regułami walidacji. Gdy użytkownik wprowadzi nieprawidłową wartość, styl zmienia kolor tła komórki i dodaje etykietkę narzędzia. Zwróć uwagę na użycie wyzwalacza, aby określić, czy wystąpił błąd walidacji. Jest to wymagane, ponieważ dla komórek nie ma obecnie dedykowanego szablonu błędu.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Można zaimplementować bardziej rozległe dostosowanie, zastępując <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> użycie kolumny.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>Aby sprawdzić poprawność wielu wartości w pojedynczym wierszu  
  
1. Zaimplementuj <xref:System.Windows.Controls.ValidationRule> podklasę sprawdzającą wiele właściwości powiązanego obiektu danych. W implementacji `value`metodynależy rzutować wartość parametru na <xref:System.Windows.Data.BindingGroup> wystąpienie. <xref:System.Windows.Controls.ValidationRule.Validate%2A> Następnie można uzyskać dostęp do obiektu danych za pomocą <xref:System.Windows.Data.BindingGroup.Items%2A> właściwości.  
  
     Poniższy przykład ilustruje ten proces, aby sprawdzić, `StartDate` czy wartość `Course` właściwości obiektu jest wcześniejsza niż jego `EndDate` wartość właściwości.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2. Dodaj regułę walidacji do <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> kolekcji. Właściwość zapewnia bezpośredni dostęp <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> do właściwości <xref:System.Windows.Data.BindingGroup> wystąpienia, które grupuje wszystkie powiązania używane przez formant. <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A>  
  
     Poniższy przykład ustawia <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> właściwość w języku XAML. Właściwość jest ustawiona na <xref:System.Windows.Controls.ValidationStep.UpdatedValue> tak, aby Walidacja była wykonywana dopiero po zaktualizowaniu powiązanego obiektu danych. <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Gdy użytkownik określi datę końcową wcześniejszą niż data rozpoczęcia, w nagłówku wiersza pojawi się czerwony wykrzyknik (!). Możesz zmienić te domyślne informacje zwrotne, zgodnie z opisem w poniższej procedurze.  
  
### <a name="to-customize-row-validation-feedback"></a>Aby dostosować opinię dotyczącą weryfikacji wierszy  
  
- <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> Ustaw właściwość. Ta właściwość umożliwia dostosowanie informacji zwrotnych dotyczących sprawdzania poprawności wierszy <xref:System.Windows.Controls.DataGrid> dla poszczególnych kontrolek. Możesz również mieć wpływ na wiele formantów przy użyciu niejawnego stylu wiersza do <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> ustawiania właściwości.  
  
     W poniższym przykładzie jest zastępowana domyślna opinia weryfikacji wiersza z bardziej widocznym wskaźnikiem. Gdy użytkownik wprowadzi nieprawidłową wartość, w nagłówku wiersza pojawia się czerwony okrąg z białym znakiem wykrzyknika. Dzieje się tak w przypadku błędów walidacji wierszy i komórek. Skojarzony komunikat o błędzie jest wyświetlany w etykietce narzędzia.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera kompletną demonstrację dla walidacji komórek i wierszy. Klasa zawiera przykładowy obiekt danych, który implementuje <xref:System.ComponentModel.IEditableObject> obsługę transakcji. `Course` Formant współdziała z <xref:System.ComponentModel.IEditableObject> programem, aby umożliwić użytkownikom przywracanie zmian przez naciśnięcie klawisza ESC. <xref:System.Windows.Controls.DataGrid>  
  
> [!NOTE]
> Jeśli używasz Visual Basic, w pierwszym wierszu MainWindow. XAML Zastąp `x:Class="DataGridValidation.MainWindow"` ciąg opcją. `x:Class="MainWindow"`  
  
 Aby przetestować sprawdzanie poprawności, spróbuj wykonać następujące czynności:  
  
- W kolumnie Identyfikator kursu wprowadź wartość różną od liczby całkowitej.  
  
- W kolumnie Data końcowa wprowadź datę wcześniejszą niż data rozpoczęcia.  
  
- Usuń wartość w polu Identyfikator kursu, datę rozpoczęcia lub datę zakończenia.  
  
- Aby cofnąć nieprawidłową wartość komórki, umieść kursor z powrotem w komórce i naciśnij klawisz ESC.  
  
- Aby cofnąć zmiany dla całego wiersza, gdy bieżąca komórka jest w trybie edycji, naciśnij dwukrotnie klawisz ESC.  
  
- Gdy wystąpi błąd walidacji, Przenieś wskaźnik myszy nad wskaźnikiem w nagłówku wiersza, aby zobaczyć skojarzony komunikat o błędzie.  
  
 [!code-csharp[DataGrid_Validation#FullCode](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.DataGrid>
- [DataGrid](datagrid.md)
- [Powiązanie danych](../data/data-binding-wpf.md)
- [Implementowanie powiązanej walidacji](../data/how-to-implement-binding-validation.md)
- [Implementowanie logiki walidacji w obiektach niestandardowych](../data/how-to-implement-validation-logic-on-custom-objects.md)
