---
title: DataGridView — Informacje o formancie
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
ms.openlocfilehash: 74de5b449525be9ff93fcbef0ddabd041470177c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742497"
---
# <a name="datagridview-control-overview-windows-forms"></a>DataGridView — Informacje o formancie [Formularze systemu Windows]
> [!NOTE]
> Formant <xref:System.Windows.Forms.DataGridView> zamienia i dodaje funkcje do kontrolki <xref:System.Windows.Forms.DataGrid>; Niemniej jednak kontrolka <xref:System.Windows.Forms.DataGrid> jest zachowywana na potrzeby zgodności z poprzednimi wersjami i w przyszłości. Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Za pomocą kontrolki <xref:System.Windows.Forms.DataGridView> można wyświetlać i edytować dane tabelaryczne z wielu różnych rodzajów źródeł danych.  
  
 Powiązanie danych z formantem <xref:System.Windows.Forms.DataGridView> jest proste i intuicyjne, a w wielu przypadkach jest tak proste jak ustawienie właściwości <xref:System.Windows.Forms.DataGridView.DataSource%2A>. Po utworzeniu powiązania ze źródłem danych zawierającym wiele list lub tabel ustaw właściwość <xref:System.Windows.Forms.DataGridView.DataMember%2A> na ciąg, który określa listę lub tabelę, z którą ma zostać utworzone powiązanie.  
  
 Kontrolka <xref:System.Windows.Forms.DataGridView> obsługuje model powiązań danych w warstwie Standardowa Windows Forms, więc zostanie powiązana z wystąpieniami klas opisanymi na poniższej liście:  
  
- Każda klasa implementująca interfejs <xref:System.Collections.IList>, w tym tablice jednowymiarowe.  
  
- Każda klasa implementująca interfejs <xref:System.ComponentModel.IListSource>, taka jak klasy <xref:System.Data.DataTable> i <xref:System.Data.DataSet>.  
  
- Każda klasa implementująca interfejs <xref:System.ComponentModel.IBindingList>, taka jak Klasa <xref:System.ComponentModel.BindingList%601>.  
  
- Każda klasa implementująca interfejs <xref:System.ComponentModel.IBindingListView>, taka jak Klasa <xref:System.Windows.Forms.BindingSource>.  
  
 Formant <xref:System.Windows.Forms.DataGridView> obsługuje powiązanie danych z publicznymi właściwościami obiektów zwróconych przez te interfejsy lub do kolekcji właściwości zwracanych przez interfejs <xref:System.ComponentModel.ICustomTypeDescriptor>, jeśli zaimplementowano dla zwracanych obiektów.  
  
 Zazwyczaj utworzysz powiązanie ze składnikiem <xref:System.Windows.Forms.BindingSource> i powiążesz składnik <xref:System.Windows.Forms.BindingSource> z innym źródłem danych lub wypełnij je obiektami biznesowymi. Składnik <xref:System.Windows.Forms.BindingSource> jest preferowanym źródłem danych, ponieważ może być powiązany z wieloma różnymi źródłami danych i może automatycznie rozwiązywać wiele problemów z powiązaniem danych. Aby uzyskać więcej informacji, zobacz [Składnik BindingSource](bindingsource-component.md).  
  
 Formant <xref:System.Windows.Forms.DataGridView> może być również używany w trybie *niezwiązanym* bez podstawowego magazynu danych. Aby zapoznać się z przykładem kodu korzystającym z niepowiązanej kontrolki <xref:System.Windows.Forms.DataGridView>, zobacz [Przewodnik: Tworzenie niepowiązanego Windows Forms formantu DataGridView](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
 Formant <xref:System.Windows.Forms.DataGridView> jest wysoce konfigurowalny i rozszerzalny oraz zawiera wiele właściwości, metod i zdarzeń, aby dostosować jego wygląd i zachowanie. Jeśli chcesz, aby aplikacja Windows Forms wyświetlała dane tabelaryczne, rozważ użycie kontrolki <xref:System.Windows.Forms.DataGridView> przed innymi (na przykład <xref:System.Windows.Forms.DataGrid>). Jeśli jest wyświetlana Mała siatka wartości tylko do odczytu lub jeśli użytkownik chce edytować tabelę z milionami rekordów, formant <xref:System.Windows.Forms.DataGridView> zapewnia łatwo programowalne, wydajne rozwiązanie pamięci.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [DataGridView, kontrolka — podsumowanie technologii](datagridview-control-technology-summary-windows-forms.md)  
 Podsumowuje <xref:System.Windows.Forms.DataGridView> koncepcje kontroli i użycie powiązanych klas.  
  
 [DataGridView, kontrolka — architektura](datagridview-control-architecture-windows-forms.md)  
 Opisuje architekturę formantu <xref:System.Windows.Forms.DataGridView>, co wyjaśnia jego hierarchię typów i strukturę dziedziczenia.  
  
 [DataGridView, kontrolka — scenariusze](datagridview-control-scenarios-windows-forms.md)  
 Opisuje najczęstsze scenariusze, w których są używane kontrolki <xref:System.Windows.Forms.DataGridView>.  
  
 [DataGridView, kontrolka — katalog kodu](datagridview-control-code-directory-windows-forms.md)  
 Zawiera łącza do przykładów kodu w dokumentacji dotyczącej różnych <xref:System.Windows.Forms.DataGridView> zadań. Te przykłady są podzielone według typu zadania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)  
 W tym artykule omówiono typy kolumn w kontrolce <xref:System.Windows.Forms.DataGridView> Windows Forms używane do wyświetlania informacji i Zezwalanie użytkownikom na modyfikowanie lub Dodawanie informacji.  
  
 [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)  
 Zawiera tematy opisujące sposób wypełniania kontrolki danymi ręcznie lub z zewnętrznego źródła danych.  
  
 [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](customizing-the-windows-forms-datagridview-control.md)  
 Zawiera tematy opisujące niestandardowe malowanie <xref:System.Windows.Forms.DataGridView> komórek i wierszy oraz tworzenie pochodnej komórki, kolumny i typów wierszy.  
  
 [Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Zawiera tematy opisujące sposób efektywnego używania kontrolki w celu uniknięcia problemów z wydajnością podczas pracy z dużymi ilościami danych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView, kontrolka](datagridview-control-windows-forms.md)
- [Funkcje domyślne w kontrolce DataGridView formularzy Windows Forms](default-functionality-in-the-windows-forms-datagridview-control.md)
- [Domyślna obsługa myszy i klawiatury w kontrolce DataGridView formularzy Windows Forms](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
