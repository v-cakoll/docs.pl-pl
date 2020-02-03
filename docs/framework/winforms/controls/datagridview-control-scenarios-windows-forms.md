---
title: Scenariusze formantu DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], about data grids
- DataGridView control [Windows Forms], scenarios
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
ms.openlocfilehash: 160d967c6445fb753cb6c73babfb02a734a07e28
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742463"
---
# <a name="datagridview-control-scenarios-windows-forms"></a>Scenariusze formantu DataGridView (Formularze systemu Windows)
Za pomocą kontrolki <xref:System.Windows.Forms.DataGridView> można wyświetlać dane tabelaryczne z różnych źródeł danych. W przypadku prostych operacji można ręcznie wypełnić <xref:System.Windows.Forms.DataGridView> i manipulować danymi bezpośrednio przez formant. Zwykle jednak dane będą przechowywane w zewnętrznym źródle danych i powiązane z nim formant przez składnik <xref:System.Windows.Forms.BindingSource>.  
  
 W tym temacie opisano niektóre typowe scenariusze, które obejmują formant <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="scenario-1-displaying-small-amounts-of-data"></a>Scenariusz 1: wyświetlanie małych ilości danych  
 Nie jest konieczne przechowywanie danych w zewnętrznym źródle danych, aby wyświetlić je w kontrolce <xref:System.Windows.Forms.DataGridView>. Jeśli pracujesz z małą ilością danych, możesz samodzielnie wypełnić formant i manipulować danymi za pomocą kontrolki. Jest to nazywane *trybem niezwiązanym*. Aby uzyskać więcej informacji, zobacz [How to: Create a Unbound Windows Forms DataGridView Control](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Punkty kluczowych scenariuszy  
  
- W trybie niezwiązanym należy ręcznie wypełnić formant.  
  
- Tryb niepowiązany jest szczególnie dostosowany do małych ilości danych tylko do odczytu.  
  
- Tryb niezwiązany jest również dostosowany do tabel przypominających arkusze kalkulacyjne lub rozrzedzonie.  
  
## <a name="scenario-2-viewing-and-updating-data-stored-in-an-external-data-source"></a>Scenariusz 2: przeglądanie i aktualizowanie danych przechowywanych w zewnętrznym źródle danych  
 Można użyć formantu <xref:System.Windows.Forms.DataGridView> jako interfejsu użytkownika, za pomocą którego użytkownicy mogą uzyskać dostęp do danych przechowywanych w źródle danych, takim jak tabela bazy danych lub kolekcja obiektów firmowych. Aby uzyskać więcej informacji, zobacz [How to: bind Data w formancie DataGridView Windows Forms](how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Punkty kluczowych scenariuszy  
  
- Tryb powiązania pozwala połączyć się ze źródłem danych, automatycznie generować kolumny na podstawie właściwości źródła danych lub kolumn bazy danych, a także automatycznie wypełniać formant.  
  
- Tryb związany jest przystosowany do dużego oddziaływania użytkowników z danymi. Dane można sformatować do wyświetlania, a dane określone przez użytkownika można analizować w formacie oczekiwanym przez źródło danych. Błędy formatowania wprowadzania danych i błędy ograniczeń bazy danych mogą być wykrywane, aby użytkownicy mogli być ostrzegani i poprawiać błędne komórki.  
  
- Dodatkowe funkcje, takie jak sortowanie kolumn, zamrażanie i zmiana kolejności, umożliwiają użytkownikom wyświetlanie danych w sposób najbardziej wygodny dla ich przepływu pracy.  
  
- Obsługa Schowka umożliwia użytkownikom kopiowanie danych z aplikacji do innych aplikacji.  
  
## <a name="scenario-3-advanced-data"></a>Scenariusz 3: zaawansowane dane  
 W przypadku specjalnych potrzeb, aby model powiązania danych standardowych nie był adresem, można zarządzać interakcją między formantem i danymi przez zaimplementowanie *trybu wirtualnego*. Implementacja trybu wirtualnego oznacza implementację co najmniej jednego programu obsługi zdarzeń, który umożliwia kontrolowanie informacji o komórkach, ponieważ są one zbędne.  
  
 Na przykład jeśli pracujesz z dużymi ilościami danych, możesz chcieć zaimplementować tryb wirtualny, aby zapewnić optymalną wydajność. Tryb wirtualny jest również przydatny do obsługi wartości kolumn niepowiązanych, które są wyświetlane wraz z kolumnami pobranymi z innego źródła danych.  
  
 Aby uzyskać więcej informacji na temat trybu wirtualnego, zobacz [Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Punkty kluczowych scenariuszy  
  
- Tryb wirtualny jest odpowiedni do wyświetlania bardzo dużych ilości danych, gdy trzeba poprawić wydajność.  
  
## <a name="scenario-4-automatically-resizing-rows-and-columns"></a>Scenariusz 4: automatyczne zmienianie rozmiarów wierszy i kolumn  
 Podczas wyświetlania regularnie aktualizowanych danych można automatycznie zmieniać rozmiar wierszy i kolumn, aby upewnić się, że cała zawartość jest widoczna. Kontrolka <xref:System.Windows.Forms.DataGridView> udostępnia kilka opcji umożliwiających włączenie lub wyłączenie ręcznego zmieniania rozmiaru, zmianę rozmiaru programowo w określonych godzinach lub automatyczne zmianę rozmiaru przy każdej zmianie zawartości. Aby uzyskać więcej informacji, zobacz [Opcje ustalania rozmiarów w kontrolce DataGridView Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Punkty kluczowych scenariuszy  
  
- Ręczna zmiana rozmiarów umożliwia użytkownikom dostosowanie wysokości i szerokości komórek.  
  
- Automatyczna Zmienianie rozmiaru pozwala zachować rozmiary komórek, tak aby zawartość komórki nigdy nie była obcinana.  
  
- Programowe zmiany rozmiaru umożliwiają zmianę rozmiaru komórek w określonych porach, aby uniknąć pogorszenia wydajności ciągłego automatycznego zmieniania rozmiaru.  
  
## <a name="scenario-5-simple-customization"></a>Scenariusz 5: proste Dostosowywanie  
 Formant <xref:System.Windows.Forms.DataGridView> zapewnia wiele sposobów zmiany podstawowego wyglądu i zachowania. Aby uzyskać więcej informacji, zobacz [style komórek w kontrolce DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Punkty kluczowych scenariuszy  
  
- obiekty <xref:System.Windows.Forms.DataGridViewCellStyle> umożliwiają udostępnianie informacji o kolorach, czcionkach, formatowaniu i rozmieszczenia na wielu poziomach i dla poszczególnych elementów formantu.  
  
- Style komórki mogą być warstwowe i współużytkowane przez wiele elementów, umożliwiając ponowne użycie kodu.  
  
## <a name="scenario-6-advanced-customization"></a>Scenariusz 6: zaawansowane dostosowywanie  
 Formant <xref:System.Windows.Forms.DataGridView> zapewnia wiele sposobów dostosowywania wyglądu i zachowania.  
  
### <a name="scenario-key-points"></a>Punkty kluczowych scenariuszy  
  
- Możesz podać własny kod malowania komórek. Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie wyglądu komórek w kontrolce DataGridView Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md).  
  
- Możesz zapewnić własne malowanie wierszy. Jest to przydatne na przykład w celu utworzenia wierszy zawierających zawartość obejmującą wiele kolumn. Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie wyglądu wierszy w kontrolce DataGridView Windows Forms](customize-the-appearance-of-rows-in-the-datagrid.md).  
  
- Możesz zaimplementować własne klasy komórek i kolumn, aby dostosować wygląd komórki. Aby uzyskać więcej informacji, zobacz [How to: dostosowywanie komórek i kolumn w kontrolce DataGridView Windows Forms przez rozszerzenie ich zachowania i wyglądu](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md).  
  
- Można zaimplementować własne klasy komórek i kolumn do kontrolek hosta innych niż podane przez wbudowane typy kolumn. Aby uzyskać więcej informacji, zobacz [How to: Host Controls in Windows Forms DataGridView Cells](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView, kontrolka — omówienie](datagridview-control-overview-windows-forms.md)
