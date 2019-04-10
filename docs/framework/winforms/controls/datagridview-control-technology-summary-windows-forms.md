---
title: Podsumowanie informacji o technologii formantów DataGridView (Formularze systemu Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- data grids [Windows Forms], about data grids
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
ms.openlocfilehash: ca8268137f2a154c782388d0f13cdd02504cbb64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217422"
---
# <a name="datagridview-control-technology-summary-windows-forms"></a>Podsumowanie informacji o technologii formantów DataGridView (Formularze systemu Windows)
Ten temat zawiera podsumowanie informacji o `DataGridView` kontroli i klas, które obsługują jego użycia.  
  
 Wyświetlanie danych w formacie tabelarycznym jest zadaniem, które najprawdopodobniej będzie wykonywać często. `DataGridView` Kontrolki została zaprojektowana jako kompletne rozwiązanie do prezentowania danych w siatce.  
  
## <a name="keywords"></a>słowa kluczowe  
 DataGridView, BindingSource, tabeli, komórki, powiązań danych, tryb wirtualny  
  
## <a name="namespaces"></a>Namespaces  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
 <xref:System.Data?displayProperty=nameWithType>  
  
## <a name="related-technologies"></a>Powiązane technologie  
 `BindingSource`  
  
## <a name="background"></a>Tło  
 Projektowanie interfejsu użytkownika często okazać się konieczne do wyświetlenia użytkownikom dane tabelaryczne. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Oferuje kilka sposobów, aby wyświetlić dane w tabeli lub siatki. `DataGridView` Kontrolka reprezentuje najnowszy rozwój tej technologii dla aplikacji Windows Forms.  
  
 `DataGridView` Formant może wyświetlić wiersze danych z magazynu danych. Wiele typów magazynów danych są obsługiwane. Magazyn danych może zawierać proste, bez typu danych, takich jak jednowymiarowej tablicy, lub może on przechowywać typizowane dane, takie jak <xref:System.Data.DataSet>. Aby uzyskać więcej informacji, zobacz [jak: Powiązywanie danych Windows formantu DataGridView formularzy](how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 `DataGridView` Kontrola zapewnia wydajny i elastyczny sposób wyświetlania danych w formacie tabelarycznym. Można użyć formantu, aby pokazać tylko do odczytu lub edycji widoków niewielkich do bardzo dużych zestawów danych.  
  
 Możesz rozszerzyć `DataGridView` kontroli na kilka sposobów, aby tworzyć niestandardowe zachowanie w swoich aplikacjach. Na przykład można programowo określić własny algorytmy sortujące i swój własny typ komórki. Można łatwo dostosować wygląd `DataGridView` kontroli, wybierając między kilka właściwości. Wiele typów magazynów danych może służyć jako źródła danych lub `DataGridView` kontroli może działać bez źródła danych, w którym jest powiązana.  
  
## <a name="implementing-datagridview-classes"></a>Implementowanie klas DataGridView  
 Istnieją różne sposoby umożliwiające korzystanie z zalet `DataGridView` funkcji rozszerzeń kontrolki. Można dostosować wiele aspektów kontroli za pośrednictwem właściwości i zdarzenia, ale niektóre dostosowania konieczne do tworzenia nowych klas pochodzących od istniejącego `DataGridView` klasy.  
  
 Najczęściej używanych klas bazowych są `DataGridViewCell` i `DataGridViewColumn`. Uzyskujesz własne klasy komórki z `DataGridViewCell` lub dowolny z jej klas podrzędnych. Chociaż możesz dodać dowolny typ komórki do dowolnej kolumny, będzie zazwyczaj także klasa wyprowadzona z Pomocnika kolumny z `DataGridViewColumn` obsługujący komórek tego typu niestandardowego komórki domyślnie.  
  
 Możesz zaimplementować `IDataGridViewEditingCell` interfejsu w klasie pochodnej komórki do utworzenia typ komórki, która ma, funkcji edycji, ale nie obsługuje formant w trybie edycji. Aby utworzyć formant, który może obsługiwać w komórce w trybie edycji, możesz zaimplementować `IDataGridViewEditingControl` interfejsu w klasie pochodnej od <xref:System.Windows.Forms.Control>.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie komórek i kolumn w Windows formantu DataGridView formularzy przez rozszerzanie ich zachowania i wyglądu](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md) i [jak: Kontrolki hosta w formularzach Windows Forms komórkach DataGridView](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="datagridview-classes-at-a-glance"></a>Klasy DataGridView w skrócie  
 <xref:System.Windows.Forms>  
  
|Obszar technologiczny|Elementy klas/interfejsów/konfiguracji|  
|---------------------|-------------------------------------------------|  
|Powiązanie danych|<xref:System.Windows.Forms.BindingSource>|  
|Prezentacja danych|<xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DataGridViewCell> i klasy pochodne<br /><br /> <xref:System.Windows.Forms.DataGridViewRow> i klasy pochodne<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> i klasy pochodne<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|<xref:System.Windows.Forms.DataGridView> Rozszerzalność|<xref:System.Windows.Forms.DataGridViewCell> i klasy pochodne<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> i klasy pochodne<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## <a name="whats-new"></a>Nowości  
 <xref:System.Windows.Forms.DataGridView> Kontrolki została zaprojektowana jako kompletne rozwiązanie do wyświetlania danych tabelarycznych za pomocą interfejsu Windows Forms. Należy rozważyć użycie <xref:System.Windows.Forms.DataGridView> kontrolować przed innych rozwiązań, takich jak <xref:System.Windows.Forms.DataGrid>, podczas tworzenia nowej aplikacji. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 <xref:System.Windows.Forms.DataGridView> Kontroli może współpracować Zamknij z <xref:System.Windows.Forms.BindingSource> składnika. Ten składnik jest zaprojektowane jako podstawowego źródła danych formularza. Może zarządzać interakcji między <xref:System.Windows.Forms.DataGridView> kontroli i źródłem danych, niezależnie od tego, dane typu źródła.  
  
## <a name="see-also"></a>Zobacz także

- [DataGridView, kontrolka — omówienie](datagridview-control-overview-windows-forms.md)
- [DataGridView, kontrolka — architektura](datagridview-control-architecture-windows-forms.md)
- [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md)
