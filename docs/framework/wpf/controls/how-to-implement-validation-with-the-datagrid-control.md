---
title: "Jak implementuj walidację za pomocą formantu DataGrid"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], validation
- validation [WPF], DataGrid
ms.assetid: ec6078a8-1e42-4648-b414-f4348e81bda1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 78846e2b6a1d73e011441b0ccb46b8aad365d5dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Jak implementuj walidację za pomocą formantu DataGrid
<xref:System.Windows.Controls.DataGrid> Kontroli umożliwia przeprowadzanie weryfikacji na poziomie wiersza i komórki. Z weryfikacji na poziomie komórki zweryfikować poszczególnych właściwości obiektu powiązana z danymi, gdy użytkownik zaktualizuje wartość. Z weryfikacji na poziomie wiersza sprawdzania poprawności danych obiektów, gdy użytkownik zatwierdza zmiany na wiersz. Można również podać dostosowane wizualne błędy sprawdzania poprawności lub użyć domyślnej wizualne który <xref:System.Windows.Controls.DataGrid> zawiera kontrolki.  
  
 W poniższych procedurach opisano sposób stosowania reguły walidacji do <xref:System.Windows.Controls.DataGrid> powiązania i dostosować wizualny.  
  
### <a name="to-validate-individual-cell-values"></a>Aby sprawdzić poprawność wartości pojedynczych komórek  
  
-   Określ co najmniej jednej reguły sprawdzania poprawności na używanego powiązania z kolumną. Jest to podobne do sprawdzania poprawności danych w kontrolkach proste, zgodnie z opisem w [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
     W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.DataGrid> formantu o cztery kolumny powiązane z różnych właściwości obiektu biznesowego. Określ trzy kolumny <xref:System.Windows.Controls.ExceptionValidationRule> przez ustawienie <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> właściwości `true`.  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Gdy użytkownik wprowadza wartość jest nieprawidłowa (np. nie jest liczbą całkowitą w kolumnie Identyfikator kursu), czerwonego obramowania wokół komórki. Można zmienić tej opinii sprawdzania poprawności domyślnej zgodnie z opisem w poniższej procedurze.  
  
### <a name="to-customize-cell-validation-feedback"></a>Aby dostosować komórki weryfikacji opinii  
  
-   Wartość w kolumnie <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> właściwości stylu odpowiednią dla kolumny do kontrolki edycji. Ponieważ formantów edycji są tworzone w czasie wykonywania, nie można użyć <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> dołączona właściwość, jak w przypadku prostych formantów.  
  
     Poniższy przykład aktualizuje poprzedni przykład, dodając stylu błędu, współużytkowane przez trzy kolumny z reguł sprawdzania poprawności. Gdy użytkownik wprowadza wartość jest nieprawidłowa, styl zmienia kolor tła komórki i dodaje etykietkę narzędzia. Zwróć uwagę na użycie wyzwalacza w celu ustalenia, czy występuje błąd weryfikacji. Jest to wymagane, ponieważ nie ma obecnie żaden szablon błąd dedykowane dla komórek.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Można wdrożyć bardziej dokładne dostosowanie zastępując <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> używane w kolumnie.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>Aby sprawdzić poprawność wielu wartości w jednym wierszu  
  
1.  Implementowanie <xref:System.Windows.Controls.ValidationRule> podklasy, która sprawdza wiele właściwości powiązany obiekt danych. W Twojej <xref:System.Windows.Controls.ValidationRule.Validate%2A> rzutowania implementacji metody `value` wartości parametru <xref:System.Windows.Data.BindingGroup> wystąpienia. Można następnie uzyskać dostęp do obiektu danych, za pomocą <xref:System.Windows.Data.BindingGroup.Items%2A> właściwości.  
  
     W poniższym przykładzie pokazano tego procesu, aby zweryfikować czy `StartDate` wartości właściwości dla `Course` obiektu jest starsza niż jego `EndDate` wartości właściwości.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2.  Dodawanie reguły walidacji do <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> kolekcji. <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> Właściwości zapewnia bezpośredni dostęp do <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> właściwość <xref:System.Windows.Data.BindingGroup> wystąpienia, który grupuje wszystkie powiązania, używany przez formant.  
  
     W poniższym przykładzie <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> właściwości w języku XAML. <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> Właściwość jest ustawiona na <xref:System.Windows.Controls.ValidationStep.UpdatedValue> tak, aby sprawdzanie występuje tylko wtedy, gdy powiązany obiekt danych jest aktualizowany.  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Gdy użytkownik określi Data zakończenia jest wcześniejsza niż data rozpoczęcia, w nagłówku wiersza jest wyświetlany czerwony wykrzyknik (!). Można zmienić tej opinii sprawdzania poprawności domyślnej zgodnie z opisem w poniższej procedurze.  
  
### <a name="to-customize-row-validation-feedback"></a>Aby dostosować opinii walidacji wiersza  
  
-   Ustaw <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> właściwości. Ta właściwość umożliwia dostosowanie opinii walidacji wiersza dla poszczególnych <xref:System.Windows.Controls.DataGrid> kontrolki. Może również wpływać na wiele formantów przy użyciu stylu niejawne wiersza można ustawić <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> właściwości.  
  
     Poniższy przykład zastępuje opinii walidacji wiersza domyślne wykrywalność wskaźnika. Gdy użytkownik wprowadza wartość jest nieprawidłowa, w nagłówku wiersza pojawi się czerwone kółko z białym znakiem wykrzyknika. Dzieje się tak dla wierszy i komórek błędy sprawdzania poprawności. Komunikat skojarzony błąd jest wyświetlany w etykietce narzędzia.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono pełną pokaz dla komórek, wierszy i sprawdzania poprawności. `Course` Klasa udostępnia obiekt danych przykładowych, który implementuje <xref:System.ComponentModel.IEditableObject> obsługi transakcji. <xref:System.Windows.Controls.DataGrid> Kontroli współdziała z <xref:System.ComponentModel.IEditableObject> aby użytkownicy mogli cofnięcie zmian, naciskając klawisz ESC.  
  
> [!NOTE]
>  Jeśli korzystasz z języka Visual Basic w pierwszym wierszu MainWindow.xaml, Zastąp `x:Class="DataGridValidation.MainWindow"` z `x:Class="MainWindow"`.  
  
 Aby przetestować weryfikacji, należy spróbować wykonać następujące czynności:  
  
-   W kolumnie Identyfikator kursu wprowadź wartość nie jest liczbą całkowitą.  
  
-   W kolumnie Data zakończenia wprowadź datę, która jest wcześniejsza niż data rozpoczęcia.  
  
-   Usuń wartość Identyfikatora ciągu, Data rozpoczęcia lub data zakończenia.  
  
-   Aby cofnąć wartość komórki nieprawidłowy, umieść kursor w komórce i naciśnij klawisz ESC.  
  
-   Aby cofnąć zmiany dla całego wiersza, gdy bieżąca komórka jest w trybie edycji, naciśnij dwukrotnie klawisz ESC.  
  
-   Gdy wystąpi błąd sprawdzania poprawności, przesuń wskaźnik myszy nad wskaźnika w nagłówku wiersza, aby zobaczyć powiązane komunikaty o błędach.  
  
 [!code-csharp[DataGrid_Validation#FullCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.DataGrid>  
 [DataGrid](../../../../docs/framework/wpf/controls/datagrid.md)  
 [Powiązanie danych](../../../../docs/framework/wpf/data/data-binding-wpf.md)  
 [Implementowanie powiązanej walidacji](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [Implementowanie logiki walidacji w obiektach niestandardowych](../../../../docs/framework/wpf/data/how-to-implement-validation-logic-on-custom-objects.md)
