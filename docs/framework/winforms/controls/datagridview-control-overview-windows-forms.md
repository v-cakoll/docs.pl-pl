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
ms.openlocfilehash: 992bf57642c955a87cd7675e0bbe7c52131e8039
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969150"
---
# <a name="datagridview-control-overview-windows-forms"></a>DataGridView — Informacje o formancie [Formularze systemu Windows]
> [!NOTE]
> Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.DataGrid> do <xref:System.Windows.Forms.DataGrid> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.DataGridView> Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Za pomocą <xref:System.Windows.Forms.DataGridView> kontrolki można wyświetlać i edytować dane tabelaryczne z wielu różnych rodzajów źródeł danych.  
  
 Powiązanie danych z <xref:System.Windows.Forms.DataGridView> formantem jest proste i intuicyjne, a w wielu przypadkach jest tak proste jak <xref:System.Windows.Forms.DataGridView.DataSource%2A> ustawienie właściwości. Po utworzeniu powiązania ze źródłem danych zawierającym wiele list lub tabel Ustaw <xref:System.Windows.Forms.DataGridView.DataMember%2A> właściwość na ciąg, który określa listę lub tabelę, z którą ma zostać utworzone powiązanie.  
  
 <xref:System.Windows.Forms.DataGridView> Kontrolka obsługuje model powiązań danych w warstwie Standardowa Windows Forms, więc zostanie powiązana z wystąpieniami klas opisanymi na poniższej liście:  
  
- Każda klasa implementująca <xref:System.Collections.IList> interfejs, w tym tablice jednowymiarowe.  
  
- Każda klasa implementująca <xref:System.ComponentModel.IListSource> interfejs, taka <xref:System.Data.DataTable> jak klasy i <xref:System.Data.DataSet> .  
  
- Każda klasa implementująca <xref:System.ComponentModel.IBindingList> interfejs, taka <xref:System.ComponentModel.BindingList%601> jak Klasa.  
  
- Każda klasa implementująca <xref:System.ComponentModel.IBindingListView> interfejs, taka <xref:System.Windows.Forms.BindingSource> jak Klasa.  
  
 Kontrolka obsługuje powiązanie danych z właściwościami publicznymi obiektów zwracanymi przez te interfejsy lub z kolekcją właściwości zwracaną <xref:System.ComponentModel.ICustomTypeDescriptor> przez interfejs, jeśli jest zaimplementowany dla zwracanych obiektów. <xref:System.Windows.Forms.DataGridView>  
  
 Zwykle powiązanie ze <xref:System.Windows.Forms.BindingSource> składnikiem i <xref:System.Windows.Forms.BindingSource> powiązanie składnika z innym źródłem danych lub wypełnienie go obiektami biznesowymi. <xref:System.Windows.Forms.BindingSource> Składnik jest preferowanym źródłem danych, ponieważ może być powiązany z wieloma różnymi źródłami danych i może automatycznie rozwiązywać wiele problemów z powiązaniem danych. Aby uzyskać więcej informacji, zobacz [Składnik BindingSource](bindingsource-component.md).  
  
 Formant może być również używany w trybie niezwiązanym bez podstawowego magazynu danych. <xref:System.Windows.Forms.DataGridView> Aby zapoznać się z przykładem kodu korzystającym <xref:System.Windows.Forms.DataGridView> z niepowiązanej kontrolki, zobacz [Przewodnik: Tworzenie niepowiązanej kontrolki](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)DataGridView Windows Forms.  
  
 <xref:System.Windows.Forms.DataGridView> Formant jest wysoce konfigurowalny i rozszerzalny oraz zawiera wiele właściwości, metod i zdarzeń, aby dostosować jego wygląd i zachowanie. Jeśli chcesz, aby aplikacja Windows Forms wyświetlała dane tabelaryczne, rozważ użycie <xref:System.Windows.Forms.DataGridView> kontrolki przed innymi (na <xref:System.Windows.Forms.DataGrid>przykład). Jeśli jest wyświetlana Mała siatka wartości tylko do odczytu lub jeśli użytkownik chce edytować tabelę przy użyciu milionów rekordów, <xref:System.Windows.Forms.DataGridView> formant zapewni łatwo programowalne, wydajne rozwiązanie pamięci.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [DataGridView, kontrolka — podsumowanie technologii](datagridview-control-technology-summary-windows-forms.md)  
 Podsumowuje <xref:System.Windows.Forms.DataGridView> koncepcje kontroli i używa powiązanych klas.  
  
 [DataGridView, kontrolka — architektura](datagridview-control-architecture-windows-forms.md)  
 Opisuje architekturę <xref:System.Windows.Forms.DataGridView> kontrolki, wyjaśniając jej hierarchię typów i strukturę dziedziczenia.  
  
 [DataGridView, kontrolka — scenariusze](datagridview-control-scenarios-windows-forms.md)  
 Opisuje najpopularniejsze scenariusze, w których <xref:System.Windows.Forms.DataGridView> są używane formanty.  
  
 [DataGridView, kontrolka — katalog kodu](datagridview-control-code-directory-windows-forms.md)  
 Zawiera łącza do przykładów kodu w dokumentacji dotyczącej różnych <xref:System.Windows.Forms.DataGridView> zadań. Te przykłady są podzielone według typu zadania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)  
 W tym artykule omówiono typy kolumn w <xref:System.Windows.Forms.DataGridView> kontrolce Windows Forms używane do wyświetlania informacji i Zezwalanie użytkownikom na modyfikowanie lub Dodawanie informacji.  
  
 [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)  
 Zawiera tematy opisujące sposób wypełniania kontrolki danymi ręcznie lub z zewnętrznego źródła danych.  
  
 [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](customizing-the-windows-forms-datagridview-control.md)  
 Zawiera tematy, które opisują <xref:System.Windows.Forms.DataGridView> niestandardowe komórki i wiersze rysowania, a także tworzą pochodne komórki, kolumny i typy wierszy.  
  
 [Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Zawiera tematy opisujące sposób efektywnego używania kontrolki w celu uniknięcia problemów z wydajnością podczas pracy z dużymi ilościami danych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView, kontrolka](datagridview-control-windows-forms.md)
- [Funkcje domyślne w kontrolce DataGridView formularzy Windows Forms](default-functionality-in-the-windows-forms-datagridview-control.md)
- [Domyślna obsługa myszy i klawiatury w kontrolce DataGridView formularzy Windows Forms](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
