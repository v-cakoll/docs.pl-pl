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
ms.openlocfilehash: 401949aa4bea924b458a91dc00c454c97aff4895
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458455"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Jak implementuj walidację za pomocą formantu DataGrid
Kontrolka <xref:System.Windows.Controls.DataGrid> umożliwia wykonywanie walidacji zarówno na poziomie komórki, jak i w wierszu. Walidacja na poziomie komórki polega na sprawdzeniu poprawności poszczególnych właściwości powiązanego obiektu danych, gdy użytkownik aktualizuje wartość. Za pomocą walidacji na poziomie wierszy można sprawdzać poprawność wszystkich obiektów danych, gdy użytkownik zatwierdzi zmiany w wierszu. Możesz również dostarczyć dostosowaną wizualną opinię na temat błędów walidacji lub użyć domyślnej wizualizacji, którą zapewnia formant <xref:System.Windows.Controls.DataGrid>.  
  
 W poniższych procedurach opisano sposób stosowania reguł walidacji do <xref:System.Windows.Controls.DataGrid> powiązań i dostosowywania informacji zwrotnych.  
  
### <a name="to-validate-individual-cell-values"></a>Aby sprawdzić poprawność wartości poszczególnych komórek  
  
- Określ co najmniej jedną regułę walidacji dla powiązania używanego z kolumną. Jest to podobne do sprawdzania poprawności danych w prostych kontrolkach, zgodnie z opisem w temacie [powiązanie danych — omówienie](../data/data-binding-overview.md).  
  
     Poniższy przykład przedstawia kontrolkę <xref:System.Windows.Controls.DataGrid> z czterema kolumnami związanymi z różnymi właściwościami obiektu biznesowego. Trzy kolumny określają <xref:System.Windows.Controls.ExceptionValidationRule> przez ustawienie właściwości <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> na `true`.  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Gdy użytkownik wprowadzi nieprawidłową wartość (na przykład niebędącą liczbą całkowitą w kolumnie Identyfikator kursu), wokół komórki pojawia się czerwone obramowanie. Możesz zmienić te domyślne informacje zwrotne, zgodnie z opisem w poniższej procedurze.  
  
### <a name="to-customize-cell-validation-feedback"></a>Aby dostosować opinię na temat walidacji komórki  
  
- Ustaw właściwość <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> kolumny na styl odpowiedni dla kontrolki edycji kolumny. Ponieważ kontrolki edycji są tworzone w czasie wykonywania, nie można użyć <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> dołączonej właściwości, tak jak w przypadku formantów prostych.  
  
     Poniższy przykład aktualizuje poprzedni przykład, dodając styl błędu współużytkowany przez trzy kolumny z regułami walidacji. Gdy użytkownik wprowadzi nieprawidłową wartość, styl zmienia kolor tła komórki i dodaje etykietkę narzędzia. Zwróć uwagę na użycie wyzwalacza, aby określić, czy wystąpił błąd walidacji. Jest to wymagane, ponieważ dla komórek nie ma obecnie dedykowanego szablonu błędu.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Można zaimplementować bardziej rozległe dostosowanie, zastępując <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> używany przez kolumnę.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>Aby sprawdzić poprawność wielu wartości w pojedynczym wierszu  
  
1. Zaimplementuj podklasę <xref:System.Windows.Controls.ValidationRule>, która sprawdza wiele właściwości powiązanego obiektu danych. W implementacji metody <xref:System.Windows.Controls.ValidationRule.Validate%2A> wykonaj Rzutowanie wartości parametru `value` na wystąpienie <xref:System.Windows.Data.BindingGroup>. Następnie można uzyskać dostęp do obiektu danych za pomocą właściwości <xref:System.Windows.Data.BindingGroup.Items%2A>.  
  
     Poniższy przykład ilustruje ten proces, aby sprawdzić, czy `StartDate` wartość właściwości dla obiektu `Course` jest wcześniejsza niż jego wartość właściwości `EndDate`.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2. Dodaj regułę walidacji do kolekcji <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType>. Właściwość <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> zapewnia bezpośredni dostęp do właściwości <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> wystąpienia <xref:System.Windows.Data.BindingGroup>, które grupuje wszystkie powiązania używane przez formant.  
  
     Poniższy przykład ustawia właściwość <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> w języku XAML. Właściwość <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> jest ustawiona na <xref:System.Windows.Controls.ValidationStep.UpdatedValue>, aby Walidacja była wykonywana dopiero po zaktualizowaniu powiązanego obiektu danych.  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Gdy użytkownik określi datę końcową wcześniejszą niż data rozpoczęcia, w nagłówku wiersza pojawi się czerwony wykrzyknik (!). Możesz zmienić te domyślne informacje zwrotne, zgodnie z opisem w poniższej procedurze.  
  
### <a name="to-customize-row-validation-feedback"></a>Aby dostosować opinię dotyczącą weryfikacji wierszy  
  
- Ustaw właściwość <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType>. Ta właściwość umożliwia dostosowanie informacji zwrotnych dotyczących weryfikacji wierszy dla poszczególnych formantów <xref:System.Windows.Controls.DataGrid>. Możesz również mieć wpływ na wiele formantów przy użyciu niejawnego stylu wiersza w celu ustawienia właściwości <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType>.  
  
     W poniższym przykładzie jest zastępowana domyślna opinia weryfikacji wiersza z bardziej widocznym wskaźnikiem. Gdy użytkownik wprowadzi nieprawidłową wartość, w nagłówku wiersza pojawia się czerwony okrąg z białym znakiem wykrzyknika. Dzieje się tak w przypadku błędów walidacji wierszy i komórek. Skojarzony komunikat o błędzie jest wyświetlany w etykietce narzędzia.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera kompletną demonstrację dla walidacji komórek i wierszy. Klasa `Course` dostarcza przykładowego obiektu danych, który implementuje <xref:System.ComponentModel.IEditableObject> do obsługi transakcji. Formant <xref:System.Windows.Controls.DataGrid> współdziała z <xref:System.ComponentModel.IEditableObject>, aby umożliwić użytkownikom przywracanie zmian przez naciśnięcie klawisza ESC.  
  
> [!NOTE]
> Jeśli używasz Visual Basic, w pierwszym wierszu MainWindow. XAML Zastąp `x:Class="DataGridValidation.MainWindow"` elementem `x:Class="MainWindow"`.  
  
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
- [Powiązanie danych](../../../desktop-wpf/data/data-binding-overview.md)
- [Implementowanie powiązanej walidacji](../data/how-to-implement-binding-validation.md)
- [Implementowanie logiki walidacji w obiektach niestandardowych](../data/how-to-implement-validation-logic-on-custom-objects.md)
