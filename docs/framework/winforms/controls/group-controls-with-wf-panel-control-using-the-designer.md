---
title: 'Instrukcje: grupowanie kontrolek z kontrolką panelu formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: cadfa715b140c63b216ec0ca2e6d6a6589ae3458
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040384"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>Instrukcje: grupowanie kontrolek z kontrolką panelu formularzy systemu Windows przy użyciu narzędzia Projektant
Kontrolki Windows Forms <xref:System.Windows.Forms.Panel> są używane do grupowania innych kontrolek. Istnieją trzy powody, dla których należy grupować formanty. Jednym z nich jest wizualne grupowanie elementów formularza dla czystego interfejsu użytkownika; innym jest programistyczne Grupowanie przycisków radiowych na przykład; ostatnim jest do przesuwania kontrolek jako jednostki w czasie projektowania.

## <a name="to-create-a-group-of-controls"></a>Aby utworzyć grupę kontrolek

1. Przeciągnij kontrolkę z karty Windows Forms przybornika na formularz. <xref:System.Windows.Forms.Panel>

2. Dodaj inne kontrolki do panelu, rysując każdy wewnątrz panelu.

     Jeśli masz istniejące kontrolki, które chcesz umieścić w panelu, możesz zaznaczyć wszystkie kontrolki, wyciąć je do schowka, zaznaczyć <xref:System.Windows.Forms.Panel> kontrolkę, a następnie wkleić je do panelu. Możesz również przeciągnąć je do panelu.

3. Obowiązkowe Jeśli chcesz dodać obramowanie do panelu, ustaw jego <xref:System.Windows.Forms.BorderStyle> właściwość. Dostępne są trzy opcje: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>i <xref:System.Windows.Forms.BorderStyle.None>.

## <a name="see-also"></a>Zobacz także

- [Panel, kontrolka](panel-control-windows-forms.md)
- [Panel, kontrolka — omówienie](panel-control-overview-windows-forms.md)
- [Instrukcje: Ustawianie tła panelu](how-to-set-the-background-of-a-windows-forms-panel.md)
