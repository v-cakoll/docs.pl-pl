---
title: TreeView — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- TreeView
helpviewer_keywords:
- TreeView control [Windows Forms], about TreeView control
ms.assetid: 0ece823a-9508-478a-bbdb-7d7c3bae51d5
ms.openlocfilehash: cc3fb394a2c55b7095a8111e7018b754985ab0e1
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48793594"
---
# <a name="treeview-control-overview-windows-forms"></a>TreeView — Informacje o formancie [Formularze systemu Windows]

Za pomocą interfejsu Windows Forms <xref:System.Windows.Forms.TreeView> kontrolki, można wyświetlić hierarchię węzłów do użytkowników, takie jak sposób pliki i foldery są wyświetlane w okienku po lewej stronie funkcji Eksploratora Windows, systemu operacyjnego Windows. Każdy węzeł w widoku drzewa może zawierać innych węzłów o nazwie *węzłów podrzędnych*. Można wyświetlić węzły nadrzędne lub węzły, które zawierają węzeł podrzędny jako rozwinięta czy zwinięta. Widok drzewa za pomocą pola wyboru obok węzłów można również wyświetlić, ustawiając w widoku drzewa <xref:System.Windows.Forms.TreeView.CheckBoxes%2A> właściwość `true`. Możesz następnie programowo zaznacz lub usuń zaznaczenie węzłów, ustawiając węzła <xref:System.Windows.Forms.TreeNode.Checked%2A> właściwości `true` lub `false`.

## <a name="key-properties"></a>Właściwości klucza

Właściwości klucza obiektu <xref:System.Windows.Forms.TreeView> sterowania stanowią <xref:System.Windows.Forms.TreeView.Nodes%2A> i <xref:System.Windows.Forms.TreeView.SelectedNode%2A>. <xref:System.Windows.Forms.TreeView.Nodes%2A> Właściwość zawiera listę węzłów najwyższego poziomu w widoku drzewa. <xref:System.Windows.Forms.TreeView.SelectedNode%2A> Właściwość ustawia aktualnie zaznaczonego węzła. Można wyświetlać ikony obok węzłów. Kontrolki przy użyciu obrazów z <xref:System.Windows.Forms.ImageList> o nazwie w widoku drzewa <xref:System.Windows.Forms.TreeView.ImageList%2A> właściwości. <xref:System.Windows.Forms.TreeView.ImageIndex%2A> Właściwość ustawia domyślny obraz dla węzłów w widoku drzewa. Aby uzyskać więcej informacji na temat wyświetlania obrazów, zobacz [porady: Ustawianie ikon dla kontrolki TreeView formularzy Windows](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md). Jeśli używasz programu Visual Studio 2005 jest dostępna z obszernej biblioteki standardowych obrazów, korzystających z <xref:System.Windows.Forms.TreeView> kontroli.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.TreeView>
- [TreeView, kontrolka](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
- [Instrukcje: ustawienie ikon dla kontrolki TreeView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Instrukcje: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Instrukcje: iterowanie po wszystkich węzłach kontrolki TreeView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Instrukcje: określanie, który węzeł TreeView został kliknięty](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)