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
ms.openlocfilehash: 9806583fda60f1cb8a5ef2d97f42eba158593f61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011232"
---
# <a name="how-to-add-a-control-to-a-tab-page"></a>Instrukcje: dodawanie kontrolki do karty
Można używać formularzy Windows <xref:System.Windows.Forms.TabControl> Aby wyświetlić inne formanty w sposób zorganizowany. Poniższa procedura pokazuje, jak dodać przycisk do pierwszej karcie. Aby dowiedzieć się, jak dodawanie ikony etykieta części karty, zobacz [jak: Zmienianie wyglądu kontrolki TabControl formularzy Windows Forms](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).  
  
### <a name="to-add-a-control-programmatically"></a>Aby programowo dodać kontrolkę  
  
1. Użyj <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> metoda zbiorze zwróconym przez <xref:System.Windows.Forms.Control.Controls%2A> właściwość <xref:System.Windows.Forms.TabPage>:  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](~/samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](~/samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [TabControl, kontrolka](tabcontrol-control-windows-forms.md)
- [TabControl, kontrolka — omówienie](tabcontrol-control-overview-windows-forms.md)
- [Instrukcje: Zmienianie wyglądu kontrolki TabControl formularzy Windows Forms](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
- [Instrukcje: Wyłączanie kart](how-to-disable-tab-pages.md)
- [Instrukcje: Dodawanie i usuwanie kart za pomocą kontrolki TabControl formularzy Windows Forms](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
