---
title: 'Instrukcje: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: ef3a963b5621f0b972b02a007681f600fbdb1050
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "69040075"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>Instrukcje: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy systemu Windows przy użyciu narzędzia Projektant

Ponieważ kontrolka <xref:System.Windows.Forms.TreeView> Windows Forms wyświetla węzły w sposób hierarchiczny, podczas dodawania węzła należy zwrócić uwagę na to, co jego węzeł nadrzędny.

Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.TreeView> kontrolkę. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-add-or-remove-nodes-in-the-designer"></a>Aby dodać lub usunąć węzły w projektancie

1. <xref:System.Windows.Forms.TreeView> Zaznacz kontrolkę.

2. W oknie **Właściwości** kliknij przycisk **wielokropka** (![przycisk wielokropka (...) w okno właściwości programu Visual Studio <xref:System.Windows.Forms.TreeView.Nodes%2A> .](./media/visual-studio-ellipsis-button.png)) obok właściwości.

     Zostanie wyświetlony **Edytor TreeNode** .

3. Aby dodać węzły, musi istnieć węzeł główny; Jeśli jeszcze nie istnieje, należy najpierw dodać katalog główny, klikając przycisk **Dodaj element główny** . Następnie można dodać węzły podrzędne, wybierając główny lub inny węzeł i klikając przycisk **Dodaj element podrzędny** .

4. Aby usunąć węzły, wybierz węzeł, który chcesz usunąć, a następnie kliknij przycisk **Usuń** .

## <a name="see-also"></a>Zobacz także

- [TreeView, kontrolka](treeview-control-windows-forms.md)
- [TreeView, kontrolka — omówienie](treeview-control-overview-windows-forms.md)
- [Instrukcje: Ustawianie ikon dla formantu Windows Forms TreeView](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Instrukcje: Wykonaj iterację wszystkich węzłów kontrolki Windows Forms TreeView](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Instrukcje: Określ, który węzeł TreeView został kliknięty](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Instrukcje: Dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
