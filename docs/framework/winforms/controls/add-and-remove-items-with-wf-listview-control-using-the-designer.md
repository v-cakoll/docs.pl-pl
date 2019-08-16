---
title: 'Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 62665746ea9fcd1553717b02b1f1349dc6415ab2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040086"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a>Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy systemu Windows przy użyciu narzędzia Projektant

Proces dodawania elementu do kontrolki Windows Forms <xref:System.Windows.Forms.ListView> składa się głównie z określania elementu i przypisywania do niego właściwości. Dodawanie lub usuwanie elementów listy można wykonać w dowolnym momencie.

Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.ListView> kontrolkę. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-add-or-remove-items-using-the-designer"></a>Aby dodać lub usunąć elementy przy użyciu narzędzia Projektant

1. <xref:System.Windows.Forms.ListView> Zaznacz kontrolkę.

2. W oknie **Właściwości** kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio <xref:System.Windows.Forms.ListView.Items%2A> .](./media/visual-studio-ellipsis-button.png)) obok właściwości.

     Zostanie wyświetlony **Edytor kolekcji ListViewItem** .

3. Aby dodać element, kliknij przycisk **Dodaj** . Następnie można ustawić właściwości nowego elementu, <xref:System.Windows.Forms.ListView.Text%2A> na przykład właściwości i. <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>

4. Aby usunąć element, zaznacz go i kliknij przycisk **Usuń** .

## <a name="see-also"></a>Zobacz także

- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
- [Instrukcje: Dodawanie kolumn do kontrolki ListView Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [Instrukcje: Wyświetlanie elementów SubItems w kolumnach za pomocą kontrolki ListView Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Instrukcje: Wyświetl ikony dla kontrolki ListView Windows Forms](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Instrukcje: Dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [Instrukcje: Grupuj elementy w Windows Forms formancie ListView](how-to-group-items-in-a-windows-forms-listview-control.md)
