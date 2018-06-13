---
title: 'Wskazówki: obsługa błędów występujących podczas wprowadzania danych w formancie DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
ms.openlocfilehash: 92525d1818160f5645b95948910547c7d1541897
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529237"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>Wskazówki: obsługa błędów występujących podczas wprowadzania danych w formancie DataGridView formularzy systemu Windows
Obsługa błędów z odpowiedni magazyn danych jest wymagana funkcja dla wprowadzania danych aplikacji. Formularze systemu Windows <xref:System.Windows.Forms.DataGridView> kontroli ułatwia to w przypadku wystawianego <xref:System.Windows.Forms.DataGridView.DataError> zdarzenie, które jest wywoływane, gdy magazyn danych wykryje naruszenie ograniczenia lub reguła biznesowa przerwane.  
  
 W tym przewodniku pobierze wiersze z `Customers` tabeli w bazie danych Northwind i wyświetlić je w <xref:System.Windows.Forms.DataGridView> formantu. Gdy duplikat `CustomerID` wartość zostanie wykryta w nowym wierszu lub edycji istniejącego wiersza, <xref:System.Windows.Forms.DataGridView.DataError> wystąpi zdarzenie, który będzie obsługiwany przez wyświetlanie <xref:System.Windows.Forms.MessageBox> opisujący wyjątek.  
  
 Aby skopiować kod w tym temacie na jednej liście, zobacz [porady: obsługa błędów czy występuje podczas wprowadzania danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W celu przeprowadzenia tego instruktażu potrzebne są:  
  
-   Dostęp do serwera z przykładowej bazy danych Northwind programu SQL Server.  
  
## <a name="creating-the-form"></a>Tworzenie formularza  
  
#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>Do obsługi błędów wprowadzania danych w formancie DataGridView  
  
1.  Utwórz klasę pochodną <xref:System.Windows.Forms.Form> i zawiera <xref:System.Windows.Forms.DataGridView> kontroli i <xref:System.Windows.Forms.BindingSource> składnika.  
  
     Poniższy przykład kodu zawiera podstawowe inicjowania oraz `Main` metody.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]  
  
2.  W definicji klasy formularza obsługi szczegóły połączenia z bazą danych, należy zaimplementować metodę.  
  
     W tym przykładzie kodu używane `GetData` metodę zwracającą wypełnione <xref:System.Data.DataTable> obiektu. Upewnij się, że możesz `connectionString` zmiennej na wartość, która jest odpowiednia dla Twojej bazy danych.  
  
    > [!IMPORTANT]
    >  Przechowywanie poufne informacje, takie jak hasła, w ciągu połączenia może mieć wpływ na bezpieczeństwo aplikacji. Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych. Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]  
  
3.  Implementowanie obsługi dla formularza użytkownika <xref:System.Windows.Forms.Form.Load> zdarzenie, które inicjuje <xref:System.Windows.Forms.DataGridView> i <xref:System.Windows.Forms.BindingSource> i konfiguruje wiązania danych.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]  
  
4.  Obsługa <xref:System.Windows.Forms.DataGridView.DataError> zdarzenia <xref:System.Windows.Forms.DataGridView>.  
  
     Kontekst dla błędu w przypadku operacji przekazywania, wyświetla błąd w <xref:System.Windows.Forms.MessageBox>.  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Teraz możesz przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.  
  
#### <a name="to-test-the-form"></a>Aby przetestować formularz  
  
-   Naciśnij klawisz F5, aby uruchomić aplikację.  
  
     Zobaczysz <xref:System.Windows.Forms.DataGridView> kontroli wypełnione przy użyciu danych z tabeli Klienci. Po wprowadzeniu zduplikowane wartości dla `CustomerID` i zatwierdzić edycji, wartość komórki zostanie automatycznie przywrócona i zostanie wyświetlony <xref:System.Windows.Forms.MessageBox> która zawiera błąd wpisywania danych.  
  
## <a name="next-steps"></a>Następne kroki  
 Ta aplikacja zawiera podstawowe <xref:System.Windows.Forms.DataGridView> funkcje formantu. Można dostosować wygląd i zachowanie <xref:System.Windows.Forms.DataGridView> sterowania na kilka sposobów:  
  
-   Zmienianie stylów obramowania i nagłówek. Aby uzyskać więcej informacji, zobacz [porady: Zmiana obramowania i style linii siatki w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
-   Włącz lub ograniczanie danych wejściowych użytkownika na <xref:System.Windows.Forms.DataGridView> formantu. Aby uzyskać więcej informacji, zobacz [porady: Zapobiegaj dodawaniu i usuwaniu rzędów do formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), i [jak: utworzyć tylko do odczytu w kolumn w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
-   Sprawdzanie poprawności danych wejściowych użytkownika na <xref:System.Windows.Forms.DataGridView> formantu. Aby uzyskać więcej informacji, zobacz [wskazówki: Sprawdzanie poprawności danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
-   Obsłużyć bardzo dużych zestawów danych przy użyciu trybu wirtualnego. Aby uzyskać więcej informacji, zobacz [wskazówki: Implementowanie trybu wirtualnego w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
-   Dostosowywanie wyglądu komórek. Aby uzyskać więcej informacji, zobacz [porady: Dostosowywanie wyglądu komórek w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) i [porady: Ustaw domyślnych stylów komórki dla formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [Instrukcje: obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [Przewodnik: sprawdzanie poprawności danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 [Ochrona informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md)
