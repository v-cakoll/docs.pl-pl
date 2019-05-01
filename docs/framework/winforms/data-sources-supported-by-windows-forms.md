---
title: Źródła danych obsługiwane przez formularze systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- collections [Windows Forms], binding to
- OLE DB providers [Windows Forms], Windows Forms
- DataTable class [Windows Forms], binding and Windows Forms
- Windows Forms, data binding
- DataView class [Windows Forms], binding and Windows Forms
- DataViewManager class [Windows Forms], binding and Windows Forms
- Windows Forms, source data
- arrays [Windows Forms]
- data sources [Windows Forms]
- data providers [Windows Forms]
- DataSet class [Windows Forms], binding and Windows Forms
- data [Windows Forms], data providers
ms.assetid: 3d2c43f6-462b-4d35-9c86-13e9afe012e1
ms.openlocfilehash: b648d62c9128f0864d60ace1ca56700f594b78c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967092"
---
# <a name="data-sources-supported-by-windows-forms"></a>Źródła danych obsługiwane przez formularze systemu Windows
Tradycyjnie powiązanie danych został użyty w ramach aplikacji może korzystać z danych przechowywanych w bazach danych. Powiązanie danych formularzy Windows, umożliwia dostęp do danych z bazy danych, a także dane w innych strukturach, takich jak tablice i kolekcje, tak długo, jak niektóre minimalne wymagania zostały spełnione.  
  
## <a name="structures-to-bind-to"></a>Struktury, do powiązania  
 W formularzach Windows Forms, można powiązać cały szereg struktur, od prostego obiektów (proste powiązanie) do złożonych list, takich jak tabel danych ADO.NET (złożone powiązanie). Proste powiązanie formularzy Windows obsługuje powiązania właściwości publiczne dla prostego obiektu. Formularze Windows oparte na liście powiązań ogólnie wymaga obiekt obsługuje <xref:System.Collections.IList> interfejsu lub <xref:System.ComponentModel.IListSource> interfejsu. Ponadto są wiązane z za pośrednictwem <xref:System.Windows.Forms.BindingSource> składnik, można powiązać obiektu, który obsługuje <xref:System.Collections.IEnumerable> interfejsu. Aby uzyskać więcej informacji na temat interfejsy dotyczące wiązania danych, zobacz [interfejsy powiązane powiązanie danych](interfaces-related-to-data-binding.md).  
  
 Na poniższej liście przedstawiono struktur, że można powiązać w formularzach Windows Forms.  
  
 <xref:System.Windows.Forms.BindingSource>  
 Element <xref:System.Windows.Forms.BindingSource> jest najbardziej typowe źródła danych Windows Forms i działa serwer proxy między źródłem danych i kontrolek formularzy Windows Forms. Ogólne <xref:System.Windows.Forms.BindingSource> wzorzec użycia jest do powiązania kontrolki <xref:System.Windows.Forms.BindingSource> i powiąż <xref:System.Windows.Forms.BindingSource> do źródła danych (na przykład tabela danych ADO.NET lub obiektem biznesowym). <xref:System.Windows.Forms.BindingSource> Udostępnia usługi, które umożliwiają i zwiększyć poziom pomocy technicznej powiązanie danych. Na przykład listy formularzy Windows podstawie formantów, takich jak <xref:System.Windows.Forms.DataGridView> i <xref:System.Windows.Forms.ComboBox> nie obsługują bezpośrednio powiązanie <xref:System.Collections.IEnumerable> źródeł danych, można włączyć w tym scenariuszu przez powiązanie za pośrednictwem <xref:System.Windows.Forms.BindingSource>. W tym przypadku <xref:System.Windows.Forms.BindingSource> przekonwertuje źródła danych, aby <xref:System.Collections.IList>.  
  
 Proste obiekty  
 Formularze Windows obsługuje właściwości kontrolki powiązania danych właściwości publicznych w wystąpieniu obiektu przy użyciu <xref:System.Windows.Forms.Binding> typu. Windows Forms również obsługuje powiązanie kontrolek na podstawie listy, takie jak <xref:System.Windows.Forms.ListControl> do obiektu wystąpienia, gdy <xref:System.Windows.Forms.BindingSource> jest używany.  
  
 tablicy lub kolekcji  
 Do działania jako źródło danych, należy zaimplementować listy <xref:System.Collections.IList> interfejsu; jeden przykładem może być tablica, która jest wystąpieniem <xref:System.Array> klasy. Aby uzyskać więcej informacji na temat tablic, zobacz [jak: Utwórz tablicę obiektów (Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/487y7874(v=vs.100)).  
  
 Ogólnie rzecz biorąc, należy użyć <xref:System.ComponentModel.BindingList%601> podczas tworzenia list obiektów dla powiązania danych. <xref:System.ComponentModel.BindingList%601> jest ogólny wersją <xref:System.ComponentModel.IBindingList> interfejsu. <xref:System.ComponentModel.IBindingList> Interfejs rozszerza <xref:System.Collections.IList> interfejsu przez dodanie właściwości, metody i zdarzenia wymagane dla powiązania danych dwukierunkowe.  
  
 <xref:System.Collections.IEnumerable>  
 Kontrolek formularzy Windows Forms może być powiązana ze źródłami danych, które obsługują tylko <xref:System.Collections.IEnumerable> interfejsu, jeśli są one powiązane za pośrednictwem <xref:System.Windows.Forms.BindingSource> składnika.  
  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] obiekty danych  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] zawiera szereg struktur danych odpowiednie dla wiązania. Każdy różni się w jego intensywniejsze i złożoności.  
  
- <xref:System.Data.DataColumn>. A <xref:System.Data.DataColumn> jest istotne blokiem konstrukcyjnym <xref:System.Data.DataTable>, w tym, że w skład liczbę kolumn tabeli. Każdy <xref:System.Data.DataColumn> ma <xref:System.Data.DataColumn.DataType%2A> właściwość, która określa rodzaj danych zawierająca kolumny (na przykład utworzyć samochodów w tabeli opisujące samochodów). Użytkownik może prosty wiązania kontrolki (takie jak <xref:System.Windows.Forms.TextBox> kontrolki <xref:System.Windows.Forms.Control.Text%2A> właściwość) do kolumny w tabeli danych.  
  
- <xref:System.Data.DataTable>. A <xref:System.Data.DataTable> trwa reprezentujący tabelę z wierszami i kolumnami, [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]. Tabela danych zawiera dwie kolekcje: <xref:System.Data.DataColumn>, reprezentujący kolumn danych w danej tabeli, (które określa rodzaje danych, które mogą być wprowadzane do tej tabeli), a <xref:System.Data.DataRow>, reprezentujący wierszy danych w danej tabeli. Użytkownik może złożone wiązania kontrolki do informacji zawartych w tabeli danych (np. powiązania <xref:System.Windows.Forms.DataGridView> kontrolki tabeli danych). Jednak gdy możesz powiązać <xref:System.Data.DataTable>, jest naprawdę powiązania do tabeli, widoku domyślnego.  
  
- <xref:System.Data.DataView>. Element <xref:System.Data.DataView> jest dostosowany widok przedstawiający jednej tabeli danych, filtrowania lub sortowania. Widok danych to dane "snapshot" używana przez formanty powiązane z złożone. Możesz można prostego powiązania lub złożone wiązania danych w widoku danych, ale należy pamiętać, której dokonywane jest wiązanie na stałym "obraz" zamiast źródła danych zawsze przejrzyste i aktualizowanie danych.  
  
- <xref:System.Data.DataSet>. Element <xref:System.Data.DataSet> jest zbiorem tabel, relacje i ograniczenia danych w bazie danych. Możesz prostego powiązania lub złożone wiązania danych w zestawie danych, ale należy pamiętać, której dokonywane jest wiązanie domyślną <xref:System.Data.DataViewManager> dla <xref:System.Data.DataSet> (zobacz następny punkt punkt).  
  
- <xref:System.Data.DataViewManager>. A <xref:System.Data.DataViewManager> jest dostosowany widok przedstawiający całą <xref:System.Data.DataSet>, jest odpowiednikiem <xref:System.Data.DataView>, z relacjami uwzględniony, ale. Za pomocą <xref:System.Data.DataViewManager.DataViewSettings%2A> kolekcji, można ustawić domyślne filtry i opcje sortowania dla dowolnego widoków, <xref:System.Data.DataViewManager> ma dla danej tabeli.  
  
## <a name="see-also"></a>Zobacz także

- [Powiadomienie o zmianie w powiązaniu danych w formularzach Windows Forms](change-notification-in-windows-forms-data-binding.md)
- [Wiązanie danych i formularzy Windows Forms](data-binding-and-windows-forms.md)
- [Wiązanie danych formularzy Windows Forms](windows-forms-data-binding.md)
