---
title: Grupowanie kontrolek z kontrolką grupy
description: Dowiedz się, jak grupować kontrolki za pomocą kontrolki grupy Windows Forms, aby można było utworzyć wizualną grupę powiązanych elementów.
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: f84c495a18f4ae5e04367f024a1e2849f1ed59f9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618067"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a>Porady: grupowanie formantów za pomocą formantu GroupBox formularzy systemu Windows
<xref:System.Windows.Forms.GroupBox>Kontrolki Windows Forms są używane do grupowania innych kontrolek. Istnieją trzy powody, dla których należy grupować kontrolki:  
  
- Aby utworzyć wizualne grupowanie elementów formularza pokrewnych dla czystego interfejsu użytkownika.  
  
- Aby utworzyć grupowanie programistyczne (na przykład przyciski radiowe).  
  
- Do przesuwania formantów jako jednostki w czasie projektowania.  
  
### <a name="to-create-a-group-of-controls"></a>Aby utworzyć grupę kontrolek  
  
1. Narysuj <xref:System.Windows.Forms.GroupBox> kontrolkę w formularzu.  
  
2. Dodaj inne kontrolki do pola Grupa, rysując każdy wewnątrz pola grupy.  
  
     Jeśli masz istniejące kontrolki, które chcesz umieścić w polu grupy, możesz zaznaczyć wszystkie kontrolki, wyciąć je do schowka, zaznaczyć <xref:System.Windows.Forms.GroupBox> kontrolkę, a następnie wkleić do pola Grupa. Możesz również przeciągnąć je do pola Grupa.  
  
3. Ustaw <xref:System.Windows.Forms.GroupBox.Text%2A> Właściwość pola grupy na odpowiedni podpis.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.GroupBox>
- [GroupBox, kontrolka](groupbox-control-windows-forms.md)
