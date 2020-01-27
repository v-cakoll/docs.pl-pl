---
title: Obsługiwane źródła danych
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
ms.openlocfilehash: 83ce4bb0d6f0bf81bcad4e38af212dccc3483ca5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742312"
---
# <a name="data-sources-supported-by-windows-forms"></a>Źródła danych obsługiwane przez formularze systemu Windows
Tradycyjnie w aplikacjach użyto funkcji powiązania danych, aby korzystać z danych przechowywanych w bazach danych. Dzięki powiązaniu danych Windows Forms można uzyskać dostęp do danych z baz danych, a także danych w innych strukturach, takich jak tablice i kolekcje, o ile zostały spełnione pewne minimalne wymagania.  
  
## <a name="structures-to-bind-to"></a>Struktury do powiązania z  
 W Windows Forms można powiązać z wieloma różnymi strukturami, od prostych obiektów (prostego powiązania) do złożonych list, takich jak tabele danych ADO.NET (złożone powiązanie). W przypadku prostego powiązania Windows Forms obsługuje powiązania z właściwościami publicznymi obiektu prostego. Windows Forms powiązań opartych na liście zwykle wymaga, aby obiekt obsługiwał interfejs <xref:System.Collections.IList> lub interfejs <xref:System.ComponentModel.IListSource>. Ponadto, jeśli wiązanie odbywa się za pomocą składnika <xref:System.Windows.Forms.BindingSource>, można powiązać z obiektem, który obsługuje interfejs <xref:System.Collections.IEnumerable>. Aby uzyskać więcej informacji na temat interfejsów związanych z wiązaniem danych, zobacz [interfejsy powiązane z powiązaniem danych](interfaces-related-to-data-binding.md).  
  
 Na poniższej liście przedstawiono struktury, do których można powiązać w Windows Forms.  
  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingSource> jest najbardziej typowym Windows Forms źródłem danych i działa na serwerze proxy między kontrolkami źródła danych i Windows Forms. Wzorzec użycia ogólnego <xref:System.Windows.Forms.BindingSource> ma na celu powiązanie kontrolek z <xref:System.Windows.Forms.BindingSource> i powiązanie <xref:System.Windows.Forms.BindingSource> ze źródłem danych (na przykład ADO.NET tabela danych lub obiekt biznesowy). <xref:System.Windows.Forms.BindingSource> udostępnia usługi, które umożliwiają i ulepszają poziom obsługi powiązań danych. Na przykład Windows Forms na podstawie listy kontrolki, takie jak <xref:System.Windows.Forms.DataGridView> i <xref:System.Windows.Forms.ComboBox> nie obsługują bezpośrednio powiązania ze źródłami danych <xref:System.Collections.IEnumerable>, można włączyć ten scenariusz przez powiązanie przez <xref:System.Windows.Forms.BindingSource>. W takim przypadku <xref:System.Windows.Forms.BindingSource> przeprowadzi konwersję źródła danych na <xref:System.Collections.IList>.  
  
 Obiekty proste  
 Windows Forms obsługuje właściwości kontrolki powiązania danych z właściwościami publicznymi w wystąpieniu obiektu przy użyciu typu <xref:System.Windows.Forms.Binding>. Windows Forms obsługuje również kontrolki oparte na liście powiązań, takie jak <xref:System.Windows.Forms.ListControl> do wystąpienia obiektu, gdy jest używany <xref:System.Windows.Forms.BindingSource>.  
  
 Tablica lub kolekcja  
 Aby można było pełnić rolę źródła danych, na liście musi być zaimplementowany interfejs <xref:System.Collections.IList>; Przykładem może być tablica, która jest wystąpieniem klasy <xref:System.Array>. Aby uzyskać więcej informacji na temat tablic, zobacz [How to: Create a array of Objects (Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/487y7874(v=vs.100)).  
  
 Ogólnie rzecz biorąc należy używać <xref:System.ComponentModel.BindingList%601> podczas tworzenia list obiektów do powiązania danych. <xref:System.ComponentModel.BindingList%601> to ogólna wersja interfejsu <xref:System.ComponentModel.IBindingList>. Interfejs <xref:System.ComponentModel.IBindingList> rozszerza interfejs <xref:System.Collections.IList> przez dodanie właściwości, metod i zdarzeń niezbędnych do dwukierunkowego wiązania danych.  
  
 <xref:System.Collections.IEnumerable>  
 Formanty Windows Forms mogą być powiązane ze źródłami danych, które obsługują interfejs <xref:System.Collections.IEnumerable>, jeśli są one powiązane przez składnik <xref:System.Windows.Forms.BindingSource>.  
  
 ADO.NET obiektów danych  
 ADO.NET zapewnia wiele struktur danych, które są odpowiednie do powiązania z. Każdy z nich różni się w złożoności i złożoności.  
  
- <xref:System.Data.DataColumn>. <xref:System.Data.DataColumn> jest istotnym blokiem konstrukcyjnym <xref:System.Data.DataTable>, w którym wiele kolumn składa się z tabeli. Każda <xref:System.Data.DataColumn> ma właściwość <xref:System.Data.DataColumn.DataType%2A>, która określa rodzaj danych, które są przechowywane w kolumnie (na przykład marka typu "samochód" w tabeli opisującej samochody). Można prostie powiązać formant (na przykład właściwość <xref:System.Windows.Forms.Control.Text%2A> kontrolki <xref:System.Windows.Forms.TextBox>) do kolumny w tabeli danych.  
  
- <xref:System.Data.DataTable>. <xref:System.Data.DataTable> jest reprezentacją tabeli, z wierszami i kolumnami w ADO.NET. Tabela danych zawiera dwie kolekcje: <xref:System.Data.DataColumn>, reprezentujące kolumny danych w danej tabeli (co ostatecznie określa rodzaje danych, które można wprowadzić do tej tabeli), i <xref:System.Data.DataRow>, reprezentujące wiersze danych w danej tabeli. Można powiązać formant z informacjami zawartymi w tabeli danych (np. powiązać formant <xref:System.Windows.Forms.DataGridView> z tabelą danych). Jednak po powiązaniu z <xref:System.Data.DataTable>jest to naprawdę powiązanie z widokiem domyślnym tabeli.  
  
- <xref:System.Data.DataView>. <xref:System.Data.DataView> to dostosowany widok pojedynczej tabeli danych, który może być filtrowany lub posortowany. Widok danych to dane "migawka" używane przez kontrolki złożone powiązane. Możesz utworzyć proste powiązania lub złożoność powiązania z danymi w widoku danych, ale pamiętaj, że masz powiązanie ze stałym "obrazem" danych, a nie czystym, zaktualizowanym źródłem danych.  
  
- <xref:System.Data.DataSet>. <xref:System.Data.DataSet> to zbiór tabel, relacji i ograniczeń danych w bazie danych. Można utworzyć prostą lub złożoną powiązań z danymi w ramach zestawu danych, ale należy pamiętać, że powiązanie z domyślną <xref:System.Data.DataViewManager> dla <xref:System.Data.DataSet> (Zobacz następny punkt).  
  
- <xref:System.Data.DataViewManager>. <xref:System.Data.DataViewManager> to dostosowany widok całego <xref:System.Data.DataSet>, analogiczny do <xref:System.Data.DataView>, ale z zawartymi w nim relacjami. Za pomocą kolekcji <xref:System.Data.DataViewManager.DataViewSettings%2A> można ustawić domyślne filtry i opcje sortowania dla wszystkich widoków, które <xref:System.Data.DataViewManager> ma dla danej tabeli.  
  
## <a name="see-also"></a>Zobacz także

- [Powiadomienie o zmianie w powiązaniu danych w formularzach Windows Forms](change-notification-in-windows-forms-data-binding.md)
- [Wiązanie danych i formularzy Windows Forms](data-binding-and-windows-forms.md)
- [Wiązanie danych formularzy Windows Forms](windows-forms-data-binding.md)
