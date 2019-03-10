---
title: DataGridView — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- DataGridView
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- grid controls [Windows Forms]
- tables [Windows Forms], displaying in DataGridView control
- tables [Windows Forms], binding to DataGridView control
- columns [Windows Forms], DataGridView control
- bound controls [Windows Forms], dataGridView control
- datasets [Windows Forms], binding to DataGridView control
- data grids [Windows Forms], about data grids
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- grids [Windows Forms]
- data binding [Windows Forms], DataGridView control
- data sources [Windows Forms], binding to DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
ms.openlocfilehash: d7ff88f877f73382f69874c58392c3374a83c019
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57706003"
---
# <a name="datagridview-control-overview-windows-forms"></a>DataGridView — Informacje o formancie [Formularze systemu Windows]
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Za pomocą <xref:System.Windows.Forms.DataGridView> kontrolki, może wyświetlić i edytować dane tabelaryczne z wielu różnych rodzajów źródeł danych.  
  
 Powiązanie danych z <xref:System.Windows.Forms.DataGridView> kontroli jest bardzo prosty i intuicyjny, a w wielu przypadkach jest proste i polega na ustawienie <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwości. Gdy powiąże się ze źródłem danych, który zawiera kilka list lub tabel, ustaw <xref:System.Windows.Forms.DataGridView.DataMember%2A> właściwość ciągu, który określa listy lub tabeli, aby powiązać.  
  
 <xref:System.Windows.Forms.DataGridView> Kontroli obsługuje standardowe Windows Forms powiązanie modelu danych, więc powiąże wystąpień klas opisane na poniższej liście:  
  
-   Każda klasa implementująca <xref:System.Collections.IList> interfejsu, w tym tablice jednowymiarowe.  
  
-   Każda klasa implementująca <xref:System.ComponentModel.IListSource> interfejsu, takich jak <xref:System.Data.DataTable> i <xref:System.Data.DataSet> klasy.  
  
-   Każda klasa implementująca <xref:System.ComponentModel.IBindingList> interfejsu, takich jak <xref:System.ComponentModel.BindingList%601> klasy.  
  
-   Każda klasa implementująca <xref:System.ComponentModel.IBindingListView> interfejsu, takich jak <xref:System.Windows.Forms.BindingSource> klasy.  
  
 <xref:System.Windows.Forms.DataGridView> Kontrolka obsługuje powiązanie danych właściwości publicznych zwracanych przez te interfejsy obiektów lub kolekcji właściwości zwróconej przez <xref:System.ComponentModel.ICustomTypeDescriptor> interfejsu, jeśli wdrażane na zwracanych obiektów.  
  
 Zazwyczaj użytkownik zostanie z nim powiązane <xref:System.Windows.Forms.BindingSource> składnika i powiąż <xref:System.Windows.Forms.BindingSource> składnik do innego źródła danych lub go wypełnić przy użyciu obiektów biznesowych. <xref:System.Windows.Forms.BindingSource> Składnik to źródło danych preferowane, ponieważ można powiązać z wieloma różnymi źródłami danych i automatycznego rozwiązywania wielu problemów powiązanie danych. Aby uzyskać więcej informacji, zobacz [BindingSource, składnik](bindingsource-component.md).  
  
 <xref:System.Windows.Forms.DataGridView> Formantu można używać w *niepowiązanych* trybie z nie źródłowy magazyn danych. Dla przykładu kodu, który używa niepowiązanych <xref:System.Windows.Forms.DataGridView> sterowania, zobacz [instruktażu: Tworzenie Windows niezwiązanego formantu DataGridView formularzy](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
 <xref:System.Windows.Forms.DataGridView> Formant jest wysoce konfigurowalne i rozszerzalny i udostępnia wiele właściwości, metod i zdarzeń, aby dostosować wygląd i zachowanie. Aplikacja Windows Forms do wyświetlania danych tabelarycznych, należy rozważyć użycie <xref:System.Windows.Forms.DataGridView> formant przed innymi (na przykład <xref:System.Windows.Forms.DataGrid>). W przypadku wyświetlania Mała kratka wartości tylko do odczytu lub Jeśli włączasz użytkownikowi edytowanie tabelę zawierającą miliony rekordów, <xref:System.Windows.Forms.DataGridView> kontroli pozwoli łatwo programowalne, zapewniający wydajną obsługę pamięci rozwiązanie.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [DataGridView, kontrolka — podsumowanie technologii](datagridview-control-technology-summary-windows-forms.md)  
 Zawiera podsumowanie <xref:System.Windows.Forms.DataGridView> kontrolować pojęć i użytkowania powiązanych klas.  
  
 [DataGridView, kontrolka — architektura](datagridview-control-architecture-windows-forms.md)  
 W tym artykule opisano architekturę <xref:System.Windows.Forms.DataGridView> kontrolki, wyjaśniające, jego typ struktury hierarchii i dziedziczenia.  
  
 [DataGridView, kontrolka — scenariusze](datagridview-control-scenarios-windows-forms.md)  
 W tym artykule opisano najbardziej typowych scenariuszy, w którym <xref:System.Windows.Forms.DataGridView> formanty są używane.  
  
 [DataGridView, kontrolka — katalog kodu](datagridview-control-code-directory-windows-forms.md)  
 Zawiera łącza do przykładów kodu w dokumentacji dotyczącej różnych <xref:System.Windows.Forms.DataGridView> zadania. Te przykłady są pogrupowane według typu zadania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)  
 W tym artykule omówiono typy kolumn w formularzach Windows Forms <xref:System.Windows.Forms.DataGridView> kontrolkę służącą do wyświetlania informacji i zezwala użytkownikom na modyfikowanie lub dodawanie informacji.  
  
 [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)  
 Zawiera tematy, które opisują sposób wypełnienia kontrolki z danymi ręczny lub z zewnętrznego źródła danych.  
  
 [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](customizing-the-windows-forms-datagridview-control.md)  
 Zawiera tematy, które opisują niestandardowego rysowania <xref:System.Windows.Forms.DataGridView> komórek i wierszy oraz tworzenie pochodnych komórki, kolumny i typy wierszy.  
  
 [Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Zawiera tematy, które opisują sposób efektywnie wykorzystać formantu, aby uniknąć problemów z wydajnością podczas pracy z dużymi ilościami danych.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView, kontrolka](datagridview-control-windows-forms.md)
- [Funkcje domyślne w kontrolce DataGridView formularzy Windows Forms](default-functionality-in-the-windows-forms-datagridview-control.md)
- [Domyślna obsługa myszy i klawiatury w kontrolce DataGridView formularzy Windows Forms](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
