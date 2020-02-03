---
title: ToolTip, składnik — omówienie
ms.date: 03/30/2017
f1_keywords:
- ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
ms.openlocfilehash: 731f7ad0ce6670000d8c3d3e901e1506f7ef470a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741904"
---
# <a name="tooltip-component-overview-windows-forms"></a>ToolTip — Informacje o składniku (Formularze systemu Windows)
Składnik <xref:System.Windows.Forms.ToolTip> Windows Forms wyświetla tekst, gdy użytkownik wskazuje kontrolę. Etykietka narzędzia może być skojarzona z dowolną kontrolką. Przykład użycia tego składnika: aby zaoszczędzić miejsce na formularzu, można wyświetlić małą ikonę na przycisku i użyć etykietki narzędzia, aby wyjaśnić funkcję przycisku.  
  
## <a name="working-with-the-tooltip-component"></a>Praca ze składnikiem ToolTip  
 Składnik <xref:System.Windows.Forms.ToolTip> udostępnia Właściwość `ToolTip` do wielu kontrolek w formularzu systemu Windows lub w innym kontenerze. Jeśli na przykład umieścisz jeden składnik <xref:System.Windows.Forms.ToolTip> w formularzu, możesz wyświetlić "Wpisz tutaj swoją nazwę" dla kontrolki <xref:System.Windows.Forms.TextBox> i "kliknij tutaj, aby zapisać zmiany" dla kontrolki <xref:System.Windows.Forms.Button>.  
  
 Kluczowe metody składnika <xref:System.Windows.Forms.ToolTip> są <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> i <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>. Za pomocą metody <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> można ustawić etykietki narzędzi wyświetlane dla kontrolek. Aby uzyskać więcej informacji, zobacz [How to: Set etykietki narzędzi dla kontrolek w formularzu systemu Windows w czasie projektowania](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md). Właściwości klucza są <xref:System.Windows.Forms.ToolTip.Active%2A>, które muszą być ustawione na `true`, aby etykietka narzędzia była wyświetlana, i <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, która ustawia długość czasu wyświetlania ciągu etykietki narzędzia, jak długo użytkownik musi wskazywać w kontrolce etykietki narzędzia, która ma zostać wyświetlona, oraz czas, przez jaki będzie ona wyświetlana dla kolejnych okien etykietek narzędzi. Aby uzyskać więcej informacji, zobacz [How to: zmiana opóźnienia składnika ToolTip Windows Forms](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolTip>
- [Instrukcje: ustawienie elementu ToolTips dla kontrolek w formularzu systemu Windows w czasie projektowania](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [Instrukcje: zmienianie opóźnienia składnika ToolTip formularzy Windows Forms](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
