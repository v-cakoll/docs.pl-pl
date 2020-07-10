---
title: DataGridView — Informacje o formancie
description: Dowiedz się, jak używać kontrolki DataGridView Windows Forms do wyświetlania i edytowania danych tabelarycznych z wielu różnych rodzajów źródeł danych.
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
ms.openlocfilehash: 3e68f536853081453f6ba746d342bc016bc8ca17
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174617"
---
# <a name="datagridview-control-overview-windows-forms"></a>DataGridView — Informacje o formancie [Formularze systemu Windows]
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView>Formant zastępuje i dodaje funkcję do <xref:System.Windows.Forms.DataGrid> kontrolki; jednak <xref:System.Windows.Forms.DataGrid> kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Za pomocą <xref:System.Windows.Forms.DataGridView> kontrolki można wyświetlać i edytować dane tabelaryczne z wielu różnych rodzajów źródeł danych.  
  
 Powiązanie danych z <xref:System.Windows.Forms.DataGridView> formantem jest proste i intuicyjne, a w wielu przypadkach jest tak proste jak ustawienie <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwości. Po utworzeniu powiązania ze źródłem danych zawierającym wiele list lub tabel Ustaw <xref:System.Windows.Forms.DataGridView.DataMember%2A> Właściwość na ciąg, który określa listę lub tabelę, z którą ma zostać utworzone powiązanie.  
  
 <xref:System.Windows.Forms.DataGridView>Kontrolka obsługuje model powiązań danych w warstwie standardowa Windows Forms, więc zostanie powiązana z wystąpieniami klas opisanymi na poniższej liście:  
  
- Każda klasa implementująca <xref:System.Collections.IList> interfejs, w tym tablice jednowymiarowe.  
  
- Każda klasa implementująca <xref:System.ComponentModel.IListSource> interfejs, taka jak <xref:System.Data.DataTable> <xref:System.Data.DataSet> klasy i.  
  
- Każda klasa implementująca <xref:System.ComponentModel.IBindingList> interfejs, taka jak <xref:System.ComponentModel.BindingList%601> Klasa.  
  
- Każda klasa implementująca <xref:System.ComponentModel.IBindingListView> interfejs, taka jak <xref:System.Windows.Forms.BindingSource> Klasa.  
  
 <xref:System.Windows.Forms.DataGridView>Kontrolka obsługuje powiązanie danych z właściwościami publicznymi obiektów zwracanymi przez te interfejsy lub z kolekcją właściwości zwracaną przez <xref:System.ComponentModel.ICustomTypeDescriptor> interfejs, jeśli jest zaimplementowany dla zwracanych obiektów.  
  
 Zwykle powiązanie ze <xref:System.Windows.Forms.BindingSource> składnikiem i powiązanie <xref:System.Windows.Forms.BindingSource> składnika z innym źródłem danych lub wypełnienie go obiektami biznesowymi. <xref:System.Windows.Forms.BindingSource>Składnik jest preferowanym źródłem danych, ponieważ może być powiązany z wieloma różnymi źródłami danych i może automatycznie rozwiązywać wiele problemów z powiązaniem danych. Aby uzyskać więcej informacji, zobacz [Składnik BindingSource](bindingsource-component.md).  
  
 <xref:System.Windows.Forms.DataGridView>Formant może być również używany w trybie *niezwiązanym* bez podstawowego magazynu danych. Aby zapoznać się z przykładem kodu korzystającym z niepowiązanej <xref:System.Windows.Forms.DataGridView> kontrolki, zobacz [Przewodnik: Tworzenie niepowiązanej kontrolki DataGridView Windows Forms](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
 <xref:System.Windows.Forms.DataGridView>Formant jest wysoce konfigurowalny i rozszerzalny oraz zawiera wiele właściwości, metod i zdarzeń, aby dostosować jego wygląd i zachowanie. Jeśli chcesz, aby aplikacja Windows Forms wyświetlała dane tabelaryczne, rozważ użycie <xref:System.Windows.Forms.DataGridView> kontrolki przed innymi (na przykład <xref:System.Windows.Forms.DataGrid> ). Jeśli jest wyświetlana Mała siatka wartości tylko do odczytu lub jeśli użytkownik chce edytować tabelę przy użyciu milionów rekordów, <xref:System.Windows.Forms.DataGridView> formant zapewni łatwo programowalne, wydajne rozwiązanie pamięci.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [DataGridView, kontrolka — podsumowanie technologii](datagridview-control-technology-summary-windows-forms.md)  
 Podsumowuje <xref:System.Windows.Forms.DataGridView> koncepcje kontroli i używa powiązanych klas.  
  
 [DataGridView, kontrolka — architektura](datagridview-control-architecture-windows-forms.md)  
 Opisuje architekturę <xref:System.Windows.Forms.DataGridView> kontrolki, wyjaśniając jej hierarchię typów i strukturę dziedziczenia.  
  
 [DataGridView, kontrolka — scenariusze](datagridview-control-scenarios-windows-forms.md)  
 Opisuje najpopularniejsze scenariusze, w których <xref:System.Windows.Forms.DataGridView> są używane formanty.  
  
 [Katalog kodu formantu DataGridView](datagridview-control-code-directory-windows-forms.md)  
 Zawiera łącza do przykładów kodu w dokumentacji dotyczącej różnych <xref:System.Windows.Forms.DataGridView> zadań. Te przykłady są podzielone według typu zadania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy kolumn w formancie DataGridView formularzy systemu Windows](column-types-in-the-windows-forms-datagridview-control.md)  
 W tym artykule omówiono typy kolumn w <xref:System.Windows.Forms.DataGridView> kontrolce Windows Forms używane do wyświetlania informacji i Zezwalanie użytkownikom na modyfikowanie lub Dodawanie informacji.  
  
 [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)  
 Zawiera tematy opisujące sposób wypełniania kontrolki danymi ręcznie lub z zewnętrznego źródła danych.  
  
 [Dostosowywanie formantu DataGridView formularzy systemu Windows](customizing-the-windows-forms-datagridview-control.md)  
 Zawiera tematy, które opisują niestandardowe <xref:System.Windows.Forms.DataGridView> komórki i wiersze rysowania, a także tworzą pochodne komórki, kolumny i typy wierszy.  
  
 [Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Zawiera tematy opisujące sposób efektywnego używania kontrolki w celu uniknięcia problemów z wydajnością podczas pracy z dużymi ilościami danych.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView — Formant](datagridview-control-windows-forms.md)
- [Funkcje domyślne w formancie DataGridView formularzy systemu Windows](default-functionality-in-the-windows-forms-datagridview-control.md)
- [Domyślna obsługa myszy i klawiatury w kontrolce DataGridView formularzy Windows Forms](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
