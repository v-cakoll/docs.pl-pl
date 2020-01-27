---
title: Różnice między kontrolkami DataGridView i DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: 3552abe55d8e2c1cb4ae372ca64c7ca21f1fed0e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745959"
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Różnice między formantami DataGridView i DataGrid formularzy systemu Windows
Formant <xref:System.Windows.Forms.DataGridView> jest nową kontrolką, która zastępuje formant <xref:System.Windows.Forms.DataGrid>. Kontrolka <xref:System.Windows.Forms.DataGridView> udostępnia wiele podstawowych i zaawansowanych funkcji, których brakuje w kontrolce <xref:System.Windows.Forms.DataGrid>. Ponadto architektura formantu <xref:System.Windows.Forms.DataGridView> ułatwia jego rozbudowanie i dostosowywanie niż kontrolka <xref:System.Windows.Forms.DataGrid>.  
  
 W poniższej tabeli opisano niektóre podstawowe funkcje dostępne w kontrolce <xref:System.Windows.Forms.DataGridView>, których brakuje w kontrolce <xref:System.Windows.Forms.DataGrid>.  
  
|DataGridView — funkcja formantu|Opis|  
|----------------------------------|-----------------|  
|Wiele typów kolumn|Formant <xref:System.Windows.Forms.DataGridView> zawiera więcej wbudowanych typów kolumn niż kontrolka <xref:System.Windows.Forms.DataGrid>. Te typy kolumn spełniają wymagania większości typowych scenariuszy, ale są również łatwiejsze do przeciągnięcia lub zastępowania niż typy kolumn w kontrolce <xref:System.Windows.Forms.DataGrid>. Aby uzyskać więcej informacji, zobacz [typy kolumn w kontrolce DataGridView Windows Forms](column-types-in-the-windows-forms-datagridview-control.md).|  
|Wiele sposobów wyświetlania danych|Formant <xref:System.Windows.Forms.DataGrid> jest ograniczony do wyświetlania danych z zewnętrznego źródła danych. Kontrolka <xref:System.Windows.Forms.DataGridView>, jednak może wyświetlać niepowiązane dane przechowywane w kontrolce, dane z powiązanego źródła danych lub powiązane i niepowiązane ze sobą. Możesz również zaimplementować tryb wirtualny w kontrolce <xref:System.Windows.Forms.DataGridView>, aby zapewnić możliwość zarządzania danymi niestandardowymi. Aby uzyskać więcej informacji, zobacz [tryby wyświetlania danych w kontrolce DataGridView Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md).|  
|Wiele sposobów dostosowywania wyświetlania danych|Formant <xref:System.Windows.Forms.DataGridView> zawiera wiele właściwości i zdarzeń, które umożliwiają określenie sposobu formatowania i wyświetlania danych. Na przykład można zmienić wygląd komórek, wierszy i kolumn w zależności od zawartych w nich danych lub zamienić dane jednego typu danych o równoważne dane innego typu. Aby uzyskać więcej informacji, zobacz [Formatowanie danych w kontrolce DataGridView Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md).|  
|Wiele opcji zmieniania wyglądu komórek, wierszy, kolumn i nagłówków oraz zachowanie|Formant <xref:System.Windows.Forms.DataGridView> umożliwia pracy z poszczególnymi składnikami siatki na wiele sposobów. Można na przykład zablokować wiersze i kolumny, aby uniemożliwić ich przewijanie; ukrywanie wierszy, kolumn i nagłówków; Zmień sposób dopasowywania rozmiarów wierszy, kolumn i nagłówków; Zmień sposób dokonywania wyborów przez użytkowników; i udostępniaj etykietki narzędzi i menu skrótów dla poszczególnych komórek, wierszy i kolumn.|  
  
 Kontrolka <xref:System.Windows.Forms.DataGrid> jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i specjalnych potrzeb. Dla niemal wszystkich celów należy użyć kontrolki <xref:System.Windows.Forms.DataGridView>. Jedyną funkcją dostępną w kontrolce <xref:System.Windows.Forms.DataGrid>, która nie jest dostępna w kontrolce <xref:System.Windows.Forms.DataGridView>, jest hierarchiczny sposób wyświetlania informacji z dwóch powiązanych tabel w jednym formancie. Aby wyświetlić informacje z dwóch tabel, które znajdują się w relacji głównej/szczegółowej, należy użyć dwóch formantów <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="upgrading-to-the-datagridview-control"></a>Uaktualnianie do kontrolki DataGridView  
 Jeśli masz istniejące aplikacje, które używają formantu <xref:System.Windows.Forms.DataGrid> w prostym scenariuszu związanym z danymi bez dostosowań, możesz po prostu zastąpić stary formant nową kontrolką. Obie kontrolki używają standardowej architektury powiązań danych Windows Forms, dzięki czemu formant <xref:System.Windows.Forms.DataGridView> będzie wyświetlał powiązane dane bez konieczności dodatkowej konfiguracji. Warto jednak rozważyć skorzystanie z ulepszeń związanych z tworzeniem powiązań danych, ale przez powiązanie danych ze składnikiem <xref:System.Windows.Forms.BindingSource>, który można następnie powiązać z kontrolką <xref:System.Windows.Forms.DataGridView>. Aby uzyskać więcej informacji, zobacz [Składnik BindingSource](bindingsource-component.md).  
  
 Ponieważ kontrolka <xref:System.Windows.Forms.DataGridView> ma całkowicie nową architekturę, nie ma żadnej prostej ścieżki konwersji, która umożliwia używanie dostosowań <xref:System.Windows.Forms.DataGrid> z kontrolką <xref:System.Windows.Forms.DataGridView>. Wiele niestandardowych dostosowań <xref:System.Windows.Forms.DataGrid> jest niepotrzebnych z kontrolką <xref:System.Windows.Forms.DataGridView> z powodu wbudowanych funkcji dostępnych w nowej kontrolce. Jeśli utworzono niestandardowe typy kolumn dla formantu <xref:System.Windows.Forms.DataGrid>, który ma być używany z kontrolką <xref:System.Windows.Forms.DataGridView>, trzeba będzie wdrożyć je ponownie przy użyciu nowej architektury. Aby uzyskać więcej informacji, zobacz [Dostosowywanie kontrolki DataGridView Windows Forms](customizing-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView, kontrolka](datagridview-control-windows-forms.md)
- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
- [BindingSource, składnik](bindingsource-component.md)
- [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Formatowanie danych w kontrolce DataGridView formularzy Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md)
- [Opcje ustalania rozmiaru w kontrolce DataGridView formularzy Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md)
- [Tryb sortowania kolumn w kontrolce DataGridView formularzy Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Tryby wyboru w kontrolce DataGridView formularzy Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md)
- [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](customizing-the-windows-forms-datagridview-control.md)
