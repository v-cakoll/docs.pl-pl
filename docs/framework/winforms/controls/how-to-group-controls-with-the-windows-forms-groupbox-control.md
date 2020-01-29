---
title: Grupowanie kontrolek z kontrolką grupy
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: bb7476c410d2802b5d32cc9842a778f290765e32
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736650"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a>Porady: grupowanie formantów za pomocą formantu GroupBox formularzy systemu Windows
Kontrolki <xref:System.Windows.Forms.GroupBox> Windows Forms są używane do grupowania innych kontrolek. Istnieją trzy powody, dla których należy grupować kontrolki:  
  
- Aby utworzyć wizualne grupowanie elementów formularza pokrewnych dla czystego interfejsu użytkownika.  
  
- Aby utworzyć grupowanie programistyczne (na przykład przyciski radiowe).  
  
- Do przesuwania formantów jako jednostki w czasie projektowania.  
  
### <a name="to-create-a-group-of-controls"></a>Aby utworzyć grupę kontrolek  
  
1. Narysuj kontrolkę <xref:System.Windows.Forms.GroupBox> w formularzu.  
  
2. Dodaj inne kontrolki do pola Grupa, rysując każdy wewnątrz pola grupy.  
  
     Jeśli masz istniejące kontrolki, które chcesz umieścić w polu grupy, możesz zaznaczyć wszystkie kontrolki, wyciąć je do schowka, wybrać kontrolkę <xref:System.Windows.Forms.GroupBox>, a następnie wkleić ją do pola Grupa. Możesz również przeciągnąć je do pola Grupa.  
  
3. Ustaw właściwość <xref:System.Windows.Forms.GroupBox.Text%2A> pola grupy na odpowiedni podpis.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.GroupBox>
- [GroupBox, kontrolka](groupbox-control-windows-forms.md)
