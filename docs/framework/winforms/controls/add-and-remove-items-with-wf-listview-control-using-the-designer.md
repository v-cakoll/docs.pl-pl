---
title: "Porady: dodawanie i usuwanie elementów za pomocą formantu ListView formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 89665e5b4076c8746fbca939fd3f5491b03afd28
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a>Porady: dodawanie i usuwanie elementów za pomocą formantu ListView formularzy systemu Windows przy użyciu narzędzia Projektant
Proces dodawania elementu do formularzy systemu Windows <xref:System.Windows.Forms.ListView> kontroli obejmuje głównie określenie elementu i przypisywanie właściwości. Dodawanie lub usuwanie elementów listy można zrobić w dowolnym momencie.  
  
 Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.ListView> formantu. Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-or-remove-items-using-the-designer"></a>Aby dodać lub usunąć elementy przy użyciu narzędzia Projektant  
  
1.  Wybierz <xref:System.Windows.Forms.ListView> formantu.  
  
2.  W **właściwości** okna, kliknij przycisk **wielokropka** (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) znajdujący się obok <xref:System.Windows.Forms.ListView.Items%2A> właściwości.  
  
     **Edytora kolekcji ListViewItem** pojawi się.  
  
3.  Aby dodać element, kliknij przycisk **Dodaj** przycisku. Następnie można ustawić właściwości nowy element, taki jak <xref:System.Windows.Forms.ListView.Text%2A> i <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> właściwości.  
  
4.  Aby usunąć element, zaznacz go i kliknij przycisk **Usuń** przycisku.  
  
## <a name="see-also"></a>Zobacz też  
 [ListView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Instrukcje: dodawanie kolumn do kontrolki ListView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [Instrukcje: wyświetlanie podelementów w kolumnach za pomocą kontrolki ListView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [Instrukcje: wyświetlanie ikon dla kontrolki ListView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [Instrukcje: grupowanie elementów w kontrolce ListView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)
