---
title: 'Porady: ponowne przypisywanie istniejących formantów do innego elementu nadrzędnego'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1767fcff1742f4ad630b4b996c709b7ded53a129
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459197"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a>Instrukcje: ponowne przypisywanie istniejących kontrolek do innego elementu nadrzędnego

Kontrolki, które istnieją w formularzu, można przypisać do nowej kontrolki kontenera.

1. W programie Visual Studio przeciągnij trzy <xref:System.Windows.Forms.Button> kontrolki z **przybornika** na formularz. Umieść je blisko siebie, ale pozostaw nie wyrównane.

2. W **przyborniku**kliknij ikonę kontrolki <xref:System.Windows.Forms.FlowLayoutPanel>. (Nie przeciągaj ikony na formularz).

3. Przesuń wskaźnik myszy blisko trzech formantów <xref:System.Windows.Forms.Button>.

   Wskaźnik zmieni się na krzyżyk z dołączoną ikoną kontrolki <xref:System.Windows.Forms.FlowLayoutPanel>.

4. Kliknij i przytrzymaj przycisk myszy.

5. Przeciągnij wskaźnik myszy, aby narysować kontur kontrolki <xref:System.Windows.Forms.FlowLayoutPanel>.

6. Narysuj kontur wokół trzech formantów <xref:System.Windows.Forms.Button>.

7. Zwolnij przycisk myszy.

   Trzy kontrolki <xref:System.Windows.Forms.Button> są teraz wstawiane do kontrolki <xref:System.Windows.Forms.FlowLayoutPanel>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
