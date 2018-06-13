---
title: 'Porady: ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
ms.openlocfilehash: d174492e380130ad35fbc20693e18416c48a50f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533838"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a>Porady: ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego
Można przypisać formantów, które istnieją w formularzu nowego formantu kontenera.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-reassign-existing-controls-to-a-different-parent"></a>Ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego  
  
1.  Przeciągnij trzy <xref:System.Windows.Forms.Button> formantów **przybornika** na formularzu.  
  
     Umieść je się w pobliżu siebie, ale pozostaw je niewyrównany.  
  
2.  W **przybornika**, kliknij przycisk <xref:System.Windows.Forms.FlowLayoutPanel> ikona formantu.  
  
     Nie przeciągnij ikonę na formularzu.  
  
3.  Przenieś wskaźnik myszy w pobliżu trzech <xref:System.Windows.Forms.Button> kontrolki.  
  
     Wskaźnik zmieni się na krzyżyk z <xref:System.Windows.Forms.FlowLayoutPanel> ikona kontroli dołączony.  
  
4.  Kliknij i przytrzymaj przycisk myszy.  
  
5.  Przeciągnij wskaźnik myszy Rysowanie konturu <xref:System.Windows.Forms.FlowLayoutPanel> formantu.  
  
6.  Rysuj obramowania wokół trzech <xref:System.Windows.Forms.Button> kontrolki.  
  
7.  Zwolnij przycisk myszy.  
  
     Trzy <xref:System.Windows.Forms.Button> formanty zostaną wstawione do <xref:System.Windows.Forms.FlowLayoutPanel> formantu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Rozmieszczanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
