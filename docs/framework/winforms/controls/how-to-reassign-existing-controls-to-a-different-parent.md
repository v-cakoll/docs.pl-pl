---
title: 'Instrukcje: ponowne przypisywanie istniejących kontrolek do innego elementu nadrzędnego'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
ms.openlocfilehash: a65b3c2b596a2d88ce4236aeadd86993bb268aa6
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039785"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a>Instrukcje: ponowne przypisywanie istniejących kontrolek do innego elementu nadrzędnego
Kontrolki, które istnieją w formularzu, można przypisać do nowej kontrolki kontenera.

## <a name="to-reassign-existing-controls-to-a-different-parent"></a>Aby ponownie przypisać istniejące kontrolki do innego elementu nadrzędnego

1. Przeciągnij trzy <xref:System.Windows.Forms.Button> kontrolki z **przybornika** na formularz.

     Umieść je blisko siebie, ale pozostaw nie wyrównane.

2. W **przyborniku**kliknij <xref:System.Windows.Forms.FlowLayoutPanel> ikonę kontrolki.

     Nie przeciągaj ikony na formularz.

3. Przesuń wskaźnik myszy blisko trzech <xref:System.Windows.Forms.Button> kontrolek.

     Wskaźnik zmieni się w krzyżyk z <xref:System.Windows.Forms.FlowLayoutPanel> dołączoną ikoną kontrolki.

4. Kliknij i przytrzymaj przycisk myszy.

5. Przeciągnij wskaźnik myszy, aby narysować kontur <xref:System.Windows.Forms.FlowLayoutPanel> formantu.

6. Narysuj kontur wokół trzech <xref:System.Windows.Forms.Button> kontrolek.

7. Zwolnij przycisk myszy.

     Trzy <xref:System.Windows.Forms.Button> kontrolki są teraz wstawiane <xref:System.Windows.Forms.FlowLayoutPanel> do kontrolki.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Rozmieszczanie kontrolek na formularzach Windows Forms](arranging-controls-on-windows-forms.md)
- [Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu linii wyrównania](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
