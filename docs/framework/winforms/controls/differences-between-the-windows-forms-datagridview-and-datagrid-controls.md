---
title: Różnice między kontrolkami DataGridView i DataGrid
description: Poznaj różne różnice między funkcjami formantów DataGridView i DataGrid Windows Forms, a także różnice w ich architekturze.
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: 1438182d764097ae4f8fd7df046ad72c9213da19
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174591"
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Różnice między formantami DataGridView i DataGrid formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView>Kontrolka jest nową kontrolką, która zastępuje <xref:System.Windows.Forms.DataGrid> formant. <xref:System.Windows.Forms.DataGridView>Formant zawiera wiele podstawowych i zaawansowanych funkcji, których brakuje w <xref:System.Windows.Forms.DataGrid> formancie. Ponadto architektura <xref:System.Windows.Forms.DataGridView> kontrolki znacznie ułatwia ich rozbudowanie i dostosowywanie niż <xref:System.Windows.Forms.DataGrid> kontrolka.  
  
 W poniższej tabeli opisano kilka podstawowych funkcji dostępnych w <xref:System.Windows.Forms.DataGridView> kontrolce, które nie są dostępne w <xref:System.Windows.Forms.DataGrid> formancie.  
  
|DataGridView — funkcja formantu|Opis|  
|----------------------------------|-----------------|  
|Wiele typów kolumn|<xref:System.Windows.Forms.DataGridView>Formant zawiera więcej wbudowanych typów kolumn niż <xref:System.Windows.Forms.DataGrid> kontrolka. Te typy kolumn spełniają wymagania typowych scenariuszy, ale są również łatwiejsze do rozbudowania lub zastępowania niż typy kolumn w <xref:System.Windows.Forms.DataGrid> kontrolce. Aby uzyskać więcej informacji, zobacz [typy kolumn w kontrolce DataGridView Windows Forms](column-types-in-the-windows-forms-datagridview-control.md).|  
|Wiele sposobów wyświetlania danych|<xref:System.Windows.Forms.DataGrid>Kontrolka jest ograniczona do wyświetlania danych z zewnętrznego źródła danych. <xref:System.Windows.Forms.DataGridView>Kontrolka może jednak wyświetlać niepowiązane dane przechowywane w kontrolce, dane z powiązanego źródła danych lub powiązane i niepowiązane ze sobą. Możesz również zaimplementować tryb wirtualny w <xref:System.Windows.Forms.DataGridView> kontrolce, aby zapewnić możliwość zarządzania danymi niestandardowymi. Aby uzyskać więcej informacji, zobacz [tryby wyświetlania danych w kontrolce DataGridView Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md).|  
|Wiele sposobów dostosowywania wyświetlania danych|<xref:System.Windows.Forms.DataGridView>Formant zawiera wiele właściwości i zdarzeń, które umożliwiają określenie sposobu formatowania i wyświetlania danych. Na przykład można zmienić wygląd komórek, wierszy i kolumn w zależności od zawartych w nich danych lub zamienić dane jednego typu danych o równoważne dane innego typu. Aby uzyskać więcej informacji, zobacz [Formatowanie danych w kontrolce DataGridView Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md).|  
|Wiele opcji zmieniania wyglądu komórek, wierszy, kolumn i nagłówków oraz zachowanie|<xref:System.Windows.Forms.DataGridView>Kontrolka umożliwia pracy z pojedynczymi składnikami siatki na wiele sposobów. Można na przykład zablokować wiersze i kolumny, aby uniemożliwić ich przewijanie; ukrywanie wierszy, kolumn i nagłówków; Zmień sposób dopasowywania rozmiarów wierszy, kolumn i nagłówków; Zmień sposób dokonywania wyborów przez użytkowników; i udostępniaj etykietki narzędzi i menu skrótów dla poszczególnych komórek, wierszy i kolumn.|  
  
 <xref:System.Windows.Forms.DataGrid>Kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i specjalnych potrzeb. Dla niemal wszystkich celów należy użyć <xref:System.Windows.Forms.DataGridView> kontrolki. Jedyną funkcją dostępną w <xref:System.Windows.Forms.DataGrid> formancie, która nie jest dostępna w <xref:System.Windows.Forms.DataGridView> formancie, jest hierarchiczny sposób wyświetlania informacji z dwóch powiązanych tabel w jednym formancie. <xref:System.Windows.Forms.DataGridView>Aby wyświetlić informacje z dwóch tabel, które znajdują się w relacji głównej/szczegółowej, należy użyć dwóch kontrolek.  
  
## <a name="upgrading-to-the-datagridview-control"></a>Uaktualnianie do kontrolki DataGridView  
 Jeśli masz istniejące aplikacje, które używają <xref:System.Windows.Forms.DataGrid> formantu w prostym scenariuszu związanym z danymi bez dostosowań, możesz po prostu zastąpić stary formant nową kontrolką. Obie kontrolki używają standardowej architektury Windows Forms powiązań danych, więc <xref:System.Windows.Forms.DataGridView> kontrolka wyświetli powiązane dane bez konieczności dodatkowej konfiguracji. Warto jednak rozważyć skorzystanie z ulepszeń powiązań danych, ale przez powiązanie danych ze <xref:System.Windows.Forms.BindingSource> składnikiem, który można następnie powiązać z <xref:System.Windows.Forms.DataGridView> kontrolką. Aby uzyskać więcej informacji, zobacz [Składnik BindingSource](bindingsource-component.md).  
  
 Ponieważ <xref:System.Windows.Forms.DataGridView> kontrolka ma zupełnie nową architekturę, nie ma żadnej prostej ścieżki konwersji, która umożliwi używanie <xref:System.Windows.Forms.DataGrid> dostosowań z <xref:System.Windows.Forms.DataGridView> kontrolką. Nie <xref:System.Windows.Forms.DataGrid> jest to jednak wymagane w przypadku wielu dostosowań z <xref:System.Windows.Forms.DataGridView> kontrolką z powodu wbudowanych funkcji dostępnych w nowej kontrolce. Jeśli utworzono niestandardowe typy kolumn dla <xref:System.Windows.Forms.DataGrid> kontrolki, która ma być używana z <xref:System.Windows.Forms.DataGridView> kontrolką, należy wdrożyć je ponownie przy użyciu nowej architektury. Aby uzyskać więcej informacji, zobacz [Dostosowywanie kontrolki DataGridView Windows Forms](customizing-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView — Formant](datagridview-control-windows-forms.md)
- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
- [BindingSource, składnik](bindingsource-component.md)
- [Typy kolumn w formancie DataGridView formularzy systemu Windows](column-types-in-the-windows-forms-datagridview-control.md)
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Tryby wyświetlania danych w formancie DataGridView formularzy systemu Windows](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Formatowanie danych w kontrolce DataGridView formularzy Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md)
- [Opcje ustalania rozmiaru w kontrolce DataGridView formularzy Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md)
- [Tryb sortowania kolumn w kontrolce DataGridView formularzy Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Tryby wyboru w kontrolce DataGridView formularzy Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md)
- [Dostosowywanie formantu DataGridView formularzy systemu Windows](customizing-the-windows-forms-datagridview-control.md)
