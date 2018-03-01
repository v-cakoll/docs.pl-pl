---
title: "DataGridView — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6d9cc6568813af866acaf20696b870bedc3099be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="datagridview-control-overview-windows-forms"></a>DataGridView — Informacje o formancie [Formularze systemu Windows]
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Z <xref:System.Windows.Forms.DataGridView> sterowania, można wyświetlić i edytować dane tabelaryczne z wielu różnych rodzajów źródeł danych.  
  
 Wiązanie danych do <xref:System.Windows.Forms.DataGridView> formant jest bardzo proste i intuicyjne i w wielu przypadkach jest tak proste, jak ustawienie <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwości. Jeśli możesz powiązać ze źródłem danych, który zawiera wiele list lub tabele, należy skonfigurować <xref:System.Windows.Forms.DataGridView.DataMember%2A> właściwości na ciąg, który określa listy lub tabeli, aby powiązać.  
  
 <xref:System.Windows.Forms.DataGridView> Sterowanie obsługuje standardowy model powiązanie danych formularzy systemu Windows, więc będzie powiązać wystąpienia klas opisane na liście:  
  
-   Każda klasa implementująca <xref:System.Collections.IList> interfejs, w tym tablice jednowymiarowe.  
  
-   Każda klasa implementująca <xref:System.ComponentModel.IListSource> interfejsu, takich jak <xref:System.Data.DataTable> i <xref:System.Data.DataSet> klasy.  
  
-   Każda klasa implementująca <xref:System.ComponentModel.IBindingList> interfejsu, takich jak <xref:System.ComponentModel.BindingList%601> klasy.  
  
-   Każda klasa implementująca <xref:System.ComponentModel.IBindingListView> interfejsu, takich jak <xref:System.Windows.Forms.BindingSource> klasy.  
  
 <xref:System.Windows.Forms.DataGridView> Sterowanie obsługuje powiązanie danych właściwości publicznych zwracanych przez te interfejsy obiektów lub kolekcji właściwości zwróconej przez <xref:System.ComponentModel.ICustomTypeDescriptor> interfejsu, jeśli została zaimplementowana na zwracanych obiektów.  
  
 Zazwyczaj będzie można powiązać <xref:System.Windows.Forms.BindingSource> składnika i powiązania <xref:System.Windows.Forms.BindingSource> składnika do innego źródła danych lub umieścić w nim obiektów biznesowych. <xref:System.Windows.Forms.BindingSource> Składnika jest źródłem danych preferowane, ponieważ można powiązać z różnych źródeł danych i może automatycznie rozwiązać wiele problemów powiązania danych. Aby uzyskać więcej informacji, zobacz [BindingSource — składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md).  
  
 <xref:System.Windows.Forms.DataGridView> Formantu można używać w *niezwiązanego* trybie z nie odpowiedni magazyn danych. W przykładzie kodu używającej niezwiązanego <xref:System.Windows.Forms.DataGridView> sterowania, zobacz [wskazówki: utworzenie niezwiązanego formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
 <xref:System.Windows.Forms.DataGridView> Formant jest wysoce można konfigurować i rozszerzalny i oferuje wiele właściwości, metod i zdarzeń, aby dostosować wygląd i zachowanie. Do wyświetlania danych tabelarycznych aplikacji formularzy systemu Windows, należy rozważyć użycie <xref:System.Windows.Forms.DataGridView> kontroli przed innymi (na przykład <xref:System.Windows.Forms.DataGrid>). W przypadku wyświetlania Mała siatka wartości tylko do odczytu lub Jeśli włączasz użytkownika do edytowania tabeli z miliony rekordów, <xref:System.Windows.Forms.DataGridView> kontroli pozwoli łatwo programowalny, pamięci wydajne rozwiązanie.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [DataGridView, kontrolka — podsumowanie technologii](../../../../docs/framework/winforms/controls/datagridview-control-technology-summary-windows-forms.md)  
 Podsumowanie <xref:System.Windows.Forms.DataGridView> kontrolować pojęcia i korzystanie z powiązanymi klasami.  
  
 [DataGridView, kontrolka — architektura](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 Zawiera opis architektury <xref:System.Windows.Forms.DataGridView> kontroli wyjaśniający, jego typ struktury hierarchii i dziedziczenia.  
  
 [DataGridView, kontrolka — scenariusze](../../../../docs/framework/winforms/controls/datagridview-control-scenarios-windows-forms.md)  
 W tym artykule opisano najbardziej typowych scenariuszy, w którym <xref:System.Windows.Forms.DataGridView> formanty są używane.  
  
 [DataGridView, kontrolka — katalog kodu](../../../../docs/framework/winforms/controls/datagridview-control-code-directory-windows-forms.md)  
 Zawiera łącza do przykładów kodu w dokumentacji dla różnych <xref:System.Windows.Forms.DataGridView> zadania. Te przykłady są podzielone według typu zadań.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 W tym artykule omówiono typy kolumn w formularzach systemu Windows <xref:System.Windows.Forms.DataGridView> kontrolkę służącą do wyświetlania informacji i Zezwalaj użytkownikom na modyfikowanie lub dodawanie informacji.  
  
 [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 Zawiera tematy, które opisują sposób wypełnienia formantu z danymi w sposób ręczny lub z zewnętrznego źródła danych.  
  
 [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 Udostępnia tematów opisujących rysowania niestandardowych <xref:System.Windows.Forms.DataGridView> komórek i wierszy oraz tworzenie pochodnych komórki, kolumny i typy wierszy.  
  
 [Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Udostępnia tematów opisujących sposób efektywnie wykorzystać formantu, aby uniknąć problemów z wydajnością, podczas pracy z dużą ilością danych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [DataGridView, kontrolka](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Funkcje domyślne w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 [Domyślna obsługa myszy i klawiatury w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
