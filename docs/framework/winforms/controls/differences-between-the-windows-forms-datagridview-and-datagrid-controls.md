---
title: Różnice między formantami DataGridView i DataGrid formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: 02c909436bccb2af99288e522155b3f479ae782f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687725"
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Różnice między formantami DataGridView i DataGrid formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> Formant jest nowy formant, który zastępuje <xref:System.Windows.Forms.DataGrid> kontroli. <xref:System.Windows.Forms.DataGridView> Control oferuje wiele podstawowych i zaawansowanych funkcji, których brakuje w <xref:System.Windows.Forms.DataGrid> kontroli. Ponadto architektura <xref:System.Windows.Forms.DataGridView> kontroli ułatwia znacznie rozszerzyć i dostosowywać niż <xref:System.Windows.Forms.DataGrid> kontroli.  
  
 W poniższej tabeli opisano niektóre z podstawowych funkcji dostępnych w <xref:System.Windows.Forms.DataGridView> kontrolki, które są nieobecne <xref:System.Windows.Forms.DataGrid> kontroli.  
  
|Funkcja formantu DataGridView|Opis|  
|----------------------------------|-----------------|  
|Wiele typów kolumn|<xref:System.Windows.Forms.DataGridView> Control oferuje więcej wbudowanych typów kolumn niż <xref:System.Windows.Forms.DataGrid> kontroli. Te typy kolumn zaspokoić potrzeby najbardziej typowych scenariuszy, ale mogą również pozwalać na łatwiejsze rozszerzać lub zastępować niż typy kolumn w <xref:System.Windows.Forms.DataGrid> kontroli. Aby uzyskać więcej informacji, zobacz [typy kolumn w formancie DataGridView formularzy Windows](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md).|  
|Wiele sposobów, aby wyświetlić dane|<xref:System.Windows.Forms.DataGrid> Kontroli jest ograniczona do wyświetlania danych z zewnętrznego źródła danych. <xref:System.Windows.Forms.DataGridView> Formant, jednak może wyświetlać niepowiązane dane przechowywane w formantu, dane ze źródła powiązanych danych lub danych związanych i niezwiązanych ze sobą. Możesz również wdrożyć trybu wirtualnego w <xref:System.Windows.Forms.DataGridView> kontroli do zapewnienia zarządzania danych niestandardowych. Aby uzyskać więcej informacji, zobacz [tryby wyświetlania danych w formancie DataGridView formularzy Windows](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md).|  
|Wiele sposobów, aby dostosować wyświetlanie danych|<xref:System.Windows.Forms.DataGridView> Control oferuje wiele właściwości i zdarzenia, które umożliwiają określenie, jak sformatowane i wyświetlane dane. Na przykład można zmienić wygląd komórek, wierszy i kolumn, w zależności od danych, które zawierają lub danych jednego typu danych można zastąpić równoważnym danych innego typu. Aby uzyskać więcej informacji, zobacz [formatowanie danych w formancie DataGridView formularzy Windows](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md).|  
|Wiele opcji zmieniania komórek, wierszy, kolumny i nagłówek wygląd i zachowanie|<xref:System.Windows.Forms.DataGridView> Kontrolki pozwala użytkownikowi pracować ze składnikami siatkę poszczególnych na wiele różnych sposobów. Na przykład można zablokować wierszy i kolumn, aby uniemożliwić przewijania; Ukryj wiersze, kolumny i nagłówki; Zmiana rozmiarów wierszy, kolumny i nagłówek są dostosowywane; Zmień sposób, w jaki użytkownicy dokonanie wyboru; i podaj etykietki narzędzi i menu skrótów dla poszczególnych komórek, wierszy i kolumn.|  
  
 <xref:System.Windows.Forms.DataGrid> Kontroli zachowano dla zgodności z poprzednimi wersjami i specjalnymi potrzebami. Dla prawie wszystkich celów, należy użyć <xref:System.Windows.Forms.DataGridView> kontroli. Tylko funkcja, która jest dostępna w <xref:System.Windows.Forms.DataGrid> formant, który nie jest dostępna w <xref:System.Windows.Forms.DataGridView> formant jest hierarchiczną informacji z powiązanych tabel w jednym formancie. Należy użyć dwóch <xref:System.Windows.Forms.DataGridView> formantów do wyświetlania informacji z dwóch tabel, które znajdują się w relacji wzorzec/szczegół.  
  
## <a name="upgrading-to-the-datagridview-control"></a>Uaktualnianie do formantu DataGridView  
 Jeśli masz istniejące aplikacje, które używają <xref:System.Windows.Forms.DataGrid> kontroli w prostym scenariuszu powiązanych z danymi bez dostosowań, można po prostu zastąpić stary kontroli nowego formantu. Obie kontrolki używają standardowych architektury powiązanie danych formularzy Windows, więc <xref:System.Windows.Forms.DataGridView> kontrolka będzie wyświetlać dane powiązane z nie wykonywania dodatkowych czynności konfiguracyjnych. Należy wziąć pod uwagę wykorzystanie ulepszenia wiązania danych, jednak przez powiązanie danych w celu <xref:System.Windows.Forms.BindingSource> składnik, który można następnie powiązać <xref:System.Windows.Forms.DataGridView> kontroli. Aby uzyskać więcej informacji, zobacz [BindingSource, składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md).  
  
 Ponieważ <xref:System.Windows.Forms.DataGridView> kontrolkę całkowicie nową architekturę, nie ma prostego konwersji ścieżki umożliwiających przy użyciu <xref:System.Windows.Forms.DataGrid> dostosowania przy użyciu <xref:System.Windows.Forms.DataGridView> kontroli. Wiele <xref:System.Windows.Forms.DataGrid> dostosowania są zbędne z <xref:System.Windows.Forms.DataGridView> kontrolować, jednak z powodu wbudowane funkcje dostępne w nowej kontrolki. Jeśli utworzono typy kolumn niestandardowych do <xref:System.Windows.Forms.DataGrid> formant, który chcesz użyć z <xref:System.Windows.Forms.DataGridView> kontrolki, trzeba będzie wdrożyć je ponownie, używając nowej architektury. Aby uzyskać więcej informacji, zobacz [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView, kontrolka](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
- [DataGrid, kontrolka](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
- [BindingSource, składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md)
- [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
- [Style komórki w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)
- [Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Formatowanie danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)
- [Opcje ustalania rozmiaru w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)
- [Tryb sortowania kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Tryby wyboru w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)
- [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
