---
title: 'Porady: dodawanie formantu do karty'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TabPage control
- tab controls [Windows Forms], tab order
- tab pages [Windows Forms], adding controls
ms.assetid: b092532e-7346-469f-b9a1-897f9bea4fb7
ms.openlocfilehash: 1bb2233cf9e288ae89ebb8cab3df4f6451dc8eed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526699"
---
# <a name="how-to-add-a-control-to-a-tab-page"></a>Porady: dodawanie formantu do karty
Formularze systemu Windows można użyć <xref:System.Windows.Forms.TabControl> do wyświetlania innych kontrolek w sposób zorganizowany. Poniższa procedura przedstawia sposób Dodawanie przycisku do pierwszej karcie. Aby uzyskać informacji o dodawaniu ikony do etykiety część strony karty, zobacz [porady: Zmienianie wyglądu składnika TabControl formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).  
  
### <a name="to-add-a-control-programmatically"></a>Aby dodać kontrolkę programowo  
  
1.  Użyj <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> metody kolekcji zwróconej przez <xref:System.Windows.Forms.Control.Controls%2A> właściwości <xref:System.Windows.Forms.TabPage>:  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [TabControl, kontrolka](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [TabControl, kontrolka — omówienie](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [Instrukcje: zmienianie wyglądu kontrolki TabControl formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 [Instrukcje: wyłączanie kart](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [Instrukcje: dodawanie i usuwanie kart za pomocą kontrolki TabControl formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
