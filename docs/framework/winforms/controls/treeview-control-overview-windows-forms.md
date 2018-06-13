---
title: TreeView — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- TreeView
helpviewer_keywords:
- TreeView control [Windows Forms], about TreeView control
ms.assetid: 0ece823a-9508-478a-bbdb-7d7c3bae51d5
ms.openlocfilehash: 6326f8976e20b5b72e1b6690ab323c8581411156
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538631"
---
# <a name="treeview-control-overview-windows-forms"></a>TreeView — Informacje o formancie [Formularze systemu Windows]
Windows Forms <xref:System.Windows.Forms.TreeView> sterowania, można wyświetlić hierarchię węzłów do użytkowników, takich jak sposób pliki i foldery są wyświetlane w okienku po lewej stronie Eksploratora Windows funkcji systemu operacyjnego Windows. Każdy węzeł w widoku drzewa może zawierać innych węzłów, nazywany *węzłów podrzędnych*. Można wyświetlić węzłów nadrzędnych lub węzłów, które zawiera węzły podrzędne jako rozwinięte lub zwinięte. Widok drzewa o pola wyboru obok węzłów można także wyświetlić, ustawiając widok drzewa <xref:System.Windows.Forms.TreeView.CheckBoxes%2A> właściwości `true`. Można następnie programowo wybierz lub wyczyść pole wyboru węzłów przez ustawienie węzła <xref:System.Windows.Forms.TreeNode.Checked%2A> właściwości `true` lub `false`.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Właściwości klucza obiektu <xref:System.Windows.Forms.TreeView> sterowania stanowią <xref:System.Windows.Forms.TreeView.Nodes%2A> i <xref:System.Windows.Forms.TreeView.SelectedNode%2A>. <xref:System.Windows.Forms.TreeView.Nodes%2A> Właściwość zawiera listę węzły najwyższego poziomu w widoku drzewa. <xref:System.Windows.Forms.TreeView.SelectedNode%2A> Właściwość ustawia aktualnie zaznaczonego węzła. Może wyświetlać ikony obok węzłów. Formant przy użyciu obrazów z <xref:System.Windows.Forms.ImageList> o nazwie w widoku drzewa <xref:System.Windows.Forms.TreeView.ImageList%2A> właściwości. <xref:System.Windows.Forms.TreeView.ImageIndex%2A> Właściwość ustawia domyślnego obrazu dla węzłów w widoku drzewa. Aby uzyskać więcej informacji na temat wyświetlania obrazów, zobacz [porady: Ustawianie ikon dla formantu TreeView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md). Jeśli używasz [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], masz dostęp do dużych biblioteki standardowe obrazów, które można używać z <xref:System.Windows.Forms.TreeView> formantu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.TreeView>  
 [TreeView, kontrolka](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [Instrukcje: ustawienie ikon dla kontrolki TreeView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [Instrukcje: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [Instrukcje: iterowanie po wszystkich węzłach kontrolki TreeView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [Instrukcje: określanie, który węzeł TreeView został kliknięty](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
