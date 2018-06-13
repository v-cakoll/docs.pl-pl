---
title: Różnice między formantami DataGridView i DataGrid formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: d0a82d5724ebe142ae080fc930665733e701e237
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528716"
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Różnice między formantami DataGridView i DataGrid formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> Formant jest nowy formant, który zastępuje <xref:System.Windows.Forms.DataGrid> formantu. <xref:System.Windows.Forms.DataGridView> Kontrola zapewnia wiele podstawowych i zaawansowanych funkcji, które nie występują w <xref:System.Windows.Forms.DataGrid> formantu. Ponadto architektura <xref:System.Windows.Forms.DataGridView> kontroli ułatwia rozszerzyć i dostosować niż <xref:System.Windows.Forms.DataGrid> formantu.  
  
 W poniższej tabeli opisano niektóre główne funkcje dostępne w <xref:System.Windows.Forms.DataGridView> formant, który brakuje <xref:System.Windows.Forms.DataGrid> formantu.  
  
|Funkcja formantu DataGridView|Opis|  
|----------------------------------|-----------------|  
|Wiele typów kolumn|<xref:System.Windows.Forms.DataGridView> Formant zawiera więcej wbudowanych typów kolumn niż <xref:System.Windows.Forms.DataGrid> formantu. Te typy kolumn zaspokoić potrzeby najbardziej typowych scenariuszy, ale również są łatwiejsze do rozszerzać lub zastępować niż typy kolumn w <xref:System.Windows.Forms.DataGrid> formantu. Aby uzyskać więcej informacji, zobacz [typy kolumn w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md).|  
|Wiele sposobów, aby wyświetlić dane|<xref:System.Windows.Forms.DataGrid> Formantu jest ograniczona do wyświetlania danych z zewnętrznym źródłem danych. <xref:System.Windows.Forms.DataGridView> Kontroli, jednak można wyświetlić niepowiązane dane przechowywane w formantu, dane ze źródła danych powiązania lub danych związanych i niezwiązanych ze sobą. Można też wdrożyć tryb wirtualny w <xref:System.Windows.Forms.DataGridView> formantu, aby zapewnić zarządzanie danych niestandardowych. Aby uzyskać więcej informacji, zobacz [tryby wyświetlania danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md).|  
|Wiele sposobów, aby dostosować wyświetlanie danych|<xref:System.Windows.Forms.DataGridView> Formant zawiera wiele właściwości i zdarzenia, które można określić sposób sformatowany i wyświetlania danych. Na przykład można zmienić wygląd komórek, wierszy i kolumn w zależności od danych, które zawierają lub danych jednego typu danych można zastąpić równoważnym danych innego typu. Aby uzyskać więcej informacji, zobacz [formatowania danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md).|  
|Wiele opcji zmiany komórek, wierszy, kolumny i nagłówek wygląd i działanie|<xref:System.Windows.Forms.DataGridView> Kontroli umożliwia pracę z siatki poszczególnych składników na wiele sposobów. Na przykład można zablokować wierszy i kolumn, aby zapobiec przewijania; Ukryj wiersze, kolumny i nagłówki; Zmiana rozmiarów wierszy, kolumny i nagłówek są dostosowane; Zmiana sposobu użytkowników wybierz odpowiednie opcje; i podaj etykietki narzędzi i menu skrótów do pojedynczych komórek, wierszy i kolumn.|  
  
 <xref:System.Windows.Forms.DataGrid> Sterowania są przechowywane dla zgodności z poprzednimi wersjami i specjalnymi potrzebami. Do niemal wszystkich celów, należy użyć <xref:System.Windows.Forms.DataGridView> formantu. Tylko funkcja, która jest dostępna w <xref:System.Windows.Forms.DataGrid> formant, który nie jest dostępna w <xref:System.Windows.Forms.DataGridView> formant jest hierarchiczną informacji z powiązanych tabel w jeden formant. Należy użyć dwóch <xref:System.Windows.Forms.DataGridView> służy do wyświetlania informacji z dwóch tabel, które znajdują się w relacji wzorzec/szczegół.  
  
## <a name="upgrading-to-the-datagridview-control"></a>Uaktualnianie do formantu DataGridView  
 Jeśli masz istniejące aplikacje, które używają <xref:System.Windows.Forms.DataGrid> kontroli w prosty scenariusz powiązane z danymi bez dostosowań, można po prostu zastąpić starego formantu nowego formantu. Oba formanty Użyj Standardowa Architektura powiązanie danych formularzy systemu Windows, więc <xref:System.Windows.Forms.DataGridView> kontrolka będzie wyświetlać dane powiązane z potrzeba dodatkowej konfiguracji. Możesz chcieć należy rozważyć skorzystanie z ulepszenia wiązania danych, jednak przez powiązanie danych w celu <xref:System.Windows.Forms.BindingSource> składnik, który można następnie powiązać <xref:System.Windows.Forms.DataGridView> formantu. Aby uzyskać więcej informacji, zobacz [BindingSource — składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md).  
  
 Ponieważ <xref:System.Windows.Forms.DataGridView> formant ma całkowicie nowa architektura, jest nie ma ścieżki konwersji prostego, umożliwiający użyj <xref:System.Windows.Forms.DataGrid> dostosowań z <xref:System.Windows.Forms.DataGridView> formantu. Wiele <xref:System.Windows.Forms.DataGrid> dostosowań są zbędne z <xref:System.Windows.Forms.DataGridView> kontrolować, jednak z powodu wbudowane funkcje dostępne w nowej kontrolki. Jeśli utworzono typy kolumn niestandardowych dla <xref:System.Windows.Forms.DataGrid> formant, który ma być używany z <xref:System.Windows.Forms.DataGridView> kontroli, konieczne będzie ich ponownie, używając Nowa architektura wdrażania. Aby uzyskać więcej informacji, zobacz [Dostosowywanie formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGrid>  
 <xref:System.Windows.Forms.BindingSource>  
 [DataGridView, kontrolka](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [DataGrid, kontrolka](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [BindingSource, składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 [Style komórki w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)  
 [Formatowanie danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)  
 [Opcje ustalania rozmiaru w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 [Tryb sortowania kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [Tryby wyboru w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)  
 [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
