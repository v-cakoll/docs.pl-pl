---
title: Scenariusze formantu DataGridView (Formularze systemu Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], about data grids
- DataGridView control [Windows Forms], scenarios
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
ms.openlocfilehash: a320b40664e4fe2254109183731db346a5d7d0b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529041"
---
# <a name="datagridview-control-scenarios-windows-forms"></a>Scenariusze formantu DataGridView (Formularze systemu Windows)
Z <xref:System.Windows.Forms.DataGridView> sterowania, można wyświetlić dane tabelaryczne z różnych źródeł danych. Do prostych zastosowań, może ręcznie wypełnić <xref:System.Windows.Forms.DataGridView> i manipulowanie danymi bezpośrednio za pomocą formantu. Zazwyczaj można jednak będzie przechowywać dane w zewnętrznym źródłem danych i powiązać ją przy użyciu formantu <xref:System.Windows.Forms.BindingSource> składnika.  
  
 W tym temacie opisano niektóre typowe scenariusze, które obejmują <xref:System.Windows.Forms.DataGridView> formantu.  
  
## <a name="scenario-1-displaying-small-amounts-of-data"></a>Scenariusz 1: Wyświetlającą niewielką ilość danych  
 Nie masz do przechowywania danych w zewnętrznego źródła danych do wyświetlenia w <xref:System.Windows.Forms.DataGridView> formantu. Jeśli pracujesz z niewielką ilość danych, można wypełnić kontrolki użytkownika i manipulowanie danymi przy użyciu formantu. Ta metoda jest wywoływana *Tryb niepowiązany*. Aby uzyskać więcej informacji, zobacz [jak: utworzyć niezwiązanego formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Scenariusz punktów klucza  
  
-   W trybie niezwiązany należy ręcznie wypełnić kontrolki.  
  
-   Tryb niepowiązany jest szczególnie przydatna w przypadku małej ilości danych tylko do odczytu.  
  
-   Tryb niepowiązany również nadaje się do tabel przypominającą arkusz kalkulacyjny lub słabo wypełnione.  
  
## <a name="scenario-2-viewing-and-updating-data-stored-in-an-external-data-source"></a>Scenariusz 2: Przeglądanie i aktualizowanie danych przechowywanych w zewnętrznym źródłem danych  
 Można użyć <xref:System.Windows.Forms.DataGridView> kontrolować jako interfejs użytkownika (UI), przez użytkowników, którzy mają dostęp do danych przechowywane w źródle danych, takich jak tabeli bazy danych lub zestaw obiektów biznesowych. Aby uzyskać więcej informacji, zobacz [porady: powiązanie danych z formantem DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Scenariusz punktów klucza  
  
-   Tryb powiązanej pozwala połączyć się ze źródłem danych, automatyczne generowanie kolumn na podstawie właściwości źródła danych lub kolumny bazy danych i automatycznie wypełnić kontrolki.  
  
-   Tryb powiązane jest przeznaczone do duże interakcji z danymi. Dane mogą być sformatowana do wyświetlenia, a dane określone przez użytkownika może zostać rozpoznane formatu oczekiwanego przez źródło danych. Tak, aby użytkownicy mogą otrzymywać ostrzeżenie i błędne komórek można usunąć, można wykryć wprowadzania danych formatowania błędów i błędów ograniczenia bazy danych.  
  
-   Dodatkowe funkcje, takie jak sortowania kolumn, zamrażanie i zmianę kolejności Zezwól użytkownikom na wyświetlanie danych w taki sposób, jak najdogodniejszy ich przepływu pracy.  
  
-   Obsługa Schowka umożliwia kopiowanie danych z aplikacji do innych aplikacji.  
  
## <a name="scenario-3-advanced-data"></a>Scenariusz 3: Zaawansowane danych  
 Jeśli masz specjalnymi potrzebami usuwające modelu Powiązanie standardowe danych nie można zarządzać interakcji między formantem a danych dzięki implementacji *tryb wirtualny*. Implementowanie trybu wirtualnego oznacza Implementowanie obsługi zdarzeń, umożliwiających informacji żądania kontroli o komórek jako informacje są potrzebne.  
  
 Na przykład jeśli współpracujesz z dużą ilością danych, warto Implementowanie trybu wirtualnego w celu zapewnienia optymalnej wydajności. Tryb wirtualny jest również przydatne do przechowywania wartości niepowiązanych kolumn wyświetlanych wraz z kolumn pobrane z innego źródła danych.  
  
 Aby uzyskać więcej informacji o trybie wirtualnym, zobacz [wskazówki: Implementowanie trybu wirtualnego w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Scenariusz punktów klucza  
  
-   Tryb wirtualny nadaje się do wyświetlania bardzo dużych ilości danych, gdy zachodzi potrzeba poprawienia wydajności.  
  
## <a name="scenario-4-automatically-resizing-rows-and-columns"></a>Scenariusz 4: Automatyczna zmiana rozmiaru wierszy i kolumn  
 Podczas wyświetlania danych, która jest regularnie aktualizowana, można automatycznie zmienić rozmiar wierszy i kolumn, aby upewnić się, że cała zawartość jest widoczna. <xref:System.Windows.Forms.DataGridView> Kontrola zapewnia kilka opcji, które pozwalają Włącz lub wyłącz ręczne zmienianie rozmiaru, Zmień rozmiar programowo w określonym czasie lub zmiany rozmiaru automatycznie po każdej zmianie zmian zawartości. Aby uzyskać więcej informacji, zobacz [opcje rozmiaru w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Scenariusz punktów klucza  
  
-   Ręczne zmienianie rozmiaru umożliwia dostosowanie komórki wysokości i szerokości.  
  
-   Automatyczna zmiana rozmiaru pozwala zachować rozmiary komórki tak, aby zawartość komórki nigdy nie zostanie obcięta.  
  
-   Zmiana rozmiaru programowe pozwala na zmianę rozmiaru komórek w określonym czasie, aby uniknąć ciągłego automatyczną zmianę rozmiaru ograniczeń wydajności.  
  
## <a name="scenario-5-simple-customization"></a>Scenariusz 5: Dostosowywanie prosty  
 <xref:System.Windows.Forms.DataGridView> Kontrola zapewnia wiele sposobów zmieniania podstawowe wygląd i zachowanie. Aby uzyskać więcej informacji, zobacz [style komórki w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Scenariusz punktów klucza  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle> obiekty umożliwiają zapewnienie kolorów i czcionek, formatowanie i rozmieszczania informacje na różnych poziomach i dla poszczególnych elementów formantu.  
  
-   Style komórek można warstwowy i współużytkowane przez wiele elementów, co pozwala na ponowne użycie kodu.  
  
## <a name="scenario-6-advanced-customization"></a>Scenariusz 6: Dostosowywanie zaawansowane  
 <xref:System.Windows.Forms.DataGridView> Kontrola zapewnia wiele sposobów, którą można dostosować wygląd i zachowanie.  
  
### <a name="scenario-key-points"></a>Scenariusz punktów klucza  
  
-   Możesz podać swój kod rysowania komórki. Aby uzyskać więcej informacji, zobacz [porady: Dostosowywanie wyglądu komórek w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md).  
  
-   Możesz podać własne rysowania wiersza. Jest to przydatne, na przykład, aby utworzyć wiersze z zawartością, która obejmuje wielu kolumn. Aby uzyskać więcej informacji, zobacz [porady: Dostosowywanie wyglądu wierszy w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md).  
  
-   Można zaimplementować własnych klas komórek i kolumn, aby dostosować wygląd komórek. Aby uzyskać więcej informacji, zobacz [porady: dostosowywanie komórek i kolumn w formancie DataGridView formularzy systemu Windows przez rozszerzanie ich zachowania i wyglądu](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md).  
  
-   Można zaimplementować własnych klas komórek i kolumn do kontrolki hosta innych niż udostępniane przez typy wbudowane kolumn. Aby uzyskać więcej informacji, zobacz [porady: formanty hosta w komórkach DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 [DataGridView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)
