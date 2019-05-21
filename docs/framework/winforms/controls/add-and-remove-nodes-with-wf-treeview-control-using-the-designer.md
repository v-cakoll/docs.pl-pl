---
title: 'Instrukcje: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: 71ada3235343aa7e014e12ebf5b367ec744b00d3
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959658"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>Instrukcje: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy systemu Windows przy użyciu narzędzia Projektant

Ponieważ formularzy Windows Forms <xref:System.Windows.Forms.TreeView> kontrolka Wyświetla węzły w hierarchiczny sposób, podczas dodawania węzła należy zwrócić uwagę na to swojego węzła nadrzędnego.

Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą zawierający formularz <xref:System.Windows.Forms.TreeView> kontroli. Aby uzyskać informacje o konfigurowaniu taki projekt, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md).

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-add-or-remove-nodes-in-the-designer"></a>Aby dodać lub usunąć węzły w Projektancie

1. Wybierz <xref:System.Windows.Forms.TreeView> kontroli.

2. W **właściwości** okna, kliknij przycisk **wielokropka** (![przycisk wielokropka (...) w oknie dialogowym właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) znajdujący się obok <xref:System.Windows.Forms.TreeView.Nodes%2A> właściwości .

     **TreeNode Editor** pojawia się.

3. Aby dodać węzły, węzeł główny musi istnieć; Jeśli nie istnieje, należy najpierw dodać katalog główny, klikając **Dodawanie głównego** przycisku. Następnie można dodać węzły podrzędne, wybierając głównego lub dowolnego innego węzła i klikając **Dodaj element podrzędny** przycisku.

4. Aby usunąć węzły, wybierz węzeł, aby usunąć, a następnie kliknij przycisk **Usuń** przycisku.

## <a name="see-also"></a>Zobacz także

- [TreeView, kontrolka](treeview-control-windows-forms.md)
- [TreeView, kontrolka — omówienie](treeview-control-overview-windows-forms.md)
- [Instrukcje: Ustawienie ikon dla kontrolki TreeView formularzy Windows](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Instrukcje: Iterowanie wszystkich węzłów kontrolki TreeView formularzy Windows](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Instrukcje: Określanie, który węzeł TreeView został kliknięty](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Instrukcje: Dodawanie niestandardowych informacji do TreeView lub ListView — formant (formularze Windows)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
