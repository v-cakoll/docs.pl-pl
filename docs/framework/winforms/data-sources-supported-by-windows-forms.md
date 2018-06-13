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
ms.openlocfilehash: 4705c8a7153e94fa1cd23cf6c2f622d5cd66ec77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541180"
---
# <a name="data-sources-supported-by-windows-forms"></a>Źródła danych obsługiwane przez formularze systemu Windows
Tradycyjnie wiązania danych został użyty w aplikacjach mógł korzystać z danych przechowywanych w bazach danych. Wiązanie danych formularzy systemu Windows, umożliwia dostęp do danych z baz danych, a także dane w inne struktury, takich jak kolekcje i tablic tak długo, jak zostały spełnione pewne wymagania minimalne.  
  
## <a name="structures-to-bind-to"></a>Struktury do tworzenia powiązań  
 W formularzach systemu Windows można powiązać szerokiej gamy struktury, od prostego obiektów (proste powiązanie) do list złożonych, takie jak tabele danych ADO.NET (złożone powiązanie). Proste powiązanie formularzy systemu Windows obsługuje powiązania właściwości publiczne dla prostego obiektu. Formularze systemu Windows oparte na liście powiązanie wymaga ogólnie rzecz biorąc, obiekt obsługuje <xref:System.Collections.IList> interfejsu lub <xref:System.ComponentModel.IListSource> interfejsu. Ponadto są wiązane z za pośrednictwem <xref:System.Windows.Forms.BindingSource> składnik, można powiązać obiektu, który obsługuje <xref:System.Collections.IEnumerable> interfejsu. Aby uzyskać więcej informacji na temat interfejsy dotyczące powiązania danych, zobacz [interfejsy dotyczące powiązania danych](../../../docs/framework/winforms/interfaces-related-to-data-binding.md).  
  
 Poniższa lista przedstawia struktur można powiązać w formularzach systemu Windows.  
  
 <xref:System.Windows.Forms.BindingSource>  
 A <xref:System.Windows.Forms.BindingSource> jest najbardziej typowe źródła danych formularzy systemu Windows, a także pełni proxy między źródłem danych i formanty formularzy systemu Windows. Ogólne <xref:System.Windows.Forms.BindingSource> wzorca użycia ma powiązanie formantów do <xref:System.Windows.Forms.BindingSource> i powiąż <xref:System.Windows.Forms.BindingSource> do źródła danych (na przykład tabeli danych ADO.NET lub obiekt biznesowy). <xref:System.Windows.Forms.BindingSource> Udostępnia usługi umożliwiające i zwiększyć poziom powiązanie obsługi danych. Na przykład listy formularzy systemu Windows na podstawie formantów takich jak <xref:System.Windows.Forms.DataGridView> i <xref:System.Windows.Forms.ComboBox> nie obsługują bezpośrednio powiązania <xref:System.Collections.IEnumerable> źródeł danych, można włączyć w tym scenariuszu przez powiązanie za pośrednictwem <xref:System.Windows.Forms.BindingSource>. W takim przypadku <xref:System.Windows.Forms.BindingSource> przekonwertuje źródła danych, aby <xref:System.Collections.IList>.  
  
 Prostych obiektów  
 Formularze systemu Windows obsługuje właściwości kontrolki powiązania danych właściwości publicznych na wystąpienie obiektu przy użyciu <xref:System.Windows.Forms.Binding> typu. Formularze systemu Windows umożliwia powiązanie formantów na podstawie listy, takich jak <xref:System.Windows.Forms.ListControl> do obiektu wystąpienia, gdy <xref:System.Windows.Forms.BindingSource> jest używany.  
  
 tablicą lub kolekcją  
 Do działania jako źródło danych, musi implementować listy <xref:System.Collections.IList> interfejsu; przykładem może być tablicę, która jest wystąpieniem <xref:System.Array> klasy. Aby uzyskać więcej informacji na tablice, zobacz [porady: tworzenie tablicy obiektów (Visual Basic)](http://msdn.microsoft.com/library/6b64e069-0387-400c-9081-3bdc581020c3).  
  
 Ogólnie rzecz biorąc, należy użyć <xref:System.ComponentModel.BindingList%601> podczas tworzenia list obiektów dla powiązania danych. <xref:System.ComponentModel.BindingList%601> jest ogólny wersja <xref:System.ComponentModel.IBindingList> interfejsu. <xref:System.ComponentModel.IBindingList> Rozszerza interfejs <xref:System.Collections.IList> interfejsu przez dodanie właściwości, metody i wymaganych przez powiązanie dwukierunkowe danych zdarzenia.  
  
 <xref:System.Collections.IEnumerable>  
 Formanty formularzy systemu Windows może być powiązana ze źródłami danych, które obsługują tylko <xref:System.Collections.IEnumerable> interfejsu, jeśli są one powiązane za pośrednictwem <xref:System.Windows.Forms.BindingSource> składnika.  
  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] obiekty danych  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] udostępnia szereg struktur danych jest odpowiedni dla powiązania. Każdy różni się w jego wiedzy i złożoności.  
  
-   <xref:System.Data.DataColumn>. A <xref:System.Data.DataColumn> jest istotne blokiem konstrukcyjnym <xref:System.Data.DataTable>, w tym liczbę kolumn w skład tabeli. Każdy <xref:System.Data.DataColumn> ma <xref:System.Data.DataColumn.DataType%2A> właściwość, która określa rodzaj danych blokad kolumny (na przykład utworzyć samochodów w tabelę opisującą samochodów). Możesz można prosty — wiązanie formantu (takich jak <xref:System.Windows.Forms.TextBox> formantu <xref:System.Windows.Forms.Control.Text%2A> właściwości) do kolumny w tabeli danych.  
  
-   <xref:System.Data.DataTable>. A <xref:System.Data.DataTable> jest reprezentacja tabelę, z wierszy i kolumn w [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]. Tabela danych zawiera dwie kolekcje: <xref:System.Data.DataColumn>, reprezentujący kolumn danych w danej tabeli (który określa rodzajów danych, które mogą być wprowadzane do tej tabeli), i <xref:System.Data.DataRow>, reprezentujący wierszy danych w danej tabeli. Możesz można złożone — wiązanie formantu z informacji zawartych w tabeli danych (np. powiązania <xref:System.Windows.Forms.DataGridView> formantu do tabeli danych). Jednak po powiązaniu do <xref:System.Data.DataTable>, masz naprawdę powiązanie z tabeli widok domyślny.  
  
-   <xref:System.Data.DataView>. A <xref:System.Data.DataView> jest dostosowany widok tabeli danych, którą można filtrować i sortować. Widok danych to dane "snapshot" używane przez formanty powiązane z złożone. Można proste powiązania lub zespolonych — wiązanie z danych w widoku danych, ale należy pamiętać, że są wiązane stałej "obraz" dane, a nie źródła czystą, aktualizowania danych.  
  
-   <xref:System.Data.DataSet>. A <xref:System.Data.DataSet> jest zbiorem tabel, relacje i ograniczenia danych w bazie danych. Można wiązania proste lub złożone — wiązanie danych w zestawie danych, ale należy pamiętać, że są powiązanie domyślne <xref:System.Data.DataViewManager> dla <xref:System.Data.DataSet> (zobacz następny punktor punktu).  
  
-   <xref:System.Data.DataViewManager>. A <xref:System.Data.DataViewManager> jest dostosowany widok całej <xref:System.Data.DataSet>, odpowiednikiem <xref:System.Data.DataView>, ale z relacjami uwzględnione. Z <xref:System.Data.DataViewManager.DataViewSettings%2A> kolekcji, można ustawić domyślne filtry i opcje sortowania dla dowolnego widoków który <xref:System.Data.DataViewManager> ma dla danej tabeli.  
  
## <a name="see-also"></a>Zobacz też  
 [Powiadomienie o zmianie w powiązaniu danych w formularzach Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [Wiązanie danych i formularzy Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Wiązanie danych formularzy Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)
