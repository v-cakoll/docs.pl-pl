---
title: Scenariusze formantu DataGridView (Formularze systemu Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], about data grids
- DataGridView control [Windows Forms], scenarios
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
ms.openlocfilehash: 52c448f21be056e6166334785943356039baf3ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175295"
---
# <a name="datagridview-control-scenarios-windows-forms"></a>Scenariusze formantu DataGridView (Formularze systemu Windows)
Za pomocą <xref:System.Windows.Forms.DataGridView> kontrolki, można wyświetlić dane tabelaryczne z różnych źródeł danych. Do prostych zastosowań, możesz ręcznie wypełnić <xref:System.Windows.Forms.DataGridView> i manipulowanie danymi bezpośrednio za pomocą formantu. Zwykle jednak będzie przechowywać dane w zewnętrznym źródle danych i powiązywanie formantu do niego za pośrednictwem <xref:System.Windows.Forms.BindingSource> składnika.  
  
 W tym temacie opisano niektóre typowe scenariusze, które obejmują <xref:System.Windows.Forms.DataGridView> kontroli.  
  
## <a name="scenario-1-displaying-small-amounts-of-data"></a>Scenariusz 1: Wyświetlanie małe ilości danych  
 Nie masz do przechowywania danych w zewnętrznym źródle danych do wyświetlenia go w <xref:System.Windows.Forms.DataGridView> kontroli. Jeśli pracujesz z małą ilością danych, możesz samodzielnie wypełnienia kontrolki i manipulowanie danymi za pomocą formantu. Jest to nazywane *Tryb niepowiązany*. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie formantu DataGridView formularzy Windows niepowiązanych](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Scenariusz kluczowe punkty  
  
-   W trybie niepowiązanych możesz ręcznie wypełnić formantu.  
  
-   Tryb niepowiązany jest szczególnie przydatna w przypadku małych ilości danych tylko do odczytu.  
  
-   Tryb niepowiązany jest również odpowiedni dla przypominającego arkusz kalkulacyjny lub słabo wypełnionych tabel.  
  
## <a name="scenario-2-viewing-and-updating-data-stored-in-an-external-data-source"></a>Scenariusz 2: Wyświetlanie i aktualizowanie danych przechowywanych w zewnętrznym źródle danych  
 Możesz użyć <xref:System.Windows.Forms.DataGridView> powinna być kontrolka interfejsu użytkownika (UI) za pośrednictwem użytkowników, którzy mają dostęp do danych przechowywane w źródle danych, takich jak tabela bazy danych lub kolekcji obiektów biznesowych. Aby uzyskać więcej informacji, zobacz [jak: Powiązywanie danych Windows formantu DataGridView formularzy](how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Scenariusz kluczowe punkty  
  
-   Tryb powiązanej pozwala połączyć się ze źródłem danych, automatyczne generowanie kolumn na podstawie właściwości źródła danych lub kolumny bazy danych i automatycznie wypełniać formantu.  
  
-   Tryb powiązanej nadaje się do interakcji z użytkownikiem mocno z danymi. Dane mogą być sformatowane do wyświetlania i można przeanalizować określonych przez użytkownika danych do formatu oczekiwanego przez źródło danych. Wprowadzanie danych, formatowanie, błędy i błędy ograniczenie bazy danych może zostać wykryte, dzięki czemu użytkownicy mogą ostrzegani i błędne komórek można rozwiązać.  
  
-   Dodatkowe funkcje, takie jak sortowanie kolumn, zawiesza się i zmienianie kolejności umożliwiają użytkownikom wyświetlanie danych w taki sposób, jak najwygodniejszy dla przepływu pracy.  
  
-   Obsługa Schowka umożliwia użytkownikom skopiować dane z aplikacji do innych aplikacji.  
  
## <a name="scenario-3-advanced-data"></a>Scenariusz 3: Advanced Data  
 Jeśli masz specjalne potrzeby pokonywania modelu powiązanie danych w warstwie standardowa nie, można zarządzać interakcji między formantem i dane przez zaimplementowanie *trybu wirtualnego*. Implementowanie trybu wirtualnego oznacza Implementowanie obsługi zdarzeń, umożliwiających kontroli żądanie informacji o komórek jak informacje jest wymagana.  
  
 Na przykład jeśli pracujesz z dużymi ilościami danych, warto Implementowanie trybu wirtualnego w celu zapewnienia optymalnej wydajności. Tryb wirtualny jest również przydatne do przechowywania wartości niepowiązanych kolumn, które wyświetlają wraz z kolumnami pobrane z innego źródła danych.  
  
 Aby uzyskać więcej informacji na temat trybu wirtualnego zobacz [instruktażu: Implementowanie trybu wirtualnego w Windows formantu DataGridView formularzy](implementing-virtual-mode-wf-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Scenariusz kluczowe punkty  
  
-   Tryb wirtualny nadaje się do wyświetlania dużych ilości danych, gdy trzeba dostrajania wydajności.  
  
## <a name="scenario-4-automatically-resizing-rows-and-columns"></a>Scenariusz 4: Automatyczna zmiana rozmiaru wierszy i kolumn  
 Podczas wyświetlania danych, która jest regularnie aktualizowana, możesz automatycznie zmienić rozmiar wierszy i kolumn, aby upewnić się, że cała zawartość jest widoczna. <xref:System.Windows.Forms.DataGridView> Control oferuje kilka opcji umożliwiających Włącz lub wyłącz ręczne zmiany rozmiaru, zmienić rozmiar programowo w określonym czasie lub zmiany rozmiaru automatycznie zawsze, gdy zmian zawartości. Aby uzyskać więcej informacji, zobacz [opcje ustalania rozmiaru w formancie DataGridView formularzy Windows](sizing-options-in-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Scenariusz kluczowe punkty  
  
-   Ręczna zmiana rozmiaru pozwala użytkownikom na dostosowanie komórek wysokości i szerokości.  
  
-   Automatyczna zmiana rozmiaru pozwala zachować rozmiary komórek, tak aby zawartość komórki nigdy nie zostanie obcięta.  
  
-   Programowe zmienianie rozmiaru pozwala na zmianę rozmiaru komórek w określonym czasie, aby uniknąć ciągłego automatyczną zmianę rozmiaru spadek wydajności.  
  
## <a name="scenario-5-simple-customization"></a>Scenariusz 5: Proste dostosowania  
 <xref:System.Windows.Forms.DataGridView> Control oferuje wiele sposobów na zmianę jego podstawowy wygląd i zachowanie. Aby uzyskać więcej informacji, zobacz [style komórki w formancie DataGridView formularzy Windows](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Scenariusz kluczowe punkty  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle> obiekty umożliwiają zapewnienie kolor, czcionki, formatowania i pozycjonowanie informacje, na różnych poziomach, jak i dla poszczególnych elementów kontrolki.  
  
-   Style komórki można warstwowe i współużytkowane przez wiele elementów, co pozwala na ponowne użycie kodu.  
  
## <a name="scenario-6-advanced-customization"></a>Scenariusz 6: Dostosowywanie zaawansowane  
 <xref:System.Windows.Forms.DataGridView> Control oferuje wiele sposobów, którą można dostosować wygląd i zachowanie.  
  
### <a name="scenario-key-points"></a>Scenariusz kluczowe punkty  
  
-   Możesz podać swój kod rysowania komórki. Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie wyglądu komórek w formancie DataGridView formularzy Windows](customize-the-appearance-of-cells-in-the-datagrid.md).  
  
-   Możesz podać własne malowania wiersza. Jest to przydatne, na przykład, aby utworzyć wiersze z zawartością, która obejmuje wiele kolumn. Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie wyglądu wierszy w formancie DataGridView formularzy Windows](customize-the-appearance-of-rows-in-the-datagrid.md).  
  
-   Można implementować własne klasy komórek i kolumn, aby dostosować wygląd komórki. Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie komórek i kolumn w Windows formantu DataGridView formularzy przez rozszerzanie ich zachowania i wyglądu](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md).  
  
-   Można implementować własne klasy komórek i kolumn do kontrolki hosta innych niż udostępniane przez typy wbudowane kolumn. Aby uzyskać więcej informacji, zobacz [jak: Kontrolki hosta w formularzach Windows Forms komórkach DataGridView](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView, kontrolka — omówienie](datagridview-control-overview-windows-forms.md)
