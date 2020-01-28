---
title: Dodawanie i usuwanie węzłów z kontrolką TreeView przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: 7edf09539719ec76fa3f650254c5c84ff0bc3af7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732250"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>Porady: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy systemu Windows przy użyciu narzędzia Projektant

Ponieważ kontrolka <xref:System.Windows.Forms.TreeView> Windows Forms wyświetla węzły w sposób hierarchiczny, podczas dodawania węzła należy zwrócić uwagę na to, co jego węzeł nadrzędny.

Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.TreeView>. Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-add-or-remove-nodes-in-the-designer"></a>Aby dodać lub usunąć węzły w projektancie

1. Wybierz kontrolkę <xref:System.Windows.Forms.TreeView>.

2. W oknie **Właściwości** kliknij przycisk **wielokropka** (![przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości <xref:System.Windows.Forms.TreeView.Nodes%2A>.

     Zostanie wyświetlony **Edytor TreeNode** .

3. Aby dodać węzły, musi istnieć węzeł główny; Jeśli jeszcze nie istnieje, należy najpierw dodać katalog główny, klikając przycisk **Dodaj element główny** . Następnie można dodać węzły podrzędne, wybierając główny lub inny węzeł i klikając przycisk **Dodaj element podrzędny** .

4. Aby usunąć węzły, wybierz węzeł, który chcesz usunąć, a następnie kliknij przycisk **Usuń** .

## <a name="see-also"></a>Zobacz także

- [TreeView, kontrolka](treeview-control-windows-forms.md)
- [TreeView, kontrolka — omówienie](treeview-control-overview-windows-forms.md)
- [Instrukcje: ustawienie ikon dla kontrolki TreeView formularzy Windows Forms](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Instrukcje: iterowanie po wszystkich węzłach kontrolki TreeView formularzy Windows Forms](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Instrukcje: określanie, który węzeł TreeView został kliknięty](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
