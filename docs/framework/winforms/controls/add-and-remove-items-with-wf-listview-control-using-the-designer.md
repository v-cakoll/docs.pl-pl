---
title: Dodawanie i usuwanie elementów z kontrolką ListView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: cab40c556d9e5d21ce15bcd3d4da367bc08f33ab
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732300"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a>Porady: dodawanie i usuwanie elementów za pomocą formantu ListView formularzy systemu Windows przy użyciu narzędzia Projektant

Proces dodawania elementu do kontrolki <xref:System.Windows.Forms.ListView> Windows Forms składa się głównie z określania elementu i przypisywania do niego właściwości. Dodawanie lub usuwanie elementów listy można wykonać w dowolnym momencie.

Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.ListView>. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-add-or-remove-items-using-the-designer"></a>Aby dodać lub usunąć elementy przy użyciu narzędzia Projektant

1. Wybierz kontrolkę <xref:System.Windows.Forms.ListView>.

2. W oknie **Właściwości** kliknij przycisk **wielokropka** (![przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości <xref:System.Windows.Forms.ListView.Items%2A>.

     Zostanie wyświetlony **Edytor kolekcji ListViewItem** .

3. Aby dodać element, kliknij przycisk **Dodaj** . Następnie można ustawić właściwości nowego elementu, takie jak <xref:System.Windows.Forms.ListView.Text%2A> i <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> właściwości.

4. Aby usunąć element, zaznacz go i kliknij przycisk **Usuń** .

## <a name="see-also"></a>Zobacz także

- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
- [Instrukcje: dodawanie kolumn do kontrolki ListView formularzy Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Instrukcje: wyświetlanie podelementów w kolumnach za pomocą kontrolki ListView formularzy Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Instrukcje: wyświetlanie ikon dla kontrolki ListView formularzy Windows Forms](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Instrukcje: grupowanie elementów w kontrolce ListView formularzy Windows Forms](how-to-group-items-in-a-windows-forms-listview-control.md)
