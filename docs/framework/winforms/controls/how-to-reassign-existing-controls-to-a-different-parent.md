---
title: 'Instrukcje: ponowne przypisywanie istniejących kontrolek do innego elementu nadrzędnego'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
ms.openlocfilehash: 2639322707c1c7e378f6d389a1dec80fd619841c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328221"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a>Instrukcje: ponowne przypisywanie istniejących kontrolek do innego elementu nadrzędnego
Możesz przypisać formantów, które istnieją w formularzu do nowej kontrolki kontenera.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-reassign-existing-controls-to-a-different-parent"></a>Ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego  
  
1. Przeciągnij trzy <xref:System.Windows.Forms.Button> kontrolki z **przybornika** na formularz.  
  
     Umieść je blisko siebie, ale pozostawić je niewyrównanych.  
  
2. W **przybornika**, kliknij przycisk <xref:System.Windows.Forms.FlowLayoutPanel> ikonę kontrolki.  
  
     Nie przeciągnij ikony na formularzu.  
  
3. Przesuń wskaźnik myszy w pobliżu trzy <xref:System.Windows.Forms.Button> kontrolki.  
  
     Wskaźnik zmienia się na krzyżyk z <xref:System.Windows.Forms.FlowLayoutPanel> ikonę kontrolki dołączone.  
  
4. Kliknij i przytrzymaj przycisk myszy.  
  
5. Przeciągnij kursor do rysowania konturu <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.  
  
6. Rysuj obramowania wokół trzech <xref:System.Windows.Forms.Button> kontrolki.  
  
7. Zwolnij przycisk myszy.  
  
     Trzy <xref:System.Windows.Forms.Button> formanty są wstawiane <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Rozmieszczanie formantów na formularzach systemu Windows](arranging-controls-on-windows-forms.md)
- [Przewodnik: rozmieszczanie kontrolek w aplikacji formularzy systemu Windows za pomocą TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Przewodnik: rozmieszczanie kontrolek w formularzach systemu Windows za pomocą linii przyciągania](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
