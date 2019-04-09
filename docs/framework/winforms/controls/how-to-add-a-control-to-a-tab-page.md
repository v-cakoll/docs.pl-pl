---
title: 'Instrukcje: dodawanie kontrolki do karty'
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
ms.openlocfilehash: b42845ab996c0985fe6a48ac588e6d706905faac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195855"
---
# <a name="how-to-add-a-control-to-a-tab-page"></a>Instrukcje: dodawanie kontrolki do karty
Można używać formularzy Windows <xref:System.Windows.Forms.TabControl> Aby wyświetlić inne formanty w sposób zorganizowany. Poniższa procedura pokazuje, jak dodać przycisk do pierwszej karcie. Aby dowiedzieć się, jak dodawanie ikony etykieta części karty, zobacz [jak: Zmienianie wyglądu kontrolki TabControl formularzy Windows Forms](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).  
  
### <a name="to-add-a-control-programmatically"></a>Aby programowo dodać kontrolkę  
  
1.  Użyj <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> metoda zbiorze zwróconym przez <xref:System.Windows.Forms.Control.Controls%2A> właściwość <xref:System.Windows.Forms.TabPage>:  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](~/samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](~/samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [TabControl — Formant](tabcontrol-control-windows-forms.md)
- [TabControl, kontrolka — omówienie](tabcontrol-control-overview-windows-forms.md)
- [Instrukcje: zmienianie wyglądu składnika TabControl formularzy systemu Windows](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
- [Instrukcje: wyłączanie kart](how-to-disable-tab-pages.md)
- [Instrukcje: dodawanie i usuwanie kart za pomocą kontrolki TabControl formularzy systemu Windows](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
