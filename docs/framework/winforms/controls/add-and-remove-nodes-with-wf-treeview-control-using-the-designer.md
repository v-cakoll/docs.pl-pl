---
title: 'Porady: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: 2bf62601ae2257a098be0dc5c2cf8b5b1ba2b618
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528207"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>Porady: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy systemu Windows przy użyciu narzędzia Projektant
Ponieważ formularzy systemu Windows <xref:System.Windows.Forms.TreeView> kontroli wyświetlane węzły w hierarchiczny sposób, dodając należy zwrócić uwagę na to jego węzeł nadrzędny węzła.  
  
 Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.TreeView> formantu. Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-or-remove-nodes-in-the-designer"></a>Aby dodać lub usunąć węzły w Projektancie  
  
1.  Wybierz <xref:System.Windows.Forms.TreeView> formantu.  
  
2.  W **właściwości** okna, kliknij przycisk **wielokropka** (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) znajdujący się obok <xref:System.Windows.Forms.TreeView.Nodes%2A> właściwości.  
  
     **Edytor TreeNode** pojawi się.  
  
3.  Aby dodać węzły, węzeł główny musi istnieć; Jeśli nie istnieje, należy najpierw dodać głównego, klikając **Dodawanie głównego** przycisku. Następnie można dodać węzłów podrzędnych Wybieranie katalogu głównego lub inny węzeł, a następnie klikając polecenie **Dodaj obiekt podrzędny** przycisku.  
  
4.  Aby usunąć węzłów, wybierz węzeł, aby usunąć, a następnie kliknij przycisk **usunąć** przycisku.  
  
## <a name="see-also"></a>Zobacz też  
 [TreeView, kontrolka](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [TreeView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [Instrukcje: ustawienie ikon dla kontrolki TreeView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [Instrukcje: iterowanie po wszystkich węzłach kontrolki TreeView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [Instrukcje: określanie, który węzeł TreeView został kliknięty](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
