---
title: TreeView, kontrolka — omówienie
ms.date: 03/30/2017
f1_keywords:
- TreeView
helpviewer_keywords:
- TreeView control [Windows Forms], about TreeView control
ms.assetid: 0ece823a-9508-478a-bbdb-7d7c3bae51d5
ms.openlocfilehash: 44b5e27273d122f38ea00e009302d427305977a3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743222"
---
# <a name="treeview-control-overview-windows-forms"></a>TreeView — Informacje o formancie [Formularze systemu Windows]

Za pomocą kontrolki <xref:System.Windows.Forms.TreeView> Windows Forms można wyświetlić hierarchię węzłów dla użytkowników, podobnie jak pliki i foldery są wyświetlane w lewym okienku funkcji Eksploratora Windows w systemie operacyjnym Windows. Każdy węzeł w widoku drzewa może zawierać inne węzły zwane *węzłami podrzędnymi*. Można wyświetlić węzły nadrzędne lub węzły, które zawierają węzły podrzędne, jako rozwinięte lub zwinięte. Możesz również wyświetlić widok drzewa z polami wyboru obok węzłów, ustawiając właściwość <xref:System.Windows.Forms.TreeView.CheckBoxes%2A> widoku drzewa na `true`. Następnie można programowo zaznaczyć lub wyczyścić węzły przez ustawienie właściwości <xref:System.Windows.Forms.TreeNode.Checked%2A> węzła na `true` lub `false`.

## <a name="key-properties"></a>Właściwości klucza

Właściwości klucza kontrolki <xref:System.Windows.Forms.TreeView> są <xref:System.Windows.Forms.TreeView.Nodes%2A> i <xref:System.Windows.Forms.TreeView.SelectedNode%2A>. Właściwość <xref:System.Windows.Forms.TreeView.Nodes%2A> zawiera listę węzłów najwyższego poziomu w widoku drzewa. Właściwość <xref:System.Windows.Forms.TreeView.SelectedNode%2A> ustawia aktualnie wybrany węzeł. Możesz wyświetlić ikony obok węzłów. Kontrolka używa obrazów z <xref:System.Windows.Forms.ImageList> o nazwie we właściwości <xref:System.Windows.Forms.TreeView.ImageList%2A> widoku drzewa. Właściwość <xref:System.Windows.Forms.TreeView.ImageIndex%2A> ustawia domyślny obraz dla węzłów w widoku drzewa. Aby uzyskać więcej informacji na temat wyświetlania obrazów, zobacz [How to: Set Ikons for the Windows Forms TreeView](how-to-set-icons-for-the-windows-forms-treeview-control.md). W przypadku korzystania z programu Visual Studio 2005 masz dostęp do dużej biblioteki standardowych obrazów, których można użyć z kontrolką <xref:System.Windows.Forms.TreeView>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.TreeView>
- [TreeView, kontrolka](treeview-control-windows-forms.md)
- [Instrukcje: ustawienie ikon dla kontrolki TreeView formularzy Windows Forms](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Instrukcje: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy Windows Forms](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Instrukcje: iterowanie po wszystkich węzłach kontrolki TreeView formularzy Windows Forms](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Instrukcje: określanie, który węzeł TreeView został kliknięty](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
