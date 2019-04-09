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
ms.openlocfilehash: aead8cbd500262a4cba535fd023dd9701d50257a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086810"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Instrukcje: implementowanie weryfikowania za pomocą kontrolki DataGrid
<xref:System.Windows.Controls.DataGrid> Control umożliwia wykonywanie walidacji na poziomie komórki i wierszy. Z weryfikacją poziomie komórki sprawdzania poprawności poszczególnych właściwości powiązany obiekt danych po użytkownik aktualizuje wartość. Z weryfikacją na poziomie wiersza Sprawdź wszystkie dane obiektów po użytkownik zatwierdzenia zmian w wierszu. Można również przekazać niestandardowe wizualną opinię błędy sprawdzania poprawności lub użyć domyślnej wizualną opinię, <xref:System.Windows.Controls.DataGrid> zawiera formant.  
  
 W poniższych procedurach opisano sposób zastosowania reguły sprawdzania poprawności <xref:System.Windows.Controls.DataGrid> powiązania i dostosowywanie wizualną opinię.  
  
### <a name="to-validate-individual-cell-values"></a>Aby sprawdzić poprawność wartości poszczególnych komórek  
  
-   Określ jedną lub więcej reguł sprawdzania poprawności w powiązaniu używane z kolumną. Jest to podobne do sprawdzania poprawności danych w kontrolkach prosty, zgodnie z opisem w [Przegląd wiązanie danych](../data/data-binding-overview.md).  
  
     W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.DataGrid> formantu o cztery kolumny powiązane z różnymi właściwościami obiektu biznesowego. Określ trzy kolumny <xref:System.Windows.Controls.ExceptionValidationRule> , ustawiając <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> właściwość `true`.  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Gdy użytkownik wprowadza wartość jest nieprawidłowa (na przykład nie jest liczbą całkowitą w kolumnie Identyfikator kursu), zostanie wyświetlone czerwone obramowanie, która wokół komórki. Można zmienić tej opinii do sprawdzania poprawności domyślnej zgodnie z opisem w poniższej procedurze.  
  
### <a name="to-customize-cell-validation-feedback"></a>Aby dostosować komórki sprawdzania poprawności opinii  
  
-   W kolumnie ustaw <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> właściwości stylu właściwe dla kolumny w formancie edycji. Ponieważ formanty edycji są tworzone w czasie wykonywania, nie można użyć <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> dołączona właściwość, jak w przypadku prostych kontrolek.  
  
     Poniższy przykład aktualizuje poprzedniego przykładu, dodając stylu błędu współużytkowane przez trzy kolumny przy użyciu reguł sprawdzania poprawności. Gdy użytkownik wprowadza wartość jest nieprawidłowa, styl zmienia kolor tła komórek i dodaje etykietkę narzędzia. Zwróć uwagę na użycie wyzwalacza, aby ustalić, czy jest to błąd sprawdzania poprawności. Jest to wymagane, ponieważ obecnie nie ma błędów dedykowanych szablonu dla komórek.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Możesz zaimplementować bardziej dokładne dostosowanie, zastępując <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> używane przez wartość z kolumny.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>Aby sprawdzić poprawność wielu wartości w jednym wierszu  
  
1.  Implementowanie <xref:System.Windows.Controls.ValidationRule> podklasy, która sprawdza wiele właściwości powiązany obiekt danych. W swojej <xref:System.Windows.Controls.ValidationRule.Validate%2A> rzutowania implementacji metody `value` wartości parametru <xref:System.Windows.Data.BindingGroup> wystąpienia. Mogą uzyskiwać dostęp do obiektu danych za pośrednictwem <xref:System.Windows.Data.BindingGroup.Items%2A> właściwości.  
  
     Poniższy przykład ilustruje ten proces, aby sprawdzić czy `StartDate` wartości właściwości dla `Course` obiekt jest wcześniejsza niż jego `EndDate` wartości właściwości.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2.  Dodaj regułę walidacji do <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> kolekcji. <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> Właściwości zapewnia bezpośredni dostęp do <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> właściwość <xref:System.Windows.Data.BindingGroup> wystąpienia, który grupuje wszystkie powiązania, które są używane przez kontrolkę.  
  
     Poniższy przykład ustawia <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> właściwości w XAML. <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> Właściwość jest ustawiona na <xref:System.Windows.Controls.ValidationStep.UpdatedValue> tak, aby sprawdzanie występuje tylko wtedy, gdy powiązany obiekt danych jest aktualizowany.  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Gdy użytkownik określi datę końcową, która jest wcześniejsza niż data rozpoczęcia, nagłówek wiersza jest wyświetlany czerwony wykrzyknik (!). Można zmienić tej opinii do sprawdzania poprawności domyślnej zgodnie z opisem w poniższej procedurze.  
  
### <a name="to-customize-row-validation-feedback"></a>Aby dostosować wiersz sprawdzania poprawności opinii  
  
-   Ustaw <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> właściwości. Ta właściwość umożliwia dostosowanie opinii walidacji wiersza dla poszczególnych <xref:System.Windows.Controls.DataGrid> kontrolki. Może również wpływać na wiele formantów, za pomocą styl niejawny wierszy można ustawić <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> właściwości.  
  
     Poniższy przykład zastępuje domyślny wiersz sprawdzania poprawności opinii bardziej widoczny wskaźnik. Po użytkownik wprowadzi nieprawidłową wartość, w nagłówku wiersza pojawi się czerwone kółko z białym znakiem wykrzyknika. Operacja wykonywana dla wierszy i komórek błędy sprawdzania poprawności. Komunikat o błędzie skojarzony jest wyświetlany w etykietce narzędzia.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono pełny pokaz weryfikacji wierszy i komórek. `Course` Klasa udostępnia przykładowy obiekt danych, który implementuje <xref:System.ComponentModel.IEditableObject> obsługi transakcji. <xref:System.Windows.Controls.DataGrid> Kontroli wchodzi w interakcję z <xref:System.ComponentModel.IEditableObject> aby umożliwić użytkownikom cofnąć zmiany, naciskając klawisz ESC.  
  
> [!NOTE]
>  Jeśli używasz języka Visual Basic w pierwszym wierszu pliku MainWindow.xaml, Zastąp `x:Class="DataGridValidation.MainWindow"` z `x:Class="MainWindow"`.  
  
 Aby przetestować sprawdzania poprawności, spróbuj wykonać następujące czynności:  
  
-   W kolumnie Identyfikator kursu wprowadź wartość nie jest liczbą całkowitą.  
  
-   W kolumnie daty zakończenia wprowadź datę, która jest wcześniejsza niż data rozpoczęcia.  
  
-   Usuń wartość w identyfikator kursu, Data rozpoczęcia lub datę zakończenia.  
  
-   Aby cofnąć to wartość nieprawidłowa komórka, umieść kursor w komórce i naciśnij klawisz ESC.  
  
-   Aby cofnąć zmiany dla całego wiersza po bieżącej komórki w trybie edycji, naciśnij dwa razy klawisz ESC.  
  
-   Gdy wystąpi błąd sprawdzania poprawności, przesuń wskaźnik myszy nad wskaźnikiem w nagłówku wiersza, aby wyświetlić komunikat o błędzie skojarzony.  
  
 [!code-csharp[DataGrid_Validation#FullCode](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.DataGrid>
- [DataGrid](datagrid.md)
- [Powiązanie danych](../data/data-binding-wpf.md)
- [Implementowanie weryfikacji wiązania](../data/how-to-implement-binding-validation.md)
- [Implementowanie logiki weryfikacji w obiektach niestandardowych](../data/how-to-implement-validation-logic-on-custom-objects.md)
