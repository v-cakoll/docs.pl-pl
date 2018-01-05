---
title: "Wskazówki: sprawdzanie poprawności danych w formancie DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating data [Windows Forms], Windows Forms
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: a4f1d015-2969-430c-8ea2-b612d179c290
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b2ede616b311119d174534e53cb3aaf9e366c7c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>Wskazówki: sprawdzanie poprawności danych w formancie DataGridView formularzy systemu Windows
Po wyświetleniu funkcji zapis danych dla użytkowników, często konieczne sprawdzanie poprawności danych wprowadzonych do formularza. <xref:System.Windows.Forms.DataGridView> Klasa oferuje wygodny sposób sprawdzania poprawności, zanim danych zostanie przekazany do magazynu danych. Sprawdzanie poprawności danych Obsługa <xref:System.Windows.Forms.DataGridView.CellValidating> zdarzenie, które jest wywoływane przez <xref:System.Windows.Forms.DataGridView> podczas zmiany bieżącej komórki.  
  
 W tym przewodniku pobierze wiersze z `Customers` tabeli w bazie danych Northwind i wyświetlić je w <xref:System.Windows.Forms.DataGridView> formantu. Gdy użytkownik edytuje komórki w `CompanyName` kolumny i próbuje komórka, <xref:System.Windows.Forms.DataGridView.CellValidating> obsługi zdarzeń zbada nowy ciąg nazwy firmy do upewnij się, że nie jest nie pusty; Jeśli nowa wartość jest ciągiem pustym <xref:System.Windows.Forms.DataGridView> uniemożliwi kursora użytkownika opuszczania komórki, dopóki nie zostanie wprowadzona niepustym ciągiem.  
  
 Aby skopiować kod w tym temacie na jednej liście, zobacz [porady: Sprawdzanie poprawności danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W celu przeprowadzenia tego instruktażu potrzebne są:  
  
-   Dostęp do serwera z przykładowej bazy danych Northwind programu SQL Server.  
  
## <a name="creating-the-form"></a>Tworzenie formularza  
  
#### <a name="to-validate-data-entered-in-a-datagridview"></a>Aby sprawdzić poprawność danych wprowadzonych w parametrze DataGridView  
  
1.  Utwórz klasę pochodną <xref:System.Windows.Forms.Form> i zawiera <xref:System.Windows.Forms.DataGridView> kontroli i <xref:System.Windows.Forms.BindingSource> składnika.  
  
     Poniższy przykład kodu zawiera podstawowe inicjowania oraz `Main` metody.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]  
  
2.  W definicji klasy formularza obsługi szczegóły połączenia z bazą danych, należy zaimplementować metodę.  
  
     W tym przykładzie kodu używane `GetData` metodę zwracającą wypełnione <xref:System.Data.DataTable> obiektu. Upewnij się, że możesz `connectionString` zmiennej na wartość, która jest odpowiednia dla Twojej bazy danych.  
  
    > [!IMPORTANT]
    >  Przechowywanie poufne informacje, takie jak hasła, w ciągu połączenia może mieć wpływ na bezpieczeństwo aplikacji. Przy użyciu uwierzytelniania systemu Windows, nazywane również zintegrowane zabezpieczenia jest bardziej bezpieczny sposób kontrolowania dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]  
  
3.  Implementowanie obsługi dla formularza użytkownika <xref:System.Windows.Forms.Form.Load> zdarzenie, które inicjuje <xref:System.Windows.Forms.DataGridView> i <xref:System.Windows.Forms.BindingSource> i konfiguruje wiązania danych.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]  
  
4.  Implementowanie obsługi <xref:System.Windows.Forms.DataGridView> formantu <xref:System.Windows.Forms.DataGridView.CellValidating> i <xref:System.Windows.Forms.DataGridView.CellEndEdit> zdarzenia.  
  
     <xref:System.Windows.Forms.DataGridView.CellValidating> Procedura obsługi zdarzeń jest, gdy okaże się, czy wartość komórki w `CompanyName` kolumny jest pusta. W przypadku niepowodzenia weryfikacji wartość komórki ustawić <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> właściwość <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType> klasy do `true`. Powoduje to <xref:System.Windows.Forms.DataGridView> formantu, aby zapobiec pozostawienie komórki kursora. Ustaw <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> właściwości na wiersz, aby wyjaśniające ciągu. Spowoduje to wyświetlenie ikony błędu z etykietka narzędzia zawierająca tekst błędu. W <xref:System.Windows.Forms.DataGridView.CellEndEdit> program obsługi zdarzeń, ustaw <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> właściwości w wierszu do pustego ciągu. <xref:System.Windows.Forms.DataGridView.CellEndEdit> Wystąpi zdarzenie tylko, gdy komórki zamyka tryb edycji, co nie można zrobić, w przypadku niepowodzenia weryfikacji.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz możesz przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.  
  
#### <a name="to-test-the-form"></a>Aby przetestować formularz  
  
-   Kompilowanie i uruchamianie aplikacji.  
  
     Zobaczysz <xref:System.Windows.Forms.DataGridView> wypełnione danymi z `Customers` tabeli. Po dwukrotnym kliknięciu komórki w `CompanyName` kolumny, można edytować wartość. Czy usunąć wszystkie znaki i naciśnij klawisz TAB, aby zakończyć komórki, <xref:System.Windows.Forms.DataGridView> uniemożliwia został zakończony. Po wpisaniu niepustego ciągu w komórce, <xref:System.Windows.Forms.DataGridView> kontroli umożliwia wyjście komórki.  
  
## <a name="next-steps"></a>Następne kroki  
 Ta aplikacja zawiera podstawowe <xref:System.Windows.Forms.DataGridView> funkcje formantu. Można dostosować wygląd i zachowanie <xref:System.Windows.Forms.DataGridView> sterowania na kilka sposobów:  
  
-   Zmienianie stylów obramowania i nagłówek. Aby uzyskać więcej informacji, zobacz [porady: Zmiana obramowania i style linii siatki w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Włącz lub ograniczanie danych wejściowych użytkownika na <xref:System.Windows.Forms.DataGridView> formantu. Aby uzyskać więcej informacji, zobacz [porady: Zapobiegaj dodawaniu i usuwaniu rzędów do formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), i [jak: utworzyć tylko do odczytu w kolumn w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Sprawdź dane wejściowe użytkownika błędy związane z bazy danych. Aby uzyskać więcej informacji, zobacz [wskazówki: obsługa błędów tego Occur podczas wprowadzania danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
-   Obsłużyć bardzo dużych zestawów danych przy użyciu trybu wirtualnego. Aby uzyskać więcej informacji, zobacz [wskazówki: Implementowanie trybu wirtualnego w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Dostosowywanie wyglądu komórek. Aby uzyskać więcej informacji, zobacz [porady: Dostosowywanie wyglądu komórek w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) i [porady: Ustawianie stylów czcionek i koloru w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [Instrukcje: sprawdzanie poprawności danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control.md)  
 [Przewodnik: obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [Ochrona informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md)
