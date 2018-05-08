---
title: Podsumowanie informacji o technologii formantów DataGridView (Formularze systemu Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- data grids [Windows Forms], about data grids
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
ms.openlocfilehash: cafd832e7105540ae684dd1feb4b33ab74f72836
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="datagridview-control-technology-summary-windows-forms"></a>Podsumowanie informacji o technologii formantów DataGridView (Formularze systemu Windows)
Ten temat zawiera podsumowanie informacji o `DataGridView` kontroli i klasy, które obsługują jej zastosowania.  
  
 Wyświetlanie danych w formacie tabelarycznym jest zadaniem, które prawdopodobnie będą wykonywane. `DataGridView` Kontrolki została zaprojektowana jako kompletnego rozwiązania prezentacji danych w siatce.  
  
## <a name="keywords"></a>Słowa kluczowe  
 Formant DataGridView, BindingSource, tabeli, komórki, powiązania danych, tryb wirtualny  
  
## <a name="namespaces"></a>Namespaces  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
 <xref:System.Data?displayProperty=nameWithType>  
  
## <a name="related-technologies"></a>Powiązane technologie  
 `BindingSource`  
  
## <a name="background"></a>Tło  
 Projektanci interfejsu użytkownika często być konieczne do wyświetlenia użytkownikom danych tabelarycznych. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zapewnia wiele sposobów wyświetlania danych w tabeli lub siatki. `DataGridView` Kontroli reprezentuje najnowsze zmiany tej technologii dla aplikacji formularzy systemu Windows.  
  
 `DataGridView` Formant może wyświetlać wiersze danych z magazynu danych. Wiele typów magazynów danych są obsługiwane. Magazyn danych można zapisać proste, bez typu danych, takich jak tablicą jednowymiarową lub może on przechowywać wprowadzonych danych, takich jak <xref:System.Data.DataSet>. Aby uzyskać więcej informacji, zobacz [porady: powiązanie danych z formantem DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 `DataGridView` Kontrola zapewnia wydajny i elastyczny sposób wyświetlania danych w formacie tabelarycznym. Formant służy do wyświetlenia tylko do odczytu lub nie można edytować widoki małych bardzo dużych zestawów danych.  
  
 Można rozszerzyć `DataGridView` sterowania na kilka sposobów do tworzenia niestandardowych zachowania w aplikacji. Na przykład można programowo określić własne sortowanie algorytmów i własnych typów komórek. Można łatwo dostosować wygląd `DataGridView` kontroli, wybierając spośród kilku właściwości. Wiele typów magazynów danych może służyć jako źródła danych lub `DataGridView` formant może działać bez powiązane z nim źródła danych.  
  
## <a name="implementing-datagridview-classes"></a>Implementowanie klas DataGridView  
 Istnieje kilka sposobów, aby móc korzystać z `DataGridView` funkcji rozszerzeń formantu. Można dostosować wiele aspektów sterowanie za pośrednictwem właściwości i zdarzenia, ale niektóre dostosowania wymagają utworzenia nowej klasy pochodzące od istniejącego `DataGridView` klasy.  
  
 Najczęściej używane klasy podstawowe są `DataGridViewCell` i `DataGridViewColumn`. Mogą pochodzić własne klasy komórki z `DataGridViewCell` lub żadnej z jej klas podrzędnych. Mimo że dowolnego typu komórki można dodać do dowolnej kolumny, będzie zwykle również klasa wyprowadzona z Pomocnika kolumny z `DataGridViewColumn` obsługującego komórek danego typu niestandardowego komórki domyślnie.  
  
 Można zaimplementować `IDataGridViewEditingCell` interfejsu w klasie pochodnej komórki, aby utworzyć typ komórki ma funkcji edytowania, która nie obsługuje formantu w trybie edycji. Aby utworzyć formant, który może obsługiwać w komórce w trybie edycji, można zaimplementować `IDataGridViewEditingControl` interfejsu w klasie pochodnej z <xref:System.Windows.Forms.Control>.  
  
 Aby uzyskać więcej informacji, zobacz [porady: dostosowywanie komórek i kolumn w formancie DataGridView formularzy systemu Windows przez rozszerzanie ich zachowania i wyglądu](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md) i [porady: formanty hosta w komórkach DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="datagridview-classes-at-a-glance"></a>Klasy DataGridView w skrócie  
 <xref:System.Windows.Forms>  
  
|Obszar technologii|Elementy klasy/interfejsy/konfiguracji|  
|---------------------|-------------------------------------------------|  
|Powiązanie danych|<xref:System.Windows.Forms.BindingSource>|  
|Prezentacja danych|<xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DataGridViewCell> i klasy pochodne<br /><br /> <xref:System.Windows.Forms.DataGridViewRow> i klasy pochodne<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> i klasy pochodne<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|<xref:System.Windows.Forms.DataGridView> Rozszerzalność|<xref:System.Windows.Forms.DataGridViewCell> i klasy pochodne<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> i klasy pochodne<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## <a name="whats-new"></a>Nowości  
 <xref:System.Windows.Forms.DataGridView> Kontrolki została zaprojektowana jako kompletnego rozwiązania do wyświetlania danych tabelarycznych w formularzach systemu Windows. Należy rozważyć użycie <xref:System.Windows.Forms.DataGridView> kontrolować przed innych rozwiązań, takich jak <xref:System.Windows.Forms.DataGrid>, podczas tworzenia nowej aplikacji. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 <xref:System.Windows.Forms.DataGridView> Formant może działać Zamknij razem z <xref:System.Windows.Forms.BindingSource> składnika. Ten składnik została zaprojektowana jako podstawowego źródła danych formularza. Można zarządzać interakcji między <xref:System.Windows.Forms.DataGridView> typ źródła danych, niezależnie od danych i kontroli źródła.  
  
## <a name="see-also"></a>Zobacz też  
 [DataGridView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [DataGridView, kontrolka — architektura](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [Ochrona informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md)
