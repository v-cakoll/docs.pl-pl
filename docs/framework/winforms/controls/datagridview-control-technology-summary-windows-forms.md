---
title: DataGridView, kontrolka — podsumowanie technologii
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- data grids [Windows Forms], about data grids
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
ms.openlocfilehash: 18eebd067df9768e14cc81258184551d00dd1402
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742477"
---
# <a name="datagridview-control-technology-summary-windows-forms"></a>Podsumowanie informacji o technologii formantów DataGridView (Formularze systemu Windows)
Ten temat zawiera podsumowanie informacji o kontrolce `DataGridView` i klasach, które obsługują jej użycie.  
  
 Wyświetlanie danych w formacie tabelarycznym to zadanie, które jest często wykonywane. Formant `DataGridView` zaprojektowano jako kompletne rozwiązanie do prezentowania danych w siatce.  
  
## <a name="keywords"></a>Słowa kluczowe  
 DataGridView, BindingSource, tabela, komórka, powiązanie danych, tryb wirtualny  
  
## <a name="namespaces"></a>{1&gt;Przestrzenie nazw&lt;1}  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
 <xref:System.Data?displayProperty=nameWithType>  
  
## <a name="related-technologies"></a>Technologie pokrewne  
 `BindingSource`  
  
## <a name="background"></a>Informacje dodatkowe  
 Projektanci interfejsu użytkownika często szukają niezbędnych do wyświetlenia danych tabelarycznych dla użytkowników. .NET Framework zapewnia kilka sposobów wyświetlania danych w tabeli lub siatce. Formant `DataGridView` reprezentuje najnowszy rozwój tej technologii dla aplikacji Windows Forms.  
  
 Kontrolka `DataGridView` może wyświetlać wiersze danych z magazynu danych. Obsługiwane są wiele typów magazynów danych. Magazyn danych może przechowywać proste, nietypu dane, na przykład tablicę jednowymiarową, lub może przechowywać dane wpisane, takie jak <xref:System.Data.DataSet>. Aby uzyskać więcej informacji, zobacz [How to: bind Data w formancie DataGridView Windows Forms](how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 Formant `DataGridView` zapewnia zaawansowany i elastyczny sposób wyświetlania danych w formacie tabelarycznym. Możesz użyć kontrolki, aby wyświetlić widoki tylko do odczytu lub do edycji dla małych i bardzo dużych zestawów danych.  
  
 Formant `DataGridView` można rozbudować na kilka sposobów, aby tworzyć niestandardowe zachowania w aplikacjach. Można na przykład programowo określić własne algorytmy sortowania i można utworzyć własne typy komórek. Wygląd formantu `DataGridView` można łatwo dostosować, wybierając spośród kilku właściwości. Wiele typów magazynów danych może służyć jako źródło danych lub formant `DataGridView` może działać bez powiązanego ze źródłem danych.  
  
## <a name="implementing-datagridview-classes"></a>Implementowanie klas DataGridView  
 Istnieje kilka sposobów na skorzystanie z zalet funkcji rozszerzalności formantu `DataGridView`. Można dostosować wiele aspektów kontrolki za pośrednictwem zdarzeń i właściwości, ale niektóre dostosowania wymagają utworzenia nowych klas pochodnych dla istniejących klas `DataGridView`.  
  
 Najczęściej używane klasy podstawowe są `DataGridViewCell` i `DataGridViewColumn`. Można utworzyć własną klasę komórek z `DataGridViewCell` lub dowolnej z jej klas podrzędnych. Mimo że można dodać dowolny typ komórki do dowolnej kolumny, zazwyczaj będzie również pochodna Klasa kolumny pomocniczej z `DataGridViewColumn`, która domyślnie hostuje komórki niestandardowego typu komórki.  
  
 Można zaimplementować interfejs `IDataGridViewEditingCell` w klasie komórki pochodnej, aby utworzyć typ komórki, która ma funkcje edycji, ale nie obsługuje kontrolki w trybie edycji. Aby utworzyć kontrolkę, którą można hostować w komórce w trybie edycji, można zaimplementować interfejs `IDataGridViewEditingControl` w klasie pochodnej z <xref:System.Windows.Forms.Control>.  
  
 Aby uzyskać więcej informacji, zobacz [How to: dostosowywanie komórek i kolumn w kontrolce datagridview Windows Forms, rozszerzając ich zachowanie i wygląd](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md) oraz [sposób: kontrolki hosta w Windows Forms komórkach DataGridView](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="datagridview-classes-at-a-glance"></a>Klasy DataGridView w skrócie  
 <xref:System.Windows.Forms>  
  
|Obszar technologii|Klasy/interfejsy/elementy konfiguracji|  
|---------------------|-------------------------------------------------|  
|Powiązanie danych|<xref:System.Windows.Forms.BindingSource>|  
|Prezentacja danych|<xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DataGridViewCell> i klasy pochodne<br /><br /> <xref:System.Windows.Forms.DataGridViewRow> i klasy pochodne<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> i klasy pochodne<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|Rozszerzalność <xref:System.Windows.Forms.DataGridView>|<xref:System.Windows.Forms.DataGridViewCell> i klasy pochodne<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> i klasy pochodne<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## <a name="whats-new"></a>Nowości  
 Formant <xref:System.Windows.Forms.DataGridView> zaprojektowano jako kompletne rozwiązanie do wyświetlania danych tabelarycznych z Windows Forms. Należy rozważyć użycie kontrolki <xref:System.Windows.Forms.DataGridView> przed innymi rozwiązaniami, takimi jak <xref:System.Windows.Forms.DataGrid>, podczas tworzenia nowej aplikacji. Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Kontrolka <xref:System.Windows.Forms.DataGridView> może współpracować w bliskiej współpracy ze składnikiem <xref:System.Windows.Forms.BindingSource>. Ten składnik jest przeznaczony do podstawowego źródła danych formularza. Może ona zarządzać interakcją między kontrolką <xref:System.Windows.Forms.DataGridView> i jej źródłem danych, niezależnie od typu źródła danych.  
  
## <a name="see-also"></a>Zobacz także

- [DataGridView, kontrolka — omówienie](datagridview-control-overview-windows-forms.md)
- [DataGridView, kontrolka — architektura](datagridview-control-architecture-windows-forms.md)
- [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md)
