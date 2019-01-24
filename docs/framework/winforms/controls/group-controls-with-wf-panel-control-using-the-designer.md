---
title: 'Instrukcje: Grupowanie formantów z formantem panelu formularzy Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 706a020bfb007250b9a1b708da25704aacd755e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601544"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>Instrukcje: Grupowanie formantów z formantem panelu formularzy Windows przy użyciu narzędzia Projektant
Windows Forms <xref:System.Windows.Forms.Panel> formantów służą do grupowania innych kontrolek. Istnieją trzy powody do grupy kontrolek. Jeden jest wizualne grupowanie elementów powiązanych formularza dla interfejsu użytkownika wyraźne; innym jest programowe grupowanie przycisków radiowych np. ostatni jest przenoszenie kontrolek jako jednostki w czasie projektowania.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-group-of-controls"></a>Aby utworzyć grupę kontrolek  
  
1.  Przeciągnij <xref:System.Windows.Forms.Panel> z kontrolować **Windows Forms** kartę przybornika do formularza.  
  
2.  Dodaj inne formanty do panelu, rysowania każdego wewnątrz panelu.  
  
     W przypadku istniejących formantów, które chcesz umieścić w panelu można zaznaczyć wszystkie kontrolki, Wytnij je do Schowka, zaznacz <xref:System.Windows.Forms.Panel> sterowania, a następnie wklej je do panelu. Można również przeciągnąć je do panelu.  
  
3.  (Opcjonalnie) Jeśli chcesz dodać obramowanie do panelu, ustaw jego <xref:System.Windows.Forms.BorderStyle> właściwości. Istnieją trzy opcje: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, i <xref:System.Windows.Forms.BorderStyle.None>.  
  
## <a name="see-also"></a>Zobacz także
- [Panel, kontrolka](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)
- [Panel, kontrolka — omówienie](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)
- [Instrukcje: Ustawianie tła panelu](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)
