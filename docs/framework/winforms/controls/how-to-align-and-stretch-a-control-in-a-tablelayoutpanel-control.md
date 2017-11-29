---
title: "Porady: wyrównywanie i rozciąganie formantu w formancie TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 043adb68b88ab031cea3de1206d1f2c4252b75d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a>Porady: wyrównywanie i rozciąganie formantu w formancie TableLayoutPanel
Wyrównywanie i rozciąganie kontrolek w <xref:System.Windows.Forms.TableLayoutPanel> z <xref:System.Windows.Forms.Control.Anchor%2A> i <xref:System.Windows.Forms.Control.Dock%2A> właściwości.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-align-and-stretch-a-control"></a>Wyrównanie i rozciąganie formantu  
  
1.  Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> kontrolować z **przybornika** na formularzu.  
  
2.  Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** do lewej górnej komórki <xref:System.Windows.Forms.TableLayoutPanel> formantu. <xref:System.Windows.Forms.Button> Kontroli jest wyśrodkowywana w komórce.  
  
3.  Ustaw wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości `Left,Right`. <xref:System.Windows.Forms.Button> Kontrolować odcinkach odpowiadający szerokość komórki.  
  
4.  Ustaw wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości `Top,Bottom`. <xref:System.Windows.Forms.Button> Kontrolować odcinkach odpowiadający wysokość komórki.  
  
5.  Ustaw wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Button> Kontroli rozwijany do wypełnienia komórki.  
  
6.  Ustaw wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.None>. <xref:System.Windows.Forms.Button> Kontroli, przywracając jego oryginalny rozmiar i przechodzi do lewego górnego rogu komórki. **Projektant formularzy systemu Windows** ustawił <xref:System.Windows.Forms.Control.Anchor%2A> właściwości `Top, Left`.  
  
7.  Ustaw wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości `Bottom,Right`. <xref:System.Windows.Forms.Button> Formant przechodzi do prawego dolnego rogu komórki.  
  
8.  Ustaw wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości <xref:System.Windows.Forms.AnchorStyles.None>. <xref:System.Windows.Forms.Button> Formant przechodzi do Centrum komórki.  
  
## <a name="see-also"></a>Zobacz też  
 [TableLayoutPanel — formant](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
