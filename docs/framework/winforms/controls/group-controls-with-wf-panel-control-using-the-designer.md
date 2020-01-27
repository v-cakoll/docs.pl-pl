---
title: Grupowanie kontrolek z kontrolką panelu przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 927aeb5b51bc1ac4e22a45e487b49424b4e67b71
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745652"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>Porady: grupowanie formantów z formantem panelu formularzy systemu Windows przy użyciu narzędzia Projektant
Kontrolki <xref:System.Windows.Forms.Panel> Windows Forms są używane do grupowania innych kontrolek. Istnieją trzy powody, dla których należy grupować formanty. Jednym z nich jest wizualne grupowanie elementów formularza dla czystego interfejsu użytkownika; innym jest programistyczne Grupowanie przycisków radiowych na przykład; ostatnim jest do przesuwania kontrolek jako jednostki w czasie projektowania.

## <a name="to-create-a-group-of-controls"></a>Aby utworzyć grupę kontrolek

1. Przeciągnij kontrolkę <xref:System.Windows.Forms.Panel> z karty **Windows Forms** przybornika na formularz.

2. Dodaj inne kontrolki do panelu, rysując każdy wewnątrz panelu.

     Jeśli masz istniejące kontrolki, które chcesz umieścić w panelu, możesz zaznaczyć wszystkie kontrolki, wyciąć je do schowka, wybrać kontrolkę <xref:System.Windows.Forms.Panel>, a następnie wkleić ją do panelu. Możesz również przeciągnąć je do panelu.

3. Obowiązkowe Jeśli chcesz dodać obramowanie do panelu, ustaw jego właściwość <xref:System.Windows.Forms.BorderStyle>. Dostępne są trzy opcje: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>i <xref:System.Windows.Forms.BorderStyle.None>.

## <a name="see-also"></a>Zobacz także

- [Panel, kontrolka](panel-control-windows-forms.md)
- [Panel, kontrolka — omówienie](panel-control-overview-windows-forms.md)
- [Instrukcje: ustawianie tła panelu](how-to-set-the-background-of-a-windows-forms-panel.md)
