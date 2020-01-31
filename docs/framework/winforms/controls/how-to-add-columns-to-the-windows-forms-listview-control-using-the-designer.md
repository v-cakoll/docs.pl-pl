---
title: Dodawanie kolumn do formantu ListView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: 627f8627aac861877a05c13def07427199807754
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744606"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>Porady: dodawanie kolumn do formantu ListView formularzy systemu Windows przy użyciu narzędzia Projektant

Kontrolka <xref:System.Windows.Forms.ListView> Windows Forms może wyświetlać wiele kolumn dla każdego elementu listy w widoku **szczegółów** . Możesz użyć kolumn, aby wyświetlić kilka typów informacji dotyczących każdego elementu listy. Na przykład lista plików może zawierać nazwę pliku, typ pliku, rozmiar i datę ostatniej modyfikacji pliku. Aby uzyskać informacje na temat wypełniania kolumn po ich utworzeniu, zobacz [How to: Display SubItems in Columns with Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).

Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.ListView>. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-add-columns-in-the-designer"></a>Aby dodać kolumny w projektancie

1. W oknie **Właściwości** ustaw właściwość <xref:System.Windows.Forms.ListView.View%2A> kontrolki na <xref:System.Windows.Forms.View.Details>.

2. W oknie **Właściwości** kliknij przycisk **wielokropka** (![przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości <xref:System.Windows.Forms.ListView.Columns%2A>.

     Zostanie wyświetlony **Edytor kolekcji ColumnHeader** .

3. Użyj przycisku **Dodaj** , aby dodać nowe kolumny. Następnie można wybrać nagłówek kolumny i ustawić jego tekst (podpis kolumny), wyrównanie tekstu i szerokość.

## <a name="see-also"></a>Zobacz także

- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
- [Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Instrukcje: wyświetlanie podelementów w kolumnach za pomocą kontrolki ListView formularzy Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Instrukcje: wyświetlanie ikon dla kontrolki ListView formularzy Windows Forms](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
