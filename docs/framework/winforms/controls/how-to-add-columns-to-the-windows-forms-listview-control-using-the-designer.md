---
title: 'Instrukcje: dodawanie kolumn do kontrolki ListView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: 10963fcb6d87ed74f73ecf4f1831a56eae5a392d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658457"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>Instrukcje: dodawanie kolumn do kontrolki ListView formularzy systemu Windows przy użyciu narzędzia Projektant

Kontrolka <xref:System.Windows.Forms.ListView> Windows Forms może wyświetlać wiele kolumn dla każdego elementu listy w widoku **szczegółów** . Możesz użyć kolumn, aby wyświetlić kilka typów informacji dotyczących każdego elementu listy. Na przykład lista plików może zawierać nazwę pliku, typ pliku, rozmiar i datę ostatniej modyfikacji pliku. Aby uzyskać informacje na temat wypełniania kolumn po ich utworzeniu [, zobacz How to: Wyświetlaj elementy SubItems w kolumnach za pomocą](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)kontrolki ListView Windows Forms.

Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.ListView> kontrolkę. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-add-columns-in-the-designer"></a>Aby dodać kolumny w projektancie

1. W oknie **Właściwości** Ustaw <xref:System.Windows.Forms.ListView.View%2A> właściwość kontrolki na <xref:System.Windows.Forms.View.Details>.

2. W oknie **Właściwości** kliknij przycisk wielokropka ( ![przycisk wielokropka (...) w okno właściwości programu Visual <xref:System.Windows.Forms.ListView.Columns%2A> Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości.

     Zostanie wyświetlony **Edytor kolekcji ColumnHeader** .

3. Użyj przycisku **Dodaj** , aby dodać nowe kolumny. Następnie można wybrać nagłówek kolumny i ustawić jego tekst (podpis kolumny), wyrównanie tekstu i szerokość.

## <a name="see-also"></a>Zobacz także

- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
- [Instrukcje: Dodawanie i usuwanie elementów za pomocą kontrolki ListView Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Instrukcje: Wyświetlanie elementów SubItems w kolumnach za pomocą kontrolki ListView Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Instrukcje: Wyświetl ikony dla kontrolki ListView Windows Forms](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Instrukcje: Dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
