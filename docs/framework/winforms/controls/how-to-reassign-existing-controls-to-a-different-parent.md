---
title: 'Instrukcje: Ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
ms.openlocfilehash: fa1bd6c0274fdf702072e062e6eeab7078375491
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600287"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a>Instrukcje: Ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego
Możesz przypisać formantów, które istnieją w formularzu do nowej kontrolki kontenera.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-reassign-existing-controls-to-a-different-parent"></a>Ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego  
  
1.  Przeciągnij trzy <xref:System.Windows.Forms.Button> kontrolki z **przybornika** na formularz.  
  
     Umieść je blisko siebie, ale pozostawić je niewyrównanych.  
  
2.  W **przybornika**, kliknij przycisk <xref:System.Windows.Forms.FlowLayoutPanel> ikonę kontrolki.  
  
     Nie przeciągnij ikony na formularzu.  
  
3.  Przesuń wskaźnik myszy w pobliżu trzy <xref:System.Windows.Forms.Button> kontrolki.  
  
     Wskaźnik zmienia się na krzyżyk z <xref:System.Windows.Forms.FlowLayoutPanel> ikonę kontrolki dołączone.  
  
4.  Kliknij i przytrzymaj przycisk myszy.  
  
5.  Przeciągnij kursor do rysowania konturu <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.  
  
6.  Rysuj obramowania wokół trzech <xref:System.Windows.Forms.Button> kontrolki.  
  
7.  Zwolnij przycisk myszy.  
  
     Trzy <xref:System.Windows.Forms.Button> formanty są wstawiane <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Rozmieszczanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
- [Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
