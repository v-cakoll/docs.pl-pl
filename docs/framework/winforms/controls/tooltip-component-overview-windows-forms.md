---
title: ToolTip — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
ms.openlocfilehash: 3fbe883501d1ce36ca25ea07631f98042f451e07
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197311"
---
# <a name="tooltip-component-overview-windows-forms"></a>ToolTip — Informacje o składniku (Formularze systemu Windows)
Formularze Windows <xref:System.Windows.Forms.ToolTip> składnika wyświetla tekst, gdy użytkownik wskaże na kontrolki. Etykietka narzędzia może być skojarzona z dowolną kontrolkę. Przykładowe zastosowanie tego składnika: Aby zaoszczędzić miejsce na formularzu, mała ikona jest wyświetlana na przycisku i służyć etykietka narzędzia w celu wyjaśnienia przycisku — funkcja.  
  
## <a name="working-with-the-tooltip-component"></a>Praca z ToolTip, składnik  
 A <xref:System.Windows.Forms.ToolTip> składnik udostępnia `ToolTip` właściwości wielu formantów w formularzu Windows lub innego kontenera. Na przykład możesz umieścić jedną <xref:System.Windows.Forms.ToolTip> składnika w formularzu można wyświetlić "Wpisz tutaj nazwę" <xref:System.Windows.Forms.TextBox> kontroli i "Kliknij tutaj, aby zapisać zmiany" Aby <xref:System.Windows.Forms.Button> kontroli.  
  
 Metody klucza <xref:System.Windows.Forms.ToolTip> składnik to <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> i <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>. Możesz użyć <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metodę, aby ustawienie elementu ToolTips dla formantów. Aby uzyskać więcej informacji, zobacz [jak: Ustawienie elementu ToolTips dla formantów w formularzu Windows w czasie projektowania](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md). Właściwości klucza są <xref:System.Windows.Forms.ToolTip.Active%2A>, musi być ustawione na `true` dla etykietki narzędzi pojawia się i <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, która ustawia dla długości czasu, który jest wyświetlany ciąg etykietki narzędzi, jak długo użytkownik musi wskazywać na kontroli dla etykietka narzędzia, która pojawia się i jak go długie pobiera dla kolejnych etykietki narzędzi systemu windows są wyświetlane. Aby uzyskać więcej informacji, zobacz [jak: Zmienianie opóźnienia składnika ToolTip formularzy Windows](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolTip>
- [Instrukcje: ustawienie elementu ToolTips dla kontrolek w formularzu systemu Windows w czasie projektowania](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [Instrukcje: zmienianie opóźnienia składnika ToolTip formularzy systemu Windows](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
